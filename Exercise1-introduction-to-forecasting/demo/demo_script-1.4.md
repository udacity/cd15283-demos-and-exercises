# Demo Script 1.4: Forecasting with BI Tools

So we just built three forecasts by hand in a spreadsheet. They were useful but flat — none of them could tell us about the Saturday bump. Now let's see what happens when we hand the same data to Tableau.

I'm going to drag Date to columns, Loaves Sold to rows, and I get my line chart. Same data, 731 days. Now I right-click on the chart and hit Show Forecast. And just like that — Tableau projects forward. But look at the shape. It's not flat. It has bumps. It has a weekly pattern. Tableau detected the 7-day cycle automatically.

If I click Describe Forecast, Tableau tells me it used an ETS model — that stands for Error, Trend, Seasonal. It found a slight upward trend, which matches our TREND() result. And it found a seasonal period of 7, which is the weekly cycle. This is what our spreadsheet methods couldn't do.

But here's the tradeoff. I didn't choose ETS. I can't see the smoothing parameters. I can't decide whether to use additive vs multiplicative seasonality. Tableau made those choices for me. For the bakery owner who just needs a number, that's fine. But if you need to understand why the forecast says what it says, or if the automatic detection gets it wrong, you're stuck.

That's why we're going to learn to build these models ourselves in Python — same core ideas, but you're in the driver's seat.
