---
name: earnings-analysis
description: Create professional equity research earnings update reports (8-12 pages, 3,000-5,000 words) analyzing quarterly results for companies already under coverage. Fast-turnaround format focusing on beat/miss analysis, key metrics, updated estimates, and revised thesis. Includes 1-3 summary tables and 8-12 charts. Use when user requests "earnings update", "quarterly update", "earnings analysis", "Q1/Q2/Q3/Q4 results", or post-earnings report.
---

# Equity Research Earnings Update

Create professional **EARNINGS UPDATE REPORTS** analyzing quarterly results for companies already under coverage, following institutional standards (JPMorgan, Goldman Sachs, Morgan Stanley format).

**Key Characteristics:**
- **Length**: 8-12 sections
- **Word Count**: 3,000-5,000 words
- **Tables**: 1-3 summary tables (NOT comprehensive)
- **Figures**: 8-12 charts (saved as PNG, referenced with `![](path)`)
- **Turnaround**: 1-2 days (within 24-48 hours of earnings)
- **Audience**: Clients already familiar with the company
- **Focus**: What's NEW - beat/miss, updated estimates, thesis impact
- **Format**: GitHub-flavored Markdown (.md)

## When to Use

Use when the user requests:
- "Create an earnings update for [Company] Q3 2024"
- "Analyze [Company]'s quarterly results"
- "Post-earnings report for [Company]"
- "Q1/Q2/Q3/Q4 update for [Company]"

**Do NOT use if:**
- User requests "initiation report" → Use different skill
- User requests "flash note" or "quick take" → Different format
- Company is not already covered → Need initiation first

## Critical Requirements

### 1. Speed & Timeliness
- Publish within 24-48 hours of earnings release
- Focus on NEW information only
- Don't rehash company background extensively

### 2. Beat/Miss Analysis
- Lead with whether company beat or missed estimates
- Quantify variances (e.g., "Revenue beat by $120M or 3%")
- Explain WHY results differed from expectations

### 3. Summary Format
- Keep tables to 1-3 (summary only, not comprehensive)
- No full P&L/Cash Flow/Balance Sheet (just key metrics)
- Assume reader has seen initiation report

### 4. Citations & Source Attribution ⭐⭐⭐ MANDATORY

**CRITICAL**: Properly cite all data with SPECIFIC sources and CLICKABLE HYPERLINKS.

**Include specific citations WITH CLICKABLE LINKS in every figure and table:**

```
Source: Q3 2024 10-Q filed November 8, 2024; Company earnings release
        [Hyperlink "10-Q" to: https://www.sec.gov/cgi-bin/viewer?accession=...]
        [Hyperlink "earnings release" to: https://investor.company.com/news/q3-2024]
```

**HOW HYPERLINKS SHOULD APPEAR IN MARKDOWN:**
- Use `[display text](URL)` syntax for all links
- Document names appear as clickable inline links
- Never use raw plain-text URLs — always wrap in markdown link syntax

**REQUIRED SOURCES LIST:**

Cite in every earnings update:
- ✓ Earnings release (with date and URL)
- ✓ 10-Q filing (with filing date and EDGAR link)
- ✓ Earnings call transcript (with date)
- ✓ Investor presentation/supplemental materials (if available)
- ✓ Consensus estimates source (Bloomberg/FactSet/etc. with date)
- ✓ Prior guidance (from previous quarter's materials)

**REFERENCE SECTION WITH CLICKABLE HYPERLINKS:**

Include "Sources" section at end of report using Markdown link syntax:

```markdown
## Sources & References

**Earnings Materials (Q3 2024):**
- [Earnings Release (November 7, 2024)](https://investor.company.com/news/q3-2024-earnings)
- [Form 10-Q (Filed November 8, 2024)](https://www.sec.gov/cgi-bin/viewer?accession=...)
- [Earnings Call Transcript (November 7, 2024)](https://seekingalpha.com/article/...)
- [Investor Presentation (November 7, 2024)](https://investor.company.com/presentations/q3-2024.pdf)
```

**VERIFICATION CHECKLIST:**
- [ ] Every figure has source with specific document and date
- [ ] Every table has source with document reference
- [ ] Beat/miss analysis cites consensus source with date
- [ ] Guidance changes cite current and prior guidance sources
- [ ] Key statistics have footnotes
- [ ] Sources section lists all materials with markdown hyperlinks
- [ ] ALL URLs formatted as markdown links — display text in brackets, URL in parentheses (not plain text)
- [ ] All SEC filings linked to EDGAR viewer

### 5. Updated Estimates
- Update forward estimates based on results
- Show old vs. new estimates clearly
- Explain what changed and why

## High-Level Workflow

The earnings update process follows 5 phases:

### Phase 1: Data Collection (30-60 minutes)

**🚨🚨🚨 CRITICAL: TRAINING DATA IS OUTDATED 🚨🚨🚨**

**BEFORE STARTING - COMPLETE THESE 4 STEPS IN ORDER:**
1. **CHECK TODAY'S DATE** - Write down the current date
2. **SEARCH FOR LATEST** - Use web search: "[Company] latest earnings results"
3. **VERIFY THE DATE** - Confirm earnings release is within last 3 months
4. **CHECK TRANSCRIPT DATE** - Verify transcript date matches release date

**COMMON MISTAKE**: Using outdated earnings calls from training data instead of searching for the latest.

**REQUIREMENTS:**
- ✓ Search for latest earnings - do NOT rely on training data
- ✓ Write down today's date and the release date found
- ✓ Verify release date is within 3 months of today
- ✓ Verify transcript date matches release date
- ✓ If dates don't match or are old (>3 months), search again

**See [references/workflow.md](references/workflow.md)** for detailed search procedures and verification steps.

### Phase 2: Analysis (2-3 hours)
- Beat/miss analysis for each key metric
- Segment/geographic/product breakdown
- Margin and guidance analysis
- Update financial model and estimates

**See [references/workflow.md](references/workflow.md)** for detailed analysis framework.

### Phase 3: Chart Generation (1-2 hours)
Create 8-12 charts focusing on quarterly trends and what's new:
- Quarterly revenue progression
- Quarterly EPS progression
- Quarterly margin trends
- Revenue by segment/geography
- Key operating metrics
- Beat/miss summary
- Estimate revisions
- Valuation charts

**See [references/workflow.md](references/workflow.md)** for chart specifications.

### Phase 4: Report Creation (2-3 hours)
Create a Markdown (.md) report with specific structure.

**See [references/report-structure.md](references/report-structure.md)** for complete section-by-section templates and formatting requirements.

**High-level structure:**
- Section 1: Earnings summary with rating and price target
- Sections 2-3: Detailed results analysis
- Sections 4-5: Key metrics & guidance
- Sections 6-7: Updated investment thesis
- Sections 8-10: Valuation & estimates
- Sections 11-12: Appendix (optional)

### Phase 5: Quality Check & Delivery (30 minutes)
Verify content, formatting, accuracy, and timeliness before delivery.

**See [references/best-practices.md](references/best-practices.md)** for quality checklist and common mistakes to avoid.

## Output Specification

**Primary Deliverable**: Markdown report (.md)
**File Name**: `[Company]_Q[Quarter]_[Year]_Earnings_Update.md`
**Example**: `Nike_Q2_FY24_Earnings_Update.md`

**Contents:**
- Section 1: Summary with rating, price target, key takeaways
- Sections 2-3: Detailed results analysis
- Sections 4-5: Key metrics and guidance
- Sections 6-7: Updated thesis assessment
- Sections 8-10: Valuation and estimates
- Sections 11-12: Appendix (optional)
- 8-12 chart images referenced via `![Figure N – Title](charts/figN_name.png)`
- 1-3 summary tables (GitHub-flavored markdown table syntax)
- Complete sources section with markdown hyperlinks

**Optional Deliverable**: XLS model update (optional for earnings updates)

## Key Differences from Initiation Report

| Aspect | Earnings Update | Initiation Report |
|--------|----------------|-------------------|
| **Length** | 8-12 pages | 30-50 pages |
| **Words** | 3,000-5,000 | 10,000-15,000 |
| **Tables** | 1-3 summary | 12-20 comprehensive |
| **Figures** | 8-12 | 25-35 |
| **Turnaround** | 1-2 days | 3-6 weeks |
| **Scope** | Quarterly results | Complete company |
| **Focus** | What's NEW | Everything |
| **Company Background** | Brief mention | 6-10 pages |
| **XLS Model** | Optional | Required |

## Resources

### references/workflow.md
Detailed Phase 1-5 instructions with step-by-step procedures for data collection, analysis, chart generation, and report creation.

### references/report-structure.md
Complete page-by-page templates, table formats, and formatting requirements for the DOCX report.

### references/best-practices.md
Examples of good/bad headlines, tips for success, common mistakes to avoid, and comprehensive quality checklist.

## Dependencies

**Required:**
- Internet access for [Quickchart.io](https://quickchart.io) chart rendering (charts embedded as URLs — no Python needed)
- Write tool for creating the Markdown report

**Optional:**
- XLS skill for model updates (not required for earnings updates)
