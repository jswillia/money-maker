# Automated Money-Making Strategies: AI Agent + n8n Orchestration

**Research compiled: February 19, 2026**
**Budget: $100 | Goal: $200 in 7 days | Constraint: Minimal human involvement**

This report focuses exclusively on strategies that can be automated by Claude Code, n8n workflows, APIs, and scripts. The human owner should only need to make initial setup decisions and approve key actions.

---

## Executive Summary: Realistic Assessment

| # | Strategy | Automation Level | $100 Budget Fit | 7-Day $200 Realistic? | Risk Level |
|---|----------|-----------------|-----------------|----------------------|------------|
| 1 | Prediction Market Arbitrage Bot | 85-95% automated | Yes ($100 as capital) | Possible but unlikely | HIGH |
| 2 | Digital Product Creation + Listing | 90% automated | Yes ($0-20 in fees) | No (takes 2-8 weeks) | LOW |
| 3 | Automated Affiliate Blog | 95% automated | Yes ($10-30 hosting) | No (takes 1-3 months) | LOW |
| 4 | Sell API Access on RapidAPI | 80% automated | Yes ($5-20 hosting) | Unlikely (takes 2-4 weeks) | LOW |
| 5 | AI Newsletter (Substack/Beehiiv) | 70% automated | Yes ($0 startup) | No (takes 1-3 months) | LOW |
| 6 | n8n Workflow Templates for Sale | 60% automated | Yes ($0-20) | Unlikely | LOW |
| 7 | Cold Email Lead Gen Service | 75% automated | No ($39+/mo tools) | Possible with client | MEDIUM |
| 8 | Web Scraping + Data Reports | 80% automated | Yes ($5-20 hosting) | Unlikely (needs buyers) | MEDIUM |
| 9 | Crypto Spot-Futures Arbitrage | 95% automated | Tight ($100 capital) | Barely (0.3-1%/week) | HIGH |
| 10 | Social Media Content Automation | 85% automated | Yes ($0-20) | No (audience takes time) | LOW |

**Honest bottom line:** There is no reliable way to automatically turn $100 into $200 in 7 days with zero human involvement. The strategies below are real, but the ones that can actually double money in a week (prediction markets, crypto) carry significant loss risk. The ones that are low-risk (digital products, blogs, newsletters) take weeks to months before generating revenue. The best approach combines a high-risk/high-reward play with $50-70 of the budget alongside seeding multiple long-term automated income streams with the rest.

---

## Strategy 1: Prediction Market Arbitrage Bot

**Automation level: 85-95%**
**What Claude Code builds: The entire bot**
**What n8n does: Monitoring, alerting, execution scheduling**
**Budget allocation: $100 (all as trading capital)**

### How It Works

Prediction markets (Polymarket, Kalshi) price events as shares between $0.01 and $0.99. When the same event is priced differently across platforms, buying the cheap side on one and the expensive side on the other can lock in risk-free profit.

Example: "Will Bitcoin close above $100K on Friday?"
- Polymarket prices YES at $0.55
- Kalshi prices NO at $0.40
- Total cost: $0.55 + $0.40 = $0.95
- Guaranteed payout: $1.00
- Risk-free profit: $0.05 per share pair (5.3% return)

### APIs and Tools

| Tool | Purpose | Cost |
|------|---------|------|
| [Kalshi API](https://docs.kalshi.com) | REST API, free, CFTC-regulated, US-legal | Free (min deposit $1) |
| [Polymarket CLOB API](https://docs.polymarket.com) | WebSocket + REST, crypto-native | Free (needs USDC on Polygon) |
| [Dome API](https://dome.market) | Unified API across both platforms | Free tier available |
| [PolyRouter](https://polyrouter.com) | Normalized data from Kalshi + Polymarket | Free tier available |
| [Predly](https://predly.com) | AI-powered mispricing detection, 89% alert accuracy | Subscription |

### Open Source Bots (GitHub)

- **[ImMike/polymarket-arbitrage](https://github.com/ImMike/polymarket-arbitrage)** - Python, watches 10,000+ markets, cross-platform arbitrage detection, market making, risk management, live dashboard
- **[CarlosIbCu/polymarket-kalshi-btc-arbitrage-bot](https://github.com/CarlosIbCu/polymarket-kalshi-btc-arbitrage-bot)** - Focuses on Bitcoin 1-hour price markets between Polymarket and Kalshi
- **[realfishsam/prediction-market-arbitrage-bot](https://github.com/realfishsam/prediction-market-arbitrage-bot)** - Built with pmxt.dev, auto-buy low / sell high
- **[Polyseer](https://github.com/Polyseer)** - Open-source AI research platform using multi-agent architecture and Bayesian probability aggregation

### What Claude Code Can Build

1. **Market scanner**: Python script that polls both Kalshi and Polymarket APIs every 30-60 seconds, matching identical events across platforms
2. **Arbitrage detector**: Compares prices, flags opportunities where combined cost < $1.00
3. **Execution engine**: Places orders via API when spread exceeds threshold (e.g., > 3%)
4. **n8n monitoring workflow**: Sends Slack/email alerts on executions, daily P&L summaries, error notifications

### Realistic Returns

- Arbitrage spreads typically range 0.5-3% per opportunity
- Opportunities close within seconds to minutes (speed matters)
- Over $40 million in arbitrage profits were extracted from prediction markets between April 2024 and April 2025
- One documented bot ("0x8dxd") turned $313 into $437,600 in roughly one month (extreme outlier, not replicable by retail)
- **Realistic expectation with $100**: $1-10/week in pure arbitrage, highly variable
- **With AI-informed directional bets** (not pure arbitrage): higher potential but also risk of loss

### Platform Requirements

- **Kalshi**: US residents (excluding IL, MD, MT, NJ, NV, OH). Minimum deposit $1. API access is free with account.
- **Polymarket**: Requires USDC on Polygon network. Was restricted for US users but returning to US market as of early 2026. Needs a crypto wallet (MetaMask) funded with USDC.

### Can This Double $100 in a Week?

**Possible but unlikely with pure arbitrage.** Pure arbitrage on $100 might yield $1-5/week. To double, you would need to take directional positions informed by AI analysis, which is closer to betting than arbitrage. The AI can analyze news, probability models, and market sentiment to find mispriced contracts, but this carries real loss risk.

**Recommended approach**: Split $50 into pure arbitrage bot (safe, small returns) and $50 into 2-3 AI-researched directional bets on niche events where you believe the market is mispriced.

---

## Strategy 2: Automated Digital Product Creation + Listing

**Automation level: 90%**
**What Claude Code builds: Notion templates, spreadsheets, ebooks, guides**
**What n8n does: Auto-listing, social media promotion, analytics**
**Budget allocation: $0-20 (Etsy listing fees)**

### What AI Can Create (and What Sells)

| Product | AI Can Fully Create? | Avg Price | Best Platform | Monthly Sales Potential |
|---------|---------------------|-----------|---------------|----------------------|
| Notion templates (planners, trackers, CRMs) | Yes | $5-50 | Gumroad, Etsy | $50-500/mo after 2-3 months |
| Google Sheets / Excel budgets & trackers | Yes | $5-30 | Etsy, Gumroad | $30-200/mo |
| Printable planners / wall art (PDF) | Yes (with Canva API) | $3-15 | Etsy | $20-300/mo |
| Ebooks / guides (PDF) | Yes | $5-30 | Gumroad, Amazon KDP | $20-200/mo |
| Prompt packs (ChatGPT/Midjourney) | Yes | $5-25 | Gumroad, Etsy | $20-150/mo |
| Resume templates | Yes | $10-25 | Etsy | $30-200/mo |
| Social media Canva templates | Partial (needs Canva) | $10-50 | Etsy, Creative Market | $50-500/mo |

### Platform Fees

| Platform | Listing Fee | Transaction Fee | Marketplace Discovery |
|----------|-----------|----------------|----------------------|
| **Gumroad** | $0 | 10% + $0.50/sale (30% if found via marketplace) | Some built-in |
| **Etsy** | $0.20/listing | 6.5% + ~3% payment processing | Excellent (built-in SEO) |
| **Payhip** | $0 | 5% | None |
| **Amazon KDP** | $0 | 30-65% royalty depending on price | Excellent |
| **Notion Marketplace** | $0 | Revenue share (not publicly disclosed) | Growing |

### What Claude Code Can Build Right Now

Claude Code can generate complete, functional products:

1. **Notion templates**: Claude can output Notion-compatible markdown or use the Notion API to create templates directly. Examples: content calendar, habit tracker, project management dashboard, CRM, reading list, meal planner, budget tracker.

2. **Spreadsheets**: Claude can generate CSV files or Google Sheets via API with formulas, conditional formatting specs, and data validation rules. Examples: budget planners, investment trackers, invoice generators, KPI dashboards.

3. **Ebooks/guides**: Claude can write complete 5,000-20,000 word guides on profitable topics (productivity, AI prompts, side hustles, specific tools). Output as markdown, convert to PDF with Pandoc or a simple script.

4. **Prompt packs**: Claude can create curated, tested prompt collections for specific use cases (marketing, coding, writing, image generation).

### n8n Automation Workflow

```
Trigger (Schedule: weekly)
  -> Claude API: Generate new product idea + content
  -> Format into template/PDF
  -> Upload to Gumroad via API
  -> Create Etsy listing via Etsy API
  -> Generate social media posts (Twitter, Reddit, Pinterest)
  -> Post to social platforms via APIs
  -> Track sales via webhook
  -> Send weekly revenue report to Slack/email
```

### Realistic Revenue Timeline

- **Week 1**: 0-2 sales ($0-30). Products are listed but have no reviews or traffic.
- **Month 1**: 5-20 sales ($25-200) if actively promoted on social media and Reddit.
- **Month 3**: $100-500/month if you have 10-20 products listed and some organic traffic.
- **Month 6+**: $200-2,000/month for a well-maintained store with 30+ products.

### Can This Double $100 in a Week?

**No.** Digital products require time to gain visibility. Etsy's algorithm favors listings with sales history and reviews. Gumroad has minimal discovery. The first sale typically takes 1-4 weeks. However, this is the highest long-term automation potential on this list. Once products are created and listed, they generate revenue with zero ongoing effort.

**Best play**: Use Claude Code to create 5-10 products in a single session (a few hours of compute time), list them on both Gumroad and Etsy, set up n8n to auto-promote them on social media daily, and let the long tail work over weeks and months.

---

## Strategy 3: Automated Affiliate Blog (WordPress + n8n)

**Automation level: 95%**
**What Claude Code builds: The entire site, content pipeline, SEO**
**What n8n does: Automated content generation, publishing, social promotion**
**Budget allocation: $10-30 (hosting + domain)**

### How It Works

Build a niche blog on WordPress, automatically generate SEO-optimized articles with affiliate links, publish on schedule, and promote on social media. All orchestrated by n8n workflows.

### Existing n8n Workflow Templates

These are production-ready templates from the n8n community:

| Template | What It Does |
|----------|-------------|
| [AI Blog Automation: Publish Hourly SEO Articles to WordPress](https://n8n.io/workflows/6734) | Generates and publishes SEO articles to WordPress + Twitter on a schedule |
| [Content Farming: AI-Powered Blog Automation](https://n8n.io/workflows/5230) | Collects news, filters for relevance, generates long-form articles with images |
| [WordPress Auto-Blogging Pro with Deep Research](https://n8n.io/workflows/3041) | Deep research + content automation with Perplexity integration |
| [Amazon Affiliate Marketing Automation](https://n8n.io/workflows/7422) | Automated Amazon affiliate content creation and publishing |
| [AI-Powered Product Research & SEO Content](https://n8n.io/workflows/5195) | Product research + SEO content generation pipeline |
| [YouTube to WordPress Blog with Affiliate Integration](https://n8n.io/workflows/3714) | Converts YouTube videos to blog posts with affiliate links |
| [Multi-Agent SEO Blog Writing System](https://n8n.io/workflows/8654) | Multi-agent approach to SEO-optimized content with hyperlinks |

### Infrastructure Costs

| Component | Cost | Notes |
|-----------|------|-------|
| Domain name | $10-15/year | Namecheap, Cloudflare |
| Hosting (WordPress) | $3-10/month | Hostinger, Vultr VPS, or self-hosted |
| n8n (self-hosted) | $0 | Free, unlimited executions on your own server |
| Claude API | $0-20/month | Pay per token, ~$0.01-0.05 per article |
| Total Month 1 | $15-45 | |

### Affiliate Programs That Accept New Sites

| Program | Commission | Cookie Duration | Approval Difficulty |
|---------|-----------|----------------|-------------------|
| Amazon Associates | 1-10% | 24 hours | Easy (but low commission) |
| ShareASale | Varies by merchant | Varies | Medium |
| Impact | Varies by merchant | Varies | Medium |
| PartnerStack | 15-30% recurring | 90 days | Medium |
| Gumroad Affiliate | Up to 50% | 30 days | Easy |
| Individual SaaS programs | 20-50% recurring | 30-90 days | Varies |

### The Automated Pipeline

```
1. n8n Schedule Trigger (daily)
2. -> Keyword Research Agent (Claude API + Google Trends API)
3. -> Content Brief Generation (target keyword, outline, word count)
4. -> Article Generation (Claude API, 1500-3000 words)
5. -> SEO Optimization (meta description, headers, internal links)
6. -> Affiliate Link Injection (match products to content context)
7. -> Image Generation (DALL-E API or stock photo API)
8. -> Publish to WordPress (WordPress REST API)
9. -> Social Media Distribution (Twitter API, Reddit API, Pinterest API)
10. -> Google Search Console submission (Indexing API)
11. -> Weekly Analytics Report (Google Analytics API -> Slack/email)
```

### Realistic Revenue Timeline

- **Week 1-4**: $0. Google takes 2-8 weeks to index and rank new content. Zero organic traffic initially.
- **Month 2-3**: $0-50/month. Some articles start ranking for long-tail keywords. First affiliate clicks.
- **Month 3-6**: $50-500/month. If publishing 1-2 articles/day with good keyword targeting. Compounding SEO effect.
- **Month 6-12**: $200-2,000/month for a well-executed niche site.

### Content Quality Warning

Google's March 2024 "Helpful Content Update" (and subsequent updates through 2025-2026) aggressively penalizes "AI-generated content farms." Pure AI slop without human value gets deindexed. The n8n workflow should include:
- Human review/editing step (or at minimum, AI self-review with quality checks)
- Original data, analysis, or perspective in each article
- E-E-A-T signals (author bios, citations, first-hand experience)
- Not just rewording existing content but adding genuine value

### Can This Double $100 in a Week?

**No.** SEO is a long game. The earliest realistic revenue is 4-8 weeks out. But this is one of the most reliable automated income streams once established. Many affiliate bloggers earn $1,000-10,000/month with content that was created once and earns for years.

---

## Strategy 4: Build and Sell API Access on RapidAPI

**Automation level: 80%**
**What Claude Code builds: The API itself**
**What n8n does: Usage monitoring, billing alerts, content marketing**
**Budget allocation: $5-20 (hosting)**

### How It Works

Build a useful API, deploy it, list it on RapidAPI (or alternatives), and charge per request. The API runs 24/7, serving requests automatically. RapidAPI handles billing, authentication, and documentation.

### API Ideas Claude Code Can Build

| API Idea | Demand | Complexity | Revenue Potential |
|----------|--------|-----------|------------------|
| Text summarization / extraction | High | Low | $50-500/mo |
| Email validation / verification | High | Medium | $100-1,000/mo |
| Resume parser (PDF to structured JSON) | Medium | Medium | $50-300/mo |
| SEO meta tag analyzer | Medium | Low | $30-200/mo |
| AI content detector | High | Medium | $100-500/mo |
| Readability score calculator | Low | Low | $20-100/mo |
| Business name generator | Medium | Low | $30-200/mo |
| Color palette generator from image | Medium | Medium | $30-200/mo |
| Markdown to PDF converter | Medium | Low | $30-200/mo |
| Placeholder image generator | Medium | Low | $20-100/mo |

### Platform Options

| Platform | Commission | Developer Base | Best For |
|----------|-----------|---------------|---------|
| **RapidAPI** | 20% | 4M+ developers | Largest marketplace, most traffic |
| **APILayer** | 15% | Smaller | Higher revenue share |
| **AWS Marketplace** | 12-20% | Enterprise | Enterprise customers |
| **Your own site** | 0% (just Stripe 2.9%) | None (must market yourself) | Maximum margin |

### Deployment Stack

```
Claude Code writes the API (Python/FastAPI or Node.js/Express)
  -> Deploy to Railway ($5/mo) or Fly.io (free tier) or Vercel (free tier for serverless)
  -> List on RapidAPI with tiered pricing:
     - Free: 100 requests/month
     - Basic ($9.99/mo): 1,000 requests/month
     - Pro ($29.99/mo): 10,000 requests/month
  -> n8n monitors usage, sends alerts, auto-generates changelog posts
```

### Real Revenue Example

One developer documented making [$877 selling a ChatGPT-built API on RapidAPI](https://medium.com/@maxslashwang/how-i-made-877-selling-a-chatgpt-built-api-on-rapidapi-bb0147156450). The API was built entirely by AI, deployed, and listed in under a day.

### Can This Double $100 in a Week?

**Unlikely but not impossible.** If you build something genuinely useful and it gains traction on RapidAPI quickly, a few paying subscribers at $10-30/month could get you there. More realistically, expect $0-50 in month 1 while the API gains visibility.

---

## Strategy 5: AI-Powered Newsletter (Substack/Beehiiv)

**Automation level: 70%**
**What Claude Code builds: Content generation pipeline, growth automations**
**What n8n does: Content curation, scheduling, analytics, cross-promotion**
**Budget allocation: $0**

### How It Works

Curate and synthesize information on a specific niche using AI, publish a regular newsletter, grow subscribers, monetize through paid subscriptions, sponsorships, and affiliate links.

### Platform Comparison

| Platform | Cost | Monetization | AI-Friendly? |
|----------|------|-------------|-------------|
| **Substack** | Free (10% of paid subs) | Paid subscriptions, sponsorships | Tolerates AI-assisted but values human voice |
| **Beehiiv** | Free up to 2,500 subs | Paid subs, ad network, referral program | More automation-friendly |
| **ConvertKit** | Free up to 1,000 subs | Paid subs, tip jars | Neutral on AI |

### The Automation Pipeline

```
1. n8n Cron Trigger (2-3x per week)
2. -> RSS Feed Aggregation (industry news sources)
3. -> Web Scraping (trending topics, new data)
4. -> Claude API: Synthesize into newsletter format
   - Curated news with analysis
   - Original insights and predictions
   - Actionable takeaways
5. -> Human review queue (approve/edit in 5-10 minutes)
6. -> Publish via Substack/Beehiiv API
7. -> Cross-post snippets to Twitter, LinkedIn, Reddit
8. -> Track open rates, growth, revenue
```

### Best Niches for AI-Automated Newsletters

| Niche | Why It Works for AI | Monetization Path |
|-------|-------------------|------------------|
| AI/tech news digest | Constant stream of source material | Sponsorships, paid tier |
| Crypto market analysis | Data-driven, API-accessible | Paid tier, affiliate links |
| Job market / layoff tracker | Public data, high demand | Sponsorships |
| Niche industry roundups (e.g., solar, EVs) | Aggregation plays to AI strengths | B2B sponsorships |
| Product deal alerts | Price API monitoring | Affiliate commissions |

### Revenue Model

- **Free subscribers**: Revenue from ad network (Beehiiv: ~$1-3 CPM) and affiliate links
- **Paid subscribers**: Substack charges 10% + Stripe fees. At $5/month, you keep ~$4.20 per subscriber.
- **Sponsorships**: $25-100 per issue at 1,000-5,000 subscribers

### Realistic Timeline

- **Week 1**: 0-50 subscribers (friends, social media posts). $0 revenue.
- **Month 1**: 100-500 subscribers with active promotion. $0-50 revenue.
- **Month 3**: 500-2,000 subscribers. $50-300/month from ads + first paid subscribers.
- **Month 6**: 2,000-5,000 subscribers. $200-1,000/month.
- **Conversion rate**: Typically 2-3% free-to-paid on Substack.

### Can This Double $100 in a Week?

**No.** Newsletter monetization requires audience, which requires time. But the automation potential is high -- once the pipeline is built, each issue takes 5-10 minutes of human review time.

---

## Strategy 6: Sell n8n Workflow Templates

**Automation level: 60%**
**What Claude Code builds: The workflows themselves**
**Budget allocation: $0-20**

### How It Works

Build useful n8n automation workflows, package them as templates, and sell them on Gumroad or your own site. The market for "done-for-you automations" is growing rapidly as more businesses adopt n8n.

### What Sells

| Workflow Type | Price Range | Target Buyer |
|--------------|------------|-------------|
| Lead generation automation | $29-99 | Agencies, freelancers |
| Social media auto-posting | $19-49 | Content creators |
| CRM integration workflows | $29-79 | Small businesses |
| AI content pipeline | $39-99 | Bloggers, marketers |
| Invoice/payment automation | $29-59 | Freelancers |
| Customer onboarding sequences | $39-99 | SaaS companies |

### Revenue Evidence

One person [documented making $4,200 over four months](https://medium.com/write-a-catalyst/im-trying-to-make-3k-10k-month-selling-n8n-workflows-here-s-what-s-actually-working-a43624121b70) selling n8n workflows, with monthly revenue ranging from $800 to $2,100. The market is early enough that well-packaged workflows with documentation can find buyers.

### Selling Channels

1. **Gumroad**: Simple listing, 10% fee
2. **n8n community templates**: Free (for exposure/credibility), link to paid advanced versions
3. **Your own site**: Stripe checkout, full margin
4. **Twitter/LinkedIn**: "Built this automation, saves X hours/week" posts perform well

### Can This Double $100 in a Week?

**Unlikely.** Requires finding buyers, which takes marketing effort and time. But the creation is highly automatable.

---

## Strategy 7: Cold Email Lead Generation Service

**Automation level: 75%**
**What Claude Code builds: Email sequences, lead lists, campaign logic**
**What n8n does: Orchestrates the entire pipeline**
**Budget allocation: $39-94/month (tool costs exceed $100 budget)**

### How It Works

Offer "lead generation as a service" to small businesses. Use AI to write personalized cold emails, automated tools to send them, and charge clients per lead or per month.

### Tool Stack

| Tool | Purpose | Cost |
|------|---------|------|
| **Smartlead** | Email sending + warmup | $39/mo (2,000 leads, 6,000 emails) |
| **Instantly.ai** | Alternative to Smartlead | $30/mo (1,000 contacts, 5,000 emails) |
| **Apollo.io** | Lead database + email finding | Free tier (50 credits/mo) |
| **Hunter.io** | Email verification | Free tier (25 searches/mo) |
| **n8n** | Orchestration | Free (self-hosted) |
| **Claude API** | Email personalization | ~$5-10/mo for this volume |

### The Problem: Budget

The minimum viable tool cost is $39-50/month just for email sending infrastructure, which already consumes a large portion of the $100 budget. However, if you can land even one client paying $500-2,000/month for lead generation services, the ROI is massive.

### What the Service Looks Like

```
1. Client provides: target industry, ideal customer profile, value proposition
2. n8n workflow:
   -> Scrape leads from Apollo.io / LinkedIn (within free tier limits)
   -> Claude API personalizes email for each lead
   -> Smartlead sends sequences (3-5 emails over 2 weeks)
   -> Positive replies forwarded to client
   -> n8n tracks metrics: sent, opened, replied, booked
3. You charge: $500-2,000/month per client, or $25-100 per qualified lead
```

### Can This Double $100 in a Week?

**Possible if you land a client fast**, but the tool costs eat into the budget and finding that first client requires hustle. More realistic as a second-month play after proving the concept.

---

## Strategy 8: Web Scraping + Data Reports

**Automation level: 80%**
**What Claude Code builds: Scrapers, data pipelines, report generators**
**What n8n does: Scheduled scraping, data processing, report delivery**
**Budget allocation: $5-20 (hosting)**

### Legal Framework (Critical)

Web scraping publicly available data is **generally legal** in the US after the *hiQ Labs v. LinkedIn* ruling. However:

- Scraping data behind a login or paywall: **Likely illegal** (CFAA violations)
- Scraping personal data (emails, phone numbers) for resale: **Legally risky** (state privacy laws, CAN-SPAM, GDPR if EU residents)
- Scraping and republishing copyrighted content: **Illegal**
- Scraping public government data, public business listings, public prices: **Generally legal**

### Valuable Data Products

| Data Type | Source | Legal? | Who Buys It | Price |
|-----------|--------|--------|------------|-------|
| Real estate price trends by zip code | Zillow/Redfin (public pages) | Yes (public data) | Investors, agents | $10-50/report |
| Job posting trends by industry | Indeed, LinkedIn (public pages) | Gray area | Recruiters, consultants | $20-100/report |
| Product price monitoring | Amazon, retailers (public) | Yes | Ecommerce sellers | $10-50/month |
| Restaurant menu prices | Public menus | Yes | Market researchers | $15-50/report |
| Government contract awards | SAM.gov, FPDS (public) | Yes | Contractors, consultants | $20-100/report |
| SaaS pricing changes | Public pricing pages | Yes | Analysts, VCs | $25-100/report |
| Local business directory data | Google Maps (public) | Gray area | Marketing agencies | $10-50/list |

### Tools for Scraping

| Tool | Cost | Best For |
|------|------|----------|
| **Playwright/Puppeteer** (via Claude Code) | Free | JavaScript-rendered pages |
| **BeautifulSoup + Requests** (via Claude Code) | Free | Simple HTML pages |
| **ScraperAPI** | $49/mo (5,000 requests) | Proxy rotation, CAPTCHA bypass |
| **Bright Data** | $500/mo+ | Enterprise scale |
| **Apify** | Free tier (small scale) | Pre-built scrapers for common sites |
| **n8n HTTP Request node** | Free | Simple API-based scraping |

### n8n Data Pipeline

```
1. Schedule Trigger (daily/weekly)
2. -> HTTP Request nodes (scrape target sites)
3. -> Parse HTML / JSON
4. -> Claude API: Analyze data, generate insights
5. -> Format into PDF report (using markdown -> PDF conversion)
6. -> Deliver via email or upload to Gumroad
7. -> Track subscribers and deliveries
```

### Can This Double $100 in a Week?

**Unlikely.** Building the scraper takes 1-2 days. Finding buyers for data reports takes marketing effort. Could work if you already know someone who needs specific data, but cold-starting a data business in a week is unrealistic.

---

## Strategy 9: Crypto Spot-Futures Arbitrage (Pionex)

**Automation level: 95%**
**What you do: Deposit money, click start**
**Budget allocation: $100 (all as trading capital)**

### How It Works

Pionex's Spot-Futures Arbitrage Bot buys crypto on the spot market and simultaneously shorts the same amount on futures. This hedges out price movement entirely. You profit from the "funding rate" that futures traders pay every 8 hours.

### The Numbers

| Metric | Value |
|--------|-------|
| Minimum investment | ~10 USDT per bot |
| Annualized return (typical) | 15-50% APR |
| Weekly return (extrapolated) | 0.3-1.0% |
| Weekly return on $100 | $0.30-$1.00 |
| Pionex fee | 10% of profits |
| Risk | Low (market-neutral) but not zero (exchange risk, liquidation risk in extreme moves) |

### Platform Details

- **Pionex** is a Singapore-based exchange with built-in free trading bots
- No subscription fees; Pionex makes money from trading fees (0.05% maker/taker)
- The bot runs 24/7 automatically
- Available to US residents (Pionex.US)

### Can This Double $100 in a Week?

**No.** At 0.3-1.0% per week, you would earn $0.30-$1.00. This is a "park money and earn yield" strategy, not a doubling strategy. Over a year, $100 could become $115-$150. It is essentially a high-yield savings account denominated in crypto.

**However**, Pionex also has riskier bots (Grid Trading, Leveraged Grid) that could potentially yield higher returns but with proportionally higher risk of loss.

---

## Strategy 10: Social Media Content Automation

**Automation level: 85%**
**What Claude Code builds: Content generation scripts, scheduling logic**
**What n8n does: End-to-end content pipeline**
**Budget allocation: $0-20**

### Platforms and Their AI Policies

| Platform | AI Content Allowed? | Monetization Threshold | Monetization Method |
|----------|--------------------|-----------------------|-------------------|
| **YouTube Shorts** | Yes, with human value-add. Pure AI slop flagged as of July 2025 | 1,000 subs + 10M Shorts views (90 days) | Ad revenue share |
| **TikTok** | Yes, must label AI content | 10,000 followers + 100K views (30 days) | Creator Fund, gifts |
| **Medium** | No (AI-generated content cannot be paywalled) | 100 followers | Partner Program (reading time) |
| **Twitter/X** | Yes | None (but monetization requires Premium) | Ads revenue share, tips |
| **Instagram Reels** | Yes, with human value-add | Professional account | Bonuses (invite-only), shopping |
| **Pinterest** | Yes | None for direct monetization | Traffic to affiliate site |

### YouTube Shorts Automation Pipeline

YouTube Shorts is the most viable automated video platform, but the monetization threshold is steep:

```
n8n Workflow:
1. Schedule Trigger (2-3 times daily)
2. -> Trending topic detection (Google Trends API, Reddit API)
3. -> Claude API: Write script (hook + value + CTA, 30-60 seconds)
4. -> Text-to-Speech API (ElevenLabs: $5/mo, or free alternatives)
5. -> Video generation (Veo 3 via YouTube, or Runway/Pika for B-roll)
6. -> Combine audio + video (FFmpeg)
7. -> Upload to YouTube via YouTube Data API v3
8. -> Cross-post to TikTok, Instagram Reels
```

### Revenue Reality for YouTube Shorts

- Shorts RPM (revenue per mille): $0.01-$0.07
- To earn $100/month: Need ~1.5-10 million views/month
- To reach monetization: 10 million Shorts views in 90 days = ~111K views/day
- **This is a 3-12 month play minimum**

### Can This Double $100 in a Week?

**Absolutely not.** Building an audience takes months. The monetization thresholds are designed to require sustained viewership. However, the content creation pipeline itself can be 95% automated, so the ongoing time investment is minimal once built.

---

## The Recommended Portfolio Approach

Given the $100 budget and 7-day timeline, here is the optimal allocation:

### Tier 1: High-Risk / Short-Term Potential ($50-70)

| Strategy | Allocation | Expected 7-Day Return | Automation |
|----------|-----------|----------------------|-----------|
| **Prediction Market Arbitrage + AI Bets** | $50-70 | -$50 to +$150 | Bot runs 24/7 |

Deploy a Polymarket/Kalshi arbitrage bot (Claude Code can build this in a day). Run pure arbitrage for safe small gains. Allocate $20-30 for 2-3 AI-informed directional bets on events you research thoroughly.

### Tier 2: Zero-Cost / Long-Term Seeding ($0-20)

| Strategy | Allocation | Expected 7-Day Return | Expected 3-Month Return |
|----------|-----------|----------------------|------------------------|
| **Digital Products on Gumroad/Etsy** | $5-10 (listing fees) | $0-30 | $100-500/month |
| **Automated Affiliate Blog** | $10-15 (hosting) | $0 | $50-500/month |
| **API on RapidAPI** | $0-5 (free tier hosting) | $0-20 | $50-300/month |

Use Claude Code to create 5-10 digital products in a single session. Set up a WordPress blog with n8n content automation. Build and list one useful API. These cost almost nothing but compound over time.

### Tier 3: Background Automation (Free)

| Strategy | Allocation | Purpose |
|----------|-----------|---------|
| **Newsletter pipeline** | $0 | Start building audience |
| **Social media content automation** | $0 | Start building audience |
| **n8n workflow templates** | $0 | Create sellable assets |

Set up the infrastructure now. These produce $0 in week 1 but create the foundation for $500-5,000/month within 3-6 months.

---

## Implementation Priority (What to Build First)

### Day 1: Prediction Market Bot
1. Claude Code builds Polymarket/Kalshi arbitrage scanner in Python
2. Deploy on your Mac (or a $5 VPS)
3. Fund Kalshi with $50-70
4. Start scanning for arbitrage opportunities
5. Set up n8n monitoring workflow for alerts

### Day 1-2: Digital Products
1. Claude Code generates 5 Notion templates (planner, budget tracker, CRM, content calendar, habit tracker)
2. Claude Code writes 2 short ebooks/guides (AI prompts pack, productivity guide)
3. List all on Gumroad (free to list)
4. List top 3 on Etsy ($0.20 each)
5. n8n workflow auto-posts to Twitter/Reddit daily

### Day 2-3: Affiliate Blog
1. Buy domain ($10) + hosting ($3-5/month)
2. Claude Code sets up WordPress + theme
3. n8n workflow: generate + publish 2-3 SEO articles/day
4. Sign up for Amazon Associates + 2-3 other affiliate programs
5. Submit sitemap to Google Search Console

### Day 3-4: API Product
1. Claude Code builds a useful API (e.g., text summarizer, email validator)
2. Deploy to Railway or Vercel (free tier)
3. List on RapidAPI with tiered pricing
4. n8n monitors usage and sends alerts

### Day 4-7: Monitor, Optimize, Expand
1. Check prediction market bot performance, adjust thresholds
2. Promote digital products on social media
3. Monitor blog indexing and traffic
4. Create additional digital products based on what's trending
5. Set up newsletter if time permits

---

## Tools and APIs Reference

### AI / Content Generation
| Tool | Purpose | Cost |
|------|---------|------|
| Claude API (Anthropic) | Content generation, code, analysis | $0.003-$0.015 per 1K tokens |
| OpenAI API | Alternative content generation | $0.005-$0.06 per 1K tokens |
| ElevenLabs | Text-to-speech for videos | $5/mo starter |
| Canva API | Design automation | $13/mo (Pro) |
| DALL-E / Midjourney | Image generation | $0.04/image (DALL-E), $10/mo (MJ) |

### Automation / Orchestration
| Tool | Purpose | Cost |
|------|---------|------|
| n8n (self-hosted) | Workflow automation | Free |
| GitHub Actions | CI/CD, scheduled tasks | Free (2,000 min/mo) |
| Cron jobs (your Mac) | Simple scheduling | Free |

### Publishing / Selling
| Tool | Purpose | Cost |
|------|---------|------|
| WordPress REST API | Blog publishing | Free (API) |
| Gumroad API | Digital product sales | Free to list |
| Etsy API | Marketplace listing | $0.20/listing |
| Substack | Newsletter | Free |
| YouTube Data API v3 | Video uploading | Free |
| Twitter API | Social promotion | Free (basic tier) |

### Trading / Finance
| Tool | Purpose | Cost |
|------|---------|------|
| Kalshi API | Prediction market trading | Free |
| Polymarket CLOB API | Prediction market trading | Free |
| Pionex | Crypto arbitrage bots | Free (built-in) |
| CoinGecko API | Crypto price data | Free |

### Data / Scraping
| Tool | Purpose | Cost |
|------|---------|------|
| ScraperAPI | Proxy rotation for scraping | $49/mo |
| Apify | Pre-built scrapers | Free tier |
| Playwright | Browser automation / scraping | Free |
| BeautifulSoup | HTML parsing | Free |

---

## Sources

### Prediction Markets & Trading
- [Best Prediction Market APIs for Developers](https://newyorkcityservers.com/blog/best-prediction-market-apis)
- [Best Prediction Market Bots & Tools](https://newyorkcityservers.com/blog/best-prediction-market-bots-tools)
- [Polymarket-Kalshi Arbitrage Bot (GitHub)](https://github.com/realfishsam/prediction-market-arbitrage-bot)
- [Polymarket Arbitrage Scanner (GitHub)](https://github.com/ImMike/polymarket-arbitrage)
- [AI Trading Bots on Polymarket](https://andrew.ooo/posts/ai-trading-bots-polymarket-profits/)
- [Building an Automated Event Trading Bot with Kalshi](https://jinlow.medium.com/building-an-automated-event-trading-bot-with-kalshi-prediction-markets-a-practical-engineering-a1af3ee619e6)
- [Polymarket Arbitrage Bot Guide - PolyTrack](https://www.polytrackhq.app/blog/polymarket-arbitrage-bot-guide)
- [Definitive Guide to the Polymarket Ecosystem](https://defiprime.com/definitive-guide-to-the-polymarket-ecosystem)
- [Kalshi API Documentation](https://docs.kalshi.com/getting_started/rate_limits)
- [Kalshi Guide - PredictorsBest](https://predictorsbest.com/kalshi-guide/)

### Crypto Arbitrage
- [Best Crypto Arbitrage Bots 2026 - 99Bitcoins](https://99bitcoins.com/analysis/crypto-arbitrage-bots/)
- [Crypto Arbitrage Bots - Cloudzy](https://cloudzy.com/blog/crypto-arbitrage-bots/)
- [Pionex Spot-Futures Arbitrage Bot](https://www.pionex.com/blog/pionex-arbitrage-bot/)
- [Are Crypto Trading Bots Worth It in 2025?](https://coincub.com/are-crypto-trading-bots-worth-it-2025/)
- [How to Build a Crypto Arbitrage Bot - CoinGecko](https://www.coingecko.com/learn/crypto-arbitrage-bot-python)

### Digital Products & Templates
- [7 Digital Products That Will Print Money in 2026 (Medium)](https://medium.com/write-a-catalyst/7-digital-products-that-will-print-money-in-2026-6aaa32b39021)
- [Best Digital Products to Sell on Etsy, Gumroad & Shopify](https://resellready.co/blogs/news/best-digital-products-to-sell-on-etsy-gumroad-shopify)
- [Most Profitable Digital Products 2026](https://resellready.co/blogs/news/most-profitable-digital-products-for-passive-income-in-2026)
- [28 Unique Digital Products to Sell in 2026](https://wpastra.com/resources/digital-products-to-sell/)
- [Gumroad Pricing](https://gumroad.com/pricing)
- [Gumroad vs Etsy Fees Comparison](https://medium.com/@loveshazain/gumroad-vs-etsy-fees-which-paid-me-more-on-1-000-in-sales-fbbafd6c70d6)
- [How I Made $877 Selling a ChatGPT-Built API on RapidAPI](https://medium.com/@maxslashwang/how-i-made-877-selling-a-chatgpt-built-api-on-rapidapi-bb0147156450)

### n8n Automation & Affiliate Marketing
- [n8n for Marketing in 2026](https://marketingagent.blog/2026/01/22/n8n-for-marketing-in-2026-the-automation-fabric-behind-ai-first-growth-with-real-workflow-examples/)
- [AI Blog Automation: Hourly SEO Articles to WordPress (n8n template)](https://n8n.io/workflows/6734-ai-blog-automation-publish-hourly-seo-articles-to-wordpress-and-twitter-v3/)
- [Amazon Affiliate Marketing Automation (n8n template)](https://n8n.io/workflows/7422-amazon-affiliate-marketing-automation/)
- [Content Farming: AI-Powered Blog Automation (n8n template)](https://n8n.io/workflows/5230-content-farming-ai-powered-blog-automation-for-wordpress/)
- [WordPress Auto-Blogging Pro with Deep Research (n8n template)](https://n8n.io/workflows/3041-wordpress-auto-blogging-pro-with-deep-research-content-automation-machine/)
- [n8n Automation for SEO in 2026](https://writersoftheworld.com/n8n-automation-for-seo-in-2026/)
- [Building an SEO Workflow in n8n - CXL](https://cxl.com/blog/seo-workflow-n8n-automation/)
- [Making $3K-10K/Month Selling n8n Workflows](https://medium.com/write-a-catalyst/im-trying-to-make-3k-10k-month-selling-n8n-workflows-here-s-what-s-actually-working-a43624121b70)
- [n8n Monetization: 5 Proven Strategies](https://ritz7.com/blog/monetize-n8n-automation-skills)

### Content Monetization & Platforms
- [YouTube Monetization 2026: Human vs AI Content](https://digehub.com/youtube-monetization-2026-human-vs-ai-content/)
- [AI YouTube Shorts Monetization Guide 2026](https://virvid.ai/blog/ai-youtube-shorts-monetization-guide-2026)
- [YouTube AI Monetization Policy](https://blog.veefly.com/youtube-marketing/youtube-ai-monetization-policy-are-creators-at-risk/)
- [How to Make Money with AI Video (2026 Edition)](https://www.aistudios.com/how-to-guides/how-to-make-money-with-ai-video-2026-edition)
- [Substack in 2026: Usage, Revenue, Growth Statistics](https://fueler.io/blog/substack-usage-revenue-valuation-growth-statistics)
- [How to Make Money on Substack in 2026 - Shopify](https://www.shopify.com/blog/how-to-make-money-on-substack)
- [Medium AI Content Policy](https://zidailma.medium.com/a-new-medium-policy-you-didnt-know-76a751aaaf16)

### Cold Email & Lead Generation
- [Smartlead vs Instantly 2026 Comparison](https://instantly.ai/blog/smartlead-alternatives-pipeline-2026/)
- [How to Automate Lead Generation in 2026 - Smartlead](https://www.smartlead.ai/blog/lead-generation-automation)
- [Cold Email AI: Close 10x More Deals in 2026](https://www.saleshandy.com/blog/cold-email-ai/)

### Web Scraping Legality
- [Is Web Scraping Legal? 2026 Guide - ScraperAPI](https://www.scraperapi.com/web-scraping/is-web-scraping-legal/)
- [Is Web Scraping Legal? 2025 Breakdown - Attorney](https://mccarthylg.com/is-web-scraping-legal-a-2025-breakdown-of-what-you-need-to-know/)
- [Legality of Web Scraping 2026 - Grepsr](https://www.grepsr.com/blog/overview-web-scraping-legality/)

### API Marketplaces
- [RapidAPI - Build and Sell Your Own API](https://rapidapi.com/courses/build-and-sell-your-own-api)
- [Top 8 API Marketplaces 2026](https://www.softwaretestinghelp.com/best-api-marketplaces/)
- [Top 12 Platforms to Monetize Your API](https://mktclarity.com/blogs/news/list-sell-api-data)
