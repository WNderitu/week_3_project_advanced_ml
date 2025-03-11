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

---

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

For the exploratory data analysis and time Series forecasting modelling, the dataset for **one monitoring station; Aotizhongxin** will be used.

- The Aotizhongxin dataset has 35,064 observations and 17 features (4 time features, 6 target variables & 7 environmental factors).

---

## 6. Key insights from Exploratory Data Analysis

### Univariate analysis

#### Air Pollutants

- PM2.5 and PM10 are dangerously high with occasional extreme peaks.(PM2.5 - Mean: 83.16, SD:82.29, Median:60, Min-Max: 3-898), - PM10 - (Mean: 110.73, SD:95.37, Median:88, Min- Max:2-984)
- SO2: Mostly controlled, but occasional high levels suggest industrial emissions. (Mean:17.57, SD:22.82, Median:9, Min-Max:0.29 - 341)
- NO2 levels are consistently high, indicating major traffic or industrial contributions.(Mean:59.29, SD:37.00, Median:54, Min-Max:2 - 290)
- CO levels vary greatly, suggesting pollution hotspots. (Mean:1267.07, SD:1242.12, Median:900, Min-Max:100 - 10,000)
- 03 pollution is seasonal and affected by sunlight and NO₂ emissions. (Mean:55.18, SD:57.58, Median:41, Min-Max:0.21 - 423)

#### Environmental Factors

There are large seasonal variations in temperature and dew point with bimodal distributions. In terms of rainfall, there are mostly dry conditions, with rare heavy rainfall events. Pressure remains stable, with minor variations. Light winds dominate, but occasional strong gusts occur. The wind direction is variable.

### Bivariate analysis

#### Trend analysis

Seasonal Trends:
  
Daily trends

PM2.5 and PM10 follow similar trends, suggesting shared pollution sources. SO2, NO2, and CO show mid-month peaks. Ozone rises gradually, indicating photochemical formation.
  
Monthly trends

Winter months show high PM2.5, PM10, SO2, NO2, and CO levels. Summer months have higher O3 levels. Spring and autumn act as transition periods between these extremes.

Yearly trends

There is an increase in PM2.5 & PM10 from 2013 to 2014 followed by a decline until 2016, then a  sharp rise in 2017. There is a steady decline in SO2 levels from 2013 to 2016, however, a noticeable increase in 2017. NO2 levels are relatively stable until 2015 followed by a decline in 2016 with a s sharp increase in 2017. For CO levels, a general upward trend from 2013 to 2015 indicating worsening air quality. Then a decline in 2016 followed by a sharp increase in 2017. There is a steady increase in 03 levels from 2013 to 2015 peaking in 2015, then declines slightly in 2016 and drops significantly in 2017.

#### Correlation Analysis

There is strong positive linear relationship (as one variable increases, the other increases) between PM2.5 & PM10, temperature & dewpoint temperature, PM 2.5 & CO. A strong negative relationship between PRES & DEWP and TEMP & PRES. 

### Multivariate analysis

#### Prediciting future fine particulate matter levels (PM2.5)

ARIMA(1,1,2) model for prediction, where 3 predictor variables have effects. Dew point has a highly significant positive effect, pressure and wind direction have small negative effects.

#### Prediciting future coarse particulate matter levels

ARIMA(2,1,2) model for prediction, where 4 predictor variables have effects. Dew point and wind speed have strong significant positive effects, while rain, wind direction and presure are negatively associated.

#### Prediciting future sulphur dioxide levels

ARIMA(2,1,2) model for prediction, where 4 predictor variables have effects. Dew point has a strong significant positive effect, while temperature and pressure have significant negative effects, with wind direction having a small negative effect.

#### Predicting future nitrogen dioxide levels

ARIMA(1,0,1) model for prediction, where 4 predictor variables have effects. Dew point has a strong significant positive effect, while temperature and pressure have significant negative effects, with wind direction having a small negative effect.

#### Prediciting future carbon monoxide levels

ARIMA(2,1,1) model for for prediction, where 3 predictor variables have effects. Dew point has a strong significant positive effect, temperature has a strong significant negative effect while wind direction has a small negative effect.

#### Prediciting 0zone levels

ARIMA 2,0,1 Model for prediction, where 2 predictor variables have effects. Temperature has a strong significant positive effect and rain has a small positive effect.

## 7. Performance Measurement

- 6 air pollutants (PM2.5, PM10, SO2, NO2, CO & 03) predicted using a multivariate time series forecasting model that included exogenous variables
- Quality of the tested models for each predicted target variable assessed using **AIC, BIC, Log likelihood ratio** among other criterai
- Accuracy of the the time series forecasting model evaluated using **Mean Absolute Error (MAE) and Root Mean Squared Error (RMSE)**.
- The time series forecasting model for a specific air pollutant will be succesful if it's able to predict with the highest accuracy possible and determine which exogenous variables are significiant predictors.

## 8. Scope of Solution Space

Data Preprocessing:

- Handling of missing values.
- Conversion of timestamps to datetime dtype.
- Setting time as the index for time series analysis.
- Setting hourly frequency to convert to time series data.
- Converting categorical features to numerical features.
- Deletion of unneccessary features.

Model:

- ARIMA (p,d,q) models used to predict 6 future air pollutant levels at Aotizhongxin monitoring station based on historical pollutant data.
  
## 9. Constraints / Potential Challenges

- Data Quality:
  - Missing values
  - Noise in readings
- Model Interpretability:
  - Seasonal variations and external factors (e.g., industrial activity) affecting air quality
- Other:
  - Computational cost of training complex models such as SARIMA.

## 10. Stakeholders

- Environmental agencies and policymakers for monitoring and intervention.
- Urban planners for designing pollution control strategies.
- General public for awareness and preparedness against air pollution levels.
