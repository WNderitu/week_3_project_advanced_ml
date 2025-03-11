# **Air Quality Forecasting using Time Series Machine Learning Models**

---

## 1. Project Goal

The goal of this project is to develop a robust predictive model that predicts future air quality levels based on historical air quality data and relevant environmental factors.

## 2. Context/ Problem Statement

A few years ago, China established the Air Quality Index (AQI) based on the level of five pollutant atmospheres, namely sulfur dioxide (SO2), nitrogen dioxide (NO2), particulate matter (PM10), carbon monoxide (CO) and ozone (O3) measured at monitoring stations in each city.

## 3. Table of Contents

Notebook 1: Data Cleaning
Notebook 2: Exploratory Data Analysis
Notebook 3: Time Series Forecasting

## 4. Key Data Sources

The Data is sourced from <https://www.openml.org/search?type=data&status=active&id=42933&sort=runs>

## 5. Data Characteristics

- **The full dataset consists of 420,768 rows and 18 columns.**
- The dataset spans from 1st March 2013 to 28th February 2017.
- There are 6 target variables, namely:
  - PM2.5: Fine particulate matter. Defined as particles that are 2.5 microns or less in diameter.
  - PM10: Coarse particulate matter. Defined as particles that are 10 microns or less in diameter.
  - S02: Sulfur dioxide levels.
  - NO2: nitrogen dioxide levels.
  - CO: Carbon Monoxide levels.
  - 03: Ozone.
- There are 6 environmental factors namely:
  - TEMP: Temperature in degrees celsius
  - PRES: Pressure
  - DEWP: Dew Point in degrees celsius
  - RAIN: Rain
  - wd: wind direction (categorical feature)
  - WSPM: wind speed
- There are 4 columns containing time features, namely:
  - year
  - month
  - day
  - hour
- The last column; station contains the names of the monitoring stations in Beijing where the air pollutant measurements were collected
- There are 12 monitoring stations where data was collected, namely:
  1. Aotizhongxin
  2. Changping
  3. Dingling
  4. Dongsi
  5. Guanyuan
  6. Gucheng
  7. Huairou
  8. Nongzhanguan
  9. Shunyi
  10. Tiantan
  11. Wanliu
  12. Wanshouxigong

---

For the Time Series Forecasting Model, the dataset for **one monitoring station; Aotizhongxin** will be used for EDA & predicting levels for the 6 air pollutants.

- The Aotizhongxin dataset has 35,064 observations and 17 features (4 time features, 6 target variables & 7 environmental factors).

---

## 6. Key insights from Exploratory Data Analysis

**Univariate Analysis:**

**Bivariate Analysis:**

**Multivariate Analysis:**

## 7. Performance Measurement

- The time series forecasting model will be evaluated using **Mean Absolute Error (MAE) and Root Mean Squared Error (RMSE)**.
- The time series forecasting model will be succesful if it's able to predict the 6 air pollutants with the highest accuracy possible.

## 8. Scope of Solution Space

- Model: ARIMA (p,d,q) for prediciting 6 air pollutants for Aotizhongxin monitoring station.

Data Preprocessing:

- Handling of missing values using ffill and bfill
- Creation of date column with datetime dtype
- Setting of hourly frequency to convert datae set to time series data
- Converting categorical features to numerical features
- Deletion of unneccessary features; no, year, month, day, hour and wd
  
## 9. Constraints / Potential Challenges

- Data Quality:
  
- Model Interpretability

## 10. Stakeholders
