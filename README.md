# ⚡ Anomaly Detection and Load Prediction in Smart Grids

## 1. Introduction
This project develops a two-part system for Smart Grids:
- **Short-Term Load Forecasting (STLF)** for operational planning.
- **Anomaly Detection** for identifying faults, theft, or cyber-attacks in real-time.

Dataset: `smart_grid_dataset.csv` (time-series data including load, time, and possibly weather/price features).

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



## 🖼️ Plots and Figures

### 1. Model Performance Comparison on Test Set

This figure visually compares the final performance of all four explored models on the unseen test data. Lower values are better for error metrics (RMSE, MAE), and higher values are better for $R^2$.

![Model Performance Comparison on Test Set](results/model_comparison_bar_chart.json)

### 2. Generalization Comparison ($R^2$): Train vs. Test

This plot highlights the critical difference between model performance on the training data (what the model learned) versus the test data (how the model generalizes).

* The **Decision Tree Regressor** exhibits near-perfect performance on the training set ($R^2 \approx 1.0$), but its performance plummets on the test set, indicating severe **overfitting**.
* The **Random Forest Regressor** maintains a much smaller gap between train and test scores, confirming its **robustness and superior generalization**.

![Generalization Comparison ($R^2$): Train vs. Test](results/r2_generalization_comparison.json)

### 3. Suggested Future Plots (To complete the six figures)

* **Time Series Plot:** Actual Load vs. Predicted Load for a selected 7-day period on the test set.
* **Anomaly Detection Plot:** A time series plot illustrating the calculated Anomaly Score with the dynamic threshold clearly marked.
* **Residuals Histogram:** A histogram of the prediction errors (Actual - Predicted) to verify model bias.
* **Feature Importance Plot:** A bar chart showing the relative importance of engineered time and external features to the final Random Forest prediction.


## 5. Deployment / Future Work
- Integration into real-time data streams (e.g., Kafka).
- Hyperparameter tuning of Random Forest.
- Explore deep learning models (LSTM, CNN-LSTM) for potentially higher accuracy.
