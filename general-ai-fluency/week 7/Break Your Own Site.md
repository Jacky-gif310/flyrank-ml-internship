# Break Your Own Site — Hardening Review
**Site:** jacky-gif310.github.io/jackline-portfolio
**Pages tested:** Home, Case Studies, Process, About
## What I tried
- Loaded all four pages directly and checked every image, icon, and PDF link resolves (not just the happy-path click-through)
- Checked SEO/meta (title, description, Open Graph, Twitter card) is present on every page, not just the homepage
- Tested the contact form for a fast double-click / double-submit
- Clicked every outbound link (GitHub, LinkedIn, Calendly, CV, notebook links)
## Where it broke
| Finding | Page | Status |
|---|---|---|
| Missing SEO/meta tags (description, OG, Twitter card) | About, Case Studies | **Fixed** |
| Missing SEO/meta tags | Home, Process | **Fixed** |
| Three images returning 404: `notebook-screenshot-cropped.png`, `github-repo-screenshot.png`, `research-doc-cropped.png` | Case Studies | **Fixed** — [describe what you did: uploaded real screenshots / removed the broken figures] |
| Contact form had no guard against a fast double-click submitting twice | About | **Fixed** — submit button now disables itself while the request is in flight and re-enables on success or error |
| No live model demo | Process | **Known limitation, not hidden** — documented on the Process page itself as a deliberate scope decision (no trained model to demo yet at build time) |
| Formspree free tier has no server-side spam filtering beyond HTML5 `required` validation | About (contact form) | **Known limitation** — acceptable for a portfolio-scale contact form, would need a captcha or server-side check for higher traffic |
## Speed check
PageSpeed Insights score for the homepage: **[Desktop 99/100 Performance. Mobile — Performance 90, Accessibility 95, Best Practices 100, SEO 100.]**
## Outcome
All fix-now items above are resolved and live. The two known limitations are named rather than hidden, and neither blocks core site function.
