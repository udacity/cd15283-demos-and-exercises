Demo: Training a Neural Forecasting Model

We have monthly subscriber data for a streaming service. The growth follows an S-curve -- explosive early growth that's now decelerating. There's a COVID bump and a price-hike dip baked in. ARIMA assumes linear dynamics, so it can't capture any of this. N-BEATS can.

First we load the data and plot it. The S-curve shape is immediately visible. We split at end of 2023 and train N-BEATS with two years of input history, predicting 12 months ahead. The quantile regression gives us uncertainty bands -- not just a single number but a range of plausible outcomes.

Then we fit an ARIMA baseline for comparison. Same data, same split.

When you plot both forecasts against actual subscribers, the difference is obvious. ARIMA projects a straight line -- it literally can't bend. N-BEATS follows the curve because it learned the nonlinear growth pattern from the data. The uncertainty bands give you the range of outcomes, which is what you actually need for capacity planning and budgeting.

The tradeoff: ARIMA gives you interpretable coefficients and formal diagnostics. N-BEATS is a black box -- you can see that it works, but you can't explain why it chose a particular forecast shape. For this problem, the accuracy improvement is worth it. For a problem where you need to justify every modeling decision to a regulator, maybe not.
