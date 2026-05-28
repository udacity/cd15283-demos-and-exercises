Solution: Running Time-Series Diagnostics in Python

Before we put any model into production we need to know whether its errors are random or whether they still contain predictable structure. Residuals that are not random mean the model is missing something. Residuals that are not normal mean the confidence intervals are not trustworthy. Diagnostics separate models that look good on paper from models that are actually reliable.

We fit ARIMA(2,1,1) and SARIMAX(1,1,1)(1,1,1,12) with temperature on the same electricity demand data. Both converge and both produce forecasts. That is where most people stop. We keep going.

For each model we pull the residuals and look at three things. The Ljung-Box test at lag 12 checks whether any autocorrelation remains in the first twelve lags. A p-value above 0.05 means the residuals are consistent with white noise. Below means the model left structure on the table. The normality test checks whether the residuals follow a normal distribution. If they do not, the 95 percent prediction interval is not actually 95 percent. It is still useful but the stated confidence level is approximate. AIC and BIC tell us whether the extra parameters in SARIMAX are paying for themselves.

ARIMA fails the Ljung-Box test because the annual cycle is still sitting in the residuals. The model has no seasonal component, so the summer and winter peaks remain as predictable structure that could have been captured. SARIMAX passes because the seasonal terms absorbed that cycle. SARIMAX also wins on AIC and BIC, confirming the extra complexity was worth it.

The residual ACF plot makes the same point visually. ARIMA has a spike at lag twelve that sticks out past the confidence band. That spike is the missed annual cycle. SARIMAX has no such spike. The plot is what you show a stakeholder who wants to understand why you chose the more complex model.
