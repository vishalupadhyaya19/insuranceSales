# insuranceSales

# Insurance Sales: Agent Bonus Prediction (Linear Regression)

## Business Problem
An insurance company wants to understand what drives the bonus paid to its agents (`AgentBonus`) and predict it from customer and policy details.

## Dataset
Insurance sales data with 4,520 customers and 20 columns (customer age and tenure, income, sum assured, channel, occupation, designation, zone, payment method and more). [Add the source, e.g. Great Learning course dataset.]

## Approach
1. **Data cleaning:** fixed inconsistent labels (e.g. "Fe male" to Female, "Laarge Business" to Large Business, "Exe" to Executive, "UG" to Under Graduate), checked for duplicates (none found)
2. **Missing values:** filled 7 columns with the median (1% to 6% missing) and added a missing-indicator column for each
3. **Outlier analysis:** checked outliers with the IQR rule and compared average bonus for outliers vs the rest. Outliers had a much higher average bonus (about 7,300 vs 4,000 for Age), so they look genuine and were kept [confirm]
4. **Modelling:** OLS regression (statsmodels) with dummy-encoded categories and a 70/30 train-test split
5. **Model refinement:** removed multicollinear and insignificant variables step by step (VIF and p-values), going from 40 to 28 predictors with no loss in fit
6. **Assumption checks:** residuals vs fitted plot, residual histogram, Q-Q plot, Shapiro-Wilk (normality) and Goldfeld-Quandt (constant variance)

## Results
| Metric | Train | Test |
|---|---|---|
| RMSE | 603 | 619 |
| MAE | 477 | 493 |

- R² = 0.816, Adjusted R² = 0.814 (training data)
- Train and test errors are close, so the model is not overfitting
- Average bonus is about 4,080, so the typical error is about 12% of the average

## Key Insights
- Age and customer tenure both raise the bonus by about 22 per unit, holding other variables constant
- [Add 2-3 more from your final coefficients, e.g. channel, designation, sum assured]

## Limitations
- Shapiro-Wilk rejects normality of residuals (p < 0.05). Goldfeld-Quandt gives p = 0.10, so there is no strong evidence of changing variance
- [Add next steps, e.g. log-transform the target, try regularization or tree-based models]

## Tools
Python, pandas, NumPy, matplotlib, seaborn, statsmodels, scikit-learn, SciPy
