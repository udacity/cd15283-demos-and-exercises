Solution: Transforming Time-Series Data in pandas

The exercise gives you two series—bike-share rides and Melbourne temperatures—and asks which one is already stationary and which needs transformation before ARIMA. This is a decision problem, not a rote application of diff().

Load both datasets with parse_dates and set_index so each has a DatetimeIndex. For the bike rides, compute a 30-day rolling mean and standard deviation. The mean shows a clear seasonal wave that confirms the mean is changing over time. The standard deviation stays roughly flat, which tells you the variability itself is stable. That combination—drifting mean, stable variance—is the signature of a series that needs differencing, not a log transform.

Run ADF on the raw bike rides with autolag="AIC". The p-value comes out above 0.05, confirming non-stationary. Apply first differencing with diff().dropna(). What was "4,200 rides today" becomes "+150 rides compared to yesterday." Run ADF again on the differenced output. The p-value drops below 0.05, confirming stationarity.

For the Melbourne temperatures, repeat the same steps. The rolling mean is flat, and the ADF p-value on the raw series is already below 0.05. That means temperatures are stationary as-is—no differencing needed. The comparison table shows Bike Rides going from non-stationary to stationary, while Melbourne Temps stay stationary throughout.

The plot shows the original bike rides with the rolling mean and a one-standard-deviation band overlaid, and below it the differenced series with a zero line. The visual confirms what the test said: the original has a seasonal wave, the differenced version is flat around zero.
