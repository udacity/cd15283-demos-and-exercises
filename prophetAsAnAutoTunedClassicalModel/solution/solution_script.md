Solution: Prophet as an Auto-Tuned Classical Model

The exercise gives you electricity demand data and asks you to fit Prophet with a temperature regressor and evaluate the forecast against actuals. This is a practical deployment problem: can an auto-tuned model beat the manual specification you wrote in the statsmodels exercise?

Load electricity_demand.csv, parse the date column, set it as the index, and enforce monthly frequency. Split chronologically at the end of 2023. Prophet wants columns named ds and y, not a DatetimeIndex. Reset the index and rename date to ds and demand_mwh to y. Keep avg_temp_f as a separate column.

Instantiate Prophet with yearly_seasonality=True, weekly_seasonality=False, and daily_seasonality=False because this is monthly data. Add avg_temp_f as a regressor with add_regressor. Fit on the training DataFrame. Build a future DataFrame with make_future_dataframe(periods=12, freq="MS") that covers the training period plus twelve forecast months. Merge the actual temperature values for the future period from the original dataset. In production you would use weather forecasts, but here we have the real values.

Call predict on the future DataFrame and extract the last twelve rows indexed by ds. Compute MAE and MAPE against the actual test demand. The component plot shows three panels: trend, yearly seasonality, and temperature effect. The trend panel shows the long-run direction. The yearly panel shows the annual cycle shape—demand peaks in summer and winter. The temperature panel shows the independent effect of temperature after seasonality is already accounted for. These three plots are what stakeholders ask for when they want to understand what is driving the forecast.

The forecast plot overlays Prophet against actuals. Prophet captures the seasonal shape automatically rather than requiring you to specify seasonal orders manually. Compare the MAPE here to the MAPE from the SARIMAX exercise on the same data to see which model performs better.
