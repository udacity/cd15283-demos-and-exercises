Prophet as an Auto-Tuned Classical Model

Prophet does the opposite of ARIMA. Instead of specifying AR and MA orders, you hand it the data and it decomposes the forecast into trend, seasonality, and regressors automatically. Less control. Sensible defaults.

Prophet wants ds and y columns, not a DatetimeIndex. Regressors go in their own columns. Add temperature.

Fit with yearly seasonality on, weekly and daily off because this is monthly data. One call to fit and it's done.

The component plot is the most useful output. Trend shows the long-run direction. Yearly seasonality shows the annual cycle. Temperature effect shows demand response independently of seasonality. You get this without touching a single parameter.

Compare to ARIMA visually. ARIMA projects a flat line without a seasonal component. Prophet captures the summer and winter peaks.

The tradeoff is real. With ARIMA you control every parameter, run Ljung-Box, check normality, compare AIC. With Prophet you get nice component plots and less insight into the math. For a quick business forecast Prophet is often the right choice. When you need to justify every decision to a regulator or risk committee, ARIMA gives you more to work with.
