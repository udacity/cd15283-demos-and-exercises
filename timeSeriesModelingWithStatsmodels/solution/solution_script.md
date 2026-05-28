Solution: Time-Series Modeling with statsmodels

The exercise gives you monthly airline passenger data and asks whether adding a seasonal component is worth the extra complexity. This is a model selection problem, not a parameter-tuning drill.

Load airline_passengers.csv, parse the date column, set it as the index, and enforce monthly frequency. Split chronologically: hold out the last twelve months as test. Fit ARIMA(2,1,1) with no seasonal or exogenous components. This model has no idea that demand peaks in summer, so it treats the seasonal cycle as noise. Call get_forecast(steps=12) and extract predicted_mean and conf_int().

Next, fit SARIMAX(1,1,1)(1,1,1,12). The seasonal_order tells the model to look twelve months back for repeating patterns. Generate the same twelve-month forecast. Extract the prediction intervals for both models. Compare the average interval width: ARIMA produces wide intervals because it has no seasonal component. SARIMAX produces tighter intervals because the seasonal terms explain variation that ARIMA treated as uncertainty.

Build a comparison table with AIC, BIC, and average interval width for both models. For the airline data, SARIMAX wins on all three metrics. The better model is the one with lower AIC. The plot shows the two forecasts side by side against train and test. The difference in interval width is the value of adding domain knowledge.
