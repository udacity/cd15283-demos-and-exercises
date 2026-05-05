Demo: Forecasting in Spreadsheets

We have 731 days of bread sales and the bakery owner wants to know how much to bake next week, so we are going to see what we can do with just spreadsheet functions and no code at all.

The naive forecast is literally just "whatever happened yesterday, do that again." We take the last day's sales and paste that forward for two weeks. It is dead simple and dead flat and it serves as a baseline.

The moving average is better because it smooths out the randomness. We take AVERAGE of the last 7 days and if Monday was weirdly low and Wednesday was weirdly high they cancel out. The 7-day window is nice because it covers a full week. The 30-day window is smoother still but it is averaging over a whole month so it is slower to react to recent changes.

TREND actually fits a line through all 731 days and the slope is positive. The bakery is growing, roughly an extra loaf every three days. That is useful information but it is still just a line. It cannot bend and it certainly cannot tell you that Saturdays are 15 percent busier than Mondays.

All three methods give you a number. They answer "roughly how much." But none of them can answer "how much on Saturday versus Wednesday." For that you need something that understands the weekly cycle which is what we will get to with decomposition and seasonal models.
