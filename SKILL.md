---
name: indie-affiliate-site-playbook
description: Complete playbook for building profitable affiliate niche sites as a solo indie builder. From idea validation to first revenue in 90 days. Universal framework for any tool/content site.
version: 2.1.0
author: Hermes Agent Community
prerequisites:
  skills:
    - affiliate-growth-analytics
    - vercel-deploy
    - nextjs-seo
    - github-pr-workflow
  commands: [git, node, pnpm, curl]
metadata:
  hermes:
    tags: [affiliate-marketing, SEO, indie-hacker, niche-site, side-project, monetization, validation, open-source]
---

# Indie Affiliate Site Playbook

**From idea to revenue in 90 days.** Complete tactical playbook for solo indie builders to launch and monetize affiliate niche sites using AI-native workflows.

**Universal framework** — applies to any tool/content site: testing tools, calculators, generators, converters, comparison sites, resource hubs.

**Open source** — MIT licensed, community-maintained, evolving with every successful builder.

---

## Who This Is For

- **AI-native indie builders** — solo developers who use AI (Claude/GPT/Hermes) to 10x productivity
- **Side project hustlers** — people with a day job looking for $500-2k/mo passive income
- **One-person companies** — 一人公司 mindset, build in public, ship fast

**Prerequisites:**
- Can code (web development — React/Vue/vanilla JS)
- Understand basic SEO concepts (keywords, backlinks, SERP)
- Have AI tooling (Hermes Agent, Claude, GPT, or similar)
- Time: 2-3 weeks full-time OR 1-2 months part-time

**What you'll build:**
- 3-6 core features (interactive tools OR content calculators OR resource directories)
- 20-50 SEO-optimized pages (buying guides, how-tos, comparisons)
- Affiliate integration (Amazon Associates, impact.com, ShareASale, or product-specific programs)
- Analytics pipeline (GA4 + Google Search Console)
- 10-50 DoFollow backlinks from niche blogs + GitHub awesome-lists

**Expected outcome:**
- Month 1: Site live, 10+ daily organic visitors
- Month 2: 50+ daily visitors, first affiliate clicks
- Month 3: First revenue ($0.50-$50)
- Month 6: $100-500/mo (conservative), $500-2k/mo (aggressive)

---

## The 8-Stage Playbook

```
Stage 0: Idea Validation (48h) → gate: find 1 success case >$500/mo
Stage 1: Tech Stack (1 day) → pick stack + boilerplate
Stage 2: MVP Build (3-5 days) → 1 core feature + 2 auxiliary
Stage 3: SEO Foundation (2 days) → sitemap, schema, GSC
Stage 4: Content Strategy (ongoing) → long-tail keywords
Stage 5: Affiliate Integration (2 days) → product cards + event tracking
Stage 6: Analytics & Reporting (1 day + ongoing) → data pipeline
Stage 7: Growth — Backlinks (3-6 months) → awesome-lists + niche blogs
Stage 8: Optimization & Scale (ongoing) → data-driven iteration
```

Each stage has: validation checklist, recommended tools, decision gates, common pitfalls.

---

## Quick Start

### 1. Read the README
```bash
skill_view('indie-affiliate-site-playbook', 'references/README.md')
```
Full overview + FAQ + contribution guide.

### 2. Study the Full Playbook
```bash
skill_view('indie-affiliate-site-playbook', 'references/full-playbook.md')
```
Complete 1300-line tactical manual. Read stages 0-3 before building anything.

### 3. Start Building
- Stage 0: 48h validation (find 1 competitor making >$500/mo)
- Stages 1-3: 1-2 weeks to MVP
- Stages 4-8: Ongoing growth + optimization

---

## Core Principles

1. **48h validation gate** — If you can't find 1 competitor making >$500/mo, pivot immediately
2. **Long-tail SEO first** — 50 keywords @ 100 searches/mo > 1 keyword @ 10k ranked #10
3. **AI-native workflow** — Use AI for SERP analysis, outlines, drafts — but always humanize + manual review
4. **Data-driven pivots** — Each month has clear "abandon signals" and "double-down signals"
5. **Backlinks > Content** — 20 posts + 5 backlinks > 50 posts + 0 backlinks

---

## Recommended Tech Stack

**Frontend:**
- **Framework:** Next.js 15 App Router (SSG for SEO) OR Astro (content-heavy) OR Nuxt (Vue)
- **Styling:** Tailwind CSS (fast iteration, dark themes)
- **i18n:** next-intl OR astro-i18next

**Backend (if needed):**
- **Serverless:** Vercel Edge Functions OR Cloudflare Workers (<$10/mo)
- **Database:** Vercel Postgres OR Supabase free tier

**Analytics:**
- **GA4** (free, custom events)
- **Google Search Console** (free, keyword data)

**Deployment:**
- **Vercel Hobby** (free, auto CI/CD) OR Cloudflare Pages OR Netlify

**Affiliate:**
- **Amazon Associates** (1-10% commission)
- **Impact.com / ShareASale** (if Amazon not available)
- **Direct programs** (Bluehost, Shopify, etc.)

**Why this stack?** $0-10/mo cost, deploys in <5 minutes, SEO-friendly by default, scales to 100k visitors/mo.

**Other stacks work too** — framework-agnostic. Replace Next.js → Nuxt/Astro, Vercel → Cloudflare/Netlify. Core playbook stays the same.

---

## Example Niches This Applies To

- **Testing tools:** audio test, color blindness test, typing speed, wifi analyzer, monitor test
- **Calculators:** mortgage, BMI, pregnancy, retirement, crypto ROI, loan, tip
- **Generators:** QR code, password, invoice, resume, color palette, lorem ipsum
- **Converters:** unit converter, file format, timezone, currency, image compression
- **Comparison sites:** best X for Y, X vs Y, tool directories
- **Resource hubs:** free fonts, stock photos, code snippets, design assets, templates

---

## Decision Trees (Quick Reference)

### Month 1: Launch or Pivot?
- ✅ GSC indexed >5 pages + impressions >10/day + 1+ backlink → **Continue to Stage 4**
- ⚠️ 1-2 metrics below threshold → **Diagnose + fix, wait 2 weeks**
- ❌ 3+ metrics below threshold → **Pivot to adjacent niche or abandon**

### Month 2: Growth or Stall?
- ✅ Impressions >50/day + 1 keyword in page 2 (rank 11-20) → **Double down: Stage 7 backlinks**
- ⚠️ Impressions <20/day → **Add 10-20 long-tail content pages**
- ❌ Added 20 pages + 5 backlinks, still <20/day → **Niche too small or competitive, pivot**

### Month 3: Revenue or Rethink?
- ✅ First order (even $0.50) → **PMF validated, enter Stage 8 (scale)**
- ⚠️ 0 orders but clicks >20 → **Normal conversion delay, wait 2 weeks**
- ❌ Sessions <30/day with flat trend → **SEO ceiling, pivot to paid traffic or abandon**

### Month 6: Scale or Sell?
- ✅ Revenue >$500/mo → **Scale to $2k/mo OR sell site (24-36x monthly profit)**
- ⚠️ Revenue $100-200/mo → **Maintain mode OR start 2nd niche site**
- ❌ Revenue <$100/mo, 6 months flat → **Sell for $1-3k, document lessons, next idea**

Full decision matrices in `references/full-playbook.md` → "When to Pivot" section.

---

## Key Insights (Cross-Project Patterns)

### What Works Universally

1. **Niche blog outreach** — Find 10-20 indie blogs (DR 20-50) with /tools or /resources pages. 20-40% conversion to backlinks.

2. **GitHub awesome-lists** — Search `awesome-[your-niche]`. Fork, add your site, PR. 50-80% merge rate if list is active.

3. **Long-tail keyword clusters** — Use Google Search Console actual queries (position 11-50) as seed. Expand via AlsoAsked/AnswerThePublic.

4. **Inline contextual affiliate cards** — Place products inline with content (not sidebar). CTR 3-5x higher.

5. **Visual reporting** — Dark-themed HTML dashboard → Playwright screenshot → Slack/Discord. More actionable than CSV/JSON.

### What Doesn't Work (Avoid These)

1. **Zero backlinks + 100 pages** — Google won't rank you without domain authority. 20 pages + 10 backlinks > 100 pages + 0 backlinks.

2. **Generic sidebar affiliate cards** — Users are blind to sidebars. Inline contextual placement converts 3-5x better.

3. **Ignoring mobile** — 60-70% of niche site traffic is mobile. Test on iPhone Safari.

4. **Launching without GSC** — Can't iterate SEO without keyword data. Submit sitemap day 1.

5. **Competitor keyword stuffing** — Copying competitors without adding value = Google penalty.

---

## Success Benchmarks

**Traffic (organic only):**
- Month 1: 10-50 visitors/day
- Month 3: 50-200 visitors/day
- Month 6: 200-1000 visitors/day
- Month 12: 1000-5000 visitors/day

**Revenue (affiliate):**
- Typical CTR: 0.5-2% (inline cards)
- Typical conversion: 3-8% (Amazon)
- Typical commission: $2-5/item (Amazon), $20-100 (SaaS)
- **Formula:** 1000 sessions/mo × 1% CTR × 5% conversion × $3 = $1.50/mo (early)
- **Target:** 10k sessions/mo × 1.5% CTR × 5% conversion × $4 = $300/mo (6-month milestone)

**Site valuation (when selling):**
- 24-36x monthly **profit** (not revenue)
- $500/mo profit = $12-18k sale price
- Marketplaces: Flippa, Empire Flippers, Motion Invest

---

## Tools & Dependencies

### Essential Hermes Skills (Optional)
- `affiliate-growth-analytics` — GA4 + GSC data pipeline patterns
- `vercel-deploy` — Deployment troubleshooting
- `nextjs-seo` — SEO checklist
- `github-pr-workflow` — PR best practices for awesome-lists
- `linear` — Task tracking

### External Tools (Free Tier Sufficient)
- **SEO:** Google Search Console, Ahrefs free tier, AlsoAsked, AnswerThePublic
- **Analytics:** GA4, Vercel Analytics
- **Affiliate:** Amazon Associates, Impact.com, ShareASale
- **Deployment:** Vercel / Cloudflare Pages / Netlify
- **Design:** Tailwind CSS, Playwright (for visual reports)

---

## Common Pitfalls

### Validation (Stage 0)
- **Pitfall:** Assuming idea is unique → build 2 weeks → nobody searches for it
- **Fix:** 48h validation. Find 1 competitor making >$500/mo or pivot.

### SEO (Stages 3-4)
- **Pitfall:** Targeting only high-volume keywords (10k+ searches, KD 60+) → can't rank
- **Fix:** Target 50-100 long-tail keywords (50-500 searches, KD <30)

### Affiliate (Stage 5)
- **Pitfall:** Amazon cold start — can't apply without traffic
- **Fix:** Use GA4 custom events to track during early stage. Apply at 50+ sessions/day.

### Backlinks (Stage 7)
- **Pitfall:** Mass emailing 100 blogs with generic template → 0% response
- **Fix:** Research 10-20 relevant blogs. Personalize each email. 20-40% response.

Full pitfall list (30+ items) in `references/full-playbook.md`.

---

## Meta: Playbook Philosophy

**This is NOT:**
- A "get rich quick" scheme (realistic: $100-500/mo in 6 months)
- A passive income fairy tale (requires 10-20 hrs/week for 3-6 months)
- A content farm playbook (quality > quantity)

**This IS:**
- A proven validation-first framework
- An AI-native productivity multiplier
- A data-driven iteration loop
- A solo-builder-optimized workflow

**Core belief:** Solo builders can out-compete VC-backed startups in niche markets by building 10x faster, validating 100x cheaper, and iterating smarter.

---

## Contributing

This is an **open-source, community-maintained** playbook. Contributions welcome:

**What to contribute:**
- Case studies (success or failure, both valuable)
- New growth tactics
- Pitfalls discovered
- Tech stack alternatives

**How to contribute:**
See `references/README.md` → "Contributing" section for full guidelines.

**GitHub:** https://github.com/[your-org]/indie-affiliate-site-playbook

---

## Related Skills

- `affiliate-growth-analytics` — Data pipeline patterns
- `vercel-deploy` — Deployment patterns
- `nextjs-seo` — SEO checklist
- `github-pr-workflow` — PR best practices
- `linear` — Task tracking

---

## License

MIT — Use freely, modify freely, contribute back if you find value.

---

## Support

- **GitHub Issues:** Bug reports + feature requests
- **Discussions:** Share your learnings
- **Discord:** Hermes Agent community

---

**Built with ❤️ by indie builders, for indie builders.**  
_Empowering solo creators to compete with venture-backed startups, one niche site at a time._
