# Gold Price Prediction Project

## 1. Project Overview
This project aims to predict daily gold prices using historical price data and financial indicators. Two machine learning models were developed and evaluated:
- **Random Forest Regressor**
- **Gradient Boosting Regressor**

### Objectives
- **Data Preprocessing**: Handle missing values, convert date information, and apply scaling as needed.
- **Model Development**: Train different regression models and optimize hyperparameters.
- **Model Evaluation**: Evaluate models using error metrics (MAE, MSE, RMSE, R²).
- **Feature Engineering**: Add features based on historical price trends and correlations to improve prediction accuracy.

---

## 2. Data Exploration and Preprocessing

### Dataset Overview
- **Variables**: SPX (S&P 500 Index), GLD (Gold Price), USO (Oil Prices), SLV (Silver Prices), and EUR/USD exchange rates.
- **Null Values**: Initial examination revealed no null values.
- **Date Conversion**: Date column converted to datetime format for time-based feature creation.

### Data Preprocessing Steps
1. **Lagged Features**: Added 1, 3, and 7-day lags for SPX, USO, and GLD.
2. **Rolling Statistics**: Calculated 7, 14, and 30-day moving averages and standard deviations for SPX, USO, and GLD.
3. **Ratios and Percentage Changes**: Calculated SPX-to-GLD ratios and percentage changes to capture momentum.
4. **Cumulative Measures**: Calculated expanding averages and sums for SPX.
5. **Scaling**: Standardized numerical features.

---

## 3. Exploratory Data Analysis (EDA)

### Correlation Analysis
- **GLD and SLV**: Strong positive correlation (0.87), indicating that silver prices are a significant predictor of gold prices.
- **GLD and USO**: Moderate positive correlation (0.18), suggesting a slight impact.
- **Lagged GLD Values**: Strong correlation with current GLD, indicating price continuity.
- **GLD and SPX**: Low correlation (0.05), indicating minimal impact on gold prices.

---

## 4. Model Development and Rationale

### Model Selection
- **Random Forest Regressor**: Suitable for capturing complex, non-linear relationships.
- **Gradient Boosting Regressor**: Effective for modeling non-linear interactions.

### Hyperparameter Tuning
- **Random Forest**: Tuned `n_estimators`, `max_depth`.
- **Gradient Boosting**: Tuned `n_estimators`, `learning_rate`, `max_depth`.

---

## 5. Model Evaluation and Comparison

| Model             | MAE   | MSE   | RMSE  | R²    |
|-------------------|-------|-------|-------|-------|
| Random Forest     | 0.943 | 1.819 | 1.349 | 0.9964 |
| Gradient Boosting | 0.883 | 1.427 | 1.194 | 0.9972 |

### Key Insights
- **Accuracy**: Gradient Boosting has lower MAE and MSE.
- **Error Handling**: Lower RMSE in Gradient Boosting suggests better handling of larger errors.
- **Variance Explained**: Gradient Boosting’s higher R² indicates it explains more variance.

---

## 6. Feature Importance and Residual Analysis

### Feature Importance
- **Top Features**: Recent gold price data (GLD_lag1, GLD_lag7) and SLV are key predictors.
- **Other Factors**: SPX and USO have moderate to low importance.

### Residual Plot Analysis
- **Gradient Boosting**: Residuals are centered around zero with a slight spread.
- **Random Forest**: Residuals show minimal overfitting.

---

## 7. Error Distribution Analysis
- **Shape**: Both models’ error distributions are bell-shaped and centered around zero.
- **Spread**: Gradient Boosting’s distribution has a tighter spread, handling prediction errors more effectively.

---

## Overall Comparison and Final Conclusion
- **Key Predictors**: Recent gold price trends (GLD_lag1, GLD_lag7) and silver prices (SLV).
- **Influence of Other Factors**: Minimal direct impact from SPX and EUR/USD exchange rates.
- **Model Comparison**: Gradient Boosting outperformed Random Forest on all key metrics, indicating it better captures complex relationships.

### Final Recommendation
The **Gradient Boosting Regressor** is recommended for predicting gold prices due to its precision and minimized prediction error.
