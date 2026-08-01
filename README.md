# 📊 Loan-Default-Prediction-Risk-Analytics-Excel-Dashboard
An end-to-end Excel-based analytics project analyzing 32,579 loan applicants to uncover patterns in loan default risk, financial performance, and profitability. The project combines data cleaning, dimensional modeling, and interactive dashboarding to help credit teams identify high-risk borrower segments and optimize lending decisions.

### 🏗 Data Architecture & Data Modeling
The analysis relies on a clean Star Schema model created in Power Pivot, establishing clear 1-to-Many (1:∗) relationships between dimension tables and the central fact table (Facts_Table).

    +-------------------+           +------------------+           +--------------------+
    | Dim_Home_Ownership|           | Dim_Loan_Intent  |           | Dim_Loan_History   |
    +-------------------+           +------------------+           +--------------------+
             | 1                             | 1                             | 1
             |                               |                               |
             +---------------+               +---------------+               +---------------+
                             |                               |                               |
                             v *                             v *                             v *
                      +-------------------------------------------------------------+
                      |                        Facts_Table                          |
                      +-------------------------------------------------------------+
                                                     ^ *
                                                     |
                                                     | 1
                                            +------------------+
                                            |    Dim_Person    |
                                            +------------------+
Data Model Components

* Facts_Table: Contains granular loan transaction records including Loan Amount, Loan Intrest Rate, Loan Status, Bad Debt, Net Value Added, and core explicit DAX measures.

* Dim_Person: Contains borrower demographic metadata including Person Age, Person Income, Person Emp Length, custom Age Group, and Emp Length Group.

* Dim_Loan_History: Tracks historical credit performance including Person Default on File, Person Credit History Length, and Credit History Group.

* Dim_Loan_Intent: Classifies the loan purpose (e.g., Venture, Personal, Medical, Education, Debt Consolidation).

* Dim_Home_Ownership: Stores borrower housing tenure (RENT, MORTGAGE, OWN, OTHER).

### 🛠 Technology Stack & Tools Used

#### 1. Power Query (ETL & Data Transformation)
 
* Data Cleansing: Handled missing values, standardized data types, and cleansed inconsistent inputs across credit records.

* Created custom conditional columns for grouping continuous variables into meaningful buckets (e.g., Age Group, Emp Length Group, and Credit History Group).

* Calculated derived metrics such as Loan Percent Income buckets for enhanced granular drill-downs.

#### 2. Power Pivot & Data Modeling

* designed a normalized Star Schema establishing one-to-many relationships anchored around Person ID.

* Configured implicit and explicit data structures to ensure optimal operational efficiency and seamless slicing.

#### 3. DAX (Data Analysis Expressions)
 
Formulated dynamic measures to calculate profitability metrics, risk ratios, and KPI card values:

* Total Applicants:
Total Applicants = COUNT(Facts_Table[Person ID])

* Default Rate %:
Default Rate % = DIVIDE(SUM(Facts_Table[Loan Status]), [Total Applicants], 0)

* Average Interest Rate:
AVG Intrest Rate = AVERAGE(Facts_Table[Loan Intrest Rate])

* Net Value Added (NVA):
Total NVA = [Total Intrest Income] - [Total Bad Dept]

* NVA Margin:
NVA Margin = DIVIDE([Total NVA], [Total Intrest Income], 0)

#### 4. Interactive Dashboards & Pivot Tables

* Built 3 cohesive interactive dashboard views integrated with cross-filtering slicers (Loan Grade, Age Group, Home Ownership, Loan Intent):

* Loan Default Prediction & Risk Analytics (Executive Summary)

* Financial Performance & Profitability Analysis

* Risk & Default Deep-Dive Analysis

### 📈 Key Analysis & Insights

#### 1. Portfolio Overview & Key Performance Indicators

* Total Applicants Analyzed: 32,579

* Overall Default Rate: 21.81%

* Average Loan Amount: $9,588.27

* Average Interest Rate: 11.01%

#### Financial Risk Summary:

* Total Interest Income: $35.34M

* Total Bad Debt: $77.09M

* Total Net Value Added (NVA): -$41.75M (NVA Margin: -13.37%)

#### 2. Risk Drivers & Demographic Patterns

 * Risk by Age Group: Borrowers aged 20–25 represent the highest risk demographic segment, showing higher default rates compared to older age brackets.

#### Impact of Prior Default History:

* Repeat Defaulters (Prior Default = Y): 37.80% default rate.

* First-Time Defaulters (Prior Default = N): 18.39% default rate.

* Insight: A prior default history increases likelihood of default by >2x.

* Loan-to-Income (LTI) Thresholds:

* Default risk escalates drastically when the Loan-to-Income ratio exceeds 30%.

* A critical cohort of 247 high-risk borrowers has an LTI ratio of 50%+.

#### 3. Loan Grade & Profitability Breakdown

* Interest Rate Tiering: Interest rates scale cleanly with risk grades—from ~7% (Grade A) up to >20% (Grade G).

#### Volume vs. Risk:

* Grade A & B make up the largest proportion of total applicants while maintaining low default rates (<10–15%).

* Grade D, E, F, & G experience exponential spikes in default rates, resulting in heavy bad debt accumulation that negatively impacts overall NVA.

* Loan Intent Impact: Medical and Debt Consolidation loans account for significant negative NVA contributions, driven by default exposure in those categories.

### 💡 Strategic Recommendations

* Tighten Underwriting for High LTI: Lower automatic approval thresholds for applicants whose Loan-to-Income ratio exceeds 30%.

* Revise Pricing for Repeat Defaulters: Require higher collateral or apply premium rate adjustments for applicants with a prior default flag on file.

* Targeted Risk Controls for Young Borrowers (20–25): Introduce structured repayment plans or co-signer requirements for younger borrowers entering lower loan grades.
* 

#### 👤 Author

Anmol Verma

Business Analyst

🎓 Education: B.A. (Hons) Economics, University of Delhi

✉️ Email: manojaashp.anm@gmail.com
