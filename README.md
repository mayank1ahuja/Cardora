![Project Header](https://github.com/mayank1ahuja/Cardora/blob/31534f693710b3f4a812962a71bcd8740ee9c9ff/images/project%20header.png)
# Cardora: Predictive Credit Utilisation and Risk Analytics

## TL;DR
Cardora is a compact analytics project that translates customer credit-card records into practical insights about spending behaviour and credit risk. The analysis uses structured preprocessing, descriptive exploration, interpretable feature engineering, and regression-based predictive modeling to forecast credit utilisation and surface early warning signals. Deliverables include four reproducible notebooks, a cleaned dataset, model artifacts, and a set of visualizations.

## Project Overview
Cardora examines how customer demographics, account attributes, and recent payment activity combine to influence credit utilisation and short-term spending. The project blends data preparation, exploratory analysis, feature engineering, and a regression-based predictive model to generate forecasts and identify customers whose behaviour departs from expected norms.

This work is intended as a portfolio case study: a practical demonstration of how structured analytics and clear interpretation can support risk-aware decision making.

## Background and Motivation
Managing credit utilization and assessing financial risk have become critical challenges in modern consumer finance. The increasing volume of credit card users, combined with diverse spending and repayment behaviors, has made it difficult for institutions to predict potential defaults and maintain healthy credit portfolios. This creates operational risks that affect both lenders and consumers alike.

To explore this, data from the UCI Default of Credit Card Clients Dataset was analyzed which includes demographic information, billing histories, payment behaviors, and credit limits. By examining these patterns, the project aims to identify key indicators of financial risk and better understand how utilization trends relate to repayment outcomes.


## Data Source
- **Source:** UCI Default of Credit Card Clients dataset 
- [**Dataset**](https://www.kaggle.com/datasets/uciml/default-of-credit-card-clients-dataset)
- This public dataset contains 30,000 credit card customer records from Taiwan. It is available in Excel format and includes 23 fields per record. Each entry represents one customer and captures demographic attributes such as gender, education, marital status, and age, along with credit limit, billing amounts, and payment histories over six months.

## Objectives
Cardora answers these business questions:

1. Which customer attributes and recent behaviours help predict short-term credit utilisation or balances?  
2. How can simple, interpretable models be leveraged to forecast spending and detect customers whose behavior indicates growing risk?  
3. How can visual analysis and derived risk metrics be combined to make model outputs actionable for business users?

The outcomes are designed to support decisions such as targeted credit offers, monitoring thresholds, and prioritised outreach.

## Linear Regression

1. *What is it?*
Linear regression models the relationship between an outcome (target) and one or more input variables by estimating how a unit change in each input is associated with a change in the outcome. Practically: it gives a simple formula that predicts a numeric value from a weighted sum of features.

2. *Where it fits in Cardora?*
Linear regression is used to forecast a continuous spending-related target (for example, next month’s bill or balance) from customer features and recent billing/payment history. It forms the predictive backbone of the project and provides interpretable coefficients.

3. *Why it was chosen?*
- **Interpretability:** Coefficients are easy to explain to stakeholders.  
- **Simplicity:** The dataset is tabular and structured; a linear approach is a low-risk, high-clarity first model.  
- **Diagnostic clarity:** Residuals, coefficient signs and magnitudes, and standard metrics (R², MSE) are straightforward to compute and interpret.  
- **Fit-for-purpose:** The aim is actionable explanation and forecasting rather than opaque accuracy wins, a goal with which linear regression aligns.

4. *How it was implemented?*
- **Feature selection:** chose demographic attributes, credit limit, recent bill amounts, and engineered signals (utilisation ratio, bill trend slope).  
- **Train/test split:** created separate training and hold-out sets to evaluate generalisation.  
- **Scaling where appropriate:** numeric features were standardised when needed for coefficient comparability.  
- **Fit model:** ordinary least squares via scikit-learn’s `LinearRegression`.  
- **Interpretation:** inspected coefficients, residuals, and prediction-vs-actual plots to validate the sign and relative importance of features.  
- **Validation:** used R², RMSE, MAE and k-fold cross-validation to check robustness.

5. *What this achieves?*  
An interpretable prediction formula and concrete signals (coefficients + residual diagnostics) that can be used to highlight customers whose observed behaviour differs materially from the model’s expectation serving as a practical proxy for anomalous or risky behaviour.
