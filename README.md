# 📊 Loan Default Risk Analysis Dashboard

---

## 📌 Project Overview
This project analyzes loan application data to understand the key factors that influence loan default risk. The objective is to extract meaningful insights from borrower financial and demographic data and visualize them through a structured analytical dashboard.

The original dataset contained **148,670 rows**, but due to Google Sheets cell limitations, it was randomized and reduced to **24,999 rows** for analysis and visualization. 
The code for this is available in `random-sampler/main.py`.

The dashboard helps answer questions such as:
- Which borrowers are most likely to default?
- What financial indicators are strongest predictors?
- Do demographics affect default risk?
- How do regions compare in risk levels?

---

## 🎯 Project Objectives
- Identify variables strongly correlated with loan default
- Clean and preprocess raw financial data
- Engineer useful analytical features
- Build an insight-driven dashboard
- Present findings visually for decision-making

---

## 📂 Dataset Information
| Attribute | Value |
|--------|------|
Original Rows | 148,670 |
Working Rows | 24,999 |
Target Column | `defaulted` |
Data Type | Mixed (Numeric + Categorical) |
Domain | Finance / Lending Risk |

---

## 📖 Data Dictionary

| Column | Description | Type |
|------|-------------|------|
id | Loan application ID | Numeric |
loan_limit | Loan category | Categorical |
gender | Applicant gender | Categorical |
approv_in_adv | Pre-approval indicator | Categorical |
credit_worthiness | Credit rating level | Categorical |
loan_amount | Borrowed amount | Numeric |
rate_of_interest | Interest rate | Numeric |
interest_rate_spread | Rate difference | Numeric |
upfront_charges | Initial fees | Numeric |
term | Loan duration | Numeric |
neg_ammortization | Negative amortization flag | Categorical |
interest_only | Interest-only loan flag | Categorical |
property_value | Property value | Numeric |
income | Applicant income | Numeric |
credit_score | Credit score | Numeric |
age | Age group | Categorical |
ltv | Loan-to-value ratio | Numeric |
region | Geographic region | Categorical |
defaulted | Default indicator | Target |
dtir1 | Debt-to-income ratio | Numeric |

---

## 🧹 Data Cleaning Notes

### Columns Removed
The following columns were dropped because they provided no analytical value:

- **year** → contained only one value
- **loan_type** → unclear category meaning
- **loan_purpose** → encoded categories without explanation
- **total_units** → not relevant for risk prediction
- **security_type** → constant value for all rows

---

### Missing Value Treatment
Different strategies were applied depending on data type:

| Data Type | Method Used | Reason |
|----------|-------------|-------|
Categorical | Mode | Most representative value |
Numeric | Median | Robust to outliers |

Columns cleaned using median:
- interest_rate_spread
- rate_of_interest
- upfront_charges
- property_value
- income
- ltv
- dtir1
- term

---

### Standardization Steps
- Converted all categorical text values to **UPPERCASE**
- Unified category naming for consistency
- Replaced ambiguous values:

| Column | Replacement |
|------|-------------|
gender | joint → UNKNOWN |
gender | sex not available → UNKNOWN |

---

### Column Renaming
status → defaulted
This improves clarity by explicitly defining the target variable.

---

### Outlier Handling
Income column contained extreme values.

Action:
Outliers replaced with median
Reason:
Prevents skewed distributions and improves statistical reliability.

---

## ⚙ Feature Engineering

To simplify analysis and improve visualization clarity, a new column **`credit_score_band`** was created.

Instead of using raw credit score values, scores were grouped into ranges:
450–499
500–549
550–599
600–649
650–699
700–749
750–799
800–850
851–900

This allows:
- easier comparison across risk groups
- clearer trend visualization
- improved chart readability

---

## 📊 Dashboard KPIs

| KPI | Value |
|----|------|
Total Loans | 24,999 |
Overall Default Rate | 24.40% |
Highest Risk Region | North-East |
Highest Risk Income Band | <2000 |
Highest Risk LTV | >120 |
Highest Risk DTI | 50–59 |

---

## 📈 Dashboard Visualizations

The dashboard contains multiple analytical views:

### Risk Distribution Charts
- Default Rate by Credit Score Band
- Default Rate by Loan-to-Value
- Default Rate by Debt-to-Income
- Default Rate by Income
- Default Rate by Age
- Default Rate by Region

---

### Comparative Analysis Charts
- Regional comparison across credit score bands
- Regional distribution of default rates

---

### Structure Analysis
- Interest-only vs Non-interest loan comparison
- Negative amortization impact

---

### Interaction Analysis
- Combined Credit Score × DTI risk visualization

---

## 🧠 Key Insights

- **Loan-to-Value ratio is the strongest predictor** of default.
- Borrowers with **DTI above 50** have extremely high risk.
- Income below **2000** strongly correlates with default.
- **North-East region shows highest overall default risk.**
- Credit score alone shows relatively stable default rates.
- Loan structure types have minimal impact compared to financial metrics.


## 🛠 Tools Used
- Google Sheets
- Pivot Tables
- Conditional formatting
- Aggregation logic
- Data cleaning techniques

---

## 📌 Final Conclusion
This analysis demonstrates that financial ratios such as:

- Debt-to-Income
- Loan-to-Value
- Income level

are significantly stronger predictors of loan default than demographic factors or credit score alone.

Effective risk assessment should therefore prioritize financial capacity metrics over single-variable indicators.

---


