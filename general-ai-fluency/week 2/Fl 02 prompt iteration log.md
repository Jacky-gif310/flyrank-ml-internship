# Prompt Iteration Log — Prompting Fundamentals on Real Tasks v2

## Task

Design a machine learning solution for FlyRank's Refresh / Content Opportunity Scoring problem using anonymized search data.

The goal is to create a model that can prioritize webpages that may need content review using search performance signals.

---

# Version 0 — Naive Prompt

## Technique Applied
None (baseline)

## Prompt

Help me build a machine learning model for content opportunities.

## Output Summary

The response gave a generic machine learning workflow:

- Collect data
- Clean data
- Select features
- Train a model
- Evaluate results

## Notes

**What changed?**

Nothing. This was the original prompt I would have written before learning prompt engineering techniques.

**What improved?**

Nothing. The answer was generic and could apply to almost any ML problem.

**What failed?**

It did not understand the actual business problem, dataset, or expected output. It did not identify whether this was classification, ranking, or scoring.

**Next improvement:**

Add a clear role and objective.

---

# Version 1 — Role Assignment

## Technique Applied
Role assignment

## Prompt

Act as a machine learning engineer helping an ML intern design a search intelligence model. Help me build a machine learning solution for identifying content opportunities.

## Output Summary

The response became more practical and explained how an ML engineer would approach the problem.

It suggested:
- defining the prediction goal
- selecting features
- choosing a model
- validating results

## Notes

**What changed?**

Added a role for the AI to act as a machine learning engineer.

**What improved?**

The response became more structured and professional because it adopted the perspective of an experienced ML practitioner.

**What failed?**

It still lacked information about the actual FlyRank dataset and capstone goal.

**Next improvement:**

Add context and motivation.

---

# Version 2 — Context and Motivation

## Technique Applied
Context and motivation

## Prompt

Act as a machine learning engineer helping an ML intern. I am working on FlyRank's Machine Learning capstone. My task is Refresh / Content Opportunity Scoring using anonymized search performance data. The goal is to rank pages that may benefit from content review. Help me design an appropriate ML approach.

## Output Summary

The response recognized that this was a ranking/scoring problem rather than a simple classification problem.

It suggested:
- search performance features
- proxy targets
- ranking metrics
- leakage concerns

## Notes

**What changed?**

Added project background, dataset context, and the reason the model is needed.

**What improved?**

The response became specific to search intelligence instead of generic machine learning.

**What failed?**

The answer did not provide concrete examples of the desired output structure.

**Next improvement:**

Add examples and expected format.

---

# Version 3 — Few-Shot Examples

## Technique Applied
Few-shot examples

## Prompt

Act as a machine learning engineer helping an ML intern.

I am working on FlyRank's Refresh / Content Opportunity Scoring project using anonymized search data.

Examples of the type of reasoning I need:

Example:
Feature: CTR decline
Reason: Pages losing click efficiency may need review.

Example:
Validation: Time-based split
Reason: Future information should not leak into training.

Now design a complete ML approach for my project using similar reasoning.

## Output Summary

The response started producing explanations similar to the examples.

It included:
- feature reasoning
- validation reasoning
- model justification

## Notes

**What changed?**

Added examples showing the expected reasoning style.

**What improved?**

The output became more analytical and explained why each decision was made.

**What failed?**

The answer still combined many ideas together instead of following a clear final report structure.

**Next improvement:**

Specify the output format.

---

# Version 4 — Output Structure

## Technique Applied
Output structure

## Prompt

Act as a machine learning engineer helping an ML intern.

I am working on FlyRank's Refresh / Content Opportunity Scoring project using anonymized search data.

Provide the solution using these sections:

1. Problem Definition
2. ML Task Type
3. Features
4. Target Variable
5. Model Choice
6. Validation Strategy
7. Evaluation Metrics
8. Limitations

Ensure explanations are concise and practical.

## Output Summary

The response became easier to read and organize.

It clearly separated:
- features
- target
- model
- validation
- limitations

## Notes

**What changed?**

Added an explicit output format.

**What improved?**

The answer became easier to review and use in a technical document.

**What failed?**

The response still needed stronger reasoning checks around leakage and causation.

**Next improvement:**

Use step decomposition and quality checks.

---

# Version 5 — Step Decomposition

## Technique Applied
Step decomposition

## Prompt

Act as a machine learning engineer helping an ML intern.

I am working on FlyRank's Refresh / Content Opportunity Scoring project using anonymized search data.

Work through the solution step by step:

Step 1: Define the ML problem.
Step 2: Decide whether ranking, classification, clustering, or scoring fits best.
Step 3: Define possible features available at prediction time.
Step 4: Define a proxy target.
Step 5: Select a baseline and ML model.
Step 6: Design validation to prevent leakage.
Step 7: Explain limitations and business interpretation.

Provide the final recommendation after the reasoning process.

## Output Summary

The response became more systematic.

It considered:
- task framing
- feature availability
- leakage
- evaluation
- limitations

## Notes

**What changed?**

Added a step-by-step reasoning process.

**What improved?**

The answer became more reliable because it considered the ML workflow in the correct order.

**What failed?**

The prompt was long and still depended on the user knowing the project context.

**Next improvement:**

Create a reusable template.

---

# Cross-Model Comparison

## ChatGPT

Strengths:
- Produced structured explanations quickly.
- Was strong at organizing ML concepts into sections.
- Clearly explained limitations and validation strategies.

Weaknesses:
- Sometimes suggested assumptions before seeing the actual dataset schema.
- Required reminders to avoid causal claims.

## Claude

Strengths:
- Produced detailed reasoning and careful explanations.
- Was strong at identifying ambiguity in targets and labels.
- More cautious about assumptions.

Weaknesses:
- Responses were sometimes longer than necessary.
- Required stronger formatting instructions for concise outputs.

## Overall Difference

Both models improved significantly when given context, examples, and structure. ChatGPT was more concise and organized, while Claude was more cautious and analytical. The best results came from combining clear instructions, project context, and quality requirements.

---

# Final Reusable Prompt Template

Act as a machine learning engineer helping a [role/audience, e.g. "junior ML intern" or "product manager"].

I am working on **[project name]** using **[dataset description]**. The goal is to **[business objective, e.g. "prioritize items for manual review" or "predict customer churn"]**.

Work through the solution step by step:

Step 1: Define the ML problem.
Step 2: Decide whether classification, ranking, clustering, or scoring fits best, and explain why.
Step 3: Define features available at prediction time only (avoid leakage).
Step 4: Define the target variable, including how any proxy label would be constructed.
Step 5: Select a baseline and a candidate ML model.
Step 6: Design a validation strategy appropriate for the data (e.g. time-aware splits if time-ordered).
Step 7: Recommend evaluation metrics tied to the business goal.
Step 8: Explain limitations, including any leakage risks and the difference between correlation and causation.

Present the final solution using these sections:

- Problem Definition
- ML Task Type
- Features
- Target Variable
- Model Choice
- Validation Strategy
- Evaluation Metrics
- Limitations

Keep explanations concise and practical, and do not assume dataset details that haven't been provided — ask if anything critical is missing.
