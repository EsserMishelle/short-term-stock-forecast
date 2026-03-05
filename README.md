# Predicting NVDA Stock Prices: 
## A Comparison of Baseline, Time-Series, and Machine Learning Models

### Overview and Analysis Objective
The objective of this project is to forecast the short-term closing price of NVIDIA (NVDA) stock and evaluate the predictive performance of multiple modeling approaches across different forecast horizons. The study compares baseline models, classical time-series methods, and machine learning models to assess how forecast accuracy changes from short horizons (1–5 days) to longer horizons (up to 30 days).

### Table of Contents 
- [01_naive_baseline](#eda_and_naive_baseline)
02_arima_model.ipynb
03_prophet_model.ipynb
04_price_based_models.ipynb
05_return_based_models.ipynb
06_model_comparison.ipynb

### Data Description
This project uses historical market data for NVIDIA (NVDA) along with selected market indicators to construct forecasting models. The dataset includes daily stock prices and trading volumes covering the period 2021–2026. The data is obtained from Yahoo Finance / yfinance.

data/
results/
README.md
