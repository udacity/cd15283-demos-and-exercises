# Exercise 2: Working with Time-Series Data in Python

## Context

A city's bike-share program hands you a CSV of daily ride counts. Three years of data — but it's messy. Missing dates, duplicate rows, unit errors, outliers, and negative values are hiding in the data. None of it is labeled.

## Exercise

Open `starter/starter.ipynb` and implement the data cleaning and analysis functions:

1. **Find missing dates** and **duplicates**
2. **Detect and fix unit errors** (October 2023 hourly-vs-daily issue)
3. **Detect outliers** and **fix negative values**
4. **Fill gaps** with interpolation
5. **Compute rolling statistics** and **run the ADF stationarity test**

## Data

- `data/bikeshare_rides.csv` — daily ride counts, January 2022 through December 2024 (with intentional errors)

## Solution

See `solution/solution.ipynb` for a complete working implementation.
