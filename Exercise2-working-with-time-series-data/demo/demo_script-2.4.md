Demo: Transforming Time-Series Data in pandas

Most forecasting models assume the data is stationary -- the statistical properties don't change over time. Real data almost never starts that way. So we need tools to check and fix it.

We start with the cleaned bike-share data. First thing we do is compute rolling statistics -- a 30-day rolling mean and rolling standard deviation. The rolling mean shows a clear seasonal wave, high in summer, low in winter. That's a dead giveaway that the series isn't stationary. The mean is changing over time.

Eyeballing is useful but not rigorous. The Augmented Dickey-Fuller test gives us a number. It returns a p-value -- below 0.05 means stationary, above 0.05 means not. We run it and confirm what the plot told us.

The fix is differencing. `.diff()` replaces each value with the change from the previous day. Instead of "4,200 rides today" it becomes "+150 rides compared to yesterday." This removes the level and usually removes the trend. We run ADF again on the differenced series and now it passes.

When you plot both side by side, the difference is obvious. The original has that seasonal wave. The differenced version oscillates around zero with no visible trend. This is what ARIMA-style models work with internally -- understanding this transformation is the point.

Last thing: train/test splits for time series are always chronological. Never random. You hold out the last chunk as your test set because that's how forecasting works in practice -- you're always predicting the future from the past.
