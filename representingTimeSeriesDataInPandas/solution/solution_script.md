Solution: Representing Time-Series Data in pandas

The exercise asks whether weekend rides are consistently higher, and whether that pattern is seasonal (stronger in summer) or structural (consistent year-round). This is an analysis question, not a syntax test.

First, load the bikeshare_rides.csv, parse the date column as datetime, and set it as the index. Deduplicate any repeated dates. Then create two new columns: one for the month (as a period) and one for the day of week. Group by both and compute the average rides per day. That gives you a pivot table where rows are months and columns are days of the week.

Next, compute the weekend average (Saturday and Sunday) and the weekday average (Monday through Friday) for each month. Divide the weekend average by the weekday average. That ratio tells you how much higher weekend rides are relative to weekdays. If the ratio varies widely across months—say 1.3 in July but 1.1 in January—the effect is seasonal. If the ratio is stable around 1.2 regardless of month, the effect is structural. Return True if the standard deviation of the ratio exceeds 0.1.

The plot shows the average rides by day of week for each month on a single figure. The weekend bars stick out above the weekday bars. Whether that gap widens and narrows across months answers the question.
