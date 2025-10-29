# Model Artifacts

## `Overview`
This section documents the model design, evaluation process, and key visual diagnostics from the **credit risk forecasting model**.  
The modeling phase converts engineered behavioral and demographic features into an interpretable, data-driven prediction framework.

## `Model Choice`
**Primary model:** *Ordinary Least Squares (Linear Regression)*  
**Rationale:** Offers coefficient interpretability, stability for structured numeric data, and clear insight into the direction and strength of predictors.

The goal was **explainability**, allowing business teams to trace *why* certain behaviors (e.g., high utilization or rising bills) increase financial risk.


## `Feature Composition`
The model uses a curated blend of static and behavioral features:

- **Demographic attributes:** Age, Education, Marital status  
- **Account capacity:** Credit limit (`LIMIT_BAL`)  
- **Behavioral indicators (6 months):** Bill and payment amounts  
- **Engineered metrics:**
  - Utilization Ratio = `bill_amt1 / limit_bal`
  - Average Bill & Total Payment (6m)
  - Bill Trend Slope — linear regression on bill amounts
  - Composite Risk Score — normalized aggregate of utilization and trend signals

Together, these features capture both *who* the customer is and *how* their behavior evolves.


## `Training and Evaluation Pipeline`
1. **Data split:** 80/20 train-test  
2. **Scaling:** StandardScaler applied to continuous variables  
3. **Model fitting:** `LinearRegression()` trained on scaled features  
4. **Diagnostics:** Checked coefficient directions for economic sense  
5. **Validation:** 5-fold cross-validation for R² stability  
6. **Baseline comparison:** Lasso regression for regularization sensitivity


## `Key Metrics`
| Metric | Meaning | Value (Example)                     |
|:--------|:---------|:--------------------------------- |
| R² | Variance explained by model | ~0.72     |         |
| RMSE | Average magnitude of prediction error | ~13,000 |
| MAE | Mean absolute error | ~9,800           |         |

The model achieves solid explanatory performance, with strong interpretability for operational credit monitoring.

## `Visual Artifacts`

### Coefficient Impact Plot  
Shows each feature’s contribution to the target prediction.  
High utilization and upward bill slope have the most positive weight, confirming expected financial behavior patterns.

### Predicted vs. Actual Plot  
Compares model predictions against actual values, assessing fit quality.  
A tight alignment around the diagonal line indicates robust predictive consistency.

### Residual Distribution Plot  
Visualizes residual errors to check model bias and variance stability.  
A near-symmetric bell shape suggests unbiased performance across ranges.


## `Interpretation`
The regression model provides **transparent outputs**:
- High utilization and increasing bill slope are consistently strong risk signals.  
- Demographic variables (age, education) offer secondary explanatory power.  
- Model diagnostics confirm that the predictive behavior aligns with real-world credit logic.

## `Summary`
The modeling stage establishes the **analytical backbone** for subsequent risk segmentation.  
Its transparency and reliability enable the next layer — **Risk Analytics** — to translate numeric predictions into actionable deciles, flags, and behavioral insights for credit operations.
