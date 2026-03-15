# Exercise 3: Classical Time-Series Models

## Context

You work for a regional electric utility. Monthly demand forecasting drives generation scheduling — errors cost real money. You have eight years of monthly demand data plus temperatures.

## Exercise

Open `starter/starter.ipynb` and implement six modeling functions:

1. **`fit_arima`** — ARIMA(2,1,1) via statsmodels
2. **`fit_sarimax`** — SARIMAX(1,1,1)(1,1,1,12) with temperature
3. **`forecast_with_intervals`** — generate forecasts with 95% prediction intervals
4. **`run_residual_diagnostics`** — AIC, Ljung-Box, and normality tests
5. **`fit_prophet`** — Prophet with temperature regressor
6. **`fit_darts_arima`** — ARIMA via the Darts framework

## Data

- `data/electricity_demand.csv` — monthly demand (MWh) and temperature (F), January 2017 through December 2024

## Solution

See `solution/solution.ipynb` for a complete working implementation.
