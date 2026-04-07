# Demo 1.4: Forecasting with BI Tools

## Context

We're comparing Tableau's "one click" forecast to what we built by hand in spreadsheets (Exercise 1.2). The demo should highlight two things:

1. **What Tableau does automatically** — it detects the weekly seasonality that our spreadsheet methods completely missed.
2. **What you give up** — control and transparency. You can't see the smoothing parameters, you can't choose additive vs multiplicative, and you can't tune the model if it gets something wrong.

The narrative arc is: spreadsheets gave us useful but limited answers, Tableau gives us a better answer with less work, but to really understand and control the forecast we need to build models ourselves in Python.

See `demo_script-1.4.md` for the talk track.
