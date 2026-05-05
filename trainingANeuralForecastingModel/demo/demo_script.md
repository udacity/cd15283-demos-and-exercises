Demo: Training a Neural Forecasting Model

We have monthly subscriber data for a streaming service and the growth follows an S-curve with explosive early growth that is now decelerating. There is a COVID bump and a price-hike dip baked in. ARIMA assumes linear dynamics so it cannot capture any of this. N-BEATS can.

First we load the data and plot it. The S-curve shape is immediately visible. We split at the end of 2023 and train N-BEATS with two years of input history, predicting twelve months ahead. The quantile regression gives us uncertainty bands, not just a single number but a range of plausible outcomes.

Then we fit an ARIMA baseline for comparison with the same data and the same split.

When you plot both forecasts against actual subscribers the difference is obvious. ARIMA projects a straight line and it literally cannot bend. N-BEATS follows the curve because it learned the nonlinear growth pattern from the data and the uncertainty bands give you the range of outcomes which is what you actually need for capacity planning and budgeting.

N-BEATS also gives you uncertainty bands from the quantile regression so you get a range of plausible outcomes rather than a single number while ARIMA in this notebook is just a point forecast. N-BEATS cannot tell you why it chose that shape. There are no coefficients to inspect, no Ljung-Box test to run, no AIC to compare. If a stakeholder asks "why does the curve bend here" the honest answer is "because the network learned it from the data." For this subscriber problem that is fine because the shape is what matters. For a grid operator who needs to defend their forecast to a regulator that might not be enough.
