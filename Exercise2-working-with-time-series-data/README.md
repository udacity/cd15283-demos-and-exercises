# Exercise 2: Preparing and Exploring Time-Series Data

## Context

Before you can build a reliable forecast, you must understand your data. This exercise focuses on the essential exploratory and preparation steps that turn a raw dataset into a model-ready time series. While these steps can feel like "cleaning," they are a critical part of the analytical process that directly impacts model performance.

You have a CSV of daily ride counts from a city's bike-share program.

## Exercise

Open `starter/starter.ipynb` and implement the following data exploration and transformation functions:

1.  **Establish a Valid Time Index:** Ensure the data has a complete and unique time index by handling any missing dates or duplicate entries.
2.  **Explore and Validate Values:** Investigate the data for potential issues like outliers or errors. This step is crucial for building robust models.
3.  **Handle Gaps:** Use interpolation to fill in any missing data points so that you can apply time-series models that require continuous data.
4.  **Analyze Stationarity:** Use rolling statistics and statistical tests (like the ADF test) to understand the series' behavior over time. This will inform which modeling techniques you'll use in the next lesson.

## Data

-   `data/bikeshare_rides.csv` — daily ride counts, January 2022 through December 2024.

## Solution

See `solution/solution.ipynb` for a complete working implementation.
