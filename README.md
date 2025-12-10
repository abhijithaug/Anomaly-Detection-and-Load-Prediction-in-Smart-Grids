# ⚡ Anomaly Detection and Load Prediction in Smart Grids

## 1. Introduction
This project develops a two-part system for Smart Grids:
- **Short-Term Load Forecasting (STLF)** for operational planning.
- **Anomaly Detection** for identifying faults, theft, or cyber-attacks in real-time.

Dataset: `smart_grid_dataset.csv` (time-series data including load, time, and possibly weather/price features).

---
# 📊 Regression Model Comparison

This repository presents a comparative analysis of several regression models applied to a dataset, evaluating their performance across **Train**, **Validation**, and **Test** sets using three key metrics:

- **RMSE** (Root Mean Square Error)
- **MAE** (Mean Absolute Error)
- **R²** (Coefficient of Determination)

---

## 🚀 Models Evaluated
- RandomForestRegressor
- DecisionTreeRegressor
- MLPRegressor
- KNN
- LinearRegression (Train only)

---

## 2. Methodology
### Load Prediction
- Models explored: Random Forest, MLP, Decision Tree, KNN
- **Final Model Selected**: RandomForestRegressor

### Anomaly Detection
- Residual-based approach: anomalies flagged when prediction errors are extreme.
- Proposed models: Isolation Forest, Z-Score thresholding.

---

## 3. Feature Engineering
- Time-series features: day-of-week, hour-of-day, month, holidays, lagged load values.
- External features: temperature, price (if available).

---

## 4. Results: Load Prediction (STLF)

| Model                  | RMSE (Test) | R² (Test) | MAE (Test) |
|-------------------------|-------------|-----------|------------|
| RandomForestRegressor   | 1.780       | 0.646     | 1.434      |
| MLPRegressor            | 1.903       | 0.596     | 1.532      |
| DecisionTreeRegressor   | 2.476       | 0.316     | 1.894      |
| KNN                     | 2.995       | -0.001    | 2.512      |



**Conclusion**:  
RandomForestRegressor was chosen as the final model due to superior performance across RMSE, R², and MAE, and robustness against overfitting compared to Decision Tree.

---



## 📈 Visual Comparisons

### MAE Comparison Across Datasets
![MAE Comparison Across Datasets](./images/mae_comparison.png)

### R² Comparison Across Datasets
![R² Comparison Across Datasets](./images/r2_comparison.png)

### RMSE Comparison Across Datasets
![RMSE Comparison Across Datasets](./images/rmse_comparison.png)

### Validation MAE Comparison
![Validation MAE Comparison](./images/validation_mae.png)

### Validation R² Comparison
![Validation R² Comparison](./images/validation_r2.png)

### Validation RMSE Comparison
![Validation RMSE Comparison](./images/validation_rmse.png)

---
### 3. Suggested Future Plots (To complete the six figures)

* **Time Series Plot:** Actual Load vs. Predicted Load for a selected 7-day period on the test set.
* **Anomaly Detection Plot:** A time series plot illustrating the calculated Anomaly Score with the dynamic threshold clearly marked.
* **Residuals Histogram:** A histogram of the prediction errors (Actual - Predicted) to verify model bias.
* **Feature Importance Plot:** A bar chart showing the relative importance of engineered time and external features to the final Random Forest prediction.

---
## 🧠 Insights

- 🌲 **RandomForestRegressor** shows strong generalization with high R² and low error across all datasets.
- 📉 **DecisionTreeRegressor** overfits the training data (perfect R²) but performs poorly on validation and test sets.
- 🧠 **MLPRegressor** maintains consistent performance across datasets, indicating good generalization.
- ⚠️ **KNN** struggles with generalization, showing high error and low R², especially on validation and test sets.

  ---
  
## 5. Deployment / Future Work
- Integration into real-time data streams (e.g., Kafka).
- Hyperparameter tuning of Random Forest.
- Explore deep learning models (LSTM, CNN-LSTM) for potentially higher accuracy.
