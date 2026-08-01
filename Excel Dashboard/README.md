# Credit Portfolio Performance & Risk Modeling — Excel Dashboard

## 📌 Project Overview
An interactive Excel dashboard analyzing **32,579 loan applicants** to evaluate credit portfolio performance, profitability, and default risk. Built using a structured star-schema-style data model connecting applicant demographics, loan details, credit history, and loan intent — enabling multi-dimensional analysis through Power Pivot and DAX.

---

## 🗂️ Data Model Structure

The workbook follows a **fact-dimension model**, all linked via `Person ID`:

**Fact Table**
- `Fats Table` — core transactional data: Loan Grade, Loan Amount, Loan Interest Rate, Loan Status, Loan Percent Income, Interest Income, Bad Debt, Net Value Added (NVA), Loan Percent Income Group

**Dimension Tables**
- `Dim Person` — Person Age, Income, Employment Length, Age Group, Employment Length Group
- `Dim Loan History` — Prior Default on File, Credit History Length, Credit History Group
- `Dim Loan Intent` — Purpose of loan (Education, Medical, Venture, Debt Consolidation, etc.)
- `Dim Home Ownership` — Rent / Own / Mortgage / Other

This relational structure allows slicing the ~32.5K applicant records across grade, demographics, credit history, and loan purpose simultaneously without data duplication.

---

## 🛠️ Tools & Techniques Used
- **Power Query** — used to clean, transform, and shape raw data before loading into the model; created derived columns like **Age Group**, **Employment Length Group**, **Credit History Group**, and **Loan Percent Income Group** by binning continuous variables into meaningful categories
- **Power Pivot** — built the data model, linking fact and dimension tables via `Person ID` relationships
- **DAX Measures** — created calculated measures for portfolio-level KPIs (see below)
- **PivotTables & PivotCharts** — powered all visuals across the three dashboard pages
- **Slicers (Filter Panels)** — Loan Grade, Age Group, Home Ownership, Loan Intent for interactive drill-down

---

## 📐 Key DAX Measures / Calculated Metrics
- **Default Rate %** — proportion of applicants who defaulted, sliceable by grade, age, employment length, and credit history
- **Average Interest Rate by Loan Grade** — shows risk-based pricing trend across Grades A–G
- **Average Employment Length by Age Group** — used to study job stability vs. default risk
- **Net Value Added (NVA)** — Interest Income minus Bad Debt, measuring true profitability per segment
- **Loan Percent Income (Income-to-Loan Ratio)** — flags applicants with high loan burden relative to income
- **Bad Debt & Interest Income Aggregations** — rolled up by loan grade and intent

---

## 📊 Dashboard Pages

### 1. Financial Performance / Profitability
- Total Bad Debt: **₹77.09M** | Avg Interest Rate: **11.01%**
- Best Performing Grade: **A** | Worst Performing Grade: **D**
- Visuals: Avg Interest Rate by Loan Grade, Total NVA by Loan Intent, Interest Income by Loan Grade, Loan Amount Distribution, Credit History Length vs Default Rate %

### 2. Risk & Default Analysis
- Repeat Defaulter Rate: **37.80%** vs First-Time: **18.39%**
- Highest Risk Age Group: **20–25**
- Loan-to-Income 50%+ Count: **247** applicants
- Visuals: Age Group by Default Rate %, Loan Status by Prior Default History, Default Rate by Loan-to-Income Ratio, Bad Debt by Loan Grade, Default Rate by Employment Length

### 3. Loan Default Prediction & Risk Analytics (Executive Summary)
- Total Applicants: **32,579** | Default Rate: **21.81%**
- Total NVA: **-₹41.75M** | NVA Margin: **-13.37%** | Total Interest Income: **₹35.34M**
- Visuals: Applicants & Avg Loan Amount by Grade, Loan Default Distribution, Interest Income to NVA Bridge, Applicants vs Home Ownership, Applicants vs Loan Grade with Default Rate overlay

---

## 🔍 Key Insights
1. Interest rates scale nearly linearly with risk — from ~7% (Grade A) to ~20%+ (Grade G).
2. **Grade D carries the highest bad debt (~₹22M)** despite not being the riskiest grade by letter — the biggest financial drag on the portfolio.
3. Default risk follows a **U-shaped curve by age** — highest in the 20–25 bracket, dipping mid-career, and rising again post-50.
4. **Repeat defaulters default at ~2x the rate of first-timers** (37.8% vs 18.4%), confirming prior default history as a strong risk predictor.
5. At an aggregate level, **the portfolio is currently unprofitable** — Bad Debt (₹77.09M) outweighs Interest Income (₹35.34M), producing a negative NVA of -₹41.75M (-13.37% margin).
6. **Debt consolidation and medical loans** show the largest negative NVA, making them the riskiest loan intents.

---

## 💡 Recommendation
Tightening underwriting for **Grade D and below**, particularly for **debt consolidation/medical loan intents**, and adding closer scrutiny for **20–25 year-old applicants and repeat defaulters**, would likely improve overall portfolio profitability.

---

## ✍️ Author
**Anmol Verma** (Business Analyst)

Economics Hons, University of Delhi

📧 manojaashp.anm@gmail.com
