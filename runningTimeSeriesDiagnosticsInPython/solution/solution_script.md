Solution: Running Time-Series Diagnostics in Python

The exercise gives you electricity demand data and asks you to fit two models, then determine which one is trustworthy enough for production. This is a validation problem, not a fitting problem.

Load electricity_demand.csv, parse dates, set index, enforce monthly frequency. Split at the end of 2023: everything before is training, everything after is test. Fit ARIMA(2,1,1) with no seasonal or exogenous components. Fit SARIMAX(1,1,1)(1,1,1,12) with avg_temp_f as a regressor passed in as a DataFrame via the exog argument.

For each fitted model, extract the residuals with .resid. Run acorr_ljungbox at lag 12 with return_df=True to get a p-value that summarizes whether any autocorrelation remains across the first twelve lags. Above 0.05 means the residuals are consistent with white noise. Below means the model left predictable structure on the table. Then run stats.normaltest on the residuals to check whether the prediction intervals can be trusted—if the residuals are not normal, the stated confidence level is approximate. Extract AIC and BIC from each fitted model.

Build a comparison table with Ljung-Box p-value, normality p-value, AIC, and BIC for both models. For the electricity demand dataset, ARIMA fails the Ljung-Box test at lag twelve because it has no seasonal component—the annual cycle is still sitting in the residuals. SARIMAX passes because the seasonal terms captured that cycle. SARIMAX also wins on AIC and BIC, which tells you the extra parameters were worth the complexity.

The residual ACF plot shows both models on two subplots. ARIMA has a spike at lag twelve sticking out past the confidence band—that is the missed annual cycle. SARIMAX has no such spike. The plot makes visible what the Ljung-Box test summarized as a single number.
