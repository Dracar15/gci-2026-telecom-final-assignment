# gci-2026-telecom-final-assignment
# Predicting Customer Churn and Offering Right-Sized Plans (Company A)

**Author:** Merrick22  
**Program:** GCI World 2026 September — Final Assignment  
**License:** Apache License 2.0  

## 1. Project Overview & Business Question

Telecom operators face high subscriber churn in competitive multi-SIM markets
where acquiring new customers costs 5x to 25x more than retaining existing
ones. Using historical customer and usage data from **Company A**, this project
addresses the following business question:

> *"Which customers, especially in their second year, show early signs of
> disengagement and should be prioritised for a retention action before they
> leave?"*

## 2. Dataset & Preparation

- **Source:** Company A telecom dataset (`Client.csv` and `Record.csv`,
  GCI World 2026 September), joined on `Customer_ID` (100,000 records).
- **Cleaning:** Removed 909 rows (0.9%) with missing usage/revenue trend
  indicators or negative monthly recurring charges, resulting in **99,091
  customers** (49.3% churned within the 31–60 day observation window).
- **Feature Engineering:** 11 core behavioral and billing variables (tenure,
  monthly plan charge, minutes of use, usage/revenue trends, overage charges,
  customer-care calls) plus 2 derived ratios (overage share of revenue, minutes
  per plan dollar). Equipment and demographic variables were excluded after EDA
  showed no discriminatory power.
- **Train/Test Split:** Stratified 80/20 split (79,272 training / 19,819 test
  customers).

## 3. Modeling & Key Results

- **Model:** Random Forest Classifier (400 trees, `max_depth=10`,
  `min_samples_leaf=20`), selected over Gradient Boosting (ROC-AUC 0.647) and
  Logistic Regression (ROC-AUC 0.569) for comparable discrimination and higher
  interpretability.
- **Performance:** **ROC-AUC = 0.646** on the test set; overall accuracy of
  **59.9%** at the 0.50 threshold.
- **Top Drivers:** Customer tenure (`months`), percentage change in monthly
  usage (`change_mou`), and monthly recurring plan charge (`totmrc_Mean`).
- **Targeting Efficiency:** Focusing on the **top 10% highest-risk customers**
  (1,981 subscribers) captures **73.2% precision** (~1.5x better than random
  targeting) and reaches 14.8% of all leavers.

## 4. Business Proposal & Financial Impact

- **Action:** Proactive outreach by the marketing team 2–3 months before the
  second-year churn peak (13–18 months), starting with a short feedback form
  followed by a usage-adjusted plan and regular consumption reminders.
- **Rollout Strategy:** Controlled pilot with a holdout group before full
  deployment, to prevent unintended churn from unsolicited plan offers.
- **Estimated Base-Case Impact (Test Sample):** **+$17,350/month net**
  ($21,312 retained revenue minus $3,962 contact cost at $2/contact and a 25%
  assumed success rate).

## 5. Repository Structure

- Merrick22.pdf` — 15-slide executive
  presentation.
- `Merrick22.ipynb` — Full Python notebook (EDA, preprocessing,
  modeling, evaluation, and financial simulation).
- `README.md` — This file.

## 6. AI Usage Disclosure

Claude, Quri AI, Gemini and DeepSeek were used for code explanation and
debugging, notebook interpretation, problem formulation, result comparison
and proposal refinement. ChatGPT was used for slide editing. Conversation
URLs are provided in the Omnicampus References field.
