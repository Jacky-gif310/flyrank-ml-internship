## Three Roads — Choose Your Stack with AI

---

## My Four Constraints

1. **Free only.** No budget for hosting, domains, or paid tiers.
2. **Honest skill level.** Comfortable editing files and folders directly on GitHub in the browser; not comfortable with terminal/command-line workflows; no prior experience with JavaScript frameworks like React.
3. **What my portfolio needs to do** (from my sitemap + content map): four pages — Home, Case Studies, Process/Approach, About. Each page is mostly long-form text (problem/decision/outcome case studies), screenshot galleries (notebook outputs, GitHub repo views), and links out to my GitHub repo. No page currently needs a live, interactive demo.
4. **Is anything dynamic yet?** No. My capstone model (Refresh / Content Opportunity Scoring) hasn't been trained and evaluated yet, so there's nothing live to embed. My "still need to gather" list from the content-map assignment already flagged this honestly — no live demo exists right now.

---

## Three Stack Options

### Option 1 — Simplest: Plain HTML/CSS + GitHub Pages
- **How I'd build:** Hand-write each page as a static HTML file, reuse the palette/fonts from my Identity Kit directly in the CSS.
- **Where I'd host (free):** GitHub Pages, deployed straight from the same repo.
- **Backend needed?** No.
- **Real trade-off:** Zero build tooling, nothing to break, matches exactly what I already know how to do in the GitHub browser interface. The cost is that every page's header/nav has to be copy-pasted by hand, so keeping four pages visually consistent takes discipline, not automation — and if I ever wanted a genuinely interactive demo later, this stack can't do that on its own.

### Option 2 — Middle: Jekyll (GitHub Pages' built-in static site generator)
- **How I'd build:** Write case studies in Markdown, use a shared layout template so the header/nav/footer are defined once and reused automatically across all four pages.
- **Where I'd host (free):** Still GitHub Pages — Jekyll is natively supported, no separate hosting account needed.
- **Backend needed?** No.
- **Real trade-off:** Solves the repetition problem from Option 1 (one layout file instead of four copy-pasted headers), but adds a real learning curve — front matter syntax, `_config.yml`, Jekyll's folder conventions — for a portfolio that's only four pages. The added structure may cost more setup time than it saves for something this small.

### Option 3 — Most Powerful: React (Next.js) + Vercel, with a live model demo
- **How I'd build:** Build the site as React components, and actually embed an interactive chart or a small live demo of the opportunity-scoring model's output (e.g., a table a visitor can sort/filter).
- **Where I'd host (free):** Vercel's free tier.
- **Backend needed?** Not for the static pages — but yes, if the live demo needs to run real model inference rather than showing precomputed results, I'd need a small backend (e.g. a serverless function) to serve predictions.
- **Real trade-off:** This is the only option that could show the model actually working, not just described in a case study. The cost is real: I have no React experience, I'd be learning a framework and a build pipeline at the same time as trying to hit a two-week deadline, and a live backend is an ongoing thing to maintain, not a one-time build.

---

## Pressure-Testing the Front-Runner (Option 1)

**What breaks if I pick the simplest?**
Nothing breaks outright, but it doesn't scale gracefully — if my portfolio grows past four pages, or if I ever do build a live demo, I'd have to migrate to something else rather than extend this. Right now, with four pages, that's a real but small cost.

**What would I maintain if I picked the most powerful (Option 3)?**
A build toolchain (`node_modules`, `package.json`), a framework I don't know yet, and — if I go all the way to a live inference demo — an actual running backend that needs to keep working, not just a site that sits there. That's ongoing maintenance work for a solo portfolio, not a one-time cost.

**Can I finish in two weeks?**
Yes for Option 1 — I already have it live. Option 2 is possible but not guaranteed, since I'd be learning Jekyll's conventions from scratch. Option 3 is genuinely risky on this timeline given I have zero React background.

**Does it show my work the way it needs to be shown?**
Yes. My content map is long-form case studies, screenshot galleries, and repo links — all things static HTML handles natively. The one thing Option 3 could do that Option 1 can't (a live interactive demo) isn't something I actually have yet, since my model isn't trained and evaluated. Choosing the "more powerful" stack to support a demo that doesn't exist yet would be solving a problem I don't have.

---

## Decision

**Chosen stack: Plain HTML/CSS + GitHub Pages** (Option 1) — already live at `https://jacky-gif310.github.io/jackline-portfolio/`.

**Why not Jekyll (Option 2):** The templating would pay off if I had many similar pages, but I have four, and I'd rather spend my two weeks writing the actual case studies than learning a templating system to avoid copy-pasting a header four times.

**Why not React + Vercel (Option 3):** It's the only option that could show a live, working demo — which is genuinely appealing for an ML portfolio — but I don't have a trained model to demo yet, so the extra complexity would be in service of something that doesn't exist. If I finish the capstone model with time to spare, this is the option I'd revisit, not because my current site is wrong, but because a live demo would be a real, new capability worth the extra maintenance.

**Can I maintain this?** Yes — it's plain files in a repo I already know how to edit from the browser. There's no dependency to update, no build step to keep working, nothing that can silently break between now and when a hiring manager clicks the link.

**Does it show my work well?** Yes, for what I actually have right now: written case studies, real screenshots, and links to my GitHub repo. It would stop being enough only if I add a live demo — which is a future decision, not a gap in this one.
