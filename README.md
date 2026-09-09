# Electricity Demand Forecasting (Time Series Analysis)

Forecasting daily electricity demand in Victoria, Australia using time series models in R, completed as part of a graduate-level Time Series Analysis for Business course.

## Overview

This project analyses 5+ years of daily electricity demand data (Jan 2015 – Oct 2020, 2,008 training observations) to forecast a 98-day test period. Exploratory analysis reveals dual seasonality (weekly and annual cycles), a U-shaped relationship between demand and temperature, and significant holiday effects.

## Methods

Three forecasting models were built and compared:

- **STL + ETS** — seasonal-trend decomposition with exponential smoothing on the adjusted series
- **TBATS** — multiple seasonal periods modeled via Fourier terms with automatic Box-Cox transformation
- **Regression with ARIMA(2,1,3) errors** — temperature (linear + quadratic), holiday, and school-day indicators as external regressors

## Results

| Model | Test RMSE (MWh) | Test MAE (MWh) |
|:---|---:|---:|
| STL+ETS | 9,527 | 7,753 |
| **TBATS** | **8,071** | **6,660** |
| Regression + ARIMA(2,1,3) errors | 14,298 | 11,493 |

TBATS achieved the best out-of-sample accuracy and passed the Ljung-Box residual test (p = 0.575), confirming no significant remaining autocorrelation.

## Tools

R · `forecast` · `dplyr` · `lubridate` · `zoo`

## Files

- `analysis.Rmd` — full analysis: EDA, model fitting, evaluation, and R code
