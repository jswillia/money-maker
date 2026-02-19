# Strategy 5 — Cross-Platform Prediction Market Arbitrage

> **Consensus Score:** 7 pts | 2/5 panels | **Capital Required:** $25-$50 | **Risk:** Low-Moderate

---

## Status

| Field | Value |
|---|---|
| **Status** | Not Started |
| **Capital Deployed** | $0 |
| **Total P&L** | $0 |
| **Arbs Executed** | 0 |
| **Avg Spread Captured** | -- |
| **Health Score** | -- |
| **Last Updated** | Feb 19, 2026 |

---

## Overview

The only strategy with theoretically guaranteed profit per completed trade. Provides **portfolio insurance** — near-zero correlation with the product strategies. When the same event is priced differently on Kalshi vs. Polymarket, buying both sides locks in a guaranteed spread.

## How It Works

```
Buy "Yes" on Platform A for $0.55
Buy "No" on Platform B for $0.40
Total cost: $0.95 → Guaranteed payout: $1.00
Locked profit: $0.05 (5.3% return)
```

## Compounding via Capital Velocity

The key metric is how many times per month capital completes the cycle:
deploy → lock in arb → contract settles → redeploy

Higher velocity = faster compounding even at small per-trade margins.

## Platforms

| Platform | Regulation | Fees | API | Notes |
|---|---|---|---|---|
| Kalshi | CFTC-regulated | 0% | REST API | Primary platform |
| Polymarket | Unregulated (crypto) | ~1% | CLOB API | Requires crypto wallet |
| PredictIt | CFTC no-action letter | 5% withdrawal | Limited | Smaller markets |

## Revenue Projections (Conservative)

| Month | Capital | Trades/Month | Monthly Return | Ending Capital |
|---|---|---|---|---|
| 1 | $50 | 15-20 | 5-15% | $55 |
| 2 | $55 | 20-25 | 8-15% | $62 |
| 3 | $62 | 20-30 | 8-15% | $70 |
| 4 | $70 | 25-35 | 8-12% | $78 |
| 5 | $78 | 25-35 | 8-12% | $86 |
| 6 | $86 | 30-40 | 5-10% | $92 |

**Realistic 6-month value:** $90-$150. Safety net, not growth engine.

## Circuit Breakers

- **Platform withdrawal delay >7 days:** Stop depositing immediately
- **Edge minimum:** Don't execute arbs with <1.5% spread after fees
- **Capital cap:** Never deploy >$50 total across platforms
- **Regulatory action:** n8n monitors CFTC/SEC news daily; begin withdrawal on enforcement

## Arb Log

| Date | Event | Platform A (Buy) | Platform B (Buy) | Total Cost | Spread | Settlement Date | P&L |
|---|---|---|---|---|---|---|---|
| | | | | | | | |

## Metrics Log

| Week | Arbs Found | Arbs Executed | Capital Deployed | Weekly P&L | Running Total | Notes |
|---|---|---|---|---|---|---|
| | | | | | | |
