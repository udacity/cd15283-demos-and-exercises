# Exercise 1.2: Forecasting in Spreadsheets

A bakery owner hands you a spreadsheet of daily bread sales and says "how much should I bake next week?" You're going to build three simple forecasts using only spreadsheet functions — no Python, no fancy models.

## Data

Import `data/bakery_sales.csv` into Google Sheets. You'll see two columns: `date` and `loaves_sold`, covering 731 days (Jan 2023 through Dec 2024).

## Tasks

### 1. Naive Forecast

In a new column, use the last day's sales as the forecast for every day of the next 2 weeks. Just reference the last cell — that's it. Whatever the bakery sold on the last day in the dataset, assume they'll sell exactly that much every day going forward.

### 2. Moving Average

Use `AVERAGE()` on the last 7 days to get a 7-day moving average. Then do the same for the last 30 days. Put both as flat-line forecasts for the next 2 weeks.

Which window feels more useful? Why?

### 3. Trend Line

Use `TREND()` to fit a straight line through all 731 days, then extend it 14 days forward. Does the bakery appear to be growing?

## Putting It Together

After building all three, make a line chart showing:
- Actual sales (last 90 days)
- Your three forecasts (naive, 7-day MA, 30-day MA, trend) projected 14 days forward

Look at the chart and answer this: **can any of these methods tell you whether to bake more on Saturdays?**
