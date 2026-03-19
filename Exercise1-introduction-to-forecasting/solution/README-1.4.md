# Solution 1.4: Forecasting with BI Tools

## What Tableau Produces

When you add a forecast to the daily sales line chart, Tableau fits an ETS (Error, Trend, Seasonal) model automatically. The Describe Forecast panel reveals the details:

- **Model:** ETS — additive or multiplicative (Tableau picks whichever fits best)
- **Trend:** Slight upward trend, which matches the `TREND()` result from the spreadsheet exercise
- **Seasonal period:** 7 (weekly) — this is the key difference from what we built by hand
- **Forecast shape:** The projected line shows weekly ups and downs, unlike the flat lines from AVERAGE and TREND

## Comparison to Spreadsheet Forecasts

In Exercise 1.2, we built three forecasts: naive (flat), moving average (flat), and trend (straight line). None of them could capture the Saturday bump or any day-of-week pattern.

Tableau does automatically what took us three separate spreadsheet functions — and it STILL does more than any of them could. The ETS model captures both the upward trend and the weekly seasonality in a single forecast.

## The Tradeoff

Tableau's one-click forecast is convenient, but you don't control the model. You can't see the smoothing parameters. You can't decide whether to use additive vs multiplicative seasonality — Tableau made those choices for you.

For the bakery owner who just needs a number, that's fine. But if you need to understand why the forecast says what it says, or if the automatic detection gets it wrong, you're stuck. That's why we're going to learn to build these models ourselves in Python — same core ideas, but you're in the driver's seat.
