# 📊 Loan Default Risk Analysis Dashboard

## 📌 Project Overview

This project analyzes a loan dataset of **24,999 records** to identify key factors influencing loan defaults.
The dashboard provides visual insights into borrower risk patterns using Google Sheets visualizations.

The goal is to determine which financial indicators best predict default risk and support data-driven lending decisions.

---

## 🎯 Objectives

* Analyze borrower characteristics affecting loan defaults
* Identify strongest predictors of default risk
* Compare risk across income, credit score, region, and loan structure
* Build an interactive dashboard for business insights

---

## 📂 Dataset Summary

| Metric                   | Value                   |
| ------------------------ | ----------------------- |
| Total Loans              | **24,999**              |
| Overall Default Rate     | **24.40%**              |
| Highest Risk Region      | **North-East (33.17%)** |
| Highest Risk LTV Band    | **>120 (100%)**         |
| Highest Risk Income Band | **<2000 (43.79%)**      |
| Highest Risk DTI Band    | **50–59 (44.01%)**      |

---

## 📊 Dashboard Visualizations

The dashboard includes:

* Default Rate by Credit Score Band
* Default Rate by Loan-to-Value (LTV)
* Default Rate by Debt-to-Income (DTI)
* Default Rate by Income Band
* Default Rate by Age Group
* Default Rate by Region
* Loan Structure Risk Comparison
* Credit Score × DTI Risk Heatmap

---

## 🔍 Key Insights

### 1️⃣ Credit Score Alone is Weak Predictor

Default rates remain nearly constant (≈23–25%) across score ranges.

---

### 2️⃣ Debt-to-Income Ratio is Critical

Risk increases sharply after **DTI > 30**, peaking above **44%**.

---

### 3️⃣ Loan-to-Value is Strongest Predictor

Higher leverage strongly increases risk.

| LTV     | Default |
| ------- | ------- |
| <60     | 14%     |
| 60–80   | 32%     |
| 100–120 | 62%     |

> 120 | **100%** |

---

### 4️⃣ Income is Inversely Related to Default

Lower income borrowers default significantly more frequently.

---

### 5️⃣ Age Shows U-Shaped Risk Pattern

Highest risk groups:

* Under 25
* Above 74

---

### 6️⃣ Regional Risk Differences

North-East region shows the highest default risk.

---

### 7️⃣ Loan Structure Has Minor Impact

Interest-only and negative amortization loans show only small differences in default rates.

---

### ⭐ Executive Conclusion

> **Debt-to-Income and Loan-to-Value ratios are the strongest predictors of loan default risk, while credit score alone is insufficient for reliable risk assessment.**

---

## 🛠 Tools Used

* Google Sheets
* Pivot Tables
* Scorecards
* Charts & Visual Analytics

---

## 📁 Repository Contents

```
📦 Loan Default Dashboard
 ┣ 📊 Dashboard Screenshot
 ┣ 📑 Dataset (if included)
 ┗ 📄 README.md
```

---

## 🚀 How to Use

1. Open the Google Sheet dashboard
2. Use filters to explore risk segments
3. Analyze charts for insights
4. Interpret KPIs for decision-making

---

## 📌 Author

**Shivansh Tiwari**
Aspiring Data Scientist & Full Stack Developer

---

⭐ If you found this project useful, consider giving it a star!
