# Survive the Crit — Final
**Jackline Mutheu**

**Reviewer:**  — via structured Google Form
**Proof statement given:** "I demonstrate practical machine learning skills by using Python and data analysis workflows to explore datasets, build beginner-level machine learning models, and communicate data-driven insights for real-world decisions... The main action I want them to take is to review my GitHub portfolio and consider me for a machine learning internship or entry-level opportunity."

## The two opening questions

**"In one sentence, what do I actually do?"**
> "You build decision-support ML systems — specifically, a model that ranks which web pages are worth reviewing for a refresh, based on search-performance signals, with the trained model's reasoning and limitations documented alongside it."

**"Would you trust me to do real ML work?"**
> "Leaning yes, but something felt thin or unproven."

## Full feedback

- **One action they'd take:** "Check the GitHub repo — specifically the modeling notebook, to see the leakage fix in the raw code rather than just the write-up."
- **Where they got confused:** "Case Studies page, at the metrics table. The three numbers (ROC-AUC, Precision@50, Precision@20) are reported with no baseline-for-comparison sentence, so I had to reread the surrounding paragraph twice to work out whether 0.320 was a strong or weak result."
- **Anything broken:** "Everything worked."
- **The one thing to fix:** "The evidence doesn't back up the claim" (selected over "opening claim unclear," "confusing to navigate," "visually broken").
- **Additional:** "Good: the Process page's honesty about false positives/negatives and the deliberate skip of a fake live demo are rare and worth keeping as-is. Critical: the biggest opening for improvement is still context on the metrics — a reader can't tell if Precision@50 = 0.320 is good without a comparison point."

## Sort

**Must-fix (one, corroborated three separate ways — in the confusion question, the pick-one question, and the free-text critique):**
- The metrics table had no plain-language interpretation, so a non-expert reader couldn't tell if the results were good or bad.

**Nice-to-have:** none surfaced — no navigation, visual, or broken-link issues reported.

**Keep as-is (explicitly praised):** the Process page's honesty about model errors, and the decision not to fake a live demo.

## What I changed

Added a plain-language interpretation sentence directly under the metrics table on the Case Studies page: *"Precision@50 of 0.320 means roughly 1 in 3 pages the model flags as top-50 priorities are genuine opportunities — versus the baseline's 0.040, which is worse than picking pages at random (the validation set's real opportunity rate was 0.232)."*

**Note on process:** I did an initial self-review before getting real feedback, which flagged the headline as the top concern. The real reviewer disagreed — they picked the metrics-context gap instead, and didn't flag the headline at all. That mismatch is exactly why this checkpoint requires a real second pair of eyes rather than self-analysis: I couldn't see the actual gap until someone else pointed at it.

**Live site re-checked after fix:** confirmed the updated metrics context is live at https://jacky-gif310.github.io/jackline-portfolio/case-studies.html
