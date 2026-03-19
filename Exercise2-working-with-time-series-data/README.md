# Exercise 2: Analyzing Time-Series Data in Python

## Context

This exercise focuses on the core analytical techniques used to understand time-series data. Instead of data cleaning, you will focus on methods that reveal patterns, trends, and statistical properties, which are essential for choosing the right forecasting model.

You have a CSV of daily ride counts from a city's bike-share program.

## Exercise

Open the new `starter/starter.ipynb` and perform the following analytical tasks:

1.  **Resampling:** Aggregate the data from a daily to a weekly frequency to analyze broader trends.
2.  **Rolling Statistics:** Calculate and visualize rolling averages to understand the series' local behavior and smooth out short-term fluctuations.
3.  **Stationarity Testing:** Use a statistical test (Augmented Dickey-Fuller) to determine if the series is stationary, a critical assumption for many classical forecasting models like ARIMA.

## Data

-   `data/bikeshare_rides.csv` — daily ride counts, January 2022 through December 2024.

## Solution

See `solution/solution.ipynb` for a complete working implementation.
