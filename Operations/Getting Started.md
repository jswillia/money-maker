# Getting Started

> Step-by-step instructions to go from zero to a running Money Maker system.

---

## Prerequisites

Before starting, you need:

- [ ] **$100 cash** available to deploy
- [ ] **Claude Max subscription** (already active — bills CLI usage)
- [ ] **MiniDev Mac Mini** running with n8n (already running)
- [ ] **This vault** open in Obsidian

---

## Phase 0: Account Setup (Human — 45 min one-time)

### Trading Accounts

| Account | Action | Time | Notes |
|---|---|---|---|
| **Kalshi** | Sign up at kalshi.com, complete identity verification, deposit $25 | 15 min | CFTC-regulated. US ID required. |
| **Polymarket** | Create account, set up crypto wallet, deposit $25 worth of USDC | 15 min | Requires MetaMask or similar wallet. |

### Product Accounts

| Account | Action | Time | Notes |
|---|---|---|---|
| **Gumroad** | Sign up as seller at gumroad.com, connect payment method | 5 min | Free to list. 10% fee per sale. |
| **Stripe** | Sign up at stripe.com, complete business verification | 10 min | For Micro-SaaS payments. |

### Infrastructure (Already Exists)

These are already set up on MiniDev:
- [x] n8n (self-hosted)
- [x] Claude Code CLI
- [x] Tailscale remote access
- [x] Telegram bot
- [x] Gmail OAuth in n8n

### Optional

| Account | Action | When |
|---|---|---|
| Supabase | Create project at supabase.com | Week 2 (before Micro-SaaS build) |
| Vercel | Sign up at vercel.com | Week 2 (before Micro-SaaS deploy) |
| Chrome Dev | Pay $5 at chrome.google.com/webstore/devconsole | Only if pursuing Chrome extension |

---

## Phase 1: Build the System (Claude Code — Week 1-3)

### Claude Code Kickoff Prompt

Open a terminal on MiniDev and run `claude`. Paste this prompt:

```
I'm building the Money Maker 6-Month Compounding Machine. This is an
automated income portfolio: $100 starting capital, 5 strategies, <1hr/week
human time after initial build.

This project has an Obsidian vault at /Users/jeffdev/dev/git/money-maker
with a CLAUDE.md, strategy notes, and full architecture docs. Read the
CLAUDE.md and Dashboard.md first to understand the project.

Today's task: Build the Daily Opportunity Researcher as an n8n workflow.

Requirements:
- n8n workflow triggered daily at 6:00 AM
- Scans: Reddit (r/entrepreneurridealong, r/microsaas), Hacker News
  (Show HN), Product Hunt, Gumroad trending, Kalshi new markets,
  n8n community forum
- Each opportunity scored by Claude (use claude -p via Execute Command
  node to leverage Max subscription — see System/Architecture.md)
- Scores: relevance, effort, revenue_potential, synergy, risk (each 0-10)
- Output: Top 5 to Telegram, full list to Supabase
- Update the Daily Researcher note in the vault when done

IMPORTANT: For AI tasks in n8n, use the Execute Command node with
"claude -p 'prompt here' --output-format json" instead of the Anthropic
API node. This uses our Max subscription instead of pay-per-token billing.
```

### Build Order

Follow this sequence. Each session is a Claude Code session:

| Session | Day | What to Build | Strategy | Time |
|---|---|---|---|---|
| 1 | Day 1 | Daily Opportunity Researcher (n8n) | Meta-A | 2-3 hrs |
| 2 | Day 2 | Kalshi weather bot (NOAA + Kelly + API) | Strategy 2 | 3-4 hrs |
| 3 | Day 3 | Cross-platform arb scanner | Strategy 5 | 2-3 hrs |
| 4 | Day 4 | First 3-5 Gumroad digital products | Strategy 1 | 2-3 hrs |
| 5 | Day 5 | 2 n8n workflow templates | Strategy 3 | 1-2 hrs |
| 6 | Day 8 | 3 more Gumroad products | Strategy 1 | 2 hrs |
| 7 | Day 9-10 | Micro-SaaS MVP (contract analyzer) | Strategy 4 | 4-5 hrs |
| 8 | Day 11 | Deploy SaaS to Vercel + Stripe | Strategy 4 | 2 hrs |
| 9 | Day 12 | Monitoring dashboards + Telegram alerts | All | 2 hrs |
| 10 | Day 15-19 | Polish, launch, start paper trading | All | 3 hrs |

### What the Human Does During Build Phase

| When | What | Time |
|---|---|---|
| After Session 2 | Fund Kalshi account with $25 | 15 min |
| After Session 3 | Fund Polymarket with $25 USDC | 15 min |
| After Session 4 | Review Gumroad products, list them | 15 min |
| After Session 7 | Review Micro-SaaS MVP, test it | 15 min |
| Day 16 | Review paper trading results | 30 min |
| Day 17 | Approve switching Kalshi bot to live | 10 min |
| Day 15 | Post Micro-SaaS in 2-3 communities | 30 min |

**Total human time during build phase:** ~3 hours over 3 weeks (front-loaded).

---

## Phase 2: Go Live Checklist

Before declaring the system "live":

- [ ] Daily Researcher running daily at 6 AM
- [ ] Kalshi bot paper trading (or live if profitable)
- [ ] Arb scanner monitoring prices across platforms
- [ ] At least 3 Gumroad products listed and live
- [ ] At least 2 n8n templates listed on Gumroad
- [ ] Micro-SaaS deployed and accepting signups
- [ ] Telegram alerts working (test each one)
- [ ] Portfolio monitoring dashboard sending weekly summary
- [ ] All strategy notes in vault updated with "Active" status
- [ ] [[Dashboard]] updated with current status

---

## Phase 3: Steady State

Once live, your weekly time commitment is:

| Task | Time | Frequency |
|---|---|---|
| Review weekly Telegram digest | 10 min | Weekly |
| Review Daily Researcher opportunities | 10 min | Weekly |
| Approve/reject capital moves via Telegram | 5 min | As needed |
| Update this vault's metrics | 5 min | Weekly |
| **Total** | **~30 min** | **Weekly** |

See [[Weekly Review Checklist]] for the exact procedure.
