# Getting Started

> Step-by-step instructions to go from zero to running strategies. Each partner follows this independently.

---

## Prerequisites

Before starting, you need:

- [ ] **$100 cash** available to deploy
- [ ] **This vault** open in Obsidian (see [[Git and Obsidian Guide]])
- [ ] **Your API keys** ready (see your Portfolio note)
- [ ] Access to the shared n8n instance at https://n8n.troontech.net

---

## Phase 0: Choose Your Strategies

Read the strategy playbooks in `Strategies/` and decide which to pursue:

| # | Playbook | Capital Required | Risk | Good For |
|---|---|---|---|---|
| 1 | [[Strategy 1 - Gumroad Digital Products]] | $0 | Low | Zero-risk start, builds catalog over time |
| 2 | [[Strategy 2 - Kalshi Weather Bot]] | $25 | Moderate | Active trading with data-driven edge |
| 3 | [[Strategy 3 - n8n Workflow Templates]] | $0 | Very Low | Zero-risk, leverages n8n community |
| 4 | [[Strategy 4 - AI Micro-SaaS]] | $0-35 | Moderate | MRR potential, needs more build time |
| 5 | [[Strategy 5 - Prediction Market Arb]] | $25 | Low-Moderate | Automated arbitrage across platforms |

**Recommendation:** Start with 1-2 strategies. Add more once the first ones are running.

---

## Phase 1: Account Setup (Human — 30-60 min one-time)

Set up accounts based on the strategies you chose. Update your Portfolio note as you go.

### If Running Trading Strategies (#2 or #5)

| Account | Action | Time |
|---|---|---|
| **Kalshi** | Sign up at kalshi.com, verify identity, deposit trading capital | 15 min |
| **Polymarket** | Create account, set up crypto wallet, deposit USDC | 15 min |

### If Running Product Strategies (#1 or #3)

| Account | Action | Time |
|---|---|---|
| **Gumroad** | Sign up as seller at gumroad.com, connect payment | 5 min |

### If Running SaaS Strategy (#4)

| Account | Action | Time |
|---|---|---|
| **Stripe** | Sign up at stripe.com, complete verification | 10 min |
| **Supabase** | Create project at supabase.com | 5 min |
| **Vercel** | Sign up at vercel.com | 5 min |

### For All Partners — API Keys

| Service | What You Need | How to Get It |
|---|---|---|
| **Claude/Anthropic** | API key | console.anthropic.com → API Keys |
| **Gmail** | OAuth or App Password | For email workflows in n8n |

> Set up your credentials directly in n8n at https://n8n.troontech.net → Credentials → Add Credential. Use your name prefix (e.g., `Patrick - Kalshi API`).

---

## Phase 2: Build Your Strategies (Claude Code Sessions)

Each strategy is built in a Claude Code session. Each partner runs their own sessions.

### Claude Code Kickoff Prompt (Template)

```
I'm building my Money Maker stack. Read the CLAUDE.md first, then read
Dashboard.md and my portfolio at [Jeff or Patrick]/Portfolio.md.

I'm running [Strategy Name]. See the playbook at Strategies/[name].md.

Today's task: Build [specific component].

Requirements:
- This is for [Jeff/Patrick]'s stack
- Name all n8n workflows with [Jeff/Patrick] prefix
- Use [my API key / Execute Command with Max sub] for AI tasks
- Update my Portfolio.md when done
```

### Build Order (Suggested — Adapt to Your Strategies)

| Session | What to Build | Notes |
|---|---|---|
| 1 | Your first strategy's core automation | The main revenue-generating workflow |
| 2 | Monitoring + alerts for strategy 1 | Telegram alerts, error handling |
| 3 | Your second strategy's core automation | If you chose a second one |
| 4 | Monitoring + alerts for strategy 2 | Telegram alerts, error handling |
| 5 | Polish, test, optimize | Make everything robust |

### What the Human Does During Build Phase

| When | What | Time |
|---|---|---|
| After each session | Review what was built, test it | 15 min |
| When trading bots are ready | Fund trading accounts | 15 min |
| When products are created | Review and list them | 15 min |
| After all strategies built | Run through go-live checklist below | 30 min |

---

## Phase 3: Go Live Checklist

Before declaring your stack "live":

- [ ] All chosen strategies have working n8n workflows
- [ ] Telegram alerts are working (test each one)
- [ ] Trading bots are paper trading (if applicable)
- [ ] Products are listed and live (if applicable)
- [ ] Your Portfolio.md is updated with "Active" status
- [ ] Your Revenue Tracker is set up
- [ ] You've done one manual weekly review cycle

---

## Phase 4: Steady State

Once live, your weekly time commitment is:

| Task | Time | Frequency |
|---|---|---|
| Review Telegram digest | 10 min | Weekly |
| Review Daily Researcher opportunities | 10 min | Weekly |
| Update your vault folder | 5 min | Weekly |
| Share learnings to playbooks | 5 min | Weekly |
| **Total** | **~30 min** | **Weekly** |

See [[Weekly Review Checklist]] for the exact procedure.
