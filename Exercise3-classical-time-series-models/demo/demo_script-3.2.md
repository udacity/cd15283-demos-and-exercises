Demo: Fitting ARIMA and SARIMAX with statsmodels

We have eight years of monthly electricity demand data plus average temperatures. The utility needs to forecast 12 months ahead so grid operators can plan capacity.

First we load the data and set up a train/test split -- everything through 2023 for training, 2024 for testing. Then we look at ACF/PACF on the seasonally differenced series. The spike at lag 1 in the ACF suggests an MA(1) component. The seasonal spikes at lag 12 confirm we need seasonal terms.

We start with a plain ARIMA(2,1,1). No seasonality, no temperature. It fits, it forecasts, but the prediction intervals are wide. The model can't capture the annual cycle so it's fundamentally uncertain about what demand will look like in July vs January.

Then we fit SARIMAX(1,1,1)(1,1,1,12) with temperature as an exogenous variable. The AIC drops substantially -- that tells us temperature is genuinely helping the model. For the forecast we need future temperatures, so we use seasonal averages from the training data. In production you'd use actual weather forecasts.

When you compare the two forecasts side by side, the difference is in the intervals. SARIMAX's are tighter because the seasonal component and temperature explain variation that ARIMA treats as noise. For grid operators, those tighter intervals are the whole point -- they tell you the range of demand you actually need to prepare for.
