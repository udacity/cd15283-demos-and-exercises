Demo: Transforming Time-Series Data in pandas

Most forecasting models assume data is stationary which means the basic statistical properties producing the variations do not change over time. Real data almost never starts that way so we need tools to check and fix it.

We start with cleaned data for a bike-sharing service and the first thing we can try to check for stationarity is to compute rolling statistics. In particular we calculate a 30-day rolling mean and rolling standard deviation. The rolling mean shows a clear seasonal wave, high in summer and low in winter, which is a dead giveaway that the series is not stationary because the mean is changing over time. The rolling standard deviation stays roughly flat which tells you the variability itself is stable.

While eyeballing is useful as a first step it is not usually rigorous enough for justifying business decisions. We can make use of the Augmented Dickey-Fuller test which gives us a number and a p-value for determining stationarity. Below 0.05 means stationary and above 0.05 means not. We run it here and we can see that the test confirms what we intuitively thought.

In order to turn this time series into one that is stationary we employ the technique called differencing. For a pandas series we run .diff() which replaces each value with the change from the previous day. Instead of "4,200 rides today" it becomes "+150 rides compared to yesterday." This removes the level and usually removes the long-term seasonal trends. We run ADF again on the differenced series and now it passes.

When you plot both side by side the difference is obvious. The original has that seasonal wave and the differenced version oscillates around zero with no visible trend. This is what ARIMA-style models work with internally.

One other thing to keep in mind when carrying out modeling of time series is to consider how to split your data into training and test sets. In many machine learning efforts one does not necessarily need to care about the order in which you split your training and test data but for time-series data you do have to think carefully and ensure that your train-test splits are always chronological. Never random. You hold out the last chunk as your test set because that is how forecasting works in practice. You are always predicting the future from the past.
