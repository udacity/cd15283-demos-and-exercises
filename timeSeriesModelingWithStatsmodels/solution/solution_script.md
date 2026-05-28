Solution: Time-Series Modeling with statsmodels

We have monthly airline passenger counts and a clear annual cycle. The question is not whether seasonality exists—we can see it in the plot. The question is whether adding a seasonal component to the model is worth the extra complexity. That is the kind of tradeoff you make in practice every time you add a parameter.

We split chronologically, holding out the last twelve months as test. Everything before is training. We fit ARIMA(2,1,1) with no seasonal terms and no exogenous variables. This model has no concept of summer versus winter. It sees the seasonal oscillation as noise it cannot explain, so its prediction intervals are wide because it treats the cycle as uncertainty rather than structure.

Then we fit SARIMAX(1,1,1)(1,1,1,12). The seasonal order tells the model to look twelve months back for repeating patterns. When we generate the same twelve-month forecast the intervals are visibly tighter. That is because the seasonal terms explain variation that ARIMA was forced to treat as random. Tighter intervals mean better decisions because they give a narrower range of outcomes to plan for.

We compare AIC, BIC, and average interval width. SARIMAX wins on all three. AIC and BIC reward better fit while penalizing extra parameters, so when they drop we know the complexity was justified. The plot shows both forecasts against train and test. ARIMA projects a flat line with wide bands. SARIMAX follows the seasonal peaks and troughs. The visual difference is the return on adding domain knowledge.
