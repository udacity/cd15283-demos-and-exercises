Training a Neural Forecasting Model

Monthly subscriber data for a streaming service. The growth follows an S-curve: explosive early growth that's now decelerating, with a COVID bump and a price-hike dip baked in. ARIMA assumes linearity so it can't capture any of this. N-BEATS can.

Load and plot. The S-curve is immediately visible. Split at end of 2023. Train N-BEATS with two years of input history predicting twelve months ahead. Quantile regression gives uncertainty bands. Not a single number. A range of plausible outcomes.

Fit an ARIMA baseline for comparison. Same data. Same split.

Plot both against actuals. ARIMA projects a straight line. It literally can't bend. N-BEATS follows the curve because it learned the nonlinear pattern from the data.

The uncertainty bands from quantile regression give you the range you need for capacity planning and budgeting. N-BEATS can't tell you why it chose that shape. No coefficients, no Ljung-Box, no AIC. If a stakeholder asks why the curve bends here, the honest answer is because the network learned it from the data. For subscriber forecasting that's fine because the shape is what matters. For a grid operator defending a forecast to a regulator it might not be enough.
