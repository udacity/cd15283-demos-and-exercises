# Solution 1.2: Forecasting in Spreadsheets

## Naive Forecast

Formula: `=B732`

That's it. Just repeats the last observed value for every future day. Simple but completely flat — it misses everything. No trend, no weekly pattern, nothing. It's a baseline, not a real forecast.

## 7-Day Moving Average

Formula: `=AVERAGE(B726:B732)`

This captures a full week, so it smooths out the day-to-day noise. If Monday was weirdly low and Wednesday was weirdly high, they cancel out. The result is a single number — still a flat line going forward, but a more stable one than the naive forecast.

## 30-Day Moving Average

Formula: `=AVERAGE(B703:B732)`

Smoother still, but now you're averaging over a whole month. It's slower to react to recent changes. If sales jumped up in the last week, the 30-day average barely notices because it's diluted by 23 other days.

## Trend

Formula: `=TREND(B2:B732, A2:A732, A733:A746)`

This fits a straight line through all 731 days and projects it forward. The slope is positive — the bakery is growing at roughly 0.3 extra loaves per day. That's useful information. But the forecast is a straight line. It can't bend, and it can't capture any repeating pattern.

## The Key Limitation

None of these methods can answer "should I bake more on Saturdays?" because none of them model the weekly cycle. The naive forecast is one number. The moving averages are one number. The trend is a straight line. They all treat every day of the week the same.

That's the limitation we'll address with more sophisticated methods — decomposition and seasonal models — later in the course.
