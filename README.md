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
<img width="1000" height="600" alt="image" src="https://github.com/user-attachments/assets/b9c36f74-9a74-4e97-bab5-a1bed3d608df" />


### R² Comparison Across Datasets
<img width="1000" height="600" alt="image" src="https://github.com/user-attachments/assets/eeb19320-438a-4f2d-9950-06c3755d98cb" />

### RMSE Comparison Across Datasets
<img width="1000" height="600" alt="image" src="https://github.com/user-attachments/assets/522e2ab0-2bbc-49db-9844-fa61ea86853d" />


### Validation MAE Comparison
<img width="800" height="500" alt="image" src="https://github.com/user-attachments/assets/1247019e-5470-4a57-aaaf-3aee19cbbde2" />

### Validation RMSE Comparison
<img width="800" height="500" alt="image" src="https://github.com/user-attachments/assets/353f5611-97d0-4f21-b4af-7d31a2090052" />



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
