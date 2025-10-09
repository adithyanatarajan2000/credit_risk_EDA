# Credit Risk EDA

**Statistical Analysis of 32K Loan Applications**

## Project Overview:

This project explores credit risk patterns across 32,581 loan applicants using statistical hypothesis testing, segmentation logic, and audit-safe data preprocessing. The goal is to uncover actionable insights for underwriting teams and risk analysts.

---

## Dataset:

- **Source**: [Kaggle Credit Risk Dataset](https://www.kaggle.com/datasets/laotse/credit-risk-dataset)
- **Size**: 32,581 rows and 12 columns

<h3 align="left"><strong>Features:</strong></h3>
<br>

| **Feature Name**           | **Description**                                             |
|---------------------------|--------------------------------------------------------------|
| person_age                | Applicant’s age in years                                     |
| person_income             | Annual income of the applicant                               |
| person_home_ownership     | Housing status (RENT, OWN, MORTGAGE, OTHER)                  |
| person_emp_length         | Employment length in years                                   |
| loan_intent               | Purpose of the loan (EDUCATION, MEDICAL, VENTURE, etc.)      |
| loan_grade                | Credit grade assigned to the loan (A – G)                    |
| loan_amnt                 | Total loan amount requested                                  |
| loan_int_rate             | Interest rate applied to the loan                            |
| loan_status               | Whether the loan was defaulted (0 = No, 1 = Yes)             |
| loan_percent_income       | Loan amount as a percentage of income                        |
| cb_person_default_on_file | Prior default history on credit file (Y/N)                   |
| cb_person_cred_hist_length| Length of credit history in years                            |

---

## Analytical Approach:

Key steps include:

- **Null & Outlier Handling**: Median imputation by loan grade, IQR-based capping.  
- **Distribution Diagnostics**: KDE plots, Q-Q plots, Anderson-Darling tests.
- **Segmentation**: Income and loan amount discretized into quantiles.
- **Hypothesis Testing**:
  - Chi-Squared Test for categorical relationships.
  - Mann-Whitney U Test for non-parametric numeric comparisons.
  - CLT reasoning applied where appropriate.
 
---

## Business Questions Answered:

- Does age group affect default risk?
- Which loan intents carry highest default risk?
- Does loan grade reflect default risk?
- Do renters default more than homeowners?
- Is there an income difference between defaulters and non-defaulters?
- Does low income + high loan combo increase risk?
- Do higher interest rates correlate with default?
- Does loan-to-income ratio affect default risk?

---

## Statistical Test Summary by Risk Factor:

| Risk Factor                     | Test Used       | Statistically Significant? | Insights|
|--------------------------------|------------------|-----------------------------|--------------------------------------------------------------------------|
| Age Group                      | Chi-Squared      | ❌ No                        | Default rates are similar across age brackets.                           |
| Loan Intent                    | Chi-Squared      | ✅ Yes                       | Medical loans have highest default rates; Ventures have the lowest.     |
| Loan Grade                     | Chi-Squared      | ✅ Yes                       | Grades E, F, and G show significant risk; Grade A is the safest.         |
| Home Ownership (Own vs Rent)   | Chi-Squared      | ✅ Yes                       | Renters default more than owners.                                        |
| Income Level                   | Mann-Whitney U   | ✅ Yes                       | Defaulters earn ~28–35K; non-defaulters earn ~40–45K.                    |
| Income + Loan Combo            | Mann-Whitney U   | ✅ Yes                       | 60% default rate in low-income + high-loan group.                        |
| Loan Interest Rate             | Mann-Whitney U   | ✅ Yes                       | Defaulters average ~15% interest; non-defaulters ~7.5%.                  |
| Loan-to-Income Ratio           | Mann-Whitney U   | ✅ Yes                       | Higher loan-to-income ratios correlate with loan default.               |

---

## Key Visualizations:

<h3 align="center"><strong>Numerical Columns Data Distribution</strong></h3>
<br>
<p align="center">
  <img src="sample_visuals/numerical_cols_distribution.png" alt="KDE Plots">
</p>
<hr>

<h3 align="center"><strong>Correlation Heatmap</strong></h3>
<br>
<p align="center">
  <img src="sample_visuals/correlation.png" alt="Correlation Heatmap">
</p>
<hr>

<h3 align="center"><strong>Box Plots for Outlier Detection</strong></h3>
<br>
<p align="center">
  <img src="sample_visuals/box_plots.png" alt="Outlier Box Plots">
</p>
<hr>

<h3 align="center"><strong>Normality Test (Q-Q + Probability Plot)</strong></h3>
<br>
<p align="center">
  <img src="sample_visuals/normality_test.png" alt="Normality Test">
</p>
<hr>

<h3 align="center"><strong>Loan Default % by Loan Grade</strong></h3>
<br>
<p align="center">
  <img src="sample_visuals/loan_grade_vs_loan_defaults.png" alt="Loan Default by Grade">
</p>
<hr>

<h3 align="center"><strong>Loan Default % by Loan Intent</strong></h3>
<br>
<p align="center">
  <img src="sample_visuals/loan_intent_vs_loan_defaults.png" alt="Loan Intent Risk">
</p>
<hr>

<h3 align="center"><strong>Income vs Loan Default Status</strong></h3>
<br>
<p align="center">
  <img src="sample_visuals/income_vs_loan_defaults.png" alt="Income vs Default">
</p>
<hr>

<h3 align="center"><strong>Loan Interest Rate vs Default Status</strong></h3>
<br>
<p align="center">
  <img src="sample_visuals/loan_interest_rates_vs_loan_defaults.png" alt="Interest Rate vs Default">
</p>
<hr>

<h3 align="center"><strong>Loan Default % by Home Ownership</strong></h3>
<br>
<p align="center">
  <img src="sample_visuals/home_ownership_vs_loan_defaults.png" alt="Home Ownership Risk">
</p>
<hr>

<h3 align="center"><strong>Loan Default Count by Income + Loan Bracket</strong></h3>
<br>
<p align="center">
  <img src="sample_visuals/loan_defaults_by_income_and_loan_brackets.png" alt="Income + Loan Combo Risk">
</p>
<hr>

---

## Strategic Takeaways:

- **High Risk Flags**: Medical intent, Grades E – G, renters, income < ₹35K, interest rate > 12%, loan-to-income ratio > 0.4  
- **Safe zones**: Grade A, Venture intent, homeowners, income > ₹45K  
- **Underwriting team recommendation**: Apply stricter scrutiny to flagged combinations

---

## Tools Used:

- Python: `pandas`, `numpy`, `seaborn`, `matplotlib`, `scipy`, `statsmodels`
- Jupyter Notebook

---

## Next Steps:

- Convert notebook into a Streamlit or Power BI dashboard  
- Package results into a stakeholder-facing report

---
