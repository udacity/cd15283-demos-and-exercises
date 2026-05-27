Transforming Time-Series Data in pandas

Forecasting models assume stationarity. Real data never starts that way. You need to check and fix it.

Clean the data first. Deduplicate, fix the October 2023 unit error where hourly counts got recorded instead of daily, drop negatives, interpolate gaps.

Compute a 30-day rolling mean and standard deviation. If the rolling mean waves up and down seasonally, the mean is changing over time. That's not stationary. The rolling std staying flat tells you the variability itself is stable.

Eyeballing is a first step. Run the Augmented Dickey-Fuller test for rigor. Below 0.05 means stationary. Above means not. It will confirm what the rolling stats already showed.

Differencing fixes it. .diff() replaces each value with the day-over-day change. That removes the level and usually the trend. Run ADF again on the differenced series and it should pass.

Split train and test chronologically. Never random. You predict the future from the past, not the middle from the edges.
