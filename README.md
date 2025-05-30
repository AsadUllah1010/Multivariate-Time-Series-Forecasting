# Multivariate-Time-Series-Forecasting
Multivariate Time Series Forecasting involves predicting future values of multiple time-dependent variables using historical data. Unlike univariate time series forecasting, which predicts a single variable (e.g., sales over time), multivariate forecasting considers several variables simultaneously. 
# Introduction
Multivariate Time Series Forecasting is preferable when the variables may have dependencies or interactions with one another. The goal is to capture these interdependencies to make accurate predictions for each variable over a future time period. Below is the process we can follow for the task of Multivariate Time Series Forecasting:
1. Determine which variables are relevant to the forecast. Besides the target variable you want to predict, identify other variables that might influence it.
2. Collect historical data for all variables identified. This data should cover a sufficient time period to capture seasonal patterns, trends, and any cyclical behaviour.
3. Handle missing values, outliers, and anomalies in the data. It might involve imputation, data smoothing, or anomaly detection techniques.
4. Use plots and charts to understand relationships between variables, identify trends, and detect seasonality or cyclic patterns.
5. Select and use forecasting models suitable for multivariate time series data. Options include Vector Auto Regression (VAR), State Space Models (like Kalman Filters), and machine learning approaches such as LSTM (Long Short-Term Memory) networks.
<br>
<br>
Next, I will perform the following tasks for Data Preparation:
1. Check for missing values in the dataset.
2. Convert the Date column to a datetime type for time series analysis.
3. Check how many unique stocks (Tickers) are present and their respective data points.
4. Resample the data to a consistent time frequency if necessary (e.g., daily, weekly), based on the data’s current granularity and the forecasting goals.
<br>
<br>
The dataset covers the time range from February 7, 2023, to May 5, 2023, which is approximately 3 months. Given this relatively short time frame, we’ll focus on visualizing the closing price trends to understand the data better.

# Features
The dataset consists of the following columns:
1. Ticker: The stock symbol.
2. Date: The date of the trading session.
3. Open: The opening price of the stock for the trading session.
4. High: The highest price of the stock during the trading session.
5. Low: The lowest price of the stock during the trading session.
6. Close: The closing price of the stock for the trading session.
7. Adj Close: The adjusted closing price of the stock (adjusted for things like dividends and stock splits).
8. Volume: The number of shares traded during the trading session.

# Conclusion
Moving on to model selection for forecasting, given the multivariate nature of our data, a Vector AutoRegression (VAR) model could be a suitable choice. VAR models can capture the linear interdependencies among multiple time series, which makes them a good fit for forecasting the prices of several stocks simultaneously. Before we proceed with VAR modelling, it’s important to ensure that the time series data for each stock is stationary, as VAR models require stationarity. Stationarity means the statistical properties of the series (mean, variance) do not change over time. Let’s perform the following steps:
1. Use the Augmented Dickey-Fuller (ADF) test for each stock’s closing price.
2. Depending on the ADF test results, we may need to transform the data (e.g., by differencing) to achieve stationarity.
3. Train the VAR model and forecast the future values.
<br>
<br>
The Augmented Dickey-Fuller (ADF) test results for each stock’s closing price indicate:
<br.
1. AAPL: The p-value is 0.927, suggesting we failed to reject the null hypothesis, and the series is non-stationary.
<br>
2. MSFT: With a p-value of 0.944, this series is also non-stationary.
<br>
3. NFLX: The p-value is 0.225, indicating non-stationarity.
<br>
4. GOOG: The p-value is 0.567, again indicating non-stationarity.
<br>
<br>
After differencing the closing prices, the Augmented Dickey-Fuller (ADF) test results for each differenced series are:
<br>
1. AAPL – Differenced: The p-value is significantly less than 0.05, indicating that we can reject the null hypothesis. The series is stationary.
<br>
2. MSFT – Differenced: Similarly, the p-value is significantly low, confirming stationarity.
<br>
3. NFLX – Differenced: With a very low p-value, this series is also stationary.
<br>
4. GOOG – Differenced: This series is stationary as well, indicated by a very low p-value.
<br>
<br>
So, this is how you can perform Multivariate Time Series Forecasting using Python. Multivariate Time Series Forecasting is preferable when the variables may have dependencies or interactions with one another. The goal is to capture these interdependencies to make accurate predictions for each variable over a future time period.

# Contributing
If you are interested in contributing to the project, please create a fork of the repository and submit a pull request. All contributions are welcome and appreciated.
