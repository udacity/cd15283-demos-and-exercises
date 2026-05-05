Demo: Running Time-Series Diagnostics
 
Diagnosing whether a model is appropriately capturing the trend is a critical step in the time-series forecasting lifecycle. Models may seem great at explaining the observed data based on aggregate statitics but it's necessary to dive deeper, to look visually at your data and the residuals between the model predictions and the real data. If your residuals still retain some clear trend or structure, a fit with additional components may be required.

In this demo, we start by fitting both models in the setup cell, ARIMA(2,1,1) and SARIMAX(1,1,1)(1,1,1,12) with temperature, and then we look at the residuals.

First we plot them. Good residuals look like random noise scattered around zero and bad residuals have visible trends or repeating patterns.

Next the ACF of residuals. If there is still autocorrelation the model left patterns on the table and you will see spikes above the confidence band if the model missed something.

Then the Ljung-Box test which is the formal version of what the ACF shows visually. It returns a p-value where above 0.05 means the residuals are consistent with white noise and below 0.05 means there is still structure the model did not capture.

We also check normality which matters for prediction intervals because if the residuals are not normal the 95 percent interval is not actually 95 percent. The model is still useful but the confidence level is approximate.

Finally we compare AIC and BIC where lower is better. We will see whether SARIMAX wins on information criteria in this dataset and whether that lines up with what the diagnostics tell us.
