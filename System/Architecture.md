# System Architecture

> How all the pieces fit together. Shared infrastructure, independent execution.

---

## High-Level Architecture

```
┌─────────────────────────────────────────────────────────┐
│              SHARED INTELLIGENCE LAYER                    │
│                                                          │
│  Daily Researcher → scores opportunities for all partners│
│  Research Archive → 6 domains, 5 expert panels           │
│  Strategy Playbooks → shared how-to guides               │
│  Obsidian Vault → shared knowledge base                  │
└────────────────────────┬────────────────────────────────┘
                         ↓
┌───────────────────────────┬─────────────────────────────┐
│   JEFF'S STACK            │   PATRICK'S STACK           │
│                           │                              │
│  [Jeff] Kalshi Bot        │  [Patrick] Kalshi Bot       │
│  [Jeff] Gumroad Tracker   │  [Patrick] Gumroad Tracker  │
│  [Jeff] Sales Alerts      │  [Patrick] Sales Alerts     │
│  [Jeff] P&L Dashboard     │  [Patrick] P&L Dashboard    │
│                           │                              │
│  Jeff's API keys          │  Patrick's API keys         │
│  Jeff's accounts          │  Patrick's accounts         │
│  Jeff's revenue           │  Patrick's revenue          │
└───────────────┬───────────┴──────────────┬──────────────┘
                ↓                           ↓
┌─────────────────────────────────────────────────────────┐
│              SHARED INFRASTRUCTURE                        │
│                                                          │
│  n8n (Mac Mini) │ Tailscale │ Git/GitHub │ Obsidian     │
│  (both partners' workflows run here)                     │
└─────────────────────────────────────────────────────────┘
```

## Infrastructure Components

| Component | Role | Host | Cost | Shared? |
|---|---|---|---|---|
| **n8n** | Automation backbone (all workflows) | Mac Mini (MiniDev) | $0 (self-hosted) | Shared infra |
| **Vercel** | Hosting for SaaS + landing pages | Cloud (free tier) | $0 | Each partner's own projects |
| **Supabase** | Database, auth, storage | Cloud (free tier) | $0 | Each partner's own projects |
| **Claude API** | Intelligence layer | Cloud | Per-partner | Each pays own |
| **Telegram** | Alerts, human I/O, digests | Cloud | $0 | Separate channels per partner |
| **Gmail** | Email delivery | Cloud (via n8n) | $0 | Each partner's own credentials |
| **Obsidian** | Knowledge base (this vault) | Local + Git sync | $0 | Shared |
| **Tailscale** | Remote access to Mac Mini | Cloud + local | $0 | Shared |
| **Mac Mini** | Always-on compute | Local (MiniDev) | $0 (already running) | Shared |

## n8n Multi-Partner Setup

### Credential Management

Each partner has their own credential sets in n8n:

| Credential | Jeff's | Patrick's |
|---|---|---|
| Gmail OAuth | `Jeff - Gmail` (ID: KZAK2kvzgPUiEBZY) | `Patrick - Gmail` (pending setup) |
| Kalshi API | `Jeff - Kalshi` (pending setup) | `Patrick - Kalshi` (pending setup) |
| Gumroad | `Jeff - Gumroad` (pending setup) | `Patrick - Gumroad` (pending setup) |
| Claude API | Uses Max CLI (`claude -p`) | `Patrick - Anthropic` (pending setup) |
| Polymarket | `Jeff - Polymarket` (pending setup) | `Patrick - Polymarket` (pending setup) |

### Workflow Naming Convention

```
[Jeff] Strategy Name - Component
[Patrick] Strategy Name - Component
[Shared] Daily Researcher
[Shared] System Heartbeat
```

### Workflow Inventory

| # | Workflow | Owner | Purpose | Status |
|---|---|---|---|---|
| 1 | [Shared] Daily Opportunity Scanner | Both | Scrape + score opportunities | Not Built |
| 2 | [Shared] Weekly Opportunity Digest | Both | Compile top opportunities | Not Built |
| 3 | [Shared] System Heartbeat | Jeff | n8n health check | Not Built |
| -- | **Per-Partner Workflows** | | *(built when partner activates a strategy)* | |
| 4+ | [Name] Gumroad Sales Tracker | Per-partner | Log sales | Not Built |
| 5+ | [Name] Kalshi Data Collector | Per-partner | Weather + market data | Not Built |
| 6+ | [Name] Kalshi Trade Bot | Per-partner | Execute trades | Not Built |
| 7+ | [Name] Trade Alerts | Per-partner | Telegram per trade | Not Built |
| 8+ | [Name] SaaS Monitor | Per-partner | Usage + revenue | Not Built |
| 9+ | [Name] Arb Scanner | Per-partner | Multi-platform price scanning | Not Built |
| 10+ | [Name] Portfolio Summary | Per-partner | Weekly revenue digest | Not Built |

## Data Flows

### Shared Intelligence Flow
Daily Scanner → scored opportunities → Obsidian vault + Telegram → Both partners review independently → Each makes own decisions

### Per-Partner Revenue Flow
Partner's workflows → Partner's accounts → Partner's Supabase/tracking → Partner's Telegram digest → Partner's Revenue Tracker in vault

### Per-Partner Trading Flow
Market data → Partner's analysis workflow → Partner's trading account → Partner's trade log → Partner's P&L digest
