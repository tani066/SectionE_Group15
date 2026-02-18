# 🧹 Data Cleaning & Preprocessing Log

This document records all preprocessing, cleaning, and transformation steps applied to the dataset before analysis and dashboard creation.

---

## 📊 Dataset Overview
- Original Rows: **148,670**
- Working Rows: **24,999**
- Goal: Prepare dataset for reliable analysis and visualization.

---

# 🗑 Dropped Columns

The following columns were removed due to lack of analytical value:

| Column | Reason |
|------|--------|
year | Same value across all rows |
loan_type | Encoded categories not interpretable |
loan_purpose | Encoded values without meaning |
total_units | Not relevant for risk analysis |
security_type | Same value for entire column |

---

# ✏ Column Renaming

| Old Name | New Name | Reason |
|---------|----------|-------|
status | defaulted | Clear target variable name |

---

# 🔤 Text Standardization

All categorical columns were cleaned using:

=UPPER(TRIM(A2))

Purpose:
- remove extra spaces
- standardize case
- avoid duplicate categories

Columns standardized:
- loan_limit
- gender
- approv_in_adv
- open_credit
- business_or_commercial
- neg_ammortization
- interest_only
- lump_sum_payment
- construction_type
- occupancy_type
- secured_by
- credit_type
- co-applicant_credit_type
- region

---

# 📊 Missing Value Treatment Strategy

| Data Type | Method Used | Reason |
|----------|-------------|-------|
Categorical | Mode | Most frequent category best represents missing values |
Numeric | Median | Robust against outliers |

---

## 🟡 Mode Imputation Columns (Categorical)

The following columns had missing values replaced using **mode**:

| Column | Missing Count | Action |
|------|----------------|-------|
loan_limit | 603 | Filled with mode |
approv_in_adv | 166 | Filled with mode |
neg_ammortization | 25 | Filled with mode |
age | 31 | Filled with mode |
submission_of_application | 31 | Filled with mode |

Reason:  
Mode imputation is appropriate for categorical variables because it preserves category distribution and avoids introducing artificial values.

---

## 🔵 Median Imputation Columns (Numeric)

Median replacement was applied to:

- rate_of_interest (6070 missing)
- interest_rate_spread (6101 missing)
- upfront_charges (6594 missing)
- term (8 missing)
- property_value (2419 missing)
- income (1558 missing)
- ltv (2419 missing)
- dtir1 (3955 missing)

Reason:  
Median is resistant to extreme values and maintains realistic distributions.

---

# 📈 Outlier Handling

## Income Column
Issues detected:
- missing values
- invalid values (0)
- extreme outliers

Method used:
- median replacement
- IQR outlier detection

Formula used:
=ARRAYFORMULA(IF(U2:U="","",
IF((U2:U=0)+
(U2:U < QUARTILE(U:U,1)-1.5*(QUARTILE(U:U,3)-QUARTILE(U:U,1)))+
(U2:U > QUARTILE(U:U,3)+1.5*(QUARTILE(U:U,3)-QUARTILE(U:U,1))),
MEDIAN(FILTER(U:U,U:U>0)),
U2:U)))

---

# 🔢 Numeric Formatting
The following columns were standardized to **2 decimal places**:

- rate_of_interest
- interest_rate_spread
- upfront_charges
- ltv

---

# ⚙ Feature Engineering

## Credit Score Band Column
A new column **credit_score_band** was created to group credit scores into ranges:

450–499
500–549
550–599
600–649
650–699
700–749
750–799
800–850
851–900

Purpose:
- easier analysis
- clearer charts
- grouped comparisons

---

# ✅ Final Dataset State

After preprocessing:

✔ Missing values handled  
✔ Outliers corrected  
✔ Invalid ranges fixed  
✔ Categories standardized  
✔ Irrelevant columns removed  
✔ Dataset consistent and analysis-ready  

---

# 📌 Conclusion
All preprocessing steps were designed to:

- preserve data integrity
- reduce noise
- improve statistical reliability
- ensure accurate analytical insights
