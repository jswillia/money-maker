# Portfolio Rebalancing

> **Status:** Not Built (build in Month 3)
> **Consensus:** 4/5 panels recommend (simplified version)

---

## Purpose

Weekly automated analysis of portfolio performance. Recommends capital reallocation using fractional Kelly Criterion. Human approves via Telegram.

## Key Guardrail

**No single strategy ever receives >40% of total capital.** This prevents catastrophic loss from any single strategy failure.

## How It Works

### Strategy Health Score (Computed Daily)

```
Health Score = weighted average of:
  Revenue trend     (30%): Growing, flat, or declining?
  ROI efficiency    (25%): Revenue per dollar deployed
  Time efficiency   (20%): Revenue per hour of human attention
  Growth potential  (15%): Is the market expanding?
  Risk level        (10%): Drawdown, variance
```

| Score | Status | Action |
|---|---|---|
| >70 | Healthy | Consider increasing allocation |
| 40-70 | Watchlist | Maintain current. Investigate. |
| <40 | Critical | Auto-pause trading. Flag for human. |
| <20 for 2 weeks | Terminal | Recommend killing the strategy. |

### Capital Reallocation (Weekly)

1. n8n pulls revenue data from all strategies (Supabase)
2. Compute health score for each
3. Fractional Kelly Criterion suggests allocation percentages
4. Generate recommendation → Telegram
5. Human approves/modifies → execute

### Financial Flows

```
Revenue → Reinvestment Pool → Portfolio Rebalancer
               │                       │
               ├── 80% reinvested ─────┘
               ├── 10% operating costs (Claude API, etc.)
               └── 10% profit withdrawal (after Month 4)
```

## Current Allocation

| Strategy | Allocated | Deployed | Revenue | Health |
|---|---|---|---|---|
| Gumroad Products | $0 | $0 | $0 | -- |
| Kalshi Bot | $25 | $0 | $0 | -- |
| n8n Templates | $0 | $0 | $0 | -- |
| AI Micro-SaaS | $0 | $0 | $0 | -- |
| Prediction Arb | $25 | $0 | $0 | -- |
| Claude API | $10 | $0 | -- | -- |
| Reserve | $35 | -- | -- | -- |
| **Total** | **$100** | **$0** | **$0** | -- |
