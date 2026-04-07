# Claude Code Plugins & Tools for Endowment Management - Training Material

## Overview

This training guide covers all available Claude Code plugins, MCP servers, community skills, and custom skill authoring relevant to endowment management workflows. Each section includes references, installation instructions, and example invocations.

---

## Table of Contents

1. [Anthropic Financial Services Plugins](#1-anthropic-financial-services-plugins)
2. [Candid MCP Connector](#2-candid-mcp-connector)
3. [Blackbaud MCP Connector](#3-blackbaud-mcp-connector)
4. [Benevity MCP Server](#4-benevity-mcp-server)
5. [MCP Investment Portfolio Server](#5-mcp-investment-portfolio-server-open-source)
6. [Financial Datasets MCP Server](#6-financial-datasets-mcp-server)
7. [JoelLewis/finance_skills](#7-joellewisfinance_skills-community-skills)
8. [Building Custom Endowment Skills](#8-building-custom-endowment-skills)
9. [Claude for Nonprofits Program](#9-claude-for-nonprofits-program)

---

## 1. Anthropic Financial Services Plugins

### Reference
- **GitHub:** https://github.com/anthropics/financial-services-plugins
- **Install Guide:** https://support.claude.com/en/articles/13851150-install-financial-services-plugins-for-cowork
- **DeepWiki Analysis:** https://deepwiki.com/anthropics/financial-services-plugins
- **Comps Command:** https://github.com/anthropics/financial-services-plugins/blob/main/financial-analysis/commands/comps.md
- **DCF Command:** https://github.com/anthropics/financial-services-plugins/blob/main/financial-analysis/commands/dcf.md
- **One-Pager Command:** https://github.com/anthropics/financial-services-plugins/blob/main/investment-banking/commands/one-pager.md
- **IC Memo Command:** https://github.com/anthropics/financial-services-plugins/blob/main/private-equity/commands/ic-memo.md
- **Source Command:** https://github.com/anthropics/financial-services-plugins/blob/main/private-equity/commands/source.md
- **Client Review Command:** https://github.com/anthropics/financial-services-plugins/blob/main/wealth-management/commands/client-review.md
- **CIM Command:** https://github.com/anthropics/financial-services-plugins/blob/main/investment-banking/commands/cim.md
- **Merger Model Command:** https://github.com/anthropics/financial-services-plugins/blob/main/investment-banking/commands/merger-model.md

### Description
Official Anthropic-maintained plugins that turn Claude into a financial services specialist. Covers investment banking, equity research, private equity, and wealth management. Bundles skills, MCP data connectors, slash commands, and sub-agents for specific financial workflows.

### Data Partners
Daloopa, Morningstar, S&P Global, FactSet, Moody's, MT Newswires, Aiera, LSEG, PitchBook, Chronograph, Egnyte.

### Available Plugin Modules

| Plugin | What It Does |
|---|---|
| **financial-analysis** (core, install first) | Comps, DCF, LBO models, 3-statement financials, QC presentations, data connectors |
| **investment-banking** | CIMs, teasers, process letters, buyer lists, merger models, strip profiles, deal tracking |
| **equity-research** | Earnings updates, initiating coverage, investment theses, catalyst tracking, morning notes, screening |
| **private-equity** | Deal sourcing/screening, due diligence checklists, unit economics, IC memos, portfolio KPIs |
| **wealth-management** | Wealth management workflows |
| **LSEG** (partner) | Bond pricing, yield curves, FX carry trades, options valuation, macro dashboards (8 commands) |
| **S&P Capital IQ** (partner) | Company tearsheets, earnings previews, funding digests |

### Installation

```bash
# Install the core plugin FIRST (required by all others)
claude plugin install financial-analysis@financial-services-plugins

# Then install function-specific plugins
claude plugin install investment-banking@financial-services-plugins
claude plugin install equity-research@financial-services-plugins
claude plugin install private-equity@financial-services-plugins
claude plugin install wealth-management@financial-services-plugins
```

### Slash Commands & Endowment Examples

| Command | Purpose | Endowment Example | Reference |
|---|---|---|---|
| `/comps [company]` | Comparable company analysis | `/comps Vanguard Total Stock Market ETF` | [comps.md](https://github.com/anthropics/financial-services-plugins/blob/main/financial-analysis/commands/comps.md) |
| `/dcf [company]` | DCF valuation model | `/dcf Tesla` -- evaluate endowment equity holding | [dcf.md](https://github.com/anthropics/financial-services-plugins/blob/main/financial-analysis/commands/dcf.md) |
| `/earnings [company] [quarter]` | Post-earnings update | `/earnings Microsoft Q1-2026` | [earnings.md](https://github.com/anthropics/financial-services-plugins/blob/main/equity-research/commands/earnings.md) |
| `/one-pager [company]` | One-page company profile (PPT slide) | `/one-pager BlackRock` -- for investment committee | [one-pager.md](https://github.com/anthropics/financial-services-plugins/blob/main/investment-banking/commands/one-pager.md) |
| `/ic-memo [project]` | Investment committee memo | `/ic-memo "Alternatives Allocation Increase"` | [ic-memo.md](https://github.com/anthropics/financial-services-plugins/blob/main/private-equity/commands/ic-memo.md) |
| `/source [criteria]` | Deal sourcing | `/source "impact investing clean energy"` | [source.md](https://github.com/anthropics/financial-services-plugins/blob/main/private-equity/commands/source.md) |
| `/client-review [client]` | Client meeting prep | `/client-review "University Endowment Q2 Review"` | [client-review.md](https://github.com/anthropics/financial-services-plugins/blob/main/wealth-management/commands/client-review.md) |
| `/cim [target]` | Confidential Information Memorandum | `/cim "Private Credit Fund Opportunity"` | [cim.md](https://github.com/anthropics/financial-services-plugins/blob/main/investment-banking/commands/cim.md) |
| `/merger-model [acquirer] acquiring [target]` | Merger model | `/merger-model "Fund A" acquiring "Fund B"` | [merger-model.md](https://github.com/anthropics/financial-services-plugins/blob/main/investment-banking/commands/merger-model.md) |

### Endowment Use Cases
- Build comparable analyses for endowment portfolio holdings
- Generate DCF models for evaluating private investment opportunities
- Create IC memos for endowment investment committee meetings
- Pull real-time data from partner MCP providers (LSEG for bonds, S&P for fundamentals)
- Generate Excel workbooks for financial models to present to the board

---

## 2. Candid MCP Connector

### Reference
- **Candid Blog:** https://candid.org/blogs/claude-for-nonprofits-candid-mcp-connector-access-nonprofit-data-ai-assistant/
- **Getting Started Guide:** https://learning.candid.org/getting-started-with-the-candid-mcp-connector/375441
- **Claude Help Center:** https://support.claude.com/en/articles/12923235-using-the-candid-connector-in-claude

### Description
Candid (formed from the merger of GuideStar and Foundation Center) provides an MCP connector that brings comprehensive nonprofit and funder data into Claude. Access 1.9M+ organizations with financial data sourced from IRS filings, official registrations, and direct organization input.

### Available Tools

| Tool | Description |
|---|---|
| **Search Organizations** | Search nonprofits and foundations by name, mission, location, leadership demographics, or area of work |
| **Lookup/Link Profiles** | Identifies organization names and links them to official Candid profiles with clickable URLs |
| **Knowledge Base Search** | Search Candid's library of research reports, training materials, blog posts, and curated news |
| **Background Tools** | Automatic geocoding, date-aware queries (used by Claude behind the scenes) |

### Setup Instructions
The Candid connector is a **hosted remote connector** -- no local server or JSON config needed.

1. In Claude, go to **Profile > Settings > Connectors > Browse connectors**
2. Select **Candid** on the Web tab
3. Click **Connect** and sign in with your Candid credentials
4. If you don't have a Candid account, register free at https://app.candid.org/registration
5. For Teams/Enterprise: admin must first click "Add to your team" to enable the connector
6. Once connected via Claude.ai, the connector is **automatically available in Claude Code** under the same account

### Example Invocations (Natural Language)

```
# Research peer endowments
"Find foundations in California that fund youth education programs"

# Benchmark endowment sizes
"Search for endowment-holding foundations with assets over $100 million
 in the state of New York"

# Discover co-funding opportunities
"What organizations are funding climate change research in the
 Pacific Northwest?"

# Deep-dive a specific foundation
"Show me the Candid profile for the Ford Foundation"

# DEI-focused research
"Find nonprofits led by women of color working in environmental justice"

# Policy research
"Search Candid's knowledge base for research on endowment spending policies"
```

### Limitations
- Does not support aggregation queries ("Which nonprofits received the 3 largest grants?")
- Advanced data (grant histories, in-depth financials) may require paid Candid subscription

### Endowment Use Cases
- Research peer endowments and their funding patterns
- Discover foundations working in similar program areas for co-investment
- Access verified IRS filing data for benchmarking endowment performance
- Link directly to Candid profiles for due diligence on grant recipients

---

## 3. Blackbaud MCP Connector

### Reference
- **Connector Page:** https://claude.com/connectors/blackbaud
- **Claude Help Center:** https://support.claude.com/en/articles/12923221-using-the-blackbaud-connector-in-claude
- **CData Alternative:** https://cdn.cdata.com/help/JZK/mcp/

### Description
Brings Raiser's Edge NXT fundraising and CRM data into Claude. Surfaces constituent profiles, donation records, event information, and engagement history to support nonprofit fundraising workflows.

### Available Functions

| Function | Description |
|---|---|
| **Donor Research** | Retrieve constituent profiles and giving histories |
| **Gift Analysis** | Pull donation records; identify giving patterns, track campaign performance, recognize major donors |
| **Event Planning Support** | Search event records, review past fundraising activities, compare results |
| **Personalized Communications** | Draft customized thank-you letters, appeals, and follow-ups using donor data |
| **Quick Data Lookups** | Answer questions about constituents, events, or gifts without opening RE NXT |

### Setup Instructions

**Option A: Hosted Remote Connector (Recommended)**
1. Your Blackbaud **Marketplace admin** must connect the "Claude for Blackbaud" application in the Blackbaud Marketplace
2. In Claude, go to **Profile > Settings > Connectors > Browse connectors**
3. Select **Blackbaud** and click **Connect**
4. Authenticate with your Blackbaud/Raiser's Edge NXT credentials
5. Claude only accesses data your Blackbaud user account is authorized to view
6. Once connected via Claude.ai, available in Claude Code automatically

**Option B: CData MCP Server (Programmatic/Local Access)**
```json
// Add to claude_desktop_config.json or .mcp.json
{
  "mcpServers": {
    "blackbaud-renxt": {
      "command": "npx",
      "args": ["-y", "@cdata/mcp-server-blackbaud-renxt"],
      "env": {
        "BLACKBAUD_API_KEY": "your_key_here"
      }
    }
  }
}
```
> **Note:** Verify exact CData package name at https://cdn.cdata.com/help/JZK/mcp/

### Example Invocations (Natural Language)

```
# Donor history lookup
"Look up the giving history for Jane Smith over the past 3 years"

# Major gift analysis
"Show me all major donors (gifts over $10,000) from the 2025 fiscal year"

# Stewardship communications
"Draft a thank-you letter to Dr. Robert Chen for his $50,000 endowment gift"

# Event performance comparison
"What events did we hold last quarter and how did they perform compared
 to the same quarter last year?"

# Endowment-specific donor tracking
"Find all constituents who gave to the scholarship endowment fund
 in the last 12 months"

# Board meeting prep
"Prepare a briefing on our top 20 endowment donors for the board meeting"
```

### Endowment Use Cases
- Track endowment-specific gifts and pledges
- Prepare donor briefings for investment committee meetings
- Analyze giving patterns to endowment funds over time
- Draft personalized stewardship communications for endowment donors

---

## 4. Benevity MCP Server

### Reference
- **Documentation:** https://causeshelp.benevity.org/hc/en-us/articles/43364091494164-Benevity-nonprofit-MCP-server
- **Anthropic Partnership:** https://causeshelp.benevity.org/hc/en-us/articles/43965246236692-Anthropic-x-Benevity
- **Community Announcement:** https://community.benevity.com/product-updates/benevity-integrates-its-trusted-global-nonprofit-network-with-anthropic-s-claude-for-nonprofits-209

### Description
Integrates Benevity's database of 2.4+ million verified nonprofit organizations into Claude. Enables conversational discovery of charitable causes, verified organization data, and location-aware search. Launched on Giving Tuesday 2025 as part of Claude for Nonprofits.

### Available Tools

| Tool | Description |
|---|---|
| **Nonprofit Search** | Search for causes by keywords, values, cause areas |
| **Location-Aware Search** | Find local or international organizations |
| **Organization Details** | Access Benevity's curated database of verified nonprofits |
| **Direct Action Links** | Get verified website links for donations |

### Setup Instructions
Hosted remote connector -- no account required.

1. In Claude, go to **Profile > Settings > Connectors**
2. Browse connectors and select **Benevity**
3. Click **Connect** (no separate Benevity account required)
4. Available for Claude Pro users; Teams/Enterprise availability in progress
5. Once connected via Claude.ai, available in Claude Code automatically

### Example Invocations (Natural Language)

```
# Discover grant recipients
"Find verified nonprofits working on affordable housing in Chicago"

# Research community foundations
"Search for organizations focused on endowment-building for
 community foundations"

# Environmental program area
"What environmental conservation nonprofits operate in the
 Pacific Northwest?"

# Financial literacy focus
"Find organizations working on financial literacy for underserved
 communities"

# Higher education endowments
"Show me nonprofits focused on higher education access with
 endowment programs"
```

### Privacy
- No personally identifiable information shared with the MCP server
- All nonprofit information provided is public data
- Follows Claude's standard privacy practices

### Endowment Use Cases
- Verify nonprofit status before endowment grant disbursements
- Discover potential grant recipients aligned with endowment mission
- Research organizations in specific geographic areas for targeted giving

---

## 5. MCP Investment Portfolio Server (Open Source)

### Reference
- **GitHub:** https://github.com/ikhyunAn/MCP_InvestmentPortfolio
- **Playbooks Listing:** https://playbooks.com/mcp/ikhyunan-investment-portfolio-manager
- **LobeHub Listing:** https://lobehub.com/mcp/ikhyunan-portfolio-manager-mcp
- **Alternative (InvestMCP):** https://github.com/arrpitk/InvestMCP

### Description
Open-source MCP server for managing and analyzing investment portfolios. Provides tools for portfolio creation, real-time market data, performance analysis, investment recommendations, and visualization. Uses Alpha Vantage and News API for data.

### Available Tools

| Tool Module | Functions |
|---|---|
| **portfolio_tools.py** | Create and update portfolios with stocks and bonds |
| **stock_tools.py** | Fetch real-time stock prices and relevant news |
| **analysis_tools.py** | Generate portfolio reports and performance analysis |
| **visualization_tools.py** | Create visual representations of portfolio allocation |

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/ikhyunAn/MCP_InvestmentPortfolio.git
cd MCP_InvestmentPortfolio

# 2. Create and activate virtual environment
python -m venv venv
source venv/bin/activate        # Mac/Linux
# venv\Scripts\activate         # Windows

# 3. Install dependencies
pip install -r requirements.txt

# 4. Set API keys (get free keys from Alpha Vantage and News API)
export ALPHA_VANTAGE_API_KEY="your_key_here"
export NEWS_API_KEY="your_key_here"

# 5. Run the server
python3 main.py
```

### Claude Desktop Configuration

Add to `claude_desktop_config.json`:
```json
{
  "mcpServers": {
    "portfolio-manager": {
      "command": "python",
      "args": ["/absolute/path/to/MCP_InvestmentPortfolio/main.py"],
      "env": {
        "PYTHONPATH": "/absolute/path/to/MCP_InvestmentPortfolio",
        "ALPHA_VANTAGE_API_KEY": "your_key_here",
        "NEWS_API_KEY": "your_key_here"
      }
    }
  }
}
```

### Claude Code Configuration

```bash
claude mcp add-json "portfolio-manager" '{
  "command": "python",
  "args": ["/absolute/path/to/MCP_InvestmentPortfolio/main.py"],
  "env": {
    "ALPHA_VANTAGE_API_KEY": "your_key_here",
    "NEWS_API_KEY": "your_key_here"
  }
}'
```

### Example Invocations (Natural Language)

```
# Create an endowment portfolio
"Create a portfolio with 40% VTI, 20% VXUS, 25% BND, and 15% VTIP
 with user ID endowment-main"

# Analyze performance
"Analyze the current allocation and performance of portfolio endowment-main"

# Monitor holdings
"Get the current price and recent news for AAPL, MSFT, and BRK.B"

# Generate reports
"Generate a comprehensive portfolio report for the endowment's equity sleeve"

# Visualize allocation
"Show me a visual breakdown of the endowment portfolio allocation"

# Get recommendations
"What investment recommendations do you have for a portfolio that is
 overweight in technology?"
```

### Endowment Use Cases
- Track endowment portfolio allocations across asset classes
- Generate performance reports for investment committee presentations
- Get real-time pricing on endowment holdings
- Visualize asset allocation for board presentations
- Portfolio data stored in JSON files (can be version-controlled)

### Alternative: InvestMCP (More Comprehensive)
**GitHub:** https://github.com/arrpitk/InvestMCP
A suite of 6 MCP servers: Stock Data, Technical Analysis, Financial News, Stock Screener, Investment Advisor, and Portfolio Tracker. More feature-rich but more complex to set up.

---

## 6. Financial Datasets MCP Server

### Reference
- **GitHub:** https://github.com/financial-datasets/mcp-server
- **Official Docs:** https://docs.financialdatasets.ai/mcp-server
- **Marketplace:** https://mcpmarket.com/server/financial-datasets

### Description
MCP server for accessing stock market data from the Financial Datasets API. Provides income statements, balance sheets, cash flow statements, stock prices, financial metrics, stock screening, and company news.

### Available Tools

| Tool | Description |
|---|---|
| `getStockPriceSnapshot` | Latest price snapshot (current price, volume, OHLC) |
| `getIncomeStatement` | Revenue, expenses, net income |
| `getBalanceSheet` | Assets, liabilities, equity |
| `getCashFlowStatement` | Operating, investing, financing cash flows |
| `getFinancialMetrics` | P/E ratio, enterprise value, revenue per share |
| `screenStocks` | Filter stocks by financial metrics, valuation ratios, company attributes |
| `getCompanyNews` | News articles for a given ticker |
| `getHistoricalStockPrices` | Historical price data |
| `getCryptoPrices` | Cryptocurrency price data |

### Installation

**Method 1: Interactive OAuth (Simplest)**
```
# Type /mcp inside Claude Code and complete the OAuth flow in your browser
# No API key needed
/mcp
```

**Method 2: Manual Setup**
```bash
# Clone the repo
git clone https://github.com/financial-datasets/mcp-server.git
cd mcp-server

# Create virtual env
uv venv
source .venv/bin/activate

# Install dependencies
uv add "mcp[cli]" httpx

# Set API key
cp .env.example .env
# Edit .env: FINANCIAL_DATASETS_API_KEY=your_key_here
```

### Claude Desktop Configuration

Add to `claude_desktop_config.json`:
```json
{
  "mcpServers": {
    "financial-datasets": {
      "command": "/path/to/uv",
      "args": [
        "--directory",
        "/absolute/path/to/financial-datasets-mcp",
        "run",
        "server.py"
      ]
    }
  }
}
```

### Claude Code Configuration

```bash
claude mcp add-json "financial-datasets" '{
  "command": "/path/to/uv",
  "args": ["--directory", "/absolute/path/to/financial-datasets-mcp", "run", "server.py"]
}'
```

### Example Invocations (Natural Language)

```
# Current pricing
"Get the current stock price for VTI (Vanguard Total Stock Market ETF)"

# Fundamental analysis
"Pull the balance sheet for Berkshire Hathaway (BRK.B) for the last 4 quarters"

# Income trends
"Show me the income statement for Apple over the last 3 years"

# Stock screening for endowment criteria
"Screen for stocks with P/E ratio under 15, dividend yield above 3%,
 and market cap over $10B"

# Bulk portfolio analysis
"What are the financial metrics for the top 10 holdings in our endowment
 equity portfolio: AAPL, MSFT, JNJ, PG, JPM, UNH, V, MA, HD, COST?"

# News monitoring
"Get recent news for companies in the energy sector that our endowment holds"
```

### Other Financial MCP Servers

| Server | Description | URL |
|---|---|---|
| **Finnhub** | Real-time quotes, company profiles, analyst recommendations | https://mcpmarket.com/server/finnhub-3 |
| **Alpha Vantage** | Official MCP server, stock data, Progressive Tool Discovery | https://mcp.alphavantage.co/ |
| **Massive.com** | Stocks, options, forex via SQL-queryable DataFrames | https://mcpmarket.com/server/massive-com |
| **Stock Price** | Yahoo Finance-based, no rate limits | https://mcpmarket.com/server/stock-price |

### Endowment Use Cases
- Screen stocks matching endowment investment policy criteria
- Pull financial statements for endowment holdings analysis
- Monitor real-time prices of endowment portfolio securities
- Research potential new investments with fundamental data

---

## 7. JoelLewis/finance_skills (Community Skills)

### Reference
- **GitHub:** https://github.com/JoelLewis/finance_skills

### Description
Community-built Claude Code skill plugins for financial services. Contains 84 skills across 7 domain plugins covering investment management, regulatory compliance, advisory practice, trading, and operations. Each skill is a SKILL.md file that teaches Claude domain-specific knowledge.

### Plugin Categories

| Plugin | Skills Count | Description |
|---|---|---|
| **core** | Always installed | Math foundations used by all other plugins; includes Python reference scripts |
| **wealth-management** | Multiple | Personal and institutional wealth management |
| **compliance** | Multiple | SEC/FINRA rules, IA Act citations, enforcement actions, compliance flagging |
| **advisory-practice** | Multiple | Client onboarding through reporting; depends on wealth-management |
| **trading-operations** | Multiple | Order lifecycle: entry through settlement |
| **client-operations** | Multiple | Back-office account operations and servicing |
| **data-integration** | Multiple | Data infrastructure for financial systems |

### Dependency Tree
```
core (implicit, always installed)
+-- wealth-management
|   +-- advisory-practice (depends on wealth-management)
+-- compliance (recommended for all)
+-- trading-operations
+-- client-operations
+-- data-integration
```

### Installation

```bash
# Install ALL skills (84 skills across 7 plugins)
npx skills add JoelLewis/finance_skills

# Install a specific plugin only
npx skills add JoelLewis/finance_skills --plugin wealth-management

# Install compliance (recommended for all endowment use cases)
npx skills add JoelLewis/finance_skills --plugin compliance

# List available plugins
npx skills add JoelLewis/finance_skills --list

# Alternative: Clone and use the installer
git clone https://github.com/JoelLewis/finance_skills.git
cd finance_skills
# The included installer symlinks skills into your project
```

### Example Invocations

Skills activate **automatically** when Claude detects relevant context:

```
# Compliance review (compliance skills activate)
"Review this investment policy statement for compliance issues"
  -> Claude cites specific SEC/FINRA rules (e.g., IA Act S202(a)(11))

# Client onboarding (advisory-practice skills activate)
"Help me design a client onboarding workflow for a new endowment client"

# Settlement rules (trading-operations skills activate)
"What are the settlement requirements for this bond trade?"

# Portfolio management (wealth-management + core skills activate)
"Build a portfolio rebalancing tool for our endowment"

# Fee structure review (compliance skills activate)
"Flag any regulatory concerns with this fee structure"
  -> Claude cites specific rule numbers and enforcement precedents
```

### Endowment Use Cases
- **Compliance plugin** cites specific rule numbers -- critical for endowment regulatory compliance
- **Wealth management** covers institutional investment management scenarios
- **Advisory practice** covers the full advisor lifecycle relevant to endowment consultants
- Skills are SKILL.md files that can be customized for your specific endowment policies

---

## 8. Building Custom Endowment Skills

### Reference
- **Official Docs:** https://code.claude.com/docs/en/skills
- **How-To Guide:** https://support.claude.com/en/articles/12512198-how-to-create-custom-skills
- **Skills Repository:** https://github.com/anthropics/skills
- **Architecture Deep Dive:** https://leehanchung.github.io/blogs/2025/10/26/claude-skills-deep-dive/
- **Anthropic Blog:** https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills

### Description
Claude Code's skill system lets you create reusable, filesystem-based resources that provide Claude with domain-specific expertise. Skills are directories containing a SKILL.md file with YAML frontmatter and markdown instructions. They load on-demand and can be invoked via slash commands.

### Directory Structure
```
.claude/skills/
+-- endowment-spending-calculator/
|   +-- SKILL.md          (required)
|   +-- scripts/
|   |   +-- calculate.py  (optional helper)
|   +-- references/
|       +-- policy.md     (optional reference)
```

Skills can live in:
- **Project:** `.claude/skills/` in the project root (shared via git)
- **Personal:** `~/.claude/skills/` in your home directory (all projects)

### YAML Frontmatter Format
```yaml
---
name: skill-name          # Becomes the /slash-command (required)
description: >-           # When Claude should use this skill (required, 200 char max)
  Brief description that Claude uses to decide
  when to invoke this skill automatically.
model: claude-sonnet-4-5  # Optional: override the model
disable-model-invocation: false  # Optional: if true, manual-only
---
```

### Complete Example: Endowment Spending Policy Calculator

**File:** `.claude/skills/endowment-spending-calculator/SKILL.md`

```yaml
---
name: endowment-spending
description: >-
  Calculate endowment spending distributions using common
  spending policies (Yale/Stanford model, percentage of
  moving average, hybrid rules). Use when asked about
  endowment payout rates, spending calculations, or
  distribution amounts.
---

# Endowment Spending Policy Calculator

## When to Use
Invoke this skill when the user asks about:
- Endowment spending rates or payout calculations
- Distribution amounts from an endowment
- Comparing spending policy models
- Underwater endowment rules

## Supported Spending Policy Models

### 1. Simple Percentage Rule
Spend a fixed percentage (typically 4-5%) of the endowment's market value.

Formula: `Distribution = Market Value x Spending Rate`

### 2. Moving Average Rule
Spend a fixed percentage of the average market value over the trailing
N quarters (typically 12 quarters / 3 years).

Formula: `Distribution = (Average of trailing 12-quarter market values)
x Spending Rate`

### 3. Yale/Stanford Hybrid Model
Weighted blend of prior-year spending (adjusted for inflation) and a
percentage of current market value.

Formula:
Distribution = (W x Prior Distribution x (1 + Inflation Rate))
             + ((1 - W) x Spending Rate x Current Market Value)

Where W is the smoothing weight (Yale uses W = 0.8).

### 4. Banded/Corridor Approach
Same as moving average, but spending is capped at a ceiling (e.g., 5.25%)
and floored at a minimum (e.g., 4.25%) of current market value.

## Output Format
Always present results as a table with:
- Policy model name
- Calculated distribution amount
- Effective spending rate (as % of current market value)
- Whether the fund is underwater (below corpus/gift value)

## Underwater Endowment Rules
- UPMIFA allows spending from underwater funds if prudent
- Many states require board approval for underwater spending
- Always flag if current market value < historical gift value

## Example Calculation
If asked: "Our endowment is $50M, last year we distributed $2.3M,
inflation is 3.2%, and our policy uses the Yale model with 80/20
weighting and a 5% target rate":

Yale model:
= (0.80 x $2,300,000 x 1.032) + (0.20 x 0.05 x $50,000,000)
= $1,898,880 + $500,000
= $2,398,880 (effective rate: 4.80%)
```

### How to Invoke

```
# Invoke explicitly via slash command
/endowment-spending

# Or it activates automatically when Claude detects the conversation
# is about endowment spending calculations

# Example prompts that trigger the skill:
"Calculate our endowment payout using the Yale model"
"What should our distribution be this year?"
"Is our fund underwater?"
```

### Additional Custom Skills You Can Build

| Skill Name | Description | Slash Command |
|---|---|---|
| **endowment-fund-accounting** | Restricted vs. unrestricted fund classification, FASB ASC 958 compliance | `/fund-accounting` |
| **investment-policy-drafter** | Template-based IPS generation for endowment committees | `/ips-draft` |
| **endowment-performance** | Period-over-period with benchmark comparison reports | `/endowment-perf` |
| **gift-acceptance-checker** | Evaluate proposed gifts against gift acceptance policy | `/gift-check` |
| **underwater-endowment-monitor** | Track funds below corpus value, flag UPMIFA issues | `/underwater-check` |

### Best Practices
- Make descriptions slightly "pushy" -- Claude tends to under-trigger skills
- Include example inputs/outputs in SKILL.md
- Use consistent 2-space YAML indentation (not tabs)
- Commit `.claude/skills/` to git so the whole team gets the skills
- Bundle reference scripts in a `scripts/` subdirectory

---

## 9. Claude for Nonprofits Program

### Reference
- **Apply:** https://claude.com/solutions/nonprofits
- **Help Center:** https://support.claude.com/en/articles/12893767-getting-started-with-claude-for-nonprofits
- **Announcement:** https://www.anthropic.com/news/claude-for-nonprofits
- **Free Training Course:** https://anthropic.skilljar.com/ai-fluency-for-nonprofits
- **Complete Guide:** https://impactenabled.com/en/blog/complete-guide-claude-for-nonprofits
- **Charity Charge Guide:** https://www.charitycharge.com/nonprofit-resources/claude-for-nonprofits/

### Description
Anthropic's program providing discounted Claude access, nonprofit-specific connectors, and free training to qualifying nonprofit organizations. Launched December 2, 2025 in partnership with GivingTuesday.

### What's Included
1. **Up to 75% discount** on Claude Team ($8/user/month) and Enterprise plans
2. **Access to all Claude models:** Opus 4.6, Sonnet 4.5, Haiku 4.5
3. **Nonprofit Connectors:** Candid, Blackbaud, and Benevity MCP integrations (covered in sections 2-4)
4. **Free Training Course:** "AI Fluency for Nonprofits" at https://anthropic.skilljar.com/ai-fluency-for-nonprofits

### Eligibility
- US 501(c)(3) organizations
- Equivalent international nonprofit designations
- NGOs (humanitarian, environmental, educational, social causes)
- K-12 public and private schools
- Mission-based healthcare with 501(c)(3) status:
  - Independent Critical Access Hospitals (CAHs)
  - Rural Emergency Hospitals (REHs)
  - HRSA-designated Federally Qualified Health Centers (FQHCs)
  - CMS-certified Rural Health Clinics (RHCs)

### How to Apply

```
Step 1: Visit https://claude.com/solutions/nonprofits
Step 2: Click Apply
Step 3: Anthropic partners with Goodstack to validate eligibility
        (if already verified on Goodstack, process is faster)
Step 4: Receive confirmation email from Anthropic
Step 5: Follow the link to sign up with your Goodstack-verified email
```

### Renewal
- Discount remains active as long as nonprofit status is maintained
- No annual reapplication required
- Anthropic may periodically verify status

### Key URLs

| Resource | URL |
|---|---|
| Program / Apply | https://claude.com/solutions/nonprofits |
| Help Center | https://support.claude.com/en/articles/12893767-getting-started-with-claude-for-nonprofits |
| Free Training Course | https://anthropic.skilljar.com/ai-fluency-for-nonprofits |
| Goodstack Verification | Via Anthropic application process |

### Endowment Use Cases
- Endowment-holding organizations with 501(c)(3) status qualify
- All three nonprofit connectors (Candid, Blackbaud, Benevity) included
- Significant cost savings for endowment offices adopting AI tools
- Free training course for onboarding endowment staff

---

## Quick Reference: Setup Summary

| Tool | Type | Setup Method | Cost |
|---|---|---|---|
| Financial Services Plugins | Plugin | `claude plugin install` | Free (data partners may have fees) |
| Candid Connector | Hosted MCP | Claude Settings > Connectors | Free (advanced data may require subscription) |
| Blackbaud Connector | Hosted MCP | Claude Settings > Connectors | Requires Blackbaud license |
| Benevity Server | Hosted MCP | Claude Settings > Connectors | Free, no account needed |
| Investment Portfolio MCP | Local MCP | Clone + `claude mcp add-json` | Free (needs Alpha Vantage + News API keys) |
| Financial Datasets MCP | Local MCP | Clone or `/mcp` OAuth | Free tier available |
| finance_skills | Skills | `npx skills add` | Free, open source |
| Custom Skills | Skills | Write SKILL.md files | Free |
| Claude for Nonprofits | Program | Apply online | Up to 75% discount |

---

## Accuracy Notes

All URLs, commands, and tool descriptions were verified through web search against official documentation as of April 2026. The endowment-specific example invocations are realistic adaptations -- the tools themselves are general-purpose, and the endowment framing demonstrates how they apply in that context.

| Item | Status |
|---|---|
| Anthropic Financial Services Plugins | Verified -- official repo with documented commands |
| Candid MCP Connector | Verified -- official Candid and Claude Help Center docs |
| Blackbaud MCP Connector | Verified -- official Claude Help Center |
| Benevity MCP Server | Verified -- official Benevity help center |
| MCP Investment Portfolio | Verified -- GitHub repo with documented setup |
| Financial Datasets MCP | Verified -- GitHub repo and official docs |
| JoelLewis/finance_skills | Verified -- GitHub repo with 84 skills |
| Custom Skills format | Verified -- official Claude Code docs |
| Claude for Nonprofits | Verified -- official Anthropic announcements |
