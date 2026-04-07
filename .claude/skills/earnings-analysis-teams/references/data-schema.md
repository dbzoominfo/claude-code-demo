# Inter-Agent Data Schema

This document defines the structured JSON data packages passed between agent tiers.
All agents must produce output conforming to their schema section.
The orchestrator collects, merges, and forwards these packages between tiers.

---

## Tier 1 Output: Raw Data Package

Each of the 4 collectors returns one section. The orchestrator merges all four into a single `raw_data` object before dispatching Tier 2.

```json
{
  "meta": {
    "company": "Apple Inc.",
    "ticker": "AAPL",
    "quarter_label": "Q1 FY2026",
    "quarter_end_date": "2025-12-27",
    "report_date": "2026-01-29",
    "fiscal_calendar": "Apple fiscal year ends September; Q1=Oct–Dec",
    "today_date": "2026-04-06",
    "timeliness_ok": true
  },

  "press_release": {
    "url": "https://www.apple.com/newsroom/2026/01/apple-reports-first-quarter-results/",
    "date": "2026-01-29",
    "headline": "Apple Reports First Quarter Results",
    "revenue_total": 143760000000,
    "net_income": 42100000000,
    "eps_diluted": 2.84,
    "gross_margin_pct": 0.482,
    "operating_cash_flow": 53900000000,
    "active_device_base": "2.5 billion",
    "dividend_per_share": 0.26,
    "buybacks": 25000000000,
    "segments": {
      "iPhone": 85270000000,
      "Services": 30000000000,
      "Mac": 8390000000,
      "iPad": 8600000000,
      "Wearables_Home_Accessories": 11510000000
    },
    "geographies": {
      "Americas": null,
      "Europe": null,
      "Greater_China": 25530000000,
      "Japan": null,
      "Rest_of_Asia_Pacific": null
    },
    "prior_year_revenue": 124300000000,
    "prior_year_eps": 2.40,
    "prior_year_gross_margin_pct": 0.469
  },

  "transcript": {
    "url": "https://www.fool.com/earnings/call-transcripts/2026/01/29/apple-aapl-q1-2026-earnings-call-transcript/",
    "date": "2026-01-29",
    "verified_date_matches_release": true,
    "management_tone": "Confident / optimistic",
    "key_quotes": [
      {
        "speaker": "Tim Cook (CEO)",
        "quote": "We are thrilled to report Apple's best quarter ever...",
        "topic": "Overall results"
      }
    ],
    "guidance_statements": [
      {
        "metric": "Revenue growth",
        "value": "13%–16% YoY",
        "period": "Q2 FY2026"
      },
      {
        "metric": "Gross margin",
        "value": "48%–49%",
        "period": "Q2 FY2026"
      },
      {
        "metric": "Operating expenses",
        "value": "$18.4B–$18.7B",
        "period": "Q2 FY2026"
      }
    ],
    "analyst_concerns": [
      "iPhone supply constraints on advanced silicon nodes",
      "Memory cost inflation in Q2",
      "China regulatory risk"
    ],
    "strategic_themes": [
      "Apple Intelligence driving iPhone 17 supercycle",
      "Google Gemini integration for complex queries",
      "India expansion — strong double-digit growth",
      "2.5B active device base milestone"
    ]
  },

  "sec_filing": {
    "url": "https://www.sec.gov/Archives/edgar/data/320193/000032019326000006/aapl-20251227.htm",
    "accession_number": "0000320193-26-000006",
    "filing_date": "2026-02-07",
    "quarter_end": "2025-12-27",
    "products_gross_margin_pct": 0.407,
    "services_gross_margin_pct": 0.765,
    "operating_expenses": 18400000000,
    "cash_and_equivalents": 45300000000,
    "total_assets": null,
    "long_term_debt": null,
    "shares_diluted": 14820000000,
    "capex": null,
    "free_cash_flow": null
  },

  "consensus": {
    "source": "LSEG",
    "as_of_date": "2026-01-28",
    "revenue_estimate": 138480000000,
    "eps_estimate": 2.67,
    "gross_margin_estimate_pct": 0.475,
    "segment_estimates": {
      "iPhone": 78650000000,
      "Services": 28500000000,
      "Mac": 8950000000,
      "iPad": 8130000000,
      "Wearables": 11800000000
    },
    "analyst_ratings": {
      "buy": 29,
      "hold": 16,
      "sell": 4,
      "total": 49
    },
    "consensus_price_target": 300.00,
    "high_price_target": 350.00,
    "low_price_target": 215.00,
    "prior_quarter_guidance": {
      "source": "Q4 FY2025 earnings call (October 30, 2025)",
      "revenue_growth_guided": null,
      "gross_margin_guided": "46.5%–47.0%"
    }
  }
}
```

---

## Tier 2 Output: Analysis Package

Each of the 5 analysts returns one section. The orchestrator merges all five into a single `analysis` object before dispatching Tier 3.

```json
{
  "beat_miss": {
    "analyst": "beat-miss-analyst",
    "overall_verdict": "BEAT",
    "metrics": [
      {
        "metric": "Total Revenue",
        "actual": 143760000000,
        "consensus": 138480000000,
        "beat_miss_abs": 5280000000,
        "beat_miss_pct": 3.81,
        "verdict": "BEAT",
        "driver": "iPhone demand exceeded all forecasts; Greater China surged 38%"
      }
    ],
    "one_time_items": [],
    "sustainability_assessment": "Beat driven by structural iPhone supercycle + Services compounding — sustainable"
  },

  "segment_geo": {
    "analyst": "segment-geo-analyst",
    "segments": [
      {
        "name": "iPhone",
        "actual": 85270000000,
        "prior_year": 69350000000,
        "yoy_growth_pct": 22.97,
        "consensus": 78650000000,
        "beat_miss_pct": 8.41,
        "key_drivers": ["AI-driven upgrade cycle", "China all-time record", "Double-digit switcher growth"]
      }
    ],
    "geographies": [
      {
        "region": "Greater China",
        "actual": 25530000000,
        "prior_year": 18470000000,
        "yoy_growth_pct": 38.2,
        "notable": "All-time record; iPhones held top 3 urban China positions"
      }
    ],
    "thesis_implications": "China bear case materially weakened; India emerging as next growth vector"
  },

  "margins": {
    "analyst": "margin-analyst",
    "consolidated_gross_margin": 0.482,
    "prior_year_gross_margin": 0.469,
    "yoy_bps_change": 130,
    "qoq_bps_change": 100,
    "vs_guidance_high_bps": 70,
    "products_gross_margin": 0.407,
    "services_gross_margin": 0.765,
    "operating_margin_est": 0.354,
    "drivers_positive": [
      "Services mix shift (76.5% vs 40.7% Products margin)",
      "Premium iPhone mix (Pro Max demand exceeded expectations)",
      "Operating leverage on record revenue base"
    ],
    "drivers_negative": [
      "Tariff headwinds on China-manufactured components",
      "Rising memory costs (flagged as greater Q2 headwind)"
    ],
    "forward_outlook": "Q2 guidance 48–49% implies continued structural improvement despite memory headwinds"
  },

  "guidance": {
    "analyst": "guidance-analyst",
    "q2_guidance": {
      "revenue_growth": "13%–16% YoY",
      "revenue_implied_range_low": 107800000000,
      "revenue_implied_range_high": 110700000000,
      "gross_margin_range": "48%–49%",
      "opex_range": "$18.4B–$18.7B"
    },
    "vs_prior_guidance": {
      "prior_gross_margin": "46.5%–47.0%",
      "change": "Significantly above prior quarter implied trajectory"
    },
    "vs_street": {
      "street_q2_revenue": 101500000000,
      "beat_implied": true,
      "beat_pct": 6.2
    },
    "full_year_implication": "FY2026 revenue tracking toward $430–$440B vs. prior consensus ~$420B",
    "credibility_assessment": "Apple has a strong history of conservative guidance; 13–16% likely sandbagged",
    "key_caveats": [
      "iPhone supply constrained by advanced node allocation",
      "Memory cost inflation more significant in Q2 than Q1"
    ]
  },

  "valuation": {
    "analyst": "valuation-analyst",
    "current_price": 259.37,
    "prior_price_target": 290.00,
    "new_price_target": 310.00,
    "rating": "BUY",
    "rating_change": "MAINTAINED",
    "methodology": {
      "pe_method": {
        "fy2026e_eps": 7.85,
        "multiple": 39.5,
        "implied_value": 310.08
      },
      "ev_ebitda_method": {
        "fy2026e_ebitda": 145000000000,
        "multiple": 25.0,
        "implied_value": 310.00
      },
      "dcf_method": {
        "wacc": 0.10,
        "terminal_growth": 0.03,
        "implied_value_range": [305, 320]
      }
    },
    "estimates": {
      "fy2026e": {
        "revenue_old": 450000000000,
        "revenue_new": 468000000000,
        "revenue_change_pct": 4.0,
        "eps_old": 7.20,
        "eps_new": 7.85,
        "eps_change_pct": 9.0,
        "gross_margin_old": 0.472,
        "gross_margin_new": 0.478
      },
      "fy2027e": {
        "revenue_new": 512000000000,
        "eps_new": 8.90,
        "gross_margin_new": 0.485
      }
    },
    "upside_pct": 19.5
  }
}
```

---

## Tier 3 Output: Report Sections Package

Each writer returns a markdown string for their section(s). The chart generator returns a dict of QuickChart.io URLs. The orchestrator concatenates sections in order to produce the final report.

```json
{
  "charts": {
    "fig1_revenue_trend": "https://quickchart.io/chart?...",
    "fig2_eps_trend": "https://quickchart.io/chart?...",
    "fig3_gross_margin": "https://quickchart.io/chart?...",
    "fig4_segment_pie": "https://quickchart.io/chart?...",
    "fig5_geo_bar": "https://quickchart.io/chart?...",
    "fig6_iphone_trend": "https://quickchart.io/chart?...",
    "fig7_services_trend": "https://quickchart.io/chart?...",
    "fig8_beat_miss": "https://quickchart.io/chart?...",
    "fig9_yoy_growth": "https://quickchart.io/chart?...",
    "fig10_capital_return": "https://quickchart.io/chart?..."
  },

  "section_executive_summary": "# [Company] ([TICKER]) — Q[X] FY[YEAR] Earnings Update\n...",
  "section_results_detail": "## Section 2: Detailed Results...\n## Section 3: ...\n",
  "section_thesis_risk": "## Section 4: Margin Analysis...\n## Section 5: Guidance...\n## Section 6: ...\n## Section 7: ...\n",
  "section_valuation": "## Section 8: Valuation...\n## Section 9: ...\n## Section 10: Updated Estimates...\n## Sources & References\n..."
}
```

---

## Assembly Order (Tier 0 Orchestrator)

```
final_report = (
  section_executive_summary +
  "\n\n---\n\n" +
  section_results_detail +
  "\n\n---\n\n" +
  section_thesis_risk +
  "\n\n---\n\n" +
  section_valuation
)
```

File name: `[Ticker]_Q[X]_FY[YEAR]_Earnings_Update.md`
