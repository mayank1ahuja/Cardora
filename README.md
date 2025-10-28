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
- !{Dataset}(https://www.kaggle.com/datasets/uciml/default-of-credit-card-clients-dataset)
- This public dataset contains 30,000 credit card customer records from Taiwan. It is available in Excel format and includes 23 fields per record. Each entry represents one customer and captures demographic attributes such as gender, education, marital status, and age, along with credit limit, billing amounts, and payment histories over six months.
