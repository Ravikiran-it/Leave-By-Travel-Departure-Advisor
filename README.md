# 🚕 Leave-By: An Uncertainty-Aware Travel Departure Advisor

## Overview

Leave-By is an academic Machine Learning Unit 1 project that predicts travel time from historical NYC taxi and weather data and recommends the latest departure time needed to reach a destination by a specified deadline.

The project combines supervised learning, unsupervised learning, polynomial curve fitting, probability theory, Bayes rule, statistical analysis, and uncertainty estimation into one application.

## Problem

Travel time is uncertain. A trip that normally takes a certain amount of time may take longer under different trip conditions.

Instead of using only the average travel time, Leave-By uses an estimated 90th-percentile travel time as an uncertainty buffer and recommends a latest feasible departure time.

## Dataset

### NYC Taxi Trip Duration
2016 NYC taxi trip records containing pickup/drop-off information, passenger count, timestamps, and trip duration.

Kaggle:
https://www.kaggle.com/competitions/nyc-taxi-trip-duration/data

### NYC Weather
2016 NYC Central Park weather observations containing temperature, precipitation, snowfall, and related measurements.

Kaggle:
https://www.kaggle.com/mathijs/weather-data-in-new-york-city-2016

### Final Working Dataset

200,000 cleaned taxi trips merged with daily weather information using pickup date.

> Weather is matched by pickup date rather than exact pickup time.

## Features

- Pickup hour
- Weekday
- Weekend indicator
- Peak-hour indicator
- Passenger count
- Pickup/drop-off coordinates
- Haversine geographic distance
- Average temperature
- Precipitation
- Rain indicator
- Snowfall
- Snow indicator

## Algorithms

### 1. Linear Regression
Used as the main supervised-learning model to predict continuous travel time.

### 2. Polynomial Curve Fitting
Used to model the nonlinear relationship between departure hour and mean travel time.

Degrees 1–5 were compared and degree 5 produced the lowest validation MSE.

### 3. K-Means Clustering
Used for unsupervised discovery of trip-condition patterns without using travel time as a clustering feature in the final clustering stage.

### 4. Probability and Statistics
The project applies:

- Discrete random variables
- Probability rules
- Bayes rule
- Independence
- Conditional independence
- Continuous random variables
- Mean
- Variance
- Quantiles
- Probability density
- Expectation
- Covariance

## Model Results

| Metric | Result |
|---|---:|
| MAE | 5.24 minutes |
| RMSE | 7.47 minutes |
| R² | 0.6016 |
| Long-trip Accuracy | 84.95% |
| Long-trip Precision | 82.55% |
| Long-trip Recall | 58.50% |
| Long-trip F1 | 68.48% |
| K-Means Silhouette | 0.1674 |

## Polynomial Results

| Degree | Validation MSE |
|---|---:|
| 1 | 3.8639 |
| 2 | 2.9619 |
| 3 | 2.2617 |
| 4 | 1.7778 |
| 5 | 1.6049 |

Selected degree: **5**

## Statistical Results

- Mean travel time: 14.07 minutes
- Variance: 119.35
- Standard deviation: 10.92 minutes
- Median: 11.15 minutes
- 75th percentile: 17.98 minutes
- 90th percentile: 27.18 minutes
- Gaussian 90th percentile: 27.56 minutes

## Leave-By Example

Input:

- Required arrival: 09:00
- Monday
- Distance: 5 km
- Passengers: 1
- Average temperature: 45°F
- Rain: Yes
- Precipitation: 0.3

Output:

- Estimated P90 travel time: 25.78 minutes
- Latest recommended departure: 08:30
- Estimated arrival: 08:55

## System Workflow

```text
NYC Taxi + Weather Data
        ↓
Data Cleaning
        ↓
Feature Engineering
        ↓
Supervised Learning
        ↓
Polynomial Analysis
        ↓
Probability & Statistics
        ↓
K-Means Clustering
        ↓
Uncertainty Estimation
        ↓
Leave-By Recommendation
