# Exercise 4: Deep Learning and Modern Forecasting

## Context

A streaming service needs to forecast subscriber growth. The data follows an S-curve with seasonal patterns and structural breaks. Classical linear models struggle here — neural and foundation models shine.

## Exercise

Open `starter/starter.ipynb` and implement four functions:

1. **`train_nbeats`** — N-BEATS with quantile regression via Darts
2. **`run_chronos_zero_shot`** — Chronos-2 zero-shot forecast (with ARIMA fallback)
3. **`backtest_model`** — historical forecasts with MAE, RMSE, MAPE
4. **`build_comparison_table`** — formatted comparison DataFrame

## Data

- `data/subscribers.csv` — monthly active subscribers, January 2020 through December 2024

## Solution

See `solution/solution.ipynb` for a complete working implementation.
