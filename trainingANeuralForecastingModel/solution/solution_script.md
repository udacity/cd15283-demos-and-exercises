Solution: Training a Neural Forecasting Model

The exercise gives you monthly subscriber data for a streaming service and asks you to compare two N-BEATS window configurations. This is a hyperparameter decision problem: does giving the model more history improve the forecast, or does it just add noise?

Load subscribers.csv, parse the date column, set it as the index, and convert to a monthly frequency. Create a Darts TimeSeries from the subscribers column. Split at the end of 2023—everything before is training, everything after is the test holdout.

Train two N-BEATS models. The short-window model uses input_chunk_length=12—one year of history—and output_chunk_length=6—six months ahead. The long-window model uses input_chunk_length=36—three years of history—and output_chunk_length=12—twelve months ahead. Both use QuantileRegression with quantiles [0.05, 0.25, 0.5, 0.75, 0.95] so they predict a distribution at each step, not a single number. The 0.5 quantile is the median forecast. The 0.05 and 0.95 quantiles form a 90 percent prediction interval. Set random_state=42 and n_epochs=50 for both.

Generate forecasts with num_samples=100 for both models. Extract the median prediction for each and compute RMSE against actuals. The comparison tells you whether more history helps or hurts. For subscriber data with S-curve growth, the long window usually wins because the model needs to see the entire curve to predict the inflection point correctly.

The plot shows train, test, and both forecasts with their quantile bands. The short-window forecast may overshoot or undershoot the inflection because it has only seen the most recent year. The long-window forecast follows the S-curve because it learned the nonlinear pattern from three years of data. The difference in shape is the whole point of tuning chunk lengths.
