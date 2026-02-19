# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is the **Money Maker** project — two partners each invest $100 into automated revenue strategies. They share an intelligence layer (research, playbooks, opportunity scanning) but run independent stacks (own strategies, capital, accounts, API keys, revenue).

**Vault:** This repository IS an Obsidian vault. The `.obsidian/` folder contains vault configuration. All markdown files are Obsidian notes with wikilinks (`[[note name]]`).

## Partner Model: Shared Intelligence, Independent Execution

- **Jeff** and **Patrick** each invest $100 independently
- **Shared:** Research, strategy playbooks, Daily Researcher, Obsidian vault, n8n infrastructure (Jeff's Mac Mini)
- **Independent:** Each partner chooses their own strategies, manages their own capital, owns 100% of their revenue, supplies their own API keys/credentials
- **n8n workflows:** Each partner has their own workflows using their own credentials. Both run on Jeff's n8n instance.

## Repository Structure

```
money-maker/
├── Dashboard.md              ← Start here. Project home page.
├── Jeff/                     ← Jeff's independent stack
│   ├── Portfolio.md          ← Jeff's strategies, capital, accounts
│   ├── Revenue Tracker.md    ← Jeff's revenue tracking
│   └── Decision Log.md       ← Jeff's decisions
├── Patrick/                  ← Patrick's independent stack
│   ├── Portfolio.md          ← Patrick's strategies, capital, accounts
│   ├── Revenue Tracker.md    ← Patrick's revenue tracking
│   └── Decision Log.md       ← Patrick's decisions
├── Strategies/               ← Shared strategy playbooks (how-to guides)
│   ├── Strategy 1 - Gumroad Digital Products.md
│   ├── Strategy 2 - Kalshi Weather Bot.md
│   ├── Strategy 3 - n8n Workflow Templates.md
│   ├── Strategy 4 - AI Micro-SaaS.md
│   └── Strategy 5 - Prediction Market Arb.md
├── Operations/               ← Shared operational guides
│   ├── Operations Guide.md   ← Master operational plan
│   ├── Getting Started.md    ← Step-by-step launch instructions
│   ├── Weekly Review Checklist.md
│   └── Git and Obsidian Guide.md
├── Research/                 ← Shared intelligence (all research reports)
├── System/                   ← Architecture, infrastructure, adaptive layer
│   ├── Architecture.md
│   ├── Daily Researcher.md
│   └── Portfolio Rebalancing.md
├── Logs/                     ← Shared operational logs
│   ├── Opportunity Log.md    ← Daily researcher output (shared)
│   └── Performance Log.md    ← System health (shared)
└── .obsidian/                ← Vault config (do not modify manually)
```

## Key Conventions

### When Building Strategies for a Partner
- Read their `Portfolio.md` to understand what strategies they're running
- Update their `Revenue Tracker.md` and `Decision Log.md`, not shared files
- Each partner's n8n workflows use THEIR credentials, not the other partner's
- Update the strategy playbook in `Strategies/` if you learn something useful (benefits both)

### When Building n8n Workflows
- Reference the workflow inventory in `System/Architecture.md`
- **CRITICAL:** Each partner has their own credentials in n8n. Name workflows with partner prefix: `[Jeff] Kalshi Bot`, `[Patrick] Gumroad Tracker`
- The n8n instance runs on MiniDev Mac Mini at localhost:5678
- Jeff's Gmail credential ID: `KZAK2kvzgPUiEBZY`
- Patrick's credentials: See `Patrick/Portfolio.md` for status
- **IMPORTANT:** Webhook nodes must include `webhookId` field matching the `path` value

### When Creating Research
- All research goes in `Research/` folder — it's shared intelligence
- Link from relevant strategy playbooks using wikilinks

### Infrastructure
- **n8n:** Self-hosted on Jeff's Mac Mini (MiniDev) — shared by both partners
- **Vercel:** Free tier — each partner can have their own projects
- **Supabase:** Free tier — each partner can have their own projects
- **Claude API:** Each partner uses their own API key (or Jeff's Max subscription for Jeff's workflows)
- **Telegram:** Alerts and human I/O — separate channels per partner
- **Git repo:** `https://github.com/jswillia/money-maker`
- **Local path (Jeff):** `/Users/jeffdev/Library/Mobile Documents/iCloud~md~obsidian/Documents/Money-Maker`

### Obsidian Link Format
Use wikilinks: `[[note name]]` or `[[note name|display text]]`
