# A deep dive into multi-store retail time series analysis

##  Overview

This project focuses on forecasting weekly sales across multiple Walmart stores.

The dataset includes weekly sales data, holiday indicators, and economic variables (fuel price, CPI, unemployment, temperature) for multiple stores operating over the same time period.

---

##  Objectives

- Analyze multi-store sales behavior and seasonal patterns.  
- Test classical SARIMA and advanced LSTM models for weekly sales prediction.  
- Compare forecasting accuracy using **RMSE** and **MAE**.  
- Derive insights about which modeling strategy generalizes better across stores.  

---

##  Data Preprocessing & Feature Engineering

**Dataset:**  
> Walmart_Data_Analysis_and_Forcasting.csv



## Models and Methodology

### 1. SARIMA (Seasonal ARIMA)
- Found that due to store-level heterogeneity, multi-store overlap, non-stationary classical ARIMA performed is inconsistently — leading to exclusion from final comparison.

### 2. LSTM (Long Short-Term Memory)
- Implemented using Keras/TensorFlow.  
- Trained globally on all stores combined — capturing shared seasonal trends and holiday effects.  
- Sequence length of 12 weeks (past three months) used for forecasting the next week’s sales.  
- Optimized with dropout, early stopping, and scaling (MinMaxScaler).  

### 3. XGBoost Regressor (Benchmark)
- Used as a non-sequential baseline for comparison.  
- Included lag features and exogenous variables.

---


## Conclusion: 
- LSTM outperformed traditional methods by effectively capturing long-term dependencies, seasonality, and non-linear effects from external features.  
- The Box–Cox transformation and global training strategy improved stability and cross-store generalization.
