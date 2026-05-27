Time-Series Modeling with statsmodels

Eight years of monthly electricity demand plus temperature. Grid operators need twelve months ahead to plan capacity.

Split at end of 2023. Everything before is training. 2024 is the test set.

Don't just throw a model at it. Look at the autocorrelation structure first. Seasonally difference at lag 12 to strip out the annual cycle. Check ACF and PACF on what's left. The spike at lag 1 in the ACF means you need an MA(1) term. The seasonal spikes at lag 12 mean you need seasonal AR and MA.

Start with plain ARIMA(2,1,1). No seasonality, no temperature. It fits, it forecasts, but the prediction intervals are wide because the model has no idea what July demand looks like versus January. It's treating the seasonal cycle as noise.

Then SARIMAX(1,1,1)(1,1,1,12) with temperature as exogenous. The AIC drops substantially. Temperature is genuinely helping. For future temps use seasonal averages from training. In production you'd plug in actual weather forecasts.

The difference between the two forecasts is in the intervals. SARIMAX intervals are tighter because the seasonal component and temperature explain variation that ARIMA treats as uncertainty. For grid operators that's the whole point. They need to know the actual range of demand they must prepare for.
