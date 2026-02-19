# Operations Guide

> The master document for how this project works and how partners collaborate. Read this first.

---

## Table of Contents

1. [[#How This All Works]]
2. [[#Partner Model — Shared Intelligence, Independent Execution]]
3. [[#What's Shared vs What's Independent]]
4. [[#n8n — Shared Infrastructure, Separate Credentials]]
5. [[#Using Claude Max Instead of API Fees]]
6. [[#Human Responsibilities]]
7. [[#How to Launch (Claude Code Prompt)]]
8. [[#Maintenance and Monitoring]]
9. [[#Keeping the System Running]]
10. [[#Escalation Procedures]]

---

## How This All Works

Two partners (Jeff and Patrick) each invest $100. Claude Code builds automated revenue strategies. n8n runs them 24/7 on Jeff's Mac Mini. A daily opportunity researcher scans the internet for new ideas. Each partner independently chooses which strategies to pursue, manages their own capital, and keeps 100% of their own revenue.

**The shared intelligence layer** means both partners benefit from:
- All research (6 research domains, 5 expert panels)
- Strategy playbooks (detailed guides for 5 proven strategies)
- Daily Opportunity Researcher (one scanner, both benefit)
- This Obsidian vault (shared knowledge base)
- Each other's learnings (what worked, what didn't)

**Independent execution** means:
- You pick which strategies to run
- You fund your own accounts
- You supply your own API keys
- You keep 100% of your revenue
- You manage your own capital allocation

---

## Partner Model — Shared Intelligence, Independent Execution

### Why This Model?

| Model | Problem |
|---|---|
| ~~Shared everything, split 50/50~~ | Disagreements on strategy priority, unequal effort, messy accounting |
| ~~Completely separate projects~~ | Duplicated research, no learning from each other |
| **Shared intelligence + independent execution** | Best of both worlds: learn together, execute independently |

### How It Works

```
SHARED (benefits both)          INDEPENDENT (yours alone)
─────────────────────           ──────────────────────────
Research reports                Your choice of strategies
Strategy playbooks              Your capital allocation
Daily Opportunity Researcher    Your accounts (Kalshi, Gumroad, etc.)
Obsidian vault                  Your API keys and credentials
n8n infrastructure              Your n8n workflows (your creds)
System architecture docs        Your revenue (100%)
Each other's learnings          Your decision-making
```

### Real Example

Both partners read the Gumroad Digital Products playbook. Jeff decides to build AI prompt packs. Patrick decides to build Notion templates. Each uses their own Gumroad account. Each keeps their own revenue. Both update the shared playbook with what they learn (e.g., "Notion templates sell better priced at $7 vs $12").

---

## What's Shared vs What's Independent

### Shared Infrastructure

| Resource | Details |
|---|---|
| **n8n** | Runs on Mac Mini (MiniDev). Both partners have full access. Each partner's workflows use their own credentials. URL: https://n8n.troontech.net |
| **Obsidian Vault** | This vault, shared via git. Both partners read/write. |
| **Daily Researcher** | One opportunity scanner serves both — shared intelligence. |
| **Research** | All research reports in `Research/` benefit everyone. |
| **Strategy Playbooks** | Shared "how to" guides in `Strategies/` — either partner can follow. |

### Independent (Each Partner Owns)

| Resource | Details |
|---|---|
| **Strategies** | Each partner chooses which playbooks to run. Can overlap — that's fine. |
| **Capital ($100)** | Each partner's $100 is entirely their own. No shared pools. |
| **Accounts** | Own Kalshi, Polymarket, Gumroad, Stripe, etc. accounts |
| **API Keys** | Own Claude API key (or use Jeff's Max subscription if Jeff agrees) |
| **Revenue** | 100% yours from your strategies |
| **n8n Workflows** | Your workflows, your credentials. Prefixed with your name: `[Jeff]` or `[Patrick]` |
| **Tracking** | Own `Portfolio.md`, `Revenue Tracker.md`, `Decision Log.md` in your folder |

---

## n8n — Shared Infrastructure, Separate Credentials

### How Multi-Partner n8n Works

n8n runs on the shared Mac Mini (MiniDev) at https://n8n.troontech.net. Both partners have full access. Each workflow uses the owner's credentials.

```
n8n Instance (Jeff's Mac Mini)
├── [Jeff] Kalshi Weather Bot      → Jeff's Kalshi API key
├── [Jeff] Gumroad Sales Tracker   → Jeff's Gumroad token
├── [Jeff] Daily P&L               → Jeff's Gmail OAuth
├── [Patrick] Kalshi Weather Bot   → Patrick's Kalshi API key
├── [Patrick] Gumroad Tracker      → Patrick's Gumroad token
├── [Patrick] Sales Alerts         → Patrick's Gmail/App Password
└── [Shared] Daily Researcher      → Jeff's credentials (shared benefit)
```

### Setting Up Your Credentials in n8n

Each partner sets up their own credentials directly in n8n:

1. Generate API keys for each service you need (see your Portfolio note)
2. Log into n8n at https://n8n.troontech.net
3. Go to **Credentials** → **Add Credential**
4. Name with your prefix: `Patrick - Kalshi API`, `Jeff - Gmail`, etc.
5. Your Claude Code sessions will reference these credentials when building workflows

### Workflow Naming Convention

All n8n workflows include a partner prefix:
- `[Jeff] Kalshi Weather Bot`
- `[Patrick] Kalshi Weather Bot`
- `[Shared] Daily Opportunity Scanner`

---

## Using Claude Max Instead of API Fees

### Jeff's Approach (Max Subscription)

Jeff's Claude Max subscription ($100-$200/month) includes Claude Code CLI access. For Jeff's workflows, use the **Execute Command** node:

```bash
claude -p "Score this opportunity" --output-format json --model sonnet
```

This bills against Jeff's Max subscription — **not** per-token API charges.

### Patrick's Approach (Own API Key)

Patrick has two options:

| Option | Pros | Cons |
|---|---|---|
| **Own Claude API key** | Full independence, clear billing | Pay-per-token (~$5-15/month for this project) |
| **Use shared Max sub** | No per-token cost | Consumes shared quota; requires Execute Command node setup |

**Recommended:** Patrick starts with his own API key for independence. If costs are too high, discuss sharing Jeff's Max subscription.

For Patrick's workflows with his own API key, use the standard **Anthropic** node in n8n (not Execute Command).

### Quota Management (Jeff's Max)

| Plan | Messages per 5-hour window | Implication |
|---|---|---|
| Max 5x ($100/mo) | ~225 messages | Budget: ~45/hour. Shared Daily Researcher uses ~25/day. Leaves plenty for interactive use. |
| Max 20x ($200/mo) | ~900 messages | Abundant. No concerns. |

---

## Human Responsibilities

### Each Partner's Role: Board Member, Not Operator

After your strategies are built, your weekly role is:
- **Review** your Telegram digest (10 min)
- **Decide** on capital moves, new strategies, kills (10 min)
- **Update** your vault folder with actuals (5 min)
- **Share learnings** — update strategy playbooks with what you discover (5 min)

### Weekly Time Budget: 30 Minutes Per Partner

| Task | Time | When |
|---|---|---|
| Read your Telegram digest | 10 min | Sunday |
| Review opportunities, approve/reject | 10 min | Sunday |
| Update your vault folder (portfolio, revenue) | 5 min | Sunday |
| Share learnings to playbooks | 5 min | Sunday |

### Things That Require Your Intervention

| Event | What You Do | Urgency |
|---|---|---|
| Telegram: "Strategy health < 40" | Review your strategy, decide: investigate or kill | Within 48 hours |
| Telegram: "n8n heartbeat missed" | Either partner: SSH to MiniDev and restart n8n | Within 24 hours |
| Telegram: "Drawdown > 30%" | Bot auto-paused. Review and decide: resume or kill | Within 48 hours |
| Partner shares a learning | Read it, consider applying to your strategies | Next weekly review |

---

## How to Launch (Claude Code Prompt)

### Step 1: Choose Your Strategies

Read the playbooks in `Strategies/` and decide which ones to pursue. You don't have to run all 5. Start with 1-2 and add more later.

### Step 2: Set Up Accounts

Based on the strategies you chose, create the necessary accounts (see your `Portfolio.md`).

### Step 3: Start Building (Claude Code)

Open terminal. Run `claude`. Start with this prompt (adjust for your name and strategies):

```
I'm starting my Money Maker stack. Read the CLAUDE.md first, then read
Dashboard.md and my portfolio at [Jeff/Portfolio.md or Patrick/Portfolio.md].

I've chosen to start with [Strategy X] and [Strategy Y].

Build the first strategy: [Strategy X]. See the playbook at
Strategies/[strategy name].md for implementation details.

Key requirements:
- This is for [Jeff/Patrick]'s independent stack
- Name all n8n workflows with [Jeff/Patrick] prefix
- Use [my credentials / Execute Command with Max sub] for AI tasks
- Update my Portfolio.md and Revenue Tracker when done
```

### Step 4: Repeat for Each Strategy

Each Claude Code session, build the next strategy from your chosen list. Update your portfolio after each session.

---

## Maintenance and Monitoring

### Automated Monitoring (Per Partner)

Each partner gets their own monitoring workflows:

| Monitor | What It Watches | Alert Channel |
|---|---|---|
| Trading bot P&L | Your bot, your account | Your Telegram |
| Sales tracker | Your Gumroad/Stripe | Your Telegram |
| Workflow failures | Your workflows | Your Telegram |

### Shared Monitoring (Either Partner Can Check)

| Monitor | Frequency | What It Checks |
|---|---|---|
| n8n heartbeat | Hourly | Is the shared n8n instance running? |
| Daily Researcher | Daily | Did the opportunity scanner run? |
| System health | Weekly | Mac Mini, Tailscale, storage |

### What Breaks and How to Fix It

| Problem | Who Fixes | How |
|---|---|---|
| n8n stopped | Either | SSH to MiniDev: `pm2 restart n8n` |
| Your trading bot losing money | You | Bot auto-pauses at 30% drawdown. Review trading log. |
| Your products not selling | You | Check playbook circuit breakers. Try different approach. |
| Shared Daily Researcher broken | Either | Check n8n execution logs at https://n8n.troontech.net. Fix and restart. |
| Vault out of sync | Either | `git pull --rebase` then resolve conflicts |

---

## Keeping the System Running

### Infrastructure Dependencies

| Component | Hosted On | Recovery |
|---|---|---|
| **Mac Mini (MiniDev)** | Physical machine | Restart Mac, `pm2 restart all`. All workflows resume. |
| **n8n** | Mac Mini | `pm2 restart n8n`. Workflows persisted in SQLite. |
| **Tailscale** | Mac Mini + cloud | `sudo tailscale up` |

### Long-Term Sustainability

| Timeframe | Action |
|---|---|
| **Weekly** | Each partner reviews their own digest. Updates their vault folder. |
| **Monthly** | Review API costs. Compare notes on what's working. |
| **Quarterly** | Full portfolio valuation. Consider adding/killing strategies. |
| **If a partner goes on vacation** | System runs autonomously. Trading bots have safety limits. All workflows keep running. |
| **If Mac Mini needs replacement** | All code in git. n8n workflows exportable. Redeploy in 2-3 hours. |

---

## Escalation Procedures

### Level 1: Automated Response (No Human Needed)
- Trading bot drawdown >30% → bot auto-pauses
- n8n workflow error → auto-retry (3 attempts)
- API rate limit → exponential backoff

### Level 2: Telegram Alert (Quick Decision — Your Own Strategies)
- Strategy health <40 → review within 48 hours
- Capital move request → approve/reject
- New high-scoring opportunity from Daily Researcher → pursue/watch/skip

### Level 3: Claude Code Session (Build/Fix Required)
- Strategy needs features or bug fixes
- New strategy to add from opportunity log
- Infrastructure issue requiring code changes

### Level 4: Manual Intervention (Rare)
- Mac Mini hardware failure → replace and redeploy from git
- Trading account issues → contact platform support yourself
- Legal/regulatory change → review and decide independently
