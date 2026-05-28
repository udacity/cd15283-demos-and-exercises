Solution: Prophet as an Auto-Tuned Classical Model

Prophet takes a different approach from ARIMA. Instead of specifying orders manually you give it the data and it decomposes the forecast into trend, seasonality, and regressors automatically. The question is whether that convenience comes at a cost in accuracy.

We load the electricity demand data and split at the end of 2023. Prophet wants a DataFrame with columns named ds and y, not a DatetimeIndex, so we reset the index and rename. We keep avg_temp_f as a separate column because temperature drives some of the summer and winter spikes independently of the seasonal cycle.

We instantiate Prophet with yearly seasonality on and weekly and daily off because this is monthly data. We add temperature as a regressor. One call to fit and the model is trained. The component plot breaks the forecast into pieces: trend shows the long-run direction, yearly seasonality shows the annual cycle, and the temperature effect shows how demand responds to temperature after seasonality is already accounted for. Those three plots are what stakeholders ask for when they want to understand what is driving the forecast.

We build a future DataFrame covering the test period and merge the actual temperatures. In production you would use weather forecasts but here we have the real values, so the comparison is fair. We predict and extract the last twelve rows. MAE and MAPE against actual test demand tell us how well the auto-tuned model performs.

The forecast plot overlays Prophet against actuals. Prophet captures the seasonal peaks automatically because it decomposes the series rather than requiring you to specify seasonal orders. Whether it beats the manual SARIMAX specification from the previous exercise is the point of the comparison.
