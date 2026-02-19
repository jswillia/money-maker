# System Architecture

> How all the pieces fit together.

---

## High-Level Architecture

```
┌─────────────────────────────────────────────────────────┐
│                 HUMAN INTERFACE LAYER                    │
│                                                         │
│  Weekly Digest (Telegram)     Decision Queue (Telegram) │
│  ├── Portfolio P&L summary    ├── Capital moves > $20   │
│  ├── Strategy health scores   ├── New strategy proposals│
│  ├── Top 3 opportunities      ├── Strategy kill decisions│
│  ├── A/B test results         └── Pricing changes       │
│  └── System health / costs                              │
└────────────────────────┬────────────────────────────────┘
                         ↓
┌─────────────────────────────────────────────────────────┐
│                META-STRATEGY LAYER                       │
│                                                         │
│  Daily Researcher → Portfolio Rebalancer → A/B Testing  │
│  (scans 20+ sources) (fractional Kelly)  (month 2-3)   │
└────────────────────────┬────────────────────────────────┘
                         ↓
┌─────────────────────────────────────────────────────────┐
│                REVENUE STRATEGIES                        │
│                                                         │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐  │
│  │ Gumroad  │ │ Kalshi   │ │ n8n      │ │ Micro-   │  │
│  │ Products │ │ Weather  │ │ Templates│ │ SaaS     │  │
│  │          │ │ Bot      │ │          │ │          │  │
│  └──────────┘ └──────────┘ └──────────┘ └──────────┘  │
│                    ┌──────────┐                         │
│                    │ Pred Mkt │                         │
│                    │ Arb      │                         │
│                    └──────────┘                         │
└────────────────────────┬────────────────────────────────┘
                         ↓
┌─────────────────────────────────────────────────────────┐
│                INFRASTRUCTURE                            │
│                                                         │
│  n8n (Mac Mini) │ Vercel │ Supabase │ Claude API       │
│  Telegram       │ Gmail  │ Obsidian │ Tailscale        │
└─────────────────────────────────────────────────────────┘
```

## Infrastructure Components

| Component | Role | Host | Cost |
|---|---|---|---|
| **n8n** | Automation backbone (all workflows) | Mac Mini (MiniDev) | $0 (self-hosted) |
| **Vercel** | Hosting for Micro-SaaS + landing pages | Cloud (free tier) | $0 |
| **Supabase** | Database, auth, storage | Cloud (free tier) | $0 |
| **Claude API** | Intelligence layer for scoring, analysis, content | Cloud | $8-$40/month |
| **Telegram** | Alerts, human I/O, daily digests | Cloud | $0 |
| **Gmail** | Email delivery, notifications | Cloud (via n8n OAuth) | $0 |
| **Obsidian** | Knowledge base (this vault) | Local + Git sync | $0 |
| **Tailscale** | Remote access to Mac Mini | Cloud + local | $0 |
| **Mac Mini** | Always-on compute for bots + n8n | Local (MiniDev) | $0 (already running) |

## n8n Workflow Inventory

| # | Workflow | Purpose | Strategy | Status |
|---|---|---|---|---|
| 1 | Daily Opportunity Scanner | Scrape + score opportunities | Meta-A | Not Built |
| 2 | Weekly Opportunity Digest | Compile top opportunities | Meta-A | Not Built |
| 3 | Gumroad Sales Tracker | Log sales to Supabase | Strategy 1 | Not Built |
| 4 | Social Promotion Engine | Generate + post content | Strategy 1 | Not Built |
| 5 | Product Idea Generator | Trending search → ideas | Strategy 1 | Not Built |
| 6 | Kalshi Data Collector | Weather + market prices | Strategy 2 | Not Built |
| 7 | Kalshi Trade Alerts | Telegram per trade | Strategy 2 | Not Built |
| 8 | Kalshi Daily P&L | Daily profit/loss summary | Strategy 2 | Not Built |
| 9 | SaaS Usage Monitor | Check limits approaching | Strategy 4 | Not Built |
| 10 | SaaS Onboarding Drip | Day 0/1/3/7 emails | Strategy 4 | Not Built |
| 11 | SaaS Revenue Dashboard | Stripe data → Supabase | Strategy 4 | Not Built |
| 12 | Arb Price Scanner | Multi-platform scanning | Strategy 5 | Not Built |
| 13 | Arb Trade Alerts | Execution + settlement | Strategy 5 | Not Built |
| 14 | Portfolio Weekly Summary | Aggregate all revenue | Meta-C | Not Built |

## Data Flows

### Revenue Tracking
All strategies → Supabase `revenue` table → Portfolio Weekly Summary → Telegram digest + this vault

### Opportunity Pipeline
Daily Scanner → scored opportunities → Supabase `opportunities` table → Weekly digest → Human review → Decision Log

### Trading Operations
NOAA data + Kalshi prices → Analysis → Trade execution → Trade log → Daily P&L → Weekly metrics
