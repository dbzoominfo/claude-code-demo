# Earnings Analysis — Agent Teams (Parallel Orchestrator)

This is the **parallel, multi-agent version** of `earnings-analysis`. It produces the same institutional-quality equity research earnings update report but uses a 4-tier agent team to complete the work 3–4x faster.

**Single-agent equivalent**: `earnings-analysis` skill  
**This skill**: `earnings-analysis-teams` — orchestrates 15 specialized agents across 4 parallel tiers

---

## Architecture Overview

```
Tier 0: YOU (Orchestrator) — parse input, dispatch agents, assemble report
  │
  ├── Tier 1 (PARALLEL — all 4 at once):
  │     press-release-collector | transcript-collector
  │     sec-filing-collector    | consensus-collector
  │
  ├── Tier 2 (PARALLEL — all 5 at once, after Tier 1 completes):
  │     beat-miss-analyst | segment-geo-analyst | margin-analyst
  │     guidance-analyst  | valuation-analyst
  │
  ├── Tier 3 (PARALLEL — all 5 at once, after Tier 2 completes):
  │     chart-generator | executive-summary-writer | results-writer
  │     thesis-risk-writer | valuation-writer
  │
  └── Tier 4 (after Tier 3 completes):
        qa-reviewer
```

Agent definition files are in `agents/`. The inter-agent data schema is in `references/data-schema.md`.

---

## Phase 0: Parse & Validate Input

Before dispatching any agents:

1. **Extract** ticker symbol and quarter from user input
2. **Normalize** quarter to standard format: `Q[1-4] FY[YEAR]` (e.g., `Q1 FY2026`)
3. **Determine** the company's fiscal calendar (Apple: Q1=Oct–Dec; calendar-year companies: Q1=Jan–Mar)
4. **Write** the current date explicitly and confirm the quarter being requested is within the last 3 months. If stale, warn the user and ask to confirm before proceeding.

---

## Phase 1: Dispatch Tier 1 — Data Collectors (ALL 4 IN PARALLEL)

**CRITICAL**: Launch all 4 collectors in a **single Agent tool call message** with 4 simultaneous `Agent` tool invocations. Do NOT launch them sequentially.

Read each agent definition from:
- `agents/tier1-press-release-collector.md`
- `agents/tier1-transcript-collector.md`
- `agents/tier1-sec-filing-collector.md`
- `agents/tier1-consensus-collector.md`

For each agent, construct its prompt by:
1. Taking the full content of its definition file
2. Appending the specific input at the bottom:
   ```
   --- INPUT ---
   Company: [Company Name]
   Ticker: [TICKER]
   Quarter: [Q# FY####]
   Quarter End Date: [YYYY-MM-DD]
   Report Date: [YYYY-MM-DD]
   Fiscal Calendar: [e.g., Apple fiscal year ends September]
   Today's Date: [YYYY-MM-DD]
   ```

Use `subagent_type: "general-purpose"` for all agents.

**Wait** for all 4 to complete, then merge their outputs into a single `raw_data` package per `references/data-schema.md`.

**Timeliness gate**: If any collector flags the earnings as older than 90 days, stop and inform the user before proceeding.

---

## Phase 2: Dispatch Tier 2 — Analysts (ALL 5 IN PARALLEL)

**CRITICAL**: Launch all 5 analysts in a **single Agent tool call message** simultaneously.

Read each agent definition from:
- `agents/tier2-beat-miss-analyst.md`
- `agents/tier2-segment-geo-analyst.md`
- `agents/tier2-margin-analyst.md`
- `agents/tier2-guidance-analyst.md`
- `agents/tier2-valuation-analyst.md`

For each analyst, construct its prompt by:
1. Taking the full content of its definition file
2. Appending the full `raw_data` JSON package from Phase 1

**Wait** for all 5 to complete, then merge their outputs into a single `analysis` package per `references/data-schema.md`.

---

## Phase 3: Dispatch Tier 3 — Writers + Chart Generator (ALL 5 IN PARALLEL)

**CRITICAL**: Launch all 5 simultaneously in a **single Agent tool call message**.

Read each agent definition from:
- `agents/tier3-chart-generator.md`
- `agents/tier3-executive-summary-writer.md`
- `agents/tier3-results-writer.md`
- `agents/tier3-thesis-risk-writer.md`
- `agents/tier3-valuation-writer.md`

For each writer, construct its prompt by:
1. Taking the full content of its definition file
2. Appending the full `raw_data` and `analysis` packages from Phases 1–2
3. Appending the chart URLs from the chart-generator (for writers that embed charts)

**Note on chart dependencies**: The chart-generator does NOT depend on the writers, and the writers only need the chart URLs (not the chart content). If the chart-generator completes first, pass its URLs to the writers. If writers complete first, they can use placeholder references `[FIG_N]` which are replaced during assembly.

**Wait** for all 5 to complete, then collect the four markdown section strings and the chart URL dict.

---

## Phase 4: Assemble Final Report

Concatenate sections in this exact order:

```
{section_executive_summary}

---

{section_results_detail}

---

{section_thesis_risk}

---

{section_valuation}
```

Replace any `[FIG_N]` placeholders with the actual QuickChart.io URLs from the chart-generator.

Save the assembled report using the Write tool:
- **Filename**: `[TICKER]_Q[X]_FY[YEAR]_Earnings_Update.md`
- **Location**: Current working directory

---

## Phase 5: Dispatch Tier 4 — QA Reviewer

Read `agents/tier4-qa-reviewer.md` and pass it the assembled report file path and the full data/analysis packages.

The QA reviewer will:
- Verify all numbers match the press release
- Check all hyperlinks use markdown syntax
- Confirm 10 charts are embedded
- Validate the sources section is complete
- Flag any issues for correction

If the QA reviewer flags critical issues, correct them directly (do not re-run the full pipeline).

---

## Phase 6: Deliver to User

Provide this summary to the user:

```
[Company] [Quarter] Earnings Update — Agent Team Run Complete

Agents launched: 15 (4 collectors + 5 analysts + 5 writers + 1 chart generator + 1 QA)
Tiers run in parallel: 4

Results: [BEAT / INLINE / MISS]
- Revenue: $X.XB (beat/missed by $XXM or X%)
- EPS: $X.XX (beat/missed by $X.XX)

Key Takeaways:
• [Takeaway 1]
• [Takeaway 2]
• [Takeaway 3]

Updated Estimates:
- FY[YEAR]E Revenue: $XX.XB (prior: $XX.XB, +/-X%)
- FY[YEAR]E EPS: $X.XX (prior: $X.XX, +/-X%)

Rating: [MAINTAINED / RAISED / LOWERED] [RATING]
Price Target: $XXX (prior: $XXX) — [+/-]XX% implied upside

Report saved: [TICKER]_Q[X]_FY[YEAR]_Earnings_Update.md
```

---

## Error Handling

- **Collector failure**: Retry that single agent once. If it fails again, proceed with partial data and note the gap in the report.
- **Analyst failure**: Retry once. If it fails, the orchestrator should produce that section's analysis directly.
- **Writer failure**: Retry once. If it fails, the orchestrator writes that section directly using the analysis data.
- **QA flags critical issue**: Fix inline — do not restart the pipeline.
