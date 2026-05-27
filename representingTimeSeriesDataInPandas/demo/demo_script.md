Demo: Representing Time-Series Data in pandas

In this demonstration, we are investigating how to represent time-series data in python using the pandas library. For this, we have three years of daily bike-share ride counts. 

Before we can do anything useful with this data. like forecasting, modeling or decomposing, we need to ensure the data is set up with the correct time index. pandas has great support for datetime types but it will not do the work for you. You have to tell it which column is a date and set it as your index.

We load the CSV and see what we get by default. The date column is an object which is just a string and the index is a boring RangeIndex. pandas does not know this is time-series data. We fix both at once by passing parse_dates=["date"] and setting that column as the index which changes the index type to DatetimeIndex and unlocks resampling, time-based slicing, and frequency detection.

Three years of daily data should be about 1,096 rows but as you can see our numbers differ slightly. To diagnose what might be causing this discrepancy, we can build a complete date range with pd.date_range and use .difference() to find what is missing. We can also check for duplicate index values. In this dataset we are missing 5 days but have 3 duplicate dates, so the math is 1,096 − 5 + 3 = 1,094. You would only catch this by checking the index because summary statistics will not help.

Then we resample. .resample("W").sum() aggregates daily rides into weekly totals and .resample("MS").sum() gives us monthly. When you plot all three side by side the tradeoff is clear. Daily is noisy, weekly is cleaner, and monthly shows the seasonal pattern with rides peaking in summer and dropping in winter.

Getting the time index right is always step one because everything else depends on it.
