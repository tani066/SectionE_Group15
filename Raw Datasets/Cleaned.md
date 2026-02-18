# 🧹 Data Cleaning & Preprocessing Log

This document records all cleaning, preprocessing, and transformation steps performed on the dataset before analysis and dashboard creation.

---

## 📊 Dataset Overview
- Original Rows: **148,670**
- Working Rows: **24,999**
- Goal: Prepare dataset for accurate analysis and visualization

---

# 🧾 Column Cleaning Summary

## Dropped Columns
The following columns were removed because they provided no analytical value:

| Column | Reason |
|------|--------|
year | Only one value present |
loan_type | Encoded values not interpretable |
loan_purpose | Encoded categories without meaning |
total_units | Not relevant for analysis |
security_type | Same value for all rows |

---

## Renamed Columns
| Old Name | New Name | Reason |
|---------|----------|-------|
status | defaulted | Clear target meaning |

---

## Missing Value Handling Strategy

| Data Type | Method | Reason |
|----------|--------|-------|
Categorical | Mode | Most frequent value best represents category |
Numeric | Median | Resistant to outliers |

---

# 🔧 Column-Wise Cleaning Actions

## Categorical Columns
Standardized text values:

- Converted to **UPPERCASE**
- Trimmed extra spaces
- Unified inconsistent categories

Formula used:
=UPPER(TRIM(A2))

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

### Special Category Fixes

| Column | Issue | Action |
|------|------|------|
gender | joint / sex not available | replaced with UNKNOWN |

---

## Numeric Columns — Missing Values

Median imputation applied to:

- rate_of_interest
- interest_rate_spread
- upfront_charges
- term
- property_value
- income
- ltv
- dtir1

Example formula:
=IF(AE2="", MEDIAN(FILTER(AE:AE, ISNUMBER(AE:AE))), AE2)

---

## Outlier Handling

### Income Column
Issues:
- missing values
- invalid values (0)
- extreme outliers

Method:
- Median imputation
- IQR-based outlier replacement

Formula used:
=ARRAYFORMULA(IF(U2:U="","",
IF((U2:U=0)+
(U2:U < QUARTILE(U:U,1)-1.5*(QUARTILE(U:U,3)-QUARTILE(U:U,1)))+
(U2:U > QUARTILE(U:U,3)+1.5*(QUARTILE(U:U,3)-QUARTILE(U:U,1))),
MEDIAN(FILTER(U:U,U:U>0)),
U2:U)))

---

## Range Validation

### Credit Score
Valid range = **300–900**

Formula used:
=MAX(300, MIN(900, C2))

---

### LTV Ratio
Valid range = **0–100**

Steps:
1. Replace missing values with median
2. Clip values to valid range

Formula:
=MAX(0, MIN(100, AA2))

---

## Decimal Formatting
Standardized numeric precision to **2 decimal places** for:

- rate_of_interest
- interest_rate_spread
- upfront_charges
- ltv

Formatting applied:
Format → Number → 2 decimal places

---

# ⚙ Feature Engineering

## Credit Score Band Column
A new column **credit_score_band** was created to group numeric credit scores into ranges:
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
- simplifies analysis
- improves visualization
- enables grouped comparisons

---

# ✅ Final Dataset State

After preprocessing:

✔ Missing values handled  
✔ Outliers corrected  
✔ Invalid ranges fixed  
✔ Categories standardized  
✔ Columns cleaned and renamed  
✔ Dataset consistent and analysis-ready  

---

# 📌 Conclusion
The dataset is now:

- Clean
- Structured
- Consistent
- Statistically reliable
- Ready for visualization or machine learning

All preprocessing decisions were made to maximize analytical accuracy while preserving original data integrity wherever possible.

