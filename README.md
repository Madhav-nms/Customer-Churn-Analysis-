# Telecom Customer Churn 

<p align="center">
  <img src="image.webp" alt="Customer Churn" width="600"/>
</p>


This project analyzes telecom customer data to find **why customers leave**, **who is at risk**, and **what actions can reduce churn**.  
It includes **EDA, KPI & cohort analysis, A/B testing**, and **ML (Logistic Regression + Random Forest)** for explainability and prediction.

---

## Key Highlights

- **Overall Churn:** ~27%  
- **Highest-Risk Segments:**  
  - **Month-to-month contracts** (churn ≈ **42.7%**)  
  - **Electronic check** payment users (churn ≈ **45%**)  
  - **New customers** (tenure **0–12 months**)  
  - **Single-service customers**  
- **Protective Factors:**  
  - **Two-year contracts** (churn ≈ **2.8%**)  
  - **Long tenure**  
  - **Multiple add-on services** (higher stickiness)

---

## KPI Summary

| KPI | Value / Insight |
|---|---|
| **Overall Churn Rate** | ~27% |
| **Churn by Contract** | Month-to-month **42.7%** · One-year **11.3%** · Two-year **2.8%** |
| **Churn by Tenure** | Highest in **0–12 months**, drops sharply afterward |
| **Churn by Payment** | **Electronic check 45%** vs **Auto-pay 17%** |
| **Stickiness** | Churn falls as **# of services** increases (3+ is much safer) |
| **RPU (derived)** | Used to segment financial impact of churn |
| **A/B Tests** | Contract & payment differences **statistically significant (p < 0.001)** |

---

## Key Insights

### 1) Customer Acquisition & Tenure
- Most churn occurs in the **first year**.  
- Customers who pass the first year are **far more loyal**.

### 2) Contract & Billing
- **Contract length** is the strongest lever: longer contracts **dramatically reduce churn**.  
- **Electronic check** users churn much more than **auto-pay** users.

### 3) Product Stickiness
- Customers with **multiple services** churn less.  
- Bundling security/backup/streaming features increases retention.

---

##  Modeling (for prioritization & explainability)

**Logistic Regression (interpretable):**
- **Accuracy:** ~75% · **Recall (churners):** ~80% 
- **Drivers (direction):**  
  - ↑ Churn: *Fiber optic*, *Month-to-month*, *Electronic check*  
  - ↓ Churn: *Long tenure*, *Two-year contract*

**Random Forest (ranking importance):**
- **Top features:** `TotalCharges`, `tenure`, `RPU`, `MonthlyCharges`, `Contract_Two year`  
- **Takeaway:** **Billing + loyalty** (tenure/contract) explain most churn risk.

> Using both models gives **clear “why”** (logistic coefficients) and **solid “what matters most”** (RF importances).

---

## A/B Testing (Hypothesis Testing)

**Contract Type vs Churn**  
- Month-to-month **42.7%**, One-year **11.3%**, Two-year **2.8%**  
- **Chi-square p < 0.001** → differences are **real**, not random.

**Payment Method vs Churn**  
- **Electronic check 45%** vs **Auto-pay 17%**  
- **Chi-square p < 0.001** → payment method **strongly affects churn**.

---

## Strategic Recommendations

1. **Promote Annual / Multi-Year Plans**  
   - Target month-to-month users with contracts + modest incentives.  
   - Measure uplift with controlled A/B tests.

2. **Push Auto-Pay Adoption**  
   - Simplify sign-up, add one-click prompts, small bill credits.  
   - Track auto-pay adoption and churn delta among converters.

3. **Strengthen First-Year Onboarding**  
   - 30/60/90-day journeys: welcome tips, proactive support, usage nudges.  
   - Trigger save-offers for high-risk accounts flagged by the model.

4. **Bundle Services to Increase Stickiness**  
   - Offer simple bundles (e.g., Security+Backup, Streaming+DeviceProtection).  
   - Prioritize single-service customers.

---

## Dataset

- **Source:** [Telco Customer Churn (Kaggle Dataset)](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)
- **Rows:** ~7,043 customers · **Target:** `Churn` (Yes/No)  
- **Main Feature Groups:** Demographics, Services, Contracts/Billing

---

## What I Did

- **Data Ingestion & Cleaning (Python):**  
  - Converted `TotalCharges` to numeric; handled blanks as 0 for tenure=0.  
  - Removed duplicates; standardized dtypes.  
  - Engineered **ARPU**, **NumServices**, **TenureGroup**.

- **EDA & KPIs:**  
  - Churn by **contract**, **payment**, **tenure cohorts**, **services**.  
  - Visualized distributions and segment differences.

- **A/B Testing:**  
  - **Contract** and **Payment** vs Churn using **Chi-Square**.

- **ML:**  
  - **Logistic Regression** (explainable drivers)  
  - **Random Forest** (feature importance ranking)

---

## Executive Summary

This project analyzes **customer churn in a telecom company**, where ~27% of customers have left. Retaining customers is far more cost-effective than acquiring new ones, so the goal was to 

        (1) identify churn drivers, 
        (2) predict at-risk customers, and 
        (3) recommend actions to improve retention.

**Key Findings:**
- **Contract type is the biggest driver of churn:**  
  - Month-to-month customers churn at **42.7%**, vs **11.3%** (one-year) and **2.8%** (two-year).  
- **Payment method matters:**  
  - Customers paying by **electronic check churn ~45%**, while **auto-pay users churn ~17%**.  
- **Tenure effects:** Most churn happens in the **first 12 months**, after which loyalty increases.  
- **Product stickiness:** Customers with **3+ services** churn far less than single-service customers.  
- **Model insights:** Logistic Regression and Random Forest confirm that **tenure, contract length, and billing patterns (MonthlyCharges, TotalCharges, ARPU)** are the strongest churn predictors.  

**Statistical Validation:**  
Chi-Square tests confirm that both **contract type** and **payment method** have **statistically significant effects (p < 0.001)**, proving the differences are real and actionable.

**Strategic Recommendations:**  
1. **Promote long-term contracts** — incentives to shift month-to-month users to annual/multi-year plans.  
2. **Encourage auto-pay enrollment** — small bill credits or one-click setup to move customers off electronic checks.  
3. **Improve first-year onboarding** — proactive engagement, welcome nudges, and retention campaigns in the first 90 days.  
4. **Bundle services** — packages that combine multiple add-ons to increase stickiness.  

**Business Impact:**  
By acting on these levers, the company can **reduce churn**, **boost retention**, and **increase RPU and profitability**, ensuring a healthier customer base and sustainable growth.

---

## Tools & Tech

- **Python:** pandas, numpy, matplotlib, seaborn, scikit-learn, scipy  
- **Methods:** EDA, cohort analysis, chi-square testing, logistic regression, random forest

---
