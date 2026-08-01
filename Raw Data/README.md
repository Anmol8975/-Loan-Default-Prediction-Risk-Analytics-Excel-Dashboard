# 📁 Dataset Documentation: Raw Credit Risk Data

## 📌 Overview
This dataset contains transactional and demographic records used to analyze credit default risk, portfolio performance, and borrower characteristics. It serves as the raw input for data cleaning, transformation in **Power Query**, and data modeling within **Power Pivot / DAX**.

* **File Format**: `.csv`
* **Total Records**: `32,581` rows
* **Total Attributes**: `12` columns

---

## 📐 Data Schema & Field Descriptions

* **`person_age`**: Integer | Age of the borrower (in years) | Range: 20 – 144 *(Contains outliers)*
* **`person_income`**: Integer | Annual income of the borrower (in USD) | Range: $4,000 – $6,000,000
* **`person_home_ownership`**: Categorical | Housing tenure of the applicant | Values: `RENT`, `OWN`, `MORTGAGE`, `OTHER`
* **`person_emp_length`**: Float | Length of employment (in years) | Range: 0.0 – 123.0 *(Contains missing values & outliers)*
* **`loan_intent`**: Categorical | Purpose of requested loan | Values: `PERSONAL`, `EDUCATION`, `MEDICAL`, `VENTURE`, `HOMEIMPROVEMENT`, `DEBTCONSOLIDATION`
* **`loan_grade`**: Categorical | Credit risk evaluation grade assigned by lender | Values: `A`, `B`, `C`, `D`, `E`, `F`, `G`
* **`loan_amnt`**: Integer | Total principal loan amount requested | Range: $500 – $35,000
* **`loan_int_rate`**: Float | Annual interest rate applied to the loan (%) | Range: 5.42% – 23.22% *(Contains missing values)*
* **`loan_status`**: Binary Integer | Target variable indicating default status | Values: `0` = Non-Default (Paid), `1` = Default (Unpaid)
* **`loan_percent_income`**: Float | Ratio of loan amount relative to annual income | Range: 0.00 – 0.83 (0% – 83%)
* **`cb_person_default_on_file`**: Categorical | Historical record of prior credit default | Values: `Y` = Prior default recorded, `N` = No prior default
* **`cb_person_cred_hist_length`**: Integer | Credit history length on Bureau record (years) | Range: 2 – 30 years

---

## 📊 Summary Statistics & Data Profiling

| Feature | Mean | Median (50%) | Min | Max |
| :--- | :--- | :--- | :--- | :--- |
| **`person_age`** | 27.73 | 26.00 | 20.00 | 144.00 |
| **`person_income`** | $66,074.85 | $55,000.00 | $4,000.00 | $6,000,000.00 |
| **`person_emp_length`** | 4.79 yrs | 4.00 yrs | 0.00 yrs | 123.00 yrs |
| **`loan_amnt`** | $9,589.37 | $8,000.00 | $500.00 | $35,000.00 |
| **`loan_int_rate`** | 11.01% | 10.99% | 5.42% | 23.22% |
| **`loan_percent_income`** | 17.02% | 15.00% | 0.00% | 83.00% |
| **`cb_person_cred_hist_length`** | 5.80 yrs | 4.00 yrs | 2.00 yrs | 30.00 yrs |

---

## 🧹 Missing Values & Data Cleaning Requirements

During the ETL phase in **Power Query**, the following data quality issues in this raw file need attention:

1. **Missing Values**:
   * **`loan_int_rate`**: **3,116 null values** (~9.5% missing). Impute via loan grade averages or median values.
   * **`person_emp_length`**: **895 null values** (~2.7% missing). Impute or treat missing records appropriately.
2. **Data Anomalies & Outliers**:
   * **`person_age`**: Maximum value recorded is `144` years (requires filtering/capping to valid working-age limits).
   * **`person_emp_length`**: Maximum value recorded is `123` years (requires validation relative to age).

---

## 👤 Author

**Anmol Verma**  
*Business Analyst*  
🎓 **Education**: B.A. (Hons) Economics, University of Delhi  
✉️ **Email**: manojaashp.anm@gmail.com
