# 🪙 Bitcoin Price Prediction: Adaptive Time Series Modeling
**Box-Jenkins Methodology & Rolling Forecast Strategy**

## 📌 Project Overview
Predicting Bitcoin (BTC-USD) prices presents a significant challenge due to its inherent volatility and non-linear market dynamics. This project implements a rigorous **Time Series Analysis** to model historical price behavior and estimate future values using the **Box-Jenkins methodology**.

---

## ⚙️ Engineering Solutions & Statistical Rigor

### 1. Advanced Data Decomposition
* **Additive vs. Multiplicative:** Initial testing of an additive model proved unsuitable due to the series' high variability.
* **Optimization:** A **Multiplicative Decomposition** was implemented to better capture the proportional relationship between the trend and volatility.

### 2. Achieving Stationarity
To satisfy the assumptions of ARIMA modeling, a multi-stage stationarization process was conducted:
* **Log-Transformation:** Applied to stabilize variance across the series.
* **Unit Root Testing:** The **Augmented Dickey-Fuller (ADF) Test** ($p = 0.795$) confirmed the series was non-stationary.
* **First-Order Differencing:** Applied to the logarithmic data to remove trends and achieve a stationary state.



### 3. Model Identification & Validation
* **Selection:** Utilized **ACF and PACF** correlograms alongside `auto_arima` to identify the most parsimonious model.
* **Final Model:** **ARIMA(0,1,1)** was selected based on optimal **AIC and BIC** scores.
* **Diagnostics:** Residuals were analyzed via the **Ljung-Box test**, confirming high empirical performance despite the complexity of financial noise.

### 4. Dynamic Strategy: Rolling Window Forecast
* **The Challenge:** Static long-term forecasts are often unreliable for volatile assets.
* **The Solution:** Implemented a **Rolling Forecast (Fenêtre Glissante)** strategy. 
* **Process:** The model is dynamically re-trained at each step, incorporating the previous day's actual value to predict the next.
* **Performance:** This adaptive approach achieved a **Mean Absolute Percentage Error (MAPE) of 1.76%**.

---

## 📊 Technical Results Summary
* **Dataset:** Daily closing prices from Sept 2014 to May 2025.
* **Optimal Model:** ARIMA(0,1,1).
* **Metrics:** 1.76% MAPE on the test set.
* **Tech Stack:** Python, Pandas, Statsmodels, Matplotlib, yfinance.

---

## 🛠️ Project Structure
* `notebooks/`: Jupyter Notebook containing the full analysis pipeline.
* `data/`: Dataset downloaded via the Yahoo Finance API.
* `documentation/`: Detailed technical project report.
