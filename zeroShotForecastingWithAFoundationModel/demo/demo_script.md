Demo: Zero-Shot Forecasting with a Foundation Model

Chronos-2 was pretrained on millions of time series. It has never seen our subscriber data but it recognizes patterns like S-curve growth from its training. No fit() call is needed.

We load the same subscriber data and split the same way. Then we load Chronos-2, the small bolt variant, and call predict with one hundred samples for uncertainty estimation. That is it. No parameter selection, no training, no waiting. If Chronos-2 is not installed we fall back to ARIMA so the demo still runs.

We fit ARIMA as a baseline and plot both forecasts. Chronos-2 should capture the nonlinear growth shape while ARIMA projects a straight line.

Then we run a backtest on ARIMA using Darts' historical_forecasts, which slides the training window forward and generates forecasts at multiple points in history, giving us MAE, RMSE, and MAPE across many evaluation windows. A single forecast can be lucky or unlucky and backtesting averages that out.

Foundation models change the workflow because instead of spending time on model selection and training you spend zero time and the model already knows general patterns. The question becomes whether that general knowledge is good enough for your specific data. For short series where training data is limited the foundation model often wins. For long, well-behaved series a tuned ARIMA or N-BEATS might still be better.
