
# ✈️ Airline Passenger Forecasting using ARIMA

Time-series forecasting of monthly international airline passengers using an **ARIMA** model in Python, including stationarity testing, train/test evaluation and a 24-month forecast.

---

## 🎯 Objective

To forecast future airline passenger demand from historical monthly data, which helps airlines plan capacity, scheduling and resources.

## 🗂️ Dataset

- **Source:** [Dataset name and link, e.g. Kaggle / Box-Jenkins airline data]
- **Period:** January 1949 to December 1960 (144 monthly observations)
- **Column:** `Thousands of Passengers` (monthly total, in thousands)

## 🛠️ Tools Used

Python · Pandas · NumPy · Matplotlib · Statsmodels (ADF test, ACF/PACF, ARIMA)

## 🔄 Project Workflow

### 1. Data Preparation
- Loaded the data and removed a non-data footer row (the only missing values)
- Converted `Month` to a datetime type and set it as the index
- Plotted the series to inspect trend and seasonality

### 2. Stationarity Check (ADF Test)
- **H₀:** the series is non-stationary | **H₁:** the series is stationary
- Original series: **p-value = 0.992**, so the series is **non-stationary**
- Applied differencing, then re-tested: **p-value = 0.039**, so the null hypothesis is rejected at the 5% level and the differenced series is **stationary**

### 3. Identifying Model Parameters
- Plotted **ACF** and **PACF** of the differenced series to guide the AR (p) and MA (q) terms

### 4. Train/Test Split
- **Training:** January 1949 to December 1955 (84 months)
- **Testing:** January 1956 to December 1960 (60 months)

### 5. Model Building & Evaluation
- Fitted an **ARIMA(14, 2, 12)** model on the training data
- Predicted the test period and compared actual vs predicted values
- Mean residual (actual − predicted): **≈ 22.9 thousand passengers**

### 6. Forecasting
- Forecast passenger numbers for the **next 24 months (1961 to 1962)**

## 📈 Results

- The raw series shows a clear upward trend and is non-stationary (ADF p-value 0.992), so differencing was required
- After differencing, the series passed the ADF test (p-value 0.039)
- On the 1956-1960 test set, the mean residual was about 22.9 thousand passengers, meaning the model under-predicted on average
- Test RMSE: **[value]** | MAE: **[value]** | MAPE: **[value]%**

## 🖼️ Charts

![Original series](images/original_series.png)
![Test vs predicted](images/test_vs_predicted.png)
![Forecast 1961-1962](images/forecast.png)

## 📁 Repository Structure

```
airline-passenger-arima-forecast/
├── data/        # Airline passengers dataset (CSV)
├── notebooks/   # ARIMA notebook
├── images/      # Charts
├── requirements.txt
└── README.md
```

## ▶️ How to Run

1. Install the libraries: `pip install -r requirements.txt`
2. Open the notebook in `notebooks/` with Jupyter
3. Run all cells

## 🔮 Possible Improvements

- Try a seasonal model (SARIMA), since the data has strong yearly seasonality
- Use `auto_arima` or AIC/BIC to choose orders more systematically
- Compare against other models such as Holt-Winters or Prophet

## 👤 Author

**Sidharth R**
[LinkedIn](https://www.linkedin.com/in/sidharth-r-943115233) · [GitHub](https://github.com/sidharthram99) · ✉️ sidharthram99@gmail.com
