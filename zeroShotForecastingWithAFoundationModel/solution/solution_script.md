Solution: Zero-Shot Forecasting with a Foundation Model

The exercise gives you monthly call volume data and asks you to run Chronos-2 without training and evaluate it with historical forecasts. This is a zero-shot problem: can a foundation model that has never seen your data still outperform models you trained yourself?

Load call_volume.csv, parse the date column, set it as the index, and enforce monthly frequency. Create a Darts TimeSeries from the calls column. Split at the end of 2023—everything before is training, everything after is test.

Try to import Chronos2Model from darts.models. If it is available, initialize it with model_name="amazon/chronos-bolt-small"—the variant small enough to run on consumer hardware. Call predict on the training series with num_samples=100. There is no fit step. The model has never seen this data. It recognizes the call volume pattern from the millions of time series it was pretrained on. If the import fails—which happens when the dependencies are not installed—fall back to DartsARIMA(p=2, d=1, q=1), fit it on the training data, and predict. The fallback ensures the exercise always runs.

Run historical_forecasts with start=0.75, forecast_horizon=12, and stride=3. This slides a training window forward through history starting at the 75 percent mark, generates a twelve-month forecast at each position, and compares each forecast to what actually happened. A single forecast can be lucky. Backtesting averages that out across many windows. Compute MAE, RMSE, and MAPE against the actual test series.

The plot shows the full actuals, the backtest, and the zero-shot forecast. The comparison is how you communicate forecast quality to a stakeholder—showing that a model with no training can still capture the pattern, or identifying where it fails so you know when to fall back to a classical model.
