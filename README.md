# Loan-Repayment-Classification-Project

**This project uses real-world loan data from LendingClub.com to predict whether a borrower will fully repay their loan. The goal is to support automated loan approval decisions by identifying high-risk borrowers.**

## 📁 Dataset Overview
The dataset contains over 9,500 loans with features related to:

Loan terms: interest rate, installment

Borrower profile: income, FICO score, credit line age

Credit behavior: revolving balance, inquiries, delinquency history

Target variable: not_fully_paid (1 = defaulted or not fully repaid)

 Binary classification problem: predict not_fully_paid

 ## Exploratory Data Analysis (EDA)
Correlation Matrix: Identified moderately high correlation between installment and int_rate (0.71). Since models like Random Forest and XGBoost are robust to multicollinearity, no features were dropped.

Distribution Plots: Compared distributions of key variables (fico, int_rate, log_annual_inc) between fully paid and not fully paid loans.

Purpose-Based Segmentation: Found certain loan purposes (e.g., small_business) more associated with non-payment.


## Hypothesis Testing
### Hypothesis	Result
H1: Borrowers who default pay higher interest rates.	✅ p-value: 1.22e-55 — Strong evidence of higher rates among defaulters.
H2: Loan purpose and repayment status are associated.	✅ p-value: 2.23e-16 — Significant association between loan purpose and default likelihood.



## Models & Evaluation

Given the class imbalance and business priority to flag non-paying borrowers, model performance was judged heavily on recall and F1-score for class 1.

| Model               | Accuracy | Recall (1) | F1-score (1) | Notes                                  |
|---------------------|---------|------------|--------------|----------------------------------------|
| Logistic Regression | 0.64    | ✅ 0.62    | ✅ 0.36      | Best at catching defaults             |
| XGBoost            | 0.70    | 0.34       | 0.26         | Balanced, decent fallback             |
| Random Forest      | ✅ 0.80 | 0.16       | 0.21         | High accuracy, poor at catching defaults |

**Final Model Chosen: Logistic Regression** — because it best satisfies the business need to maximize detection of risky borrowers, despite lower accuracy.


## Techniques Used
**Data Cleaning**: Checked for missing values and feature types

**Visualization**: Seaborn/Matplotlib histograms, heatmaps

**Feature Scaling:** StandardScaler for logistic regression

_**Modeling: Logistic Regression, Random Forest, XGBoost**_

**Class Imbalance**: Performance assessed with emphasis on class 1 (recall/F1)

**Hypothesis Testing**: t-test (interest rate), chi-square (purpose vs repayment)


 ## Key Takeaways
Borrowers who do not repay loans typically:

  Have higher interest rates
  
  Take loans for riskier purposes (e.g., small business)
  
  Interest rate, FICO score, and loan purpose are strong predictors of loan repayment
  
  Logistic Regression, despite simplicity, can be highly effective for high-stakes classification when interpretability and recall are critical

## Next Steps
Try threshold tuning to improve minority class recall

Incorporate explainability with SHAP values

Build a streamlit dashboard for business users



