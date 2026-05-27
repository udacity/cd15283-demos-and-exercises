Zero-Shot Forecasting with a Foundation Model

Chronos-2 was pretrained on millions of time series. It's never seen this subscriber data but it recognizes S-curve growth from its training. No fit call needed.

Load the same data. Split the same way. Load Chronos-2 bolt-small and call predict with 100 samples for uncertainty estimation. That's it. No parameter selection, no training, no waiting. If Chronos-2 isn't installed, fall back to ARIMA so the exercise still runs.

Fit ARIMA as a baseline. Plot both. Chronos-2 should capture the nonlinear growth shape while ARIMA projects a straight line.

Run a backtest on ARIMA using historical_forecasts. This slides the training window forward and generates forecasts at multiple points in history, giving MAE, RMSE, and MAPE across many windows. A single forecast can be lucky or unlucky. Backtesting averages that out.

Foundation models change the workflow. Instead of model selection and training, you spend zero time. The question is whether that general knowledge is good enough for your specific data. For short series with limited history, the foundation model often wins. For long well-behaved series, a tuned ARIMA or N-BEATS might still be better.
