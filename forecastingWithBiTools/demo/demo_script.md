Demo: Forecasting with BI Tools

We just built three forecasts by hand in a spreadsheet and they were useful but flat. None of them could tell us about the Saturday bump. Now we will see what happens when we hand the same bakery sales data to Tableau.

I drag Date to columns and Loaves Sold to rows and I get the line chart. Same data, 731 days. Now I right-click on the chart and hit Show Forecast and Tableau projects forward. Look at the shape. It is not flat. It has bumps. It has a weekly pattern. Tableau detected the 7-day cycle automatically.

If I click Describe Forecast Tableau tells me it used an ETS model, which stands for Error, Trend, Seasonal. It found a slight upward trend which matches our TREND() result and it found a seasonal period of 7 which is the weekly cycle. This is what our spreadsheet methods could not do.

But I did not choose ETS. I cannot see the smoothing parameters and I cannot decide whether to use additive versus multiplicative seasonality. Tableau made those choices for me. For the bakery owner who just needs a number that is fine but if you need to understand why the forecast says what it says or if the automatic detection gets it wrong you are stuck.

If you need that level of control you have to build the model yourself in Python.
