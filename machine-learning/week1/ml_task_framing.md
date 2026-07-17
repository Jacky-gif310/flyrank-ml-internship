# Machine Learning Task Framing

## Capstone Lane
Refresh / Content Opportunity Scoring

## Problem Statement
The goal is to identify and rank webpages that are most likely to benefit from a content review using anonymized search performance signals.

## Why Machine Learning?
Simple rules (for example, "CTR < 2%") cannot capture complex relationships between multiple search signals. A machine learning model can combine trends in impressions, clicks, CTR, rankings, and other features to estimate which pages deserve review.

## ML Task Type
Ranking / Scoring

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
Proxy opportunity score derived from historical search performance signals.

## Baseline
A rule-based scoring system using simple thresholds on CTR decline and ranking decline.

## Candidate Model
HistGradientBoostingRegressor

## Validation Strategy
Time-aware validation to avoid leakage by training on earlier periods and validating on later periods.

## Success Metrics
- Spearman Rank Correlation
- Precision@K
- Mean Absolute Error (if predicting a score)

## Limitations
The model identifies observed associations only. It does not prove that refreshing content causes ranking improvements and should be used for decision support rather than automated decisions.
