Representing Time-Series Data in pandas

You've got daily bike-share counts but pandas doesn't know the date column is a date. It's just a string, and the index is row numbers. Fix that first.

Use parse_dates and set_index to get a DatetimeIndex. That unlocks everything else: resampling, time-based slicing, frequency detection.

Three years of daily data should be about 1,096 rows. Build a complete date range and diff it against your actual index to find gaps. Duplicates won't show up in summary stats. Only the index catches them.

Resample to weekly and monthly. Plot all three. Daily is noisy, weekly is smoother, monthly shows the seasonal shape. That's the point of getting the time index right first.
