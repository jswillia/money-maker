# Operations Guide

> The master document for how this project works, how to run it, and what you need to do as a human. Read this first.

---

## Table of Contents

1. [[#How This All Works]]
2. [[#Partner Architecture — Sharing With a Friend]]
3. [[#Using Claude Max Instead of API Fees]]
4. [[#Human Responsibilities]]
5. [[#How to Launch (Claude Code Prompt)]]
6. [[#Maintenance and Monitoring]]
7. [[#Keeping the System Running]]
8. [[#Cost Breakdown]]
9. [[#Escalation Procedures]]

---

## How This All Works

You have $100. Claude Code builds 5 automated revenue strategies. n8n runs them 24/7 on your Mac Mini. A daily opportunity researcher scans the internet for new ideas. A portfolio rebalancer shifts capital to winners. You spend 30 minutes per week reviewing a Telegram digest and approving decisions.

**The 5 strategies:**

| # | Strategy | Revenue Type | Risk | Capital |
|---|---|---|---|---|
| 1 | Gumroad Digital Products | Product sales | Low | $0 |
| 2 | Kalshi Weather Bot | Trading profits | Moderate | $25 |
| 3 | n8n Workflow Templates | Template sales | Very Low | $0 |
| 4 | AI Micro-SaaS | MRR subscriptions | Moderate | $0-$35 |
| 5 | Prediction Market Arb | Arb spreads | Low-Moderate | $25 |

**The adaptive layer:**
- Daily Researcher scans 20+ sources, scores opportunities
- Portfolio Rebalancer suggests capital moves weekly
- Health Scoring detects failing strategies automatically

See [[Architecture]] for full technical details.

---

## Partner Architecture — Sharing With a Friend

### Recommended Setup: Shared Infrastructure, Separate Capital

Your friend does NOT need their own Mac Mini, n8n instance, or Vercel deployment. Everything runs on your infrastructure. Here's how it works:

### What's Shared (Jeff Hosts)

| Resource | Details |
|---|---|
| **n8n** | All workflows run on your Mac Mini. One set of workflows serves both partners. |
| **Vercel** | One Micro-SaaS deployment. One Gumroad storefront. |
| **Supabase** | One database with partner-tagged records for revenue tracking. |
| **Obsidian Vault** | This vault, shared via git. Both partners can read/update. |
| **Daily Researcher** | One researcher serves both — opportunities are portfolio-wide. |
| **Claude Code** | You run build sessions. Both partners benefit from what's built. |

### What's Separate (Each Partner Owns)

| Resource | Why Separate |
|---|---|
| **Kalshi account** | Regulatory requirement — each person must have their own trading account |
| **Polymarket account** | Same — each person's own crypto wallet |
| **Trading capital ($50 each)** | Each partner's $50 trades in their own account |
| **Trading P&L** | Belongs to whoever's capital generated it |

### Revenue Split

| Revenue Source | Split | Reasoning |
|---|---|---|
| Gumroad product sales | **50/50** | Shared storefront, products built by shared Claude Code |
| Micro-SaaS subscriptions | **50/50** | Shared deployment, shared infrastructure |
| n8n template sales | **50/50** | Products of shared build effort |
| Kalshi trading profits | **100% to account holder** | Each person's own capital and account |
| Prediction market arb profits | **100% to account holder** | Same |

### Cost Sharing

| Cost | Who Pays | Amount |
|---|---|---|
| Infrastructure (Mac Mini, n8n) | **Jeff** | $0 (already running) |
| Claude API (if used beyond Max) | **50/50** | ~$4-20/month each |
| Domain costs | **50/50** | ~$6/year each |
| Vercel (if upgraded from free) | **50/50** | $10/month each |
| Trading capital | **Each their own** | $50 each |

### How the Partner Gets Set Up

1. **Clone the git repo** — `git clone` gives them the vault + all code
2. **Open in Obsidian** — they see the same Dashboard, strategies, and logs
3. **Create their own trading accounts** — Kalshi + Polymarket
4. **Send Jeff their account details** — so trading bots can be configured for their accounts
5. **Venmo/Zelle monthly API cost share** — if any API costs exceed Max subscription

### How the Partner Monitors Their Portfolio

Same as you: weekly Telegram digest, vault updates, approve/reject via Telegram. You can set up a separate Telegram bot or channel for each partner.

### Git Workflow for Sharing

```
Both partners clone the same repo:
  git clone <repo-url>

Jeff pushes updates (new builds, research, vault updates):
  git add . && git commit -m "description" && git push

Partner pulls updates:
  git pull

Partner updates their own portfolio note:
  # Edit Partners/Partner - Portfolio.md
  git add . && git commit -m "Update portfolio numbers" && git push
```

---

## Using Claude Max Instead of API Fees

### The Discovery

Your Claude Max subscription ($100-$200/month) includes unlimited Claude Code CLI access. The Claude Code CLI can be invoked non-interactively from n8n using `claude -p "prompt"`. This bills against your Max subscription quota — **not** per-token API charges.

### How It Works in n8n

Instead of using n8n's built-in "Anthropic" node (which requires a separate API key + pay-per-token billing), use the **Execute Command** node:

```bash
claude -p "Score this opportunity for our portfolio: {{$json.description}}" --output-format json
```

Or via SSH (if n8n runs on a different machine than Claude Code):

```bash
ssh jeffdev@100.96.240.11 'claude -p "Your prompt here" --output-format json'
```

### Three Options (Ranked)

| Option | Setup | Pros | Cons |
|---|---|---|---|
| **1. Execute Command node** | Install Claude Code on n8n host | Simplest. Direct. Fast. | n8n and Claude Code must be on same machine. |
| **2. SSH node** | n8n SSHes to MiniDev | Works if n8n is elsewhere. | Slight latency. SSH key setup. |
| **3. Community node** | Install `@johnlindquist/n8n-nodes-claudecode` | Cleanest UI. Session persistence. MCP support. | Third-party dependency. |

### Recommended Approach

Since both n8n and Claude Code are on MiniDev, **Option 1 (Execute Command)** is simplest:

```
n8n Execute Command node:
  Command: claude -p '{{ $json.prompt }}' --output-format json --model sonnet
  Timeout: 60000
```

**Use Sonnet, not Opus** for automation — it's faster, cheaper on quota, and sufficient for scoring/analysis tasks.

### Quota Management

| Plan | Messages per 5-hour window | Implication |
|---|---|---|
| Max 5x ($100/mo) | ~225 messages | Budget: ~45 messages/hour. Daily Researcher uses ~25. Leaves plenty for interactive use. |
| Max 20x ($200/mo) | ~900 messages | Abundant. No concerns for this project. |

### Hybrid Approach (If Quota Gets Tight)

For high-volume, simple tasks (like classifying 50 Reddit posts), use Claude Haiku via the API at ~$0.25/MTok. For complex analysis, use Max CLI. Total API cost: $1-3/month.

### Key Technical Details

- Claude Code is installed at: `/Users/jeffdev/.claude/` (MiniDev)
- Authenticated with Max subscription (no `ANTHROPIC_API_KEY` env var set)
- Use `--output-format json` for machine-readable output
- Use `--model sonnet` to conserve quota (Sonnet is sufficient for automation)
- Full research: [[Using Claude Max Subscription with n8n — Research]] (in Hobby vault)

---

## Human Responsibilities

### Your Role: Board Member, Not Operator

After the 3-week build phase, your role is:
- **Review** weekly digest (10 min)
- **Decide** on capital moves, new strategies, kills (10 min)
- **Approve** what the system recommends (5 min)
- **Update** this vault with actuals (5 min)

You are NOT:
- Writing code (Claude Code does this)
- Running workflows manually (n8n does this)
- Monitoring dashboards daily (Telegram alerts handle this)
- Creating products (Claude Code creates them)

### Weekly Time Budget: 30 Minutes

| Task | Time | When |
|---|---|---|
| Read Telegram digest | 10 min | Sunday |
| Review opportunities, approve/reject | 10 min | Sunday |
| Update vault metrics | 5 min | Sunday |
| Handle any alerts | 5 min | As needed |

### Monthly Additions: +15 Minutes

| Task | Time | When |
|---|---|---|
| Monthly revenue summary | 5 min | 1st Sunday |
| Partner cost reconciliation | 5 min | 1st Sunday |
| Strategy kill/add review | 5 min | 1st Sunday |

### Things That Require Your Intervention

| Event | What You Do | Urgency |
|---|---|---|
| Telegram: "Strategy health < 40" | Review strategy, decide: investigate or kill | Within 48 hours |
| Telegram: "n8n heartbeat missed" | Check Mac Mini (is it on? is n8n running?) | Within 24 hours |
| Telegram: "Drawdown > 30%" | Bot auto-paused. Review and decide: resume or kill | Within 48 hours |
| Telegram: "Capital move > $20 requested" | Review and approve/reject | Within 1 week |
| Partner asks a question | Answer or point to vault docs | As needed |

---

## How to Launch (Claude Code Prompt)

### Step 1: Open the Vault in Obsidian

1. Open Obsidian
2. Click "Open another vault" (bottom left)
3. Select "Open folder as vault"
4. Navigate to `/Users/jeffdev/dev/git/money-maker/`
5. Click "Open"
6. You should see the Dashboard as your home page

### Step 2: Set Up Accounts (Human — 45 min)

Follow [[Getting Started#Phase 0 Account Setup Human — 45 min one-time]]

### Step 3: Start Building (Claude Code)

Open terminal on MiniDev. Run `claude`. Start with this prompt:

```
I'm starting the Money Maker project. Read /Users/jeffdev/dev/git/money-maker/CLAUDE.md
first, then read Dashboard.md and the Operations Guide.

Start with Session 1: Build the Daily Opportunity Researcher as an n8n workflow.
See System/Daily Researcher.md for the full specification.

Key requirement: For all AI tasks in n8n, use Execute Command node with
"claude -p 'prompt' --output-format json --model sonnet" instead of the
Anthropic API node. This uses our Max subscription.

After building, update the relevant vault notes with the current status.
```

Each subsequent session, point Claude Code at the next task from [[Getting Started#Build Order]].

### Step 4: Go Live

Follow [[Getting Started#Phase 2 Go Live Checklist]]

---

## Maintenance and Monitoring

### Automated Monitoring (You Don't Touch This)

| Monitor | Frequency | Alert Channel | Trigger |
|---|---|---|---|
| n8n heartbeat | Every hour | Telegram | Missed heartbeat = system down |
| Kalshi bot P&L | Every trade + daily summary | Telegram | Every trade, daily P&L |
| Arb scanner | Continuous | Telegram | On arb execution |
| SaaS errors | Every 15 min | Telegram | Any 5xx error |
| Workflow failures | On failure | Telegram | Any n8n workflow error |
| Cost tracking | Daily | Supabase + weekly digest | Daily log |

### Manual Monitoring (Your Weekly Review)

See [[Weekly Review Checklist]] for the exact procedure.

### What Breaks and How to Fix It

| Problem | Symptom | Fix |
|---|---|---|
| n8n stopped | No Telegram heartbeat for 2+ hours | SSH to MiniDev: `pm2 restart n8n` or check if Mac Mini restarted |
| Trading bot losing money | Drawdown alert in Telegram | Bot auto-pauses at 30%. Review [[Strategy 2 - Kalshi Weather Bot]] trading log. Decide: tune parameters or kill. |
| Gumroad products not selling | Zero sales after 3 weeks | Don't panic. Check: are products discoverable? Try different titles/descriptions. Build different product types. |
| SaaS not getting users | <50 users after Month 2 | Distribution problem. Post in different communities. Try Product Hunt launch. Ask Claude Code to improve landing page. |
| API costs spiking | Cost tracking shows >$20/month | Switch more workflows to Max CLI (`claude -p`). Use Haiku for simple tasks. Add caching. |
| Vault out of sync (partner) | Git conflicts | `git pull --rebase` then resolve conflicts. Strategy/log notes should rarely conflict if partners update their own sections. |

### When to Escalate to Claude Code

Start a new Claude Code session when:
- A strategy needs new features or bug fixes
- You want to add a new strategy (from the opportunity log)
- n8n workflows need modification
- The Micro-SaaS needs updates based on user feedback
- You want to create new Gumroad products

Always point Claude Code at the vault first:
```
Read /Users/jeffdev/dev/git/money-maker/CLAUDE.md and the relevant
strategy note before making changes.
```

---

## Keeping the System Running

### Infrastructure Dependencies

| Component | Hosted On | What Happens If It Dies | Recovery |
|---|---|---|---|
| **Mac Mini (MiniDev)** | Your desk | Everything stops | Restart Mac, `pm2 restart all`. All workflows resume. |
| **n8n** | Mac Mini | Automation stops | `pm2 restart n8n`. Workflows are persisted in SQLite. |
| **Vercel** | Cloud | Micro-SaaS goes down | Check Vercel dashboard. Usually auto-recovers. |
| **Supabase** | Cloud | Database unavailable | Check status.supabase.com. Free tier has good uptime. |
| **Claude Code** | Mac Mini | Can't run AI tasks | Check `claude --version`. Re-authenticate if needed. |
| **Tailscale** | Mac Mini + cloud | Can't access remotely | Restart Tailscale: `sudo tailscale up` |
| **Internet** | ISP | Everything external stops | Wait for ISP. Trading bots have stop-losses set server-side. |

### Long-Term Sustainability

| Timeframe | Action |
|---|---|
| **Weekly** | Review and approve via Telegram. Update vault. |
| **Monthly** | Check costs. Reconcile with partner. Review strategy health. |
| **Quarterly** | Full portfolio valuation. Consider adding/killing strategies. Update projections. |
| **If you go on vacation** | System runs autonomously. Trading bots have safety limits. Products sell without you. You just miss the weekly review — do it when you're back. |
| **If Mac Mini needs replacement** | All code is in git. All n8n workflows exportable. Redeploy on any new machine in 2-3 hours. |

### Backup Strategy

| What | How | Frequency |
|---|---|---|
| Vault (this repo) | Git push to GitHub | After every update |
| n8n workflows | Export via n8n API (automated backup workflow exists) | Daily |
| Supabase data | Supabase dashboard → export | Monthly |
| Trading bot config | In git repo | After every change |

---

## Cost Breakdown

### Month 1 Costs (Startup)

| Item | Cost | Notes |
|---|---|---|
| Trading capital (Kalshi) | $25 | Deployed, not spent |
| Trading capital (Arb) | $25 | Deployed, not spent |
| Claude API (if any beyond Max) | $0-$5 | Using Max CLI for most tasks |
| Gumroad listing | $0 | Free to list |
| Vercel | $0 | Free tier |
| Supabase | $0 | Free tier |
| **Total out-of-pocket** | **$0-$5** | Capital is deployed, not spent |

### Monthly Ongoing Costs

| Item | Cost | Notes |
|---|---|---|
| Claude API (overflow beyond Max) | $0-$10 | Only if Max quota insufficient |
| Vercel | $0 | Free tier covers early usage |
| Supabase | $0 | Free tier |
| Domain (shared) | ~$1 | $12/year ÷ 12 |
| Mac Mini electricity | ~$5 | Already running |
| **Total** | **$1-$16/month** | Covered by revenue after Month 2-3 |

### When Revenue Should Cover Costs

By Month 3, even modest traction should generate $50+/month across all strategies — more than enough to cover the $1-$16/month operating costs. The system becomes self-sustaining.

---

## Escalation Procedures

### Level 1: Automated Response (No Human Needed)

- Trading bot drawdown >30% → bot auto-pauses
- n8n workflow error → auto-retry (3 attempts)
- API rate limit → exponential backoff

### Level 2: Telegram Alert (Quick Human Decision)

- Strategy health <40 → review within 48 hours
- Capital move request → approve/reject within 1 week
- New high-scoring opportunity → pursue/watch/skip

### Level 3: Claude Code Session (Build/Fix Required)

- Strategy needs features or bug fixes
- New strategy to add from opportunity log
- Infrastructure issue requiring code changes

### Level 4: Manual Intervention (Rare)

- Mac Mini hardware failure → replace and redeploy from git
- Trading account issue (verification, frozen funds) → contact platform support
- Legal/regulatory change → review affected strategies, decide to continue or exit
