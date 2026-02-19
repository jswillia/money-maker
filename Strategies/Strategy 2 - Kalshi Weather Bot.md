# Strategy 2 — Kalshi Weather Prediction Market Bot

> **Consensus Score:** 11 pts | 3/5 panels | **Capital Required:** $25-$50 | **Risk:** Moderate

---

## Status

| Field | Value |
|---|---|
| **Status** | Not Started |
| **Capital Deployed** | $0 |
| **Bankroll** | $0 |
| **Win Rate** | -- |
| **Total P&L** | $0 |
| **Health Score** | -- |
| **Last Updated** | Feb 19, 2026 |

---

## Overview

The only strategy with a documented case of $204 turning into $24,000+. Weather prediction markets are inefficient — most participants trade on intuition while NOAA publishes probabilistic forecasts for free. Kalshi is CFTC-regulated, US-legal, 0% trading fees.

## How It Works

1. n8n fetches NOAA/Open-Meteo weather probability data every 30 minutes
2. Bot compares weather model probabilities to Kalshi market prices
3. When market misprices an event by >X%, bot takes a position
4. Kelly Criterion sizes each position to maximize growth while limiting ruin risk
5. Profits automatically increase bankroll → more positions → more profit

## Architecture

```
Data Collection (n8n, every 30 min)
├── Weather API (Open-Meteo) — free
├── Kalshi market prices — free API
├── Historical accuracy log
└── News headlines (RSS)
         ↓
Analysis Layer (Python + Claude)
├── Compare forecasts vs market prices
├── Identify mispriced contracts
├── Kelly criterion position sizing
└── Generate trade recommendation
         ↓
Execution Layer (Python + Kalshi API)
├── Place order if confidence > threshold
├── Max position: 10% of bankroll
├── Daily loss limit: 20% of bankroll
└── Log all trades
         ↓
Monitoring (n8n)
├── Telegram alert on every trade
├── Daily P&L summary
├── Weekly accuracy report
└── Alert if drawdown exceeds threshold
```

## Risk Controls

- **Hard stop-loss:** Bot pauses at 30% drawdown from peak
- **Position sizing:** Never risk >5% of capital on a single contract
- **Paper trading:** 2-4 weeks before real money
- **Daily loss limit:** 20% of bankroll
- **Telegram alerts:** Every trade, daily P&L

## Revenue Projections (Conservative)

| Month | Capital | Monthly Return | Ending Capital |
|---|---|---|---|
| 1 | $50 | 20-40% | $65 |
| 2 | $65 | 30-50% | $90 |
| 3 | $90 | 30-50% | $125 |
| 4 | $125 | 30-50% | $175 |
| 5 | $175 | 25-40% | $230 |
| 6 | $230 | 25-40% | $300 |

**Realistic 6-month value:** $300-$1,500 (wide range reflects trading variance).

> **Survivorship bias warning:** The $204→$24K story is one trader. Conservative modeling is essential.

## Trading Log

| Date | Market | Direction | Size | Entry | Exit | P&L | Running Total |
|---|---|---|---|---|---|---|---|
| | | | | | | | |

## Weekly Metrics

| Week | Trades | Win Rate | Weekly P&L | Bankroll | Drawdown | Notes |
|---|---|---|---|---|---|---|
| | | | | | | |
