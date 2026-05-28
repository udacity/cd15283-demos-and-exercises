Solution: Zero-Shot Forecasting with a Foundation Model

Chronos-2 was pretrained on millions of time series. It has never seen our call volume data but it recognizes general patterns from its training. No parameter selection, no training loop, no waiting. The question is whether that general knowledge is good enough for our specific data.

We load the call volume data and split the same way as the previous exercises. We try to load Chronos2Model from darts.models. If it is available we initialize the small bolt variant which is sized for consumer hardware. We call predict with one hundred samples for uncertainty estimation. There is no fit step. The model has never seen this series. It recognizes the pattern from its pretraining.

If the import fails—which happens when the optional dependencies are not installed—we fall back to DartsARIMA with order (2,1,1). The fallback ensures the exercise always runs regardless of the environment. That is a practical consideration you need for any code that depends on optional packages.

A single forecast can be lucky or unlucky. We run historical_forecasts starting at the 75 percent mark with a twelve-month horizon and a three-month stride. This slides the training window forward through history, generating forecasts at multiple points, and averages out the luck. We compute MAE, RMSE, and MAPE across all those windows.

The plot shows the full actuals, the backtest, and the zero-shot forecast. Where Chronos-2 tracks the actuals closely, the general knowledge is sufficient. Where it diverges, the specific patterns in our data differ from what the foundation model learned. That gap tells you when to use a foundation model and when to fall back to a classical model trained on your own data.
