# Contributing to Indie Affiliate Site Playbook

Thank you for considering contributing to this playbook! This is a **community-maintained, open-source resource** that evolves with every successful (and failed) indie builder.

---

## How to Contribute

### 1. Case Studies (Most Valuable)

**What we want:**
- Real metrics (GSC impressions, GA4 sessions, revenue, backlinks)
- Timeline (launch date → Month 1/2/3/6 milestones)
- Decisions made (why this niche, this tech stack, this strategy)
- What worked + what didn't (failures are more valuable than vanity metrics)

**Format:**
```markdown
# Case Study: [Your Site Name]

**Niche:** [testing tools / calculators / etc]  
**Builder:** [@your-handle]  
**Timeline:** [Launch date] → [Current status]  
**Tech Stack:** [Next.js/Astro/etc + deployment platform]

## Validation (Stage 0)
[How you validated the niche in 48h]

## MVP Build (Stages 1-3)
[What you built, how long it took, deployment issues]

## Growth (Stages 4-8)
[Content strategy, backlink tactics, metrics at each month]

## Metrics
- Month 1: X impressions/day, Y backlinks
- Month 3: X sessions/day, $Y revenue
- Month 6: X sessions/day, $Y revenue

## Lessons Learned
### What Worked
1. [Tactic that worked, with specific numbers]

### What Didn't Work
1. [Tactic that failed, why it failed, what you'd do differently]

## Replicable Patterns
[What others can copy from your approach]

## Niche-Specific Details
[What's unique to your niche and shouldn't be blindly copied]
```

**How to submit:**
1. Fork this repo
2. Add your case study to `references/case-studies/[your-site-name].md`
3. Update `references/README.md` → "Success Stories" section
4. Open a PR with title: `Case Study: [Your Site Name]`

---

### 2. Growth Tactics

Discovered a backlink source not covered in the playbook? A long-tail keyword strategy that works? Share it.

**What to include:**
- Tactic name + one-line description
- Step-by-step how-to (actionable, not vague)
- Example metrics (before/after)
- When it works / when it doesn't (constraints)

**Where to add:**
- `references/full-playbook.md` → relevant stage (e.g., Stage 7 for backlinks)
- Or create `references/tactics/[tactic-name].md` if it's long

---

### 3. Pitfalls & Fixes

Hit a blocker not documented? Save others the debugging time.

**Format:**
- **Pitfall:** [What happened]
- **Why it happens:** [Root cause]
- **Fix:** [Step-by-step solution]
- **How to avoid:** [Prevention tip]

**Where to add:**
- `references/full-playbook.md` → "Pitfalls" section of relevant stage

---

### 4. Tech Stack Alternatives

Used Astro instead of Next.js? Nuxt instead of React? Document your boilerplate.

**What to include:**
- Why you chose this stack (pros/cons vs. recommended stack)
- Boilerplate checklist (what to set up on Day 1)
- Deployment differences (if any)
- SEO considerations (SSG/SSR setup)

**Where to add:**
- `references/tech-stacks/[stack-name].md`
- Update `SKILL.md` → "Recommended Tech Stack" section with link

---

### 5. Code Templates

Built a reusable component/script that others can copy? Add it.

**Examples:**
- Sitemap generator for [your framework]
- GA4 event tracking wrapper
- Affiliate card component
- Daily report script

**Where to add:**
- `templates/[template-name].[ext]` with inline comments
- Reference it from `references/full-playbook.md` → "Code Templates" section

---

## Contribution Guidelines

### ✅ Do This

- **Be specific:** Include metrics, code snippets, screenshots
- **Be honest:** Document failures, not just successes (survivorship bias helps nobody)
- **Be actionable:** What should the reader do differently after reading your contribution?
- **Keep it real:** No vanity metrics, no survivorship bias, no hype
- **Cite sources:** If you're sharing a tactic from someone else, credit them

### ❌ Don't Do This

- **No affiliate links** in your contributions (conflict of interest — this playbook should be monetization-agnostic)
- **No promotional content** for your own products/services
- **No vague inspiration** ("just create great content!") — be tactical
- **No outdated tactics** (PBN backlinks, keyword stuffing, etc.)
- **No unverified claims** ("I made $50k/mo in 2 months" without proof)

---

## PR Review Process

1. **Submit PR** — Fork, branch, commit, open PR
2. **Community review** — Maintainers + community members review for quality/accuracy
3. **Revisions** (if needed) — Maintainer requests changes
4. **Merge** — PR merged, you're credited in changelog + contributors list

**Typical turnaround:** 3-7 days

---

## Code of Conduct

- **Be respectful** — Constructive feedback only, no personal attacks
- **Assume good intent** — Not everyone is a native English speaker or experienced writer
- **Help newcomers** — We were all beginners once
- **No spam** — Self-promotion is OK in case studies (you built it!), but not in comments/issues

Violations → warning → temp ban → permanent ban (at maintainer discretion)

---

## Questions?

- **Before contributing:** Read `references/README.md` (FAQ covers most questions)
- **During contribution:** Open a Draft PR and tag maintainers for feedback
- **After contribution:** Join the discussion in your PR thread

---

## Recognition

All contributors are credited in:
- `CHANGELOG.md` (per-version contributor list)
- `references/README.md` → "Contributors" section (linked to your GitHub profile)
- Your case study (if applicable) byline

---

## Maintainers

Current maintainers:
- [@David-DL-Space](https://github.com/David-DL-Space) — Original author, case study curator

Want to become a maintainer? Contribute 3+ high-quality PRs (case studies, tactics, or major improvements), then open an issue requesting maintainer access.

---

**Thank you for making this playbook better for the next indie builder!** 🚀
