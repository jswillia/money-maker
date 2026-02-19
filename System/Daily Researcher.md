# Daily Opportunity Researcher

> **Status:** Not Built
> **Consensus:** UNANIMOUS (5/5 panels agree: build first)
> **Cost:** $5-$15/month in Claude API

---

## Purpose

The nervous system of the entire operation. Scans 20+ sources daily for new opportunities, scores them against the existing portfolio, and surfaces the best ones for human review.

## Architecture

```
n8n Workflow: "Daily Opportunity Scanner"
├── Trigger: Daily at 6:00 AM
│
├── Source Scanners (parallel):
│   ├── Reddit API
│   │   ├── r/entrepreneurridealong
│   │   ├── r/microsaas
│   │   ├── r/passive_income
│   │   └── r/SideProject
│   ├── Hacker News API
│   │   ├── Show HN (new launches)
│   │   └── Ask HN (problems people have)
│   ├── Product Hunt API
│   │   └── New launches (competitive intelligence)
│   ├── Kalshi API
│   │   └── New market listings + pricing anomalies
│   ├── Gumroad
│   │   └── Trending products in automation/AI
│   ├── RapidAPI
│   │   └── Trending APIs, new categories
│   ├── Google Trends API
│   │   └── Breakout topics (AI/automation)
│   ├── n8n Community Forum
│   │   └── Popular template requests
│   ├── MCP.so
│   │   └── New server listings
│   └── RSS Feeds
│       └── AI/tech newsletters
│
├── Claude API Scoring (per opportunity):
│   ├── Relevance to existing strategies (0-10)
│   ├── Estimated effort to implement (hours)
│   ├── Estimated revenue potential ($/month)
│   ├── Synergy with current portfolio (0-10)
│   └── Risk assessment (low/medium/high)
│
├── Output:
│   ├── Top 5 → Telegram daily summary
│   ├── Full scored list → Supabase
│   └── Weekly digest → Telegram + this vault
│
└── Feedback Loop:
    └── Human marks as "pursued" / "passed" / "interesting"
        → Updates scoring weights over time
```

## Scoring Prompt Template

```
You are evaluating an opportunity for an automated income portfolio.
Current strategies: Gumroad products, Kalshi weather bot, n8n templates,
AI micro-SaaS, prediction market arb.
Budget: <$50 to implement. Human time: <1 hr/week.

Score this opportunity:
{opportunity_description}

Rate 0-10 on: relevance, effort (inverted), revenue_potential, synergy, risk (inverted)
Provide a 1-sentence recommendation: pursue / watch / skip
```

## Opportunity Log Format

Each opportunity logged to [[Opportunity Log]] with:
- Date found
- Source
- Description
- Scores (5 dimensions)
- Total score
- Decision (pursue / watch / skip / passed)
- Outcome (if pursued)
