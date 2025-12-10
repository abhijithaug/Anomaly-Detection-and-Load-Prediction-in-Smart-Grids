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


<img width="708" height="380" alt="image" src="https://github.com/user-attachments/assets/1b9c65f5-c53e-46fb-8b7f-7ef102c66a7e" />


**Conclusion**:  
RandomForestRegressor was chosen as the final model due to superior performance across RMSE, R², and MAE, and robustness against overfitting compared to Decision Tree.

---

## 5. Deployment / Future Work
- Integration into real-time data streams (e.g., Kafka).
- Hyperparameter tuning of Random Forest.
- Explore deep learning models (LSTM, CNN-LSTM) for potentially higher accuracy.
