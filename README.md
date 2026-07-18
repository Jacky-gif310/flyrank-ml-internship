# FlyRank AI Internship Portfolio

This repository contains my assignments, experiments, and learning journey from the **FlyRank AI Internship program**. It documents my progress in Artificial Intelligence, Machine Learning, Data Analysis, and practical AI workflows through hands-on projects.

---

# Machine Learning Track

## Week 1: First Look and Discovery

* Ran a complete machine learning pipeline using anonymized search data.
* Explored dataset structure and discovered patterns through data analysis.
* Compared a hand-written baseline rule with machine learning approaches.
* Learned the importance of building simple, explainable solutions before applying complex models.

**Notebook:**

* `machine-learning/week1/01_first_look_and_discovery.ipynb`

---

## Week 1: Your First Readable Model

* Created a simple ranking approach for content opportunities.
* Trained a decision tree model and interpreted how it made decisions.
* Compared model performance with a manual baseline approach.
* Explored data leakage and why preventing leakage is important for reliable machine learning.

**Notebook:**

* `machine-learning/week1/02_your_first_readable_model.ipynb`

---

## Week 1: Research Question and Provisional Lane

**Selected Lane:** Refresh / Content Opportunity Scoring

I selected this lane to explore how machine learning can help prioritize content pages that may deserve human review based on observable search performance signals.

### Research Question

**Decision:**
Which pages should be reviewed first for possible content improvement?

**Action:**
Help content teams prioritize pages for investigation, improvement, monitoring, or protection.

**Cost of Wrong Recommendation:**
A wrong recommendation could waste time and resources on pages that do not need changes while causing important opportunities to be overlooked.

**Why Machine Learning Can Help:**
Machine learning can identify patterns in search and engagement data that may not be obvious through simple rules.

**Notebook:**

* `work/notebooks/w01_research_question.ipynb`
---

## Week 2: ML Task Framing 

Completed the ML-03 assignment: **Frame Your Lane as an ML Task**.

The goal was to transform the Refresh / Content Opportunity Scoring idea into a clear machine learning problem by defining:

* The ML task type.
* The prediction target or proxy label.
* A measurable success metric.
* The unit of analysis.
* Why machine learning is more suitable than a fixed rule.

### Key Outcomes

* Framed the problem as a **binary classification task**.
* Created an `opportunity_proxy` target using observed search performance signals.
* Defined pages as possible content opportunities when:
  * `trend_direction` is `"down"`
  * `avg_position` is greater than `10`
* Selected **ROC-AUC** as the evaluation metric because the goal is to prioritize pages for human review.
* Confirmed that each dataset row represents one anonymized content page.

**Notebook:**

* `work/notebooks/w02_ml_task_framing.ipynb`

---
---

## Week 3: Search Intelligence Data Contract

Completed the ML-04 assignment: **Search Intelligence Data Contract**.

The goal was to define the data foundation for the Refresh / Content Opportunity Scoring lane before modeling by documenting how the dataset should be interpreted and used safely.

### Key Outcomes

* Defined the unit of analysis and clarified what each dataset row represents.
* Documented the selected data tables, time window considerations, and modeling objective.
* Identified the prediction target as a proxy decision-support signal rather than a true business outcome.
* Defined safe feature candidates that are available at decision time.
* Performed data quality checks to understand:
  * Data availability limitations.
  * Missing GSC and GA4 signals.
  * Client history imbalance.
  * Potential duplicate or overlapping records.
* Documented excluded information to prevent leakage and maintain public-safe analysis.
* Added honest limitations around:
  * Observational relationships versus causal claims.
  * Uneven data coverage.
  * Lack of confirmed content refresh success labels.

### Data Contract Considerations

The analysis acknowledges that:

* Observed search and engagement signals can support prioritization decisions but cannot prove that a content change will improve rankings or traffic.
* Some pages have limited measurable signals due to missing GSC or GA4 data.
* Client comparisons require caution because historical coverage differs across clients.
* Future feature engineering requires careful aggregation and deduplication.

**Notebook:**

* `work/notebooks/w03_data_contract.ipynb`

---
---

## Week 3: ML Task Framing

Completed the ML Task Framing assignment for the **Refresh / Content Opportunity Scoring** capstone by transforming a business problem into a well-defined machine learning task.

The document defines the prediction objective, candidate features, proxy target, validation strategy, evaluation metrics, and model limitations while emphasizing decision support rather than causal claims.

### Key Outcomes

* Framed the problem as a **ranking / scoring** task.
* Defined prediction-time features while considering data leakage.
* Designed a proxy opportunity score using historical search performance signals.
* Selected **HistGradientBoostingRegressor** as the candidate model.
* Proposed time-aware validation to better reflect real-world deployment.
* Selected Spearman Rank Correlation, Precision@K, and MAE as evaluation metrics.
* Documented limitations around observational data and causation.

**Deliverable:**

* `machine-learning/week2/ml_task_framing.md`

---
---

# General AI Fluency Track

## Week 1: Draw the Path - Portfolio Sitemap + Toolkit

* Created a portfolio sitemap to organize my professional online presence.
* Configured a Claude Project with custom instructions.
* Used AI feedback to improve portfolio structure and career positioning.

**Deliverables:**

* Portfolio sitemap
* Claude Project configuration

---

## Week 1: AI Workflow Audit and Tool Setup

* Completed a personal workflow audit by identifying recurring tasks and classifying how AI can support them.
* Created and configured a Claude Project based on my learning goals and preferred working style.
* Enrolled in the Anthropic Academy AI Fluency course and completed the first module.
* Selected reusable AI-assisted tasks with measurable success definitions.

**Deliverables:**

* AI Workflow Audit document
* Claude Project instructions
* Anthropic Academy completion evidence

---

## Week 1: Proof Statement

Created a professional proof statement using AI as a thinking partner to refine my career message.

The statement focuses on:

* **Primary skill:** Machine Learning
* **Target person:** Machine Learning hiring manager
* **Desired action:** Review my GitHub portfolio
* **Purpose:** Demonstrate practical skills and projects that cannot be fully shown through a CV or LinkedIn profile alone.

**Deliverable:**

* Proof statement PDF

---
---

## Week 2: Frame It as Cases

Completed the Week 2 AI Fluency assignment by transforming my internship work into portfolio-ready case studies that communicate the problem, my decisions, and the outcomes in my own voice.

The document includes:

* A personal **Voice Card** to guide consistent AI-assisted writing.
* Framed case studies for my internship projects using:
  * Problem
  * What I did and the decisions I made
  * Outcome
* A professional bio tailored to my target audience.
* A contact / call-to-action section.
* A before-and-after comparison showing how I edited generic AI-generated writing into language that reflects my own experience and voice.

**Deliverable:**

* `general-ai-fluency/week 2/FlyRank_Week2_Frame_It_As_Cases_Jackline_Mutheu.pdf`
---

## Week 2: Prompt Iteration Log

Completed the Prompting Fundamentals assignment by documenting how prompt engineering techniques improved AI-generated machine learning solutions for the **Refresh / Content Opportunity Scoring** capstone.

The log demonstrates an iterative refinement process, progressing from a simple prompt to a reusable prompt template through multiple prompt engineering techniques.

### Key Outcomes

* Applied role assignment to improve domain-specific responses.
* Added project context and business motivation to produce more relevant outputs.
* Used few-shot examples to guide the model's reasoning style.
* Specified an output structure to generate consistent technical reports.
* Applied step decomposition to improve reasoning quality and reduce missing steps.
* Compared responses from ChatGPT and Claude to identify their strengths and limitations.
* Created a reusable prompt template for future machine learning design tasks.

**Deliverable:**

* `general-ai-fluency/week2/prompt_iteration_log.md`

---
---
# Tools Used

* Python
* Google Colab
* Pandas
* NumPy
* Scikit-learn
* Claude AI
* Anthropic Academy
* GitHub

---

# Purpose

The goal of this repository is to document my growth in Artificial Intelligence, Machine Learning, and Data Analytics by showcasing practical assignments, experiments, and projects completed during the FlyRank AI Internship.

This portfolio demonstrates my ability to:

* Explore and analyze data.
* Frame real-world problems as machine learning tasks.
* Apply machine learning concepts.
* Build and evaluate models.
* Use AI tools responsibly.
* Communicate technical work clearly.
* Create evidence-based projects beyond traditional CV claims.

