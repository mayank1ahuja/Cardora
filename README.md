![Project Header](https://github.com/mayank1ahuja/Cardora/blob/31534f693710b3f4a812962a71bcd8740ee9c9ff/images/project%20header.png)
# Cardora: Predictive Credit Utilisation and Risk Analytics

## `TL;DR`
Cardora is a compact analytics project that translates customer credit-card records into practical insights about spending behaviour and credit risk. The analysis uses structured preprocessing, descriptive exploration, interpretable feature engineering, and regression-based predictive modeling to forecast credit utilisation and surface early warning signals. Deliverables include four reproducible notebooks, a cleaned dataset, model artifacts, and a set of visualizations.

## `Project Overview`
Cardora examines how customer demographics, account attributes, and recent payment activity combine to influence credit utilisation and short-term spending. The project blends data preparation, exploratory analysis, feature engineering, and a regression-based predictive model to generate forecasts and identify customers whose behaviour departs from expected norms.

This work is intended as a portfolio case study: a practical demonstration of how structured analytics and clear interpretation can support risk-aware decision making.

## `Background and Motivation`
Managing credit utilization and assessing financial risk have become critical challenges in modern consumer finance. The increasing volume of credit card users, combined with diverse spending and repayment behaviors, has made it difficult for institutions to predict potential defaults and maintain healthy credit portfolios. This creates operational risks that affect both lenders and consumers alike.

To explore this, data from the UCI Default of Credit Card Clients Dataset was analyzed which includes demographic information, billing histories, payment behaviors, and credit limits. By examining these patterns, the project aims to identify key indicators of financial risk and better understand how utilization trends relate to repayment outcomes.

## `Data Source`
- **Source:** UCI Default of Credit Card Clients dataset 
- [**Dataset**](https://www.kaggle.com/datasets/uciml/default-of-credit-card-clients-dataset)
- This public dataset contains 30,000 credit card customer records from Taiwan. It is available in Excel format and includes 23 fields per record. Each entry represents one customer and captures demographic attributes such as gender, education, marital status, and age, along with credit limit, billing amounts, and payment histories over six months.

## `Objectives`
Cardora answers the following business questions:

- Which customer attributes and recent behaviours help predict short-term credit utilisation or balances?  
- How can simple, interpretable models be leveraged to forecast spending and detect customers whose behavior indicates growing risk?  
- How can visual analysis and derived risk metrics be combined to make model outputs actionable for business users?

The outcomes are designed to support decisions such as targeted credit offers, monitoring thresholds, and prioritised outreach.

## `Linear Regression`

### 💳 What is it?
Linear regression models the relationship between an outcome (target) and one or more input variables by estimating how a unit change in each input is associated with a change in the outcome. Practically: it gives a simple formula that predicts a numeric value from a weighted sum of features.

### 💳 Where it fits in Cardora?
Linear regression is used to forecast a continuous spending-related target (for example, next month’s bill or balance) from customer features and recent billing/payment history. It forms the predictive backbone of the project and provides interpretable coefficients.

### 💳 Why it was chosen?
- **Interpretability:** Coefficients are easy to explain to stakeholders.  
- **Simplicity:** The dataset is tabular and structured; a linear approach is a low-risk, high-clarity first model.  
- **Diagnostic clarity:** Residuals, coefficient signs and magnitudes, and standard metrics (R², MSE) are straightforward to compute and interpret.  
- **Fit-for-purpose:** The aim is actionable explanation and forecasting rather than opaque accuracy wins, a goal with which linear regression aligns.

### 💳 How it was implemented?
- **Feature selection:** chose demographic attributes, credit limit, recent bill amounts, and engineered signals (utilisation ratio, bill trend slope).  
- **Train/test split:** created separate training and hold-out sets to evaluate generalisation.  
- **Scaling where appropriate:** numeric features were standardised when needed for coefficient comparability.  
- **Fit model:** ordinary least squares via scikit-learn’s `LinearRegression`.  
- **Interpretation:** inspected coefficients, residuals, and prediction-vs-actual plots to validate the sign and relative importance of features.  
- **Validation:** used R², RMSE, MAE and k-fold cross-validation to check robustness.

### 💳 What this achieves?
An interpretable prediction formula and concrete signals (coefficients + residual diagnostics) that can be used to highlight customers whose observed behaviour differs materially from the model’s expectation serving as a practical proxy for anomalous or risky behaviour.

## `Methodology`

The project followed a clear and structured analytical workflow designed to turn raw credit card data into meaningful, decision-ready insights. Each step was developed with an emphasis on interpretability, data quality, and practical relevance.  

### 💳 Data Ingestion & Initial Validation  
The process began with loading over 30,000 customer records from the UCI credit card dataset into a clean working environment. Basic schema checks and column validations were performed to ensure the data was properly formatted, consistent, and ready for subsequent analysis.

### 💳 Data Preprocessing & Cleaning  
Before modeling, the dataset was refined to achieve stability and accuracy. Column names were standardized, categorical fields such as education and marital status were encoded numerically, and missing or extreme values were reviewed. This ensured the data remained reliable and interpretable while minimizing noise and inconsistencies that could distort downstream insights.

### 💳 Feature Engineering  
Derived variables were created to capture key behavioural patterns that are not visible in the raw data. Examples include the **utilisation ratio** (credit used relative to limit), **average bill and payment amounts** over six months, and the **slope of bill trends** to show whether spending is increasing or stabilizing. These indicators were combined into a **composite risk score**, providing a clearer picture of customer behaviour and supporting both the model and visual analytics.

### 💳 Exploratory Data Analysis (EDA)  
Exploratory analysis was carried out to better understand customer segments and variable relationships. Using Altair visualizations, the analysis examined utilisation distributions, bill trajectories, and repayment behaviours across different demographic and behavioural groups. The goal was to identify meaningful trends and prepare a solid foundation for the modeling stage.

### 💳 Modeling  
Linear Regression was used as the main predictive model due to its interpretability and ability to highlight feature impact. The approach balanced statistical robustness with clarity, making it easier to explain how each input influences predicted risk levels.

### 💳 Risk Analytics & Scoring  
Model predictions and engineered features were combined to form a structured risk assessment system. Customers were grouped into **Low**, **Medium**, and **High-risk categories** using decile-based scoring. Interactive Altair dashboards displayed lift and capture curves, utilisation trends, and behavioural clusters, allowing risk analysts and stakeholders to explore results visually.

### 💳 Evaluation & Interpretation  
The model’s accuracy and reliability were evaluated using standard metrics like **R²**, **RMSE**, and **MAE**. Residual plots and cross-validation confirmed model consistency. Finally, results were interpreted in a business context, for example, customers with high utilisation and increasing bill trends were flagged as higher risk. These insights bridged the gap between statistical results and practical decision-making.

## `Modeling`

This section outlines the model design, training, and evaluation pipeline exactly as implemented in the notebook, aligning technical choices with practical interpretability.

### 💳 Model Choice  
The model uses **Ordinary Least Squares (Linear Regression)** as its core predictive engine.  
This approach was selected for its interpretability, stability on structured numerical data, and its ability to produce transparent coefficients that directly quantify how each feature influences the outcome.

### 💳 Target Definition  
The target variable is **`bill_amt1`**, representing the **next month’s billing amount** for a customer.  
This variable was chosen because it captures short-term financial behavior, offering actionable insight into customer spending and repayment tendencies. Predicting this value allows credit analysts to anticipate upcoming utilization and flag potential overexposure.

### 💳 Feature Set  
The input matrix `X` includes demographic attributes, account-level details (such as credit limit), recent bill and payment histories, and engineered behavioral indicators derived from six-month trends.  
These features collectively describe **who the customer is**, **their spending capacity**, and **how their repayment behavior is evolving** — ensuring that the model captures both static and dynamic aspects of financial behavior.

### 💳 Training Pipeline  
The workflow follows a structured pipeline:
- **Data Preparation:** Split the dataset into input (`X`) and target (`y`) variables to ensure clear separation of predictors and outcomes, avoiding data leakage.  
- **Train/Test Split:** Divide the data into training and testing subsets to validate real-world generalization, typically using an 80/20 ratio.  
- **Model Fitting:** Train a `LinearRegression()` model using scikit-learn’s implementation, allowing the algorithm to learn linear relationships between features and the target variable.  
- **Diagnostics:** Inspect coefficient signs and magnitudes to ensure alignment with domain logic — for instance, higher utilization ratios should reasonably predict higher billing amounts.  
- **Validation:** Assess performance on the hold-out test set to ensure robust generalization.

### 💳 Evaluation Metrics and Interpretation  
The model’s effectiveness is evaluated using standard regression metrics:
- **R²:** Measures how much of the variance in billing amounts is explained by the features.  
- **RMSE / MAE:** Quantify average prediction error in practical (monetary) units.  
- **Residual Analysis:** Checks for heteroscedasticity and ensures the model doesn’t systematically underpredict or overpredict extreme values.  
- **Coefficient Review:** Confirms interpretability and the expected directional influence of each predictor, a critical requirement for business trust.

### 💳 Why This Modeling Approach Works  
This modeling approach is both **interpretable and operationally relevant**.  
The regression outputs provide direct financial forecasts that can inform **credit limit management**, **risk monitoring**, and **early intervention strategies**.  

By combining simplicity with transparency, the model builds confidence among stakeholders while providing a clear foundation for future enhancements (e.g., incorporating regularization or non-linear terms).

## `Risk Analytics`

### 💳 Purpose
To translate model predictions and behavioral indicators into meaningful, interpretable signals that support decision-making in credit operations and portfolio monitoring.

### 💳 What is generated?
Derived variables were created to capture behavioural patterns not directly visible in the raw data. Examples include the **utilisation ratio** (credit used relative to limit), **average bill and payment amounts** across six months, and the **slope of bill trends**, which reflects whether spending behaviour is rising or stabilising.  
These features, along with regression-based forecasts, were integrated into a **composite risk score**, offering a more complete representation of customer behaviour.  

The resulting risk scores were segmented into **deciles** and further classified into **risk flags** (Low / Medium / High) to enable tiered risk management. Supporting these, **decile lift and capture curves** quantify how efficiently high-score segments capture defaults or anomalous repayment behaviours.  

### 💳 Visualisation layer 
Altair-powered interactive charts allow seamless exploration — a scatter plot paired with linked histograms highlights utilisation spikes, repayment irregularities, and clusters of high-risk customers, helping analysts visually validate model signals.

### 💳 How this fits the pipeline?
This module forms the interpretability bridge between regression outputs and operational strategy.  
While model predictions estimate *likelihood of default*, risk analytics articulate *who* to monitor and *why*.  
By framing metrics around deciles, lifts, and behavioural composites, the analysis translates statistical forecasts into practical monitoring strategies.

### 💳 What the risk outputs enable?
- Prioritised monitoring and outreach to top-risk deciles.  
- Early-warning indicators.
- Transparent and rules-based screening.

## `Key Findings`

- **Credit utilisation emerged as the most powerful signal** of elevated balances and potential repayment strain, consistently driving higher predicted risk levels.  
- **Behavioral trends carried significant weight:** Customers exhibiting upward bill trajectories (positive slopes) tended to cluster in higher-risk segments, reinforcing the value of temporal features.  
- **Demographic attributes provided contextual depth:** Factors like age and education shaped spending behavior but remained secondary to utilisation-driven dynamics.  
- **Model transparency proved valuable:** The linear regression framework offered interpretable coefficients, allowing direct translation of statistical patterns into clear, actionable risk guidelines.

## `Deliverables`

The project deliverables form a complete, reproducible **credit risk analytics workflow** transforming raw behavioral data into interpretable, decision-ready insights.

### 💳 Core Notebooks

- **Preprocessing:** Data cleaning, handling of missing values, and creation of base analytical fields.  
- **Exploratory Data Analysis (EDA):** Behavioral profiling through Seaborn visualizations.  
- **Modeling:** Linear Regression model built for explainable forecasting supported by diagnostics, coefficient review, and feature interpretation.  
- **Risk Analytics:** Translation of model outputs into operational risk signals visualized through Altair.

## `Impact and Skills Demonstrated`

This project exemplifies the ability to translate **credit card behavior data into explainable financial risk analytics**, bridging technical dilligence with real-world decision support.

### 💳 Analytical and Technical Strengths
- **End-to-end workflow design:** Orchestrated a multi-stage pipeline covering data preprocessing, feature engineering, regression modeling, and risk segmentation.  
- **Feature interpretability:** Created domain-grounded variables (utilisation ratio, bill trend slope, composite risk score) to make quantitative predictions explainable.  
- **Model transparency:** Employed Ordinary Least Squares regression for interpretable forecasting and stable parameter estimation. 
- **Integrated visualization:** Delivered Altair-based plots within Jupyter, providing interactive lift, capture, and cluster views without external tools.  

### 💳 Strategic and Business Outcomes
- Enhanced interpretability and accountability in credit risk estimation.  
- Produced operationally useful signals (e.g., top-decile monitoring, utilization spikes) for early risk detection.  
- Delivered fully reproducible analytics documentation suitable for audit, presentation, or extension.

Overall, the project highlights **practical modeling literacy, business framing ability, and visual communication skills** — all within a single, self-contained Python environment.



