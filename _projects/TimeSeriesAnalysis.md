---
name: Forecasting Using Time Series Analysis 
tools: [statsmodel, yfinance]
image: /assets/timeseries.png
description: Predict market trends using statistical tests and time series analysis.
# external_url: https://www.google.com
---
# Forecasting Using Time Series Analysis 
<p class="text-center">
{% include elements/button.html link="https://github.com/DebDDash/Time_Series_Analysis_Teams" text="Github" style="primary" size="sm" %}
</p>

## Description
This project focuses on the preprocessing and analysis of Apple Inc.’s historical stock price data, primarily the adjusted closing prices. The goal is to prepare the time series for future forecasting by performing decomposition, checking for stationarity, and applying transformations to stabilize the data. The analysis includes trend-seasonality decomposition using both classical and statistical filtering techniques, and stationarity testing using standard statistical tests.

## Dataset
The dataset consists of daily Adjusted Close Prices for Apple Inc. (Ticker: AAPL), sourced from Yahoo Finance using the yfinance Python library. The data spans from 1980 to 2023. The series includes all trading days and reflects corporate actions such as stock splits and dividends. Initial exploratory analysis identified and handled missing values, removed outliers using z-score thresholding, and isolated trends and residual components for further modeling.

## Preprocessing and Decomposition Strategy
The dataset was subjected to several transformation steps to prepare it for modeling:
- Missing Values: Filled using linear interpolation.
- Outliers: Removed using z-score method (threshold = 3).
- Additive Decomposition: Applied using statsmodels to separate the time series into trend, seasonal, and residual components.
- HP Filter Decomposition: The Hodrick-Prescott filter was used to extract the cyclical and trend elements for economic relevance.

## Stationarity Testing
The raw time series was non-stationary as confirmed by two key tests:
- ADF Test: Failed to reject the null hypothesis of a unit root (p ≈ 0.995).
- KPSS Test: Test statistic exceeded critical value, further confirming non-stationarity.

The decomposition residuals also exhibited insufficient variability for a conclusive ADF test. Therefore, the series was transformed using:
- Log Transformation: To stabilize variance.
- Differencing: To eliminate trend and achieve stationarity

