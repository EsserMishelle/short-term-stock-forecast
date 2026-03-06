# Predicting NVDA Stock Prices: 
## A Comparison of Baseline, Time-Series, and Machine Learning Models

### Overview and Analysis Objective

The objective of this project is to forecast the short-term closing price of NVIDIA (NVDA) stock and evaluate the predictive performance of multiple modeling approaches across different forecast horizons. The study compares baseline models, classical time-series methods, and machine learning models to assess how forecast accuracy changes from short horizons (1–5 days) to longer horizons (up to 30 days). 

Model performance is evaluated using Root Mean Squared Error (RMSE) to provide a consistent comparison across forecasting methods.

### Table of Contents 
- [01_naive_baseline](#eda_and_naive_baseline)

- 02_arima_model.ipynb
  
- 03_prophet_model.ipynb
  
- 04_price_based_models.ipynb

- 05_return_based_models.ipynb

- 06_model_comparison.ipynb

### Data Description
This project uses historical market data for NVIDIA (NVDA) along with selected market indicators to construct forecasting models. The dataset compares NVIDIA (NVDA) with other semiconductor companies (AMD, TSM) and the broader technology index (QQQ)T and includes daily stock prices and trading volumes covering the period 2021–2026. The historical market data is obtained from Yahoo Finance / yfinance.

## Exploratory Data Analysis(EDA) 

<img src="assets/multiple_stocks_closing_price.jpg" alt="Closing Prices" style="width: 2000px; height: 350px;">

All stocks show an upward trend over the sample period, reflecting growth in the semiconductor and technology sectors. 

NVDA exhibits the strongest growth trajectory in the later years of the dataset, coinciding with increased demand for AI-related computing hardware. While AMD and TSM also demonstrate significant growth, NVDA’s acceleration highlights its dominant role within the sector.

<img src="assets/multiple_stocks_trading_volume.jpg" alt="Trading Volume" style="width: 2000px; height:  350px;">

The volume chart shows NVDA consistently displays higher trading volume and more frequent spikes than its peers, indicating strong investor interest and active market participation. 

Periods of increased trading activity often coincide with major price movements, suggesting that changes in trading volume reflect shifts in market sentiment and information flow.

## Baseline Forecast Models

To establish a benchmark for model performance, two simple baseline forecasting approaches were implemented. These models serve as a reference point for evaluating whether forecasting methods improve predictive accuracy.

Naive Baseline: assumes the future price equals the most recent observed price.

<img src="assets/naive_baseline_results.jpg" alt="Naive Baseline Results" width='520'>

Naive Drift: extends the naive model by incorporating the average daily price change observed in the training data.

<img src="assets/naive_drift_results.jpg" alt="Naive Drift Results" width='650'>

Baseline Model Comparison

Comparing the two baseline approaches shows that the drift model leads to modest improvements, especially at longer forecast horizons. However, the gains remain relatively small, highlighting the inherent difficulty of predicting short-term stock price movements.

➡️ Full analysis: [`01_eda_and_naive_baseline.ipynb`](01_eda_and_naive_baseline.ipynb)

## ARIMA Time-Series Model

The ARIMA (AutoRegressive Integrated Moving Average) model is implemented as a classical time-series forecasting approach for predicting the short-term closing price of NVIDIA (NVDA). Model parameters are evaluated using information criteria and forecast accuracy metrics to determine an appropriate ARIMA specification.

Stock prices are typically non-stationary, meaning their mean and variance change over time. To satisfy the stationarity requirement for the ARIMA models, the NVDA price series is transformed using first differencing. First differencing removes the long-term trend by modeling day-to-day price changes rather than price levels. The transformed series fluctuates around zero, indicating that the underlying trend has been removed, and that the series is suitable for ARIMA modeling.

<img src="assets/arima_first_dif.jpg" alt="arima_first_difference" width='1000'>

ARIMA Time-Series Forecasting Model Performance

<img src="assets/arima_results.jpg" alt="arima_results.jpg" width='500'>

The ARIMA model captures the general trend of the series but produces larger forecast errors compared to simpler baseline models.

##### 30-Day Forecast Chart

The fitted ARIMA model was used to generate a 30-day forecast of NVDA closing prices.

<img src="assets/arima_next30Day_nvda_forecast.jpg" alt="arima next30Day nvda forecast.jpg" width='1000'>


<img src="assets/arima_next30Day_nvda_forecast_zoom.jpg" alt="arima next 30 Day nvda forecast zoom.jpg" width='600'>


The forecast includes a 95% confidence interval that widens over time, reflecting increasing uncertainty as the forecast horizon grows.


