Demo: Running Time-Series Diagnostics

Fitting a model is half the job. The other half is checking whether it actually captured the signal. If the residuals still have patterns, your forecasts can't be trusted.

We start with two pre-fitted models -- ARIMA and SARIMAX from the previous module. First we plot the residuals. Good residuals look like random noise around zero. Bad residuals have visible trends or repeating patterns.

Next, the ACF of residuals. If there's still autocorrelation, the model left predictable structure in the data. You'll see spikes above the confidence band if the model missed something.

Then the Ljung-Box test. This is the formal version of what the ACF shows visually. It returns a p-value -- above 0.05 means the residuals are consistent with white noise. Below 0.05 means there's still structure the model didn't capture.

We also check normality. This matters for prediction intervals -- if the residuals aren't normal, the 95% interval isn't actually 95%. The model's still useful, but the confidence level is approximate.

Finally, we compare AIC and BIC. Lower is better. SARIMAX usually wins because temperature genuinely explains variance in electricity demand. But you shouldn't just pick the model with the lowest AIC -- the diagnostics tell you whether either model is actually trustworthy.
