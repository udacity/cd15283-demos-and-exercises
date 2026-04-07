# Exercise 1.4: Forecasting with BI Tools

Same bakery data, but now you're using Tableau instead of formulas. Tableau's built-in forecasting uses exponential smoothing (ETS) under the hood — it automatically detects trend and seasonality without you specifying anything.

## Data

Use the same `data/bakery_sales.csv` from the previous exercise.

## Tasks

1. **Connect to the data.** Open Tableau and connect to `bakery_sales.csv` as a text file.

2. **Create a line chart.** Drag `Date` to Columns (set to exact date / day level) and `Loaves Sold` to Rows. You should see 731 days of daily sales.

3. **Add a forecast.** Right-click on the chart area, go to Forecast, and click Show Forecast. Tableau will project sales forward automatically.

4. **Read the forecast description.** Right-click again, go to Forecast, and click Describe Forecast. Read the description panel that appears.

5. **Answer these questions:**
   - What trend did Tableau detect?
   - What seasonal period did it find?
   - How does this forecast compare to your spreadsheet forecasts from Exercise 1.2 — does it capture the weekly pattern?
