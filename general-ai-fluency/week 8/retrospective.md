# Retrospective — FlyRank AI Internship
**Jackline Mutheu**

Dear Week-1 me:

You picked "Refresh / Content Opportunity Scoring" because it sounded like the most practical lane — content teams need to know which pages to review first, and that felt like a real problem instead of a toy one. You were right about that. What you didn't know yet was how much of the actual work would be *un*-learning the instinct to trust a good-looking number.

**What I set out to do:** build a model that ranks pages by whether they're worth a human's review time. Simple enough on paper. What actually happened was five weeks of discovering, one layer at a time, how many ways a result can look right and be wrong.

**What changed.** The first real turn was Week 4's baseline — a hand-written CTR-gap rule I was almost proud of, until I evaluated it honestly against the real target and found it scored *worse than random selection*. That stung for about five minutes, and then it became the most useful thing that happened all internship, because it meant I stopped trusting "it makes sense to me" as a substitute for "I checked." Week 5 built on that discomfort: I caught real data leakage — two features that turned out to be the literal ingredients of my own label — and had to redo the whole comparison after removing them. Week 6 went further and found that a naive random train/test split had let 31 of 32 clients leak across train and validation, inflating my ROC-AUC by nearly 0.2 points. None of these were dramatic failures. They were quiet, easy-to-miss mistakes that only showed up because I went looking for them on purpose, which is the actual skill this internship was teaching underneath the Python.

The AI Fluency track changed something different: how much I trust my own judgment over a plausible-sounding suggestion. When I built my portfolio's identity kit, I generated a network-graph hero image, looked at it, and rejected it — not because it was broken, but because it was the single most overused visual in AI-adjacent design right now, and it said nothing specific about my actual work. That rejection mattered more than any of the images I kept. Same instinct showed up building the automation workflow into an agent: the interesting part wasn't getting it to search, it was teaching it — and myself — what "enough sources" actually means, and what happens when a topic is too broad to have a clean stopping point.

**What I'd build next.** The honest answer is the thing my own README already names as a gap: my agent doesn't have a good rule for broad topics yet. I found that live, while testing it for the demo video, and it's exactly the kind of limitation worth fixing rather than hiding. I'd also want to close the loop on the model itself — right now it's evaluated on one client-grouped split; a real next version would validate across multiple splits and actually track whether Precision@50 holds up on genuinely new clients over time, not just one holdout.

**The three most transferable things I learned:**

1. **A baseline isn't a formality — it's the thing your "better" model actually has to beat, and it needs to be evaluated as harshly as the real model.** Mine lost. That was more useful than if it had won.
2. **The split matters as much as the model.** I spent more time this internship thinking about how to divide data honestly than I spent tuning any model's hyperparameters, and it was the higher-leverage time by a wide margin.
3. **Rejecting AI output on purpose is a skill, not a failure of the tool.** Whether it was an image, a stat that sounded too clean, or a claim phrased with more confidence than the evidence supported — catching that and saying "no, rewrite this honestly" was the actual work, over and over.

You started this wanting to build something that worked. What you actually built was a habit of checking whether it really did — and writing down the answer even when it was uncomfortable. That habit is the part I'm keeping.

— Jackline, Week 8
