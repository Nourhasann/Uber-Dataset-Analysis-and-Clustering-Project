# Uber Dataset Analysis and Clustering

An exploratory data analysis (EDA) and unsupervised learning project on Uber ride request data, uncovering demand patterns across time and location, and segmenting pickups into geographic clusters using K-Means.

## Overview

This project analyzes Uber ride request data to understand **when, where, and how often** rides are requested — and whether requests get completed, cancelled, or go unfulfilled due to car unavailability. It combines data cleaning, feature engineering, visualization, and K-Means clustering to surface patterns useful for operational decisions like driver positioning and demand forecasting.

## Objectives

- Clean and prepare raw Uber ride-request data (handle missing timestamps, duplicate records, and driver IDs)
- Engineer time-based features (hour, day of week, AM/PM, rush-hour flag) and trip-duration metrics
- Explore ride status (completed / cancelled / no cars available) against pickup point, time of day, and day of week
- Visualize demand patterns using bar charts, histograms, joint plots, and heatmaps
- Apply **K-Means clustering** to group ride pickups into geographic zones based on location coordinates
- Translate findings into operational insights (peak hours, high-cancellation zones, driver availability gaps)

## Dataset

Ride-level Uber request data including:
- Request and drop timestamps
- Pickup point (City / Airport)
- Driver ID
- **Status** — Trip Completed / Cancelled / No Cars Available

## Pipeline

1. **Data loading & initial exploration** — shape, dtypes, summary statistics, missing-value audit
2. **Preprocessing** — parse mixed-format timestamps, impute missing request/drop times with the median, fill missing driver IDs, drop duplicates, compute trip duration, and remove invalid (negative-duration) records
3. **Feature engineering** — extract day of week, hour, minute, AM/PM, and a rush-hour flag (7–9 AM, 5–7 PM) from request timestamps; compute per-driver trip counts and availability
4. **Visualization & EDA** — distribution plots of ride status, pickup point vs. status, day-of-week vs. status, request/drop hour distributions, and a day-by-hour demand heatmap
5. **Outlier handling** — IQR-based filtering of trip duration to remove extreme values
6. **K-Means clustering** — maps pickup points (City/Airport) to coordinates and clusters ride requests spatially to identify high-demand zones, using the elbow method to help select the number of clusters

## Key Findings

- Ride cancellations are notably higher for **City** pickups than **Airport** pickups
- Car availability is inconsistent between pickup points, with fewer cars available at the airport relative to demand
- Demand peaks during **commute hours** (7–9 AM and 5–7 PM), consistent with work-travel patterns
- Weekday demand and cancellation patterns vary — spikes in unavailability were observed early in the week
- K-Means clustering on pickup coordinates reveals distinct geographic demand zones, useful for informing driver deployment and positioning strategy

## Tech Stack

`Python` · `pandas` · `NumPy` · `scikit-learn (KMeans)` · `matplotlib` · `seaborn`

## How to Run

1. Clone this repository
2. Install dependencies: `pip install pandas numpy scikit-learn matplotlib seaborn`
3. Place `Uber Request Data.csv` in the working directory
4. Run the notebook cells in order (preprocessing → feature engineering → visualization → clustering)
