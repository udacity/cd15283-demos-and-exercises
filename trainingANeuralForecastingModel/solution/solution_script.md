Solution: Training a Neural Forecasting Model

Subscriber growth for a streaming service follows an S-curve: explosive early growth that decelerates as the market saturates. ARIMA cannot bend, so it projects a straight line. N-BEATS can learn nonlinear shapes. The question is how much history the model needs to learn that shape correctly.

We load the subscriber data and split at the end of 2023. We train two N-BEATS configurations. The short window sees twelve months of history and predicts six months ahead. The long window sees thirty-six months and predicts twelve ahead. Both use quantile regression so they output a distribution at each step, not a single number. The 0.5 quantile is the median forecast. The 0.05 and 0.95 quantiles form a 90 percent prediction interval.

The short window has only seen the most recent year of the curve. It may overshoot or undershoot the inflection because it has not seen the full S-shape. The long window has seen three years including the early explosive phase and the current deceleration. It learns the inflection point from the data itself.

We compare RMSE on the test set. For S-curve data the long window usually wins because the model needs to see the entire arc to predict where it is heading. But the comparison itself is the lesson: more history is not always better. For noisy series a shorter window can avoid overfitting to old patterns that no longer apply.

The plot shows train, test, and both forecasts with their quantile bands. The short-window forecast may flatten or spike where the long window follows the curve smoothly. The difference in shape is the return on choosing the right window length.
