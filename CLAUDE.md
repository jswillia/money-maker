# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is the **Money Maker** project — an automated income portfolio aiming to turn $100 into maximum value over 6 months. Claude Code builds everything, n8n automates everything, the system adapts itself.

**Vault:** This repository IS an Obsidian vault. The `.obsidian/` folder contains vault configuration. All markdown files are Obsidian notes with wikilinks (`[[note name]]`).

## Repository Structure

```
money-maker/
├── Dashboard.md              ← Start here. Project home page.
├── Operations/               ← Human procedures and guides
│   ├── Operations Guide.md   ← Master operational plan
│   ├── Getting Started.md    ← Step-by-step launch instructions
│   └── Weekly Review Checklist.md
├── Strategies/               ← One note per strategy with status + metrics
│   ├── Strategy 1 - Gumroad Digital Products.md
│   ├── Strategy 2 - Kalshi Weather Bot.md
│   ├── Strategy 3 - n8n Workflow Templates.md
│   ├── Strategy 4 - AI Micro-SaaS.md
│   └── Strategy 5 - Prediction Market Arb.md
├── Research/                 ← All research reports
├── System/                   ← Architecture, infrastructure, adaptive layer
│   ├── Architecture.md
│   ├── Daily Researcher.md
│   └── Portfolio Rebalancing.md
├── Logs/                     ← Operational logs
│   ├── Opportunity Log.md
│   ├── Decision Log.md
│   ├── Revenue Tracker.md
│   └── Performance Log.md
├── Partners/                 ← Per-partner capital tracking
│   ├── Jeff - Portfolio.md
│   └── Partner - Portfolio.md
└── .obsidian/                ← Vault config (do not modify manually)
```

## Key Conventions

### When Building Strategies
- Each strategy has a dedicated note in `Strategies/` — update the Status table and Metrics Log after every build session
- Log all significant decisions in `Logs/Decision Log.md` with context and reasoning
- Update `Dashboard.md` strategy status table when status changes

### When Building n8n Workflows
- Reference the workflow inventory in `System/Architecture.md`
- Update workflow status from "Not Built" to "Active" when deployed
- The n8n instance runs on MiniDev Mac Mini (this machine) at localhost:5678
- Gmail credential ID: `KZAK2kvzgPUiEBZY`
- **IMPORTANT:** Webhook nodes must include `webhookId` field matching the `path` value

### When Creating Research
- All research goes in `Research/` folder
- Link from relevant strategy notes using wikilinks

### Infrastructure
- **n8n:** Self-hosted on this Mac Mini (MiniDev)
- **Vercel:** Free tier for hosting web apps
- **Supabase:** Free tier for database + auth
- **Claude API:** Used for scoring, analysis, content generation
- **Telegram:** Alerts and human I/O
- **Git repo:** `https://github.com/jswillia/money-maker`
- **Local path (Jeff):** `/Users/jeffdev/Library/Mobile Documents/iCloud~md~obsidian/Documents/Money-Maker`

### Obsidian Link Format
Use wikilinks: `[[note name]]` or `[[note name|display text]]`

### Partner Model
Two partners share infrastructure but track capital separately. See `Partners/` for individual portfolios. Revenue from shared products (Gumroad, SaaS) is split 50/50. Trading profits belong to the account holder.
