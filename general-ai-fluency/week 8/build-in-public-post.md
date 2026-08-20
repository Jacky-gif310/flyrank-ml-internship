# Build-in-Public Post — FlyRank AI Internship

I just wrapped my FlyRank AI Internship capstone: a decision-support model that ranks content pages by likelihood of needing a refresh, built on real search-performance data across 32 anonymized clients.

**One real decision:** I built a hand-written baseline rule before touching a trained model — a CTR-gap score comparing each page's click-through rate against what its position typically earns. When I evaluated it honestly against the actual target, it scored *worse than random selection*. I could have quietly moved past that. Instead I kept it in the paper, because a baseline that loses is still useful information — it told me the rule was solving a different question than the one I actually needed answered.

**One real limitation:** my final model was validated on a single client-grouped split. When I tested a naive random split for comparison, ROC-AUC jumped by almost 0.2 points — because 31 of 32 clients ended up leaking across train and validation. The honest number is the lower one. I'm naming that limitation directly rather than reporting the flattering split and hoping no one asks.

Full write-up, code, and the deployed research paper: https://jacky-gif310.github.io/jackline-portfolio/ / https://jacky-gif310.github.io/flyrank-ml-internship/

#MachineLearning #DataScience #FlyRankInternship
