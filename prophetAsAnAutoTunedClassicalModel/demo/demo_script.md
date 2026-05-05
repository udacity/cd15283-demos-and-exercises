Demo: Prophet as an Auto-Tuned Classical Model

Prophet takes a different approach from ARIMA. Instead of specifying AR and MA orders you give it the data and it decomposes the forecast into trend, seasonality, and regressors automatically. Less control but sensible defaults for most business problems.

First we prepare the data. Prophet wants a DataFrame with columns ds and y, not a DatetimeIndex, and any regressors go in their own columns. We add temperature.

We fit the model with yearly seasonality on, weekly and daily off because this is monthly data, and temperature as a regressor. One call to .fit() and it is done.

The component plot is Prophet's killer feature. It breaks the forecast into pieces. Trend shows the long-run direction, yearly seasonality shows the annual cycle, and the temperature effect shows how demand responds to temperature independently of the seasonal pattern. You get all of this for free.

When we compare to ARIMA visually Prophet captures the seasonal shape that ARIMA misses. ARIMA projects a flat line because it has no seasonal component and Prophet's forecast has the summer and winter peaks.

With ARIMA you control every parameter. You can run Ljung-Box tests, check normality, and compare AIC. With Prophet you get sensible defaults and nice component plots but less insight into the math. For a quick business forecast Prophet is often the right choice but for a situation where you need to understand and justify every modeling decision ARIMA gives you more to work with.
