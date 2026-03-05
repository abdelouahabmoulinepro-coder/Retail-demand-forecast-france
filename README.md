📊 Forecasting Retail Demand in France
Time Series Analysis & Baseline Forecasting
🧭 Project Overview

This project analyzes and forecasts the French retail trade volume index using official data from INSEE.

The objective is to understand the structure of the time series and evaluate several baseline forecasting models before introducing more advanced approaches.

This first phase focuses on:

Exploratory data analysis

Time series decomposition

Stationarity testing

Baseline forecasting models

Forecast evaluation

The goal is to determine how predictable the system is using historical data alone.

📂 Dataset

Source: INSEE – Monthly Business Climate Indicators

Indicator used:

Retail trade volume index – Non-store retail (France)

Dataset characteristics:

Feature	Value
Frequency	Monthly
Period	2005 – 2023
Observations	228
Country	France

This long time horizon allows the identification of:

long-term structural trends

seasonal consumption patterns

macroeconomic shocks (e.g., COVID-19)

📈 Exploratory Data Analysis

After cleaning the dataset, the time series was visualized to identify structural patterns.

Retail Volume Index (Monthly)

Key observations

Strong long-term upward trend

Significant disruption during COVID-19

Stabilization after 2022

The increase reflects the structural growth of non-store retail (e-commerce).

📊 Year-Over-Year Growth Analysis

To better understand volatility, the year-over-year growth rate was computed.

Findings

Extreme volatility during 2020–2021

Rapid rebound after lockdowns

Normalization of growth after 2022

This confirms a temporary regime change during the pandemic.

🔎 Time Series Decomposition

The series was decomposed into its main components:

𝐷
𝑎
𝑡
𝑎
=
𝑇
𝑟
𝑒
𝑛
𝑑
+
𝑆
𝑒
𝑎
𝑠
𝑜
𝑛
𝑎
𝑙
𝑖
𝑡
𝑦
+
𝑅
𝑒
𝑠
𝑖
𝑑
𝑢
𝑎
𝑙

Data=Trend+Seasonality+Residual

Trend

Long-term upward trajectory

Structural level shift during COVID

Seasonality

Stable yearly pattern

Typical retail demand cycles

Residual

Mostly random fluctuations

Large shocks during exceptional events

⚙️ Stationarity Analysis

Time series models such as ARIMA require stationary data.

The Augmented Dickey-Fuller test was applied.

Raw series
p-value ≈ 0.97

The series is non-stationary.

First Difference Transformation
Δ
𝑋
𝑡
=
𝑋
𝑡
−
𝑋
𝑡
−
1
ΔX
t	
=X
t	​
−X
t−1
	​


After differencing:

p-value ≈ 0.0001

The series becomes stationary, meaning one order of differencing is sufficient:

d = 1
🔮 Forecasting Baseline Models

To evaluate forecasting performance, the dataset was split into:

Dataset	Period
Training	2005 – 2022
Test	2023

The following baseline models were evaluated.

1️⃣ Naïve Forecast
𝐹
𝑜
𝑟
𝑒
𝑐
𝑎
𝑠
𝑡
𝑡
+
1
=
𝑉
𝑎
𝑙
𝑢
𝑒
𝑡
Forecast
t+1
	​

=Value
t
	​


Prediction equals the last observed value.

Performance
MAE = 1.48
2️⃣ Seasonal Naïve Forecast
𝐹
𝑜
𝑟
𝑒
𝑐
𝑎
𝑠
𝑡
𝑡
=
𝑉
𝑎
𝑙
𝑢
𝑒
𝑡
−
12
Forecast
t
	​

=Value
t−12
	​


Each month is predicted using the same month from the previous year.

Performance
MAE = 4.34

This model performed poorly due to the strong upward trend.

3️⃣ Moving Average Forecast (MA3)

A rolling 3-month moving average was used to smooth short-term fluctuations.

Performance
MAE = 2.27

The moving average introduced lag relative to the trend.

4️⃣ Holt Trend Model

Holt’s exponential smoothing captures level + trend.

Performance
MAE = 2.38

Although it models the trend explicitly, it did not outperform the naïve forecast.

5️⃣ ARIMA Model

After achieving stationarity, an ARIMA(1,1,1) model was fitted.

Performance
MAE = 1.65

Residual diagnostics confirmed that the remaining errors behave like white noise.

📉 Forecast Comparison

Model	MAE
Naïve	1.48
ARIMA(1,1,1)	1.65
Moving Average	2.27
Holt Trend	2.38
Seasonal Naïve	4.34
💡 Key Insight

The naïve forecast outperformed all other models.

This suggests that the series behaves similarly to a random walk with drift, where the most recent observation provides the best short-term prediction.

This behavior is common in macroeconomic indicators.

🧠 Conclusion

This first phase established a complete time-series forecasting workflow:

data cleaning

exploratory analysis

stationarity testing

baseline model comparison

forecast evaluation

The results indicate that historical values alone contain limited predictive power.

🚀 Next Step — Model Upgrade

To improve forecasting performance, the next phase of the project will incorporate external economic drivers, including:

consumer confidence indicators

inflation measures

macroeconomic signals

Using these variables, a SARIMAX model (ARIMA with exogenous variables) will be implemented.

This will allow the model to capture causal relationships influencing retail demand rather than relying solely on past values.

🛠️ Tools & Libraries

Python libraries used:

pandas
numpy
matplotlib
statsmodels
scikit-learn
📌 Project Status

✅ Phase 1 – Exploratory analysis & baseline models
⬜ Phase 2 – SARIMAX with exogenous variables
⬜ Phase 3 – Forecast dashboard / visualization


