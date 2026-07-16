# The Prompt Ladder — ML Track
**Task:** Building a machine learning model for FlyRank's Refresh / Content Opportunity Scoring

**A note on the source prompts:** the original "Prompt 3 (Add Context)" and "Prompt 4 (Add Audience)" were identical — the audience line had already been folded into the "context" version, so Prompt 4 added nothing new. That breaks the "one layer per version" rule, so I split it into two clean, non-bundled versions below: context-only, then audience-only. Everything else follows what you had.

---

## Version 0 — Baseline (Weak)

**Prompt:**
> Help me build a machine learning model for content opportunities.

**Output (representative excerpt):**
> Sure! To build a machine learning model for identifying content opportunities, here's a general approach:
> 1. **Define the problem** — are you predicting which content needs updating, which topics to create, or something else?
> 2. **Collect data** — gather relevant historical data (traffic, engagement, etc.)
> 3. **Engineer features** — turn raw data into signals the model can learn from
> 4. **Choose a model** — classification or regression depending on your target
> 5. **Train and evaluate** — split data, train, check accuracy
> 6. **Deploy and monitor**
>
> Let me know more about your data and I can get more specific!

**Notes:**
- **What changed in the prompt:** Nothing — starting point.
- **What actually improved in the output:** N/A.
- **What still failed:** "Content opportunities" is so vague the model had to ask what problem I'm even solving. The five-step answer is the generic ML pipeline you'd get for literally any prediction task — nothing here is specific to search data, SEO, or FlyRank.
- **What I'd try next:** Give it an actual, named prediction goal.

---

## Version 1 — Add a Clear Goal

**Prompt:**
> Help me build a machine learning model that identifies pages needing content review using search performance data.

**Output (representative excerpt):**
> Here's how I'd approach this: since "needs review" isn't usually a label you have ground truth for, you have two options:
> - **Heuristic labeling:** define "needs review" using rules (e.g., ranking dropped 5+ positions over 90 days, or impressions grew but clicks didn't), then train a classifier to predict that label.
> - **Direct regression on decline signals:** predict a continuous "decline score" instead of a binary label, using features like ranking position trend, CTR trend, impression trend, and time since last content update.
> Candidate features from search performance data: average position, position volatility, CTR vs. expected CTR for that position, impression trend, click trend.

**Notes:**
- **What changed in the prompt:** Added a specific goal — identifying pages needing content review — instead of the vague "content opportunities."
- **What actually improved in the output:** The model stopped giving a generic ML checklist and immediately surfaced the real, non-obvious problem: there's no ground-truth label for "needs review," so it has to be constructed via heuristics or reframed as a regression problem. It also proposed a real candidate feature list grounded in search metrics instead of "gather relevant data."
- **What still failed:** It's still guessing at what data actually exists. It assumed generic SEO metrics but doesn't know this is specifically FlyRank's dataset, doesn't know the product name, and doesn't know what fields are actually available or anonymized.
- **What I'd try next:** Give it the actual dataset and product context.

---

## Version 2 — Add Context (dataset + product, only)

**Prompt:**
> Help me build a machine learning model for Refresh / Content Opportunity Scoring using FlyRank's anonymized search dataset.

**Output (representative excerpt):**
> Given the name "Content Opportunity Scoring," this sounds like a ranking/scoring problem rather than a binary classifier — you want to rank pages by opportunity, not just flag yes/no.
> Since the dataset is anonymized search data, you likely have fields like: query, page URL (or page ID), clicks, impressions, average position, and date — but probably not user-level or client-identifying data. That limits some feature ideas (no user segment features) but is fine for aggregate SEO signals.
> I'd frame this as a regression problem predicting an "opportunity score" per page, built from position trend, CTR-vs-expected-CTR gap, and impression trend, then rank pages by that score for review.

**Notes:**
- **What changed in the prompt:** Added the actual product name (Refresh / Content Opportunity Scoring) and named the real dataset (FlyRank's anonymized search dataset), with no audience specification yet.
- **What actually improved in the output:** The framing shifted from "classifier: needs review or not" to "regression/ranking: score and rank pages" — which matches what a *scoring* product actually needs. It also started reasoning about anonymization constraints (no user-level features) instead of assuming generic access to all data.
- **What still failed:** It's still explaining basic things I already know (what a regression problem is, what "ranking" means) — it doesn't know it's talking to someone with an ML background, so the explanation is padded with concepts an intern with Python/scikit-learn experience doesn't need spelled out.
- **What I'd try next:** Tell it who it's actually explaining this to.

---

## Version 3 — Add Audience (only)

**Prompt:**
> Help me build a machine learning model for Refresh / Content Opportunity Scoring using FlyRank's anonymized search dataset. Explain the solution for a machine learning intern who already understands Python and scikit-learn.

**Output (representative excerpt):**
> Frame this as a regression problem: target = an "opportunity score," features derived from position/CTR/impression trends. In `scikit-learn`, I'd start with `GradientBoostingRegressor` or `HistGradientBoostingRegressor` as a baseline over a linear model, since page-level SEO signals tend to interact non-linearly (e.g., a position improvement matters more at position 8 than position 80). Watch for class imbalance in the sense that most pages are "fine" and only a few are true opportunities — this affects how you should weight validation, even in a regression setup (consider stratifying folds by a binned version of the score). Also consider `Pipeline` + `ColumnTransformer` to handle any categorical fields (e.g., content type) alongside numeric trend features.

**Notes:**
- **What changed in the prompt:** Added the audience — a machine learning intern who already knows Python and scikit-learn.
- **What actually improved in the output:** It stopped explaining basic concepts (no more "here's what a regression problem is") and jumped straight to sklearn-specific implementation detail — actual class names (`HistGradientBoostingRegressor`, `Pipeline`, `ColumnTransformer`) and a genuinely non-obvious insight about stratifying validation folds even for a regression target. This is the "it stopped explaining basics my reader already knows" kind of improvement the assignment is looking for.
- **What still failed:** The answer is a dense, unstructured paragraph mixing target design, model choice, and validation strategy together. It's harder to scan or hand off to someone else than it needs to be.
- **What I'd try next:** Ask for a structured format so each concern (features, target, model, validation, limitations) is separated.

---

## Version 4 — Add Output Format

**Prompt:**
> Help me build a machine learning model for Refresh / Content Opportunity Scoring using FlyRank's anonymized dataset. Explain it for a machine learning intern. Present the answer with sections for Features, Target Variable, Model Choice, Validation Strategy, and Limitations.

**Output (representative excerpt):**
> **Features:** Position trend (30/90-day), CTR vs. expected CTR for position, impression trend, time since last content update, content length, internal link count.
> **Target Variable:** A continuous "opportunity score" derived from combining decline signals (e.g., weighted sum of normalized position drop and CTR gap).
> **Model Choice:** `HistGradientBoostingRegressor` as a strong non-linear baseline; compare against a simple linear baseline to justify the added complexity.
> **Validation Strategy:** Time-based split (train on older data, validate on more recent) rather than random split, since SEO trends drift over time.
> **Limitations:** The opportunity score is only as good as the heuristic used to define it; there's no true ground truth for "should be refreshed."

**Notes:**
- **What changed in the prompt:** Added a required section structure (Features, Target Variable, Model Choice, Validation Strategy, Limitations).
- **What actually improved in the output:** Much easier to scan and hand to someone else — each concern lives in its own labeled block instead of one dense paragraph.
- **What still failed (the honest "made it worse" moment):** The rigid sectioning fragmented reasoning that belongs together. "Time since last content update" got listed as a plain feature, but whether that's actually safe to use depends on *when* it's measured relative to the label — that's a leakage risk that logically belongs next to the Target Variable discussion, not buried as a bare bullet under Features. Version 3's denser paragraph, for all its scanability problems, at least kept related reasoning next to each other; forcing content into fixed buckets here scattered a concern that needed to be considered holistically, and the leakage risk got no real flag or discussion — it just quietly disappeared.
- **What I'd try next:** Add explicit quality criteria that force it to check its own feature list for leakage and causal overreach, rather than trusting the section headers alone to produce rigor.

---

## Version 5 — Final Reusable Prompt (Add Quality Criteria)

**Prompt:**
> Help me design a machine learning solution for Refresh / Content Opportunity Scoring using FlyRank's anonymized search dataset. Explain the solution for a machine learning intern who already understands Python and scikit-learn. Organize the response into sections for Features, Target Variable, Model Choice, Validation Strategy, Evaluation Metrics, and Limitations. Ensure every proposed feature is available at prediction time, avoid data leakage, distinguish correlation from causation, and recommend approaches appropriate for decision-support rather than causal prediction.

**Output (representative excerpt):**
> **Features:** Position trend, CTR-vs-expected gap, impression trend, content age *(time since last update, confirmed available at prediction time since it's just a lookup, not derived from future data)*. **Excluded:** any feature that uses post-refresh traffic to construct the opportunity score itself — that would leak the label into a feature.
> **Target Variable:** Opportunity score built purely from pre-refresh decline signals, never touching outcomes of any past refresh.
> **Model Choice:** `HistGradientBoostingRegressor`, benchmarked against a linear baseline.
> **Validation Strategy:** Time-based split; additionally validate that feature distributions don't shift in ways that would only be knowable in hindsight.
> **Evaluation Metrics:** Rank correlation (Spearman) between predicted and actual "improved after refresh" outcomes, plus precision@k for the top-N flagged pages, since this is a prioritization tool, not a binary classifier.
> **Limitations:** A high opportunity score means this page resembles others that historically improved after a refresh — it does **not** mean refreshing *causes* the improvement; other factors (seasonality, competitor changes) could explain past gains. Treat this strictly as a prioritization aid for a human reviewer, not an automated refresh trigger.

**Notes:**
- **What changed in the prompt:** Added explicit quality criteria (leakage checks, prediction-time availability, correlation-vs-causation framing, decision-support framing) plus one added section (Evaluation Metrics) to hold the new rigor.
- **What actually improved in the output:** This is where the leakage issue lost in V4 came back — but properly this time, as an explicit check applied *across* sections rather than confined to one box (it's called out in Features, reinforced in Target Variable, and checked again in Validation). It also added something no earlier version had at all: a direct statement that a high score is correlational, not causal, and a clear instruction that this is a human-reviewed prioritization tool, not an autonomous decision-maker.
- **What still failed:** It's still just reasoning about leakage and causality in the abstract — it hasn't actually seen the real anonymized dataset's schema, so "confirmed available at prediction time" is really more of a prompt to double-check than a verified fact.
- **What I'd try next:** Feed it an actual (anonymized) sample of the dataset schema so the leakage check can be made against real columns instead of hypothetical ones.

---

## Final Reusable Prompt

> Help me design a machine learning solution for [named product/task] using [actual dataset, named]. Explain the solution for [specific audience — their existing skill level, so you don't over- or under-explain].
>
> Organize the response into sections for: Features, Target Variable, Model Choice, Validation Strategy, Evaluation Metrics, and Limitations.
>
> Quality criteria — for every part of the answer:
> - Confirm every proposed feature would actually be available at prediction time (not derived from the outcome you're trying to predict).
> - Explicitly flag any risk of data leakage between features and the target.
> - Distinguish correlation from causation in the Limitations section — don't imply the model's output causes an outcome unless that's actually justified.
> - Frame the solution as decision-support for a human reviewer, not an autonomous or causal prediction, unless stated otherwise.

This works for someone else on the track because every bracket is fill-in-the-blank, and the quality-criteria block travels with the prompt regardless of what model you're asking it to design — it's the same four checks whether you're scoring content, churn, or fraud.
