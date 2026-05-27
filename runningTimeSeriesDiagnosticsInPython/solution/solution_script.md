Running Time-Series Diagnostics

Fitting a model is half the job. Checking whether it actually captured the signal is the other half. If the residuals still have structure, your forecasts and intervals can't be trusted.

Fit ARIMA(2,1,1) and SARIMAX(1,1,1)(1,1,1,12) with temperature on the training data. Then look at the residuals.

Plot them first. Good residuals look like random noise scattered around zero. Bad residuals have visible trends or repeating patterns that the model missed.

Check the ACF of the residuals. Spikes above the confidence band mean the model left predictable structure on the table. There's still signal in what the model called noise.

Run the Ljung-Box test for the formal version. Above 0.05 means white noise. Below means the model is incomplete.

Check normality. This matters for prediction intervals. If the residuals aren't normal, the 95% interval isn't actually 95%. The model is still useful but the confidence level is approximate. In high-stakes forecasting that approximation matters. In low-stakes directional estimates it matters less.

Compare AIC and BIC. Lower is better. SARIMAX should win here because temperature explains real variance. But don't just pick the lowest AIC. The diagnostics tell you whether either model is actually trustworthy.
