Demo: Representing Time-Series Data in pandas

We've got three years of daily bike-share ride counts. Before we can forecast anything, we need to get the data into a shape pandas can work with. That means parsing dates and setting a proper time index.

First, let's load the CSV without telling pandas about the dates. See what happens -- the date column comes in as a string. The index is just row numbers. pandas has no idea this is time-series data.

Now we fix it. We pass `parse_dates=["date"]` when loading, then set that column as the index. The index type changes from RangeIndex to DatetimeIndex. That one change unlocks everything -- resampling, time-based slicing, frequency detection.

Next we check for gaps. Three years of daily data should give us about 1,096 rows. We build a complete date range with `pd.date_range` and use `.difference()` to find what's missing. There are a few gaps and some duplicates. You'd never catch this from summary statistics alone.

Then we resample. `.resample("W").sum()` aggregates daily rides into weekly totals. `.resample("MS").sum()` gives us monthly. When you plot all three side by side, the tradeoff is clear -- daily is noisy, weekly is cleaner, monthly shows the seasonal pattern. Rides peak in summer, drop in winter. That shape is what forecasting models will try to capture.

The takeaway: getting the time index right is always step one. Everything else depends on it.
