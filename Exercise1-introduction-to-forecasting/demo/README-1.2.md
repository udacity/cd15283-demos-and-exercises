# Demo 1.2: Forecasting in Spreadsheets

## Context

We're using a bakery's daily sales data (731 days, Jan 2023 - Dec 2024) to show what spreadsheet forecasting can and can't do.

The point isn't that spreadsheets are bad — for a bakery owner who needs a quick answer, `AVERAGE` and `TREND` are genuinely useful. The limitation is that they can't capture patterns like day-of-week effects. All three methods (naive, moving average, trend) produce flat or straight-line forecasts that treat every day the same.

## Demo Flow

1. Open `data/bakery_sales.csv` in Google Sheets
2. Build a naive forecast (reference last cell)
3. Build 7-day and 30-day moving averages
4. Build a TREND forecast extending 14 days
5. Chart actual sales (last 90 days) alongside all three forecasts
6. Show that none of the forecasts capture the weekly pattern visible in the actuals

See `demo_script-1.2.md` for the talk track.
