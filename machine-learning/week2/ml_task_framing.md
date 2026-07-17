# Machine Learning Task Framing

## Capstone Lane
**Refresh / Content Opportunity Scoring**

## Problem Statement
The goal is to identify and rank webpages that are most likely to benefit from a content review using anonymized search performance signals.

## Why Machine Learning?
Simple rules (for example, "CTR < 2%") cannot capture complex relationships between multiple search signals. A machine learning model can combine trends in impressions, clicks, CTR, rankings, and other available features to estimate which pages deserve review.

## ML Task Type
**Ranking / Scoring**

The objective is to assign each page an opportunity score so pages can be prioritized for manual review.

## Input Features
- Click trend
- Impression trend
- CTR
- Average position
- Position trend
- Content age (if available)
- Other prediction-time features available in the dataset

## Target
A proxy opportunity score derived from historical search performance signals. The proxy will be constructed by identifying pages that later showed measurable improvement (such as CTR, position, or clicks) after a manual content refresh and comparing them with similar pages that were not refreshed and did not improve. Where refresh outcome data is unavailable, sustained negative trends in clicks, impressions, and rankings over a defined period (for example, 3–6 months), weighted by search volume, will be used to approximate opportunity.

## Baseline
A rule-based scoring system using simple thresholds on CTR decline and ranking decline.

## Candidate Model
**HistGradientBoostingRegressor**

## Validation Strategy
Use a time-aware validation strategy by training on earlier time periods and validating on later periods to reduce data leakage and better reflect real-world prediction.

## Success Metrics
- **Spearman Rank Correlation** – Measures how well the predicted ranking of pages matches the true opportunity ranking.
- **Precision@K** – Measures how many of the top-K recommended pages are truly high-opportunity pages, reflecting the usefulness of the ranking for limited manual review capacity.
- **Mean Absolute Error (MAE)** – Measures the average prediction error when estimating the continuous opportunity score.

## Limitations
This model identifies observed associations between search performance signals and content opportunities. It does not prove that refreshing content causes ranking improvements. The results should therefore be used as decision support for human reviewers rather than as automated decision-making.
