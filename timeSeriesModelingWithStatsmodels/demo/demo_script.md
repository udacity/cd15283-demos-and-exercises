Demo: Fitting ARIMA and SARIMAX with statsmodels

We have eight years of monthly electricity demand for a regional utility plus average temperatures and they need to forecast twelve months ahead so grid operators can plan capacity. We will fit two models to the same dataset and see what difference the extra information makes.

First we load the data and set up a train-test split with everything through 2023 as training and 2024 as the test set. Before picking model orders we look at the autocorrelation structure by seasonally differencing first at lag 12 to remove the annual cycle then checking ACF and PACF on what is left. The spike at lag 1 in the ACF suggests an MA(1) component and the seasonal spikes at lag 12 confirm we need seasonal terms.

We start with a plain ARIMA(2,1,1) with no seasonality and no temperature. It fits and it forecasts but the prediction intervals are wide because the model cannot capture the annual cycle so it is fundamentally uncertain about what demand will look like in July versus January.

Then we fit SARIMAX(1,1,1)(1,1,1,12) with temperature as an exogenous variable. The AIC drops substantially which tells us temperature is genuinely helping the model. For the forecast we need future temperatures so we use seasonal averages from the training data though in production you would use actual weather forecasts.

When you compare the two forecasts side by side the difference is in the intervals. SARIMAX's are tighter because the seasonal component and temperature explain variation that ARIMA treats as noise. For grid operators those tighter intervals matter because they tell you the range of demand you actually need to prepare for.
