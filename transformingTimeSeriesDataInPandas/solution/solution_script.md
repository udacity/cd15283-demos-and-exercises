Solution: Transforming Time-Series Data in pandas

We have two series that look very different on the surface and we need to know which one is ready for ARIMA and which one needs transformation first. That is a judgment call, not a mechanical recipe.

The bike-share rides have a clear seasonal wave—high in summer, low in winter—which means the mean is drifting over time. That is the classic signature of a non-stationary series. The temperatures also move up and down, but they oscillate around a fixed level with no long-term drift. One needs differencing. The other does not.

We start by computing rolling statistics for both. A 30-day rolling mean on bike rides traces the seasonal wave. The rolling standard deviation stays flat, which tells us the variability itself is stable. A drifting mean with stable variance points to differencing, not a log transform. For temperatures the rolling mean is flat from the start.

We confirm the intuition with the Augmented Dickey-Fuller test. The bike rides return a p-value above 0.05, confirming non-stationary. We apply first differencing with diff().dropna() which replaces each value with the change from the previous day. What was "4,200 rides today" becomes "+150 rides compared to yesterday." That removes the level and the seasonal trend together. ADF on the differenced series now returns a p-value below 0.05. The temperatures pass ADF on the raw series, so we leave them alone.

The plot overlays the original bike rides with its rolling mean and a one-standard-deviation band, and below it the differenced series with a zero line. The original has the wave. The differenced version is flat around zero. That visual is what you show a stakeholder who asks why you changed the data before modeling.
