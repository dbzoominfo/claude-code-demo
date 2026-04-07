---
description: Analyze quarterly earnings using a parallel agent team for faster report generation
argument-hint: "[company name or ticker] [quarter, e.g. Q3 2024]"
---

# Earnings Analysis — Agent Teams (Parallel)

Create a professional equity research earnings update report using a **parallel agent team** for 3–4x faster generation vs. the standard `/earnings` command.

## When to Use This vs. `/earnings`

| | `/earnings` (standard) | `/earnings-teams` (this command) |
|--|--|--|
| **Architecture** | Single agent, serial phases | 15 agents, 4 parallel tiers |
| **Speed** | ~5–7 hours of LLM work | ~1.5 hours of LLM work |
| **Best for** | Simple/exploratory use | Time-critical reports, production use |
| **Output** | Same format | Same format |

## Workflow

### Step 1: Parse Input

Extract from arguments:
- **Ticker / Company name** (e.g., `AAPL`, `Apple`)
- **Quarter** (e.g., `Q1 2026`, `Q3 FY25`, `Q2 2024`)

If either is missing, ask before proceeding.

### Step 2: Load and Run the Parallel Skill

Use `skill: "earnings-analysis-teams"` to orchestrate the full agent team pipeline:

```
Tier 0: Orchestrator
  └─► Tier 1 (parallel): 4 Data Collectors
        └─► Tier 2 (parallel): 5 Analysts
              └─► Tier 3 (parallel): 5 Writers + Chart Generator
                    └─► Tier 4: QA Reviewer
```

### Step 3: Deliver Output

Provide:
1. **Markdown report (.md)** saved to working directory
2. **Summary** of beat/miss, guidance changes, thesis impact
3. **Agent team run log** showing which agents ran and what each found

## Report Structure (same as `/earnings`)

```
Section 1:  Earnings Summary — Rating, PT, key takeaways, snapshot table
Sections 2–3: Detailed Results — Segment, geographic, product breakdown
Sections 4–5: Key Metrics & Guidance — Margin analysis, guidance comparison
Sections 6–7: Updated Investment Thesis — Thesis pillars, risks, catalysts
Sections 8–10: Valuation & Estimates — PT methodology, old/new estimates
Sources: All materials with clickable hyperlinks
Charts: 10 embedded QuickChart.io charts
```

## Quality Standards (same as `/earnings`)

- [ ] Earnings data verified as latest quarter (within 90 days)
- [ ] Beat/miss quantified for every key metric with drivers explained
- [ ] 10 charts embedded via QuickChart.io URLs
- [ ] Sources section with clickable markdown hyperlinks
- [ ] Every figure and table has source citation
- [ ] Rating and price target stated upfront
- [ ] 8–12 sections, 3,000–5,000 words
- [ ] Old vs. new estimates clearly shown
