# Telecom Customer Churn 

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

- **Source:** Telco Customer Churn (public dataset)  
- **Rows:** ~7,043 customers · **Target:** `Churn` (Yes/No)  
- **Main Feature Groups:** Demographics, Services, Contracts/Billing

---

## What I Did

- **Data Ingestion & Cleaning (Python):**  
  - Converted `TotalCharges` to numeric; handled blanks as 0 for tenure=0.  
  - Removed duplicates; standardized dtypes.  
  - Engineered **ARPU**, **NumServices**, **TenureGroup**.

- **EDA & KPIs:**  
  - Churn by **contract**, **payment**, **tenure cohorts**, **# services**.  
  - Visualized distributions and segment differences.

- **A/B Testing:**  
  - **Contract** and **Payment** vs Churn using **Chi-Square**.

- **ML:**  
  - **Logistic Regression** (explainable drivers)  
  - **Random Forest** (feature importance ranking)

