# US_Pollution-Project

## Group Members
1. McKaye Peterson
2. Celia Carranza
3. Michael Rodriguez
4. Samantha Borresch

## Roles
1. McKaye Peterson - Machine Learning Model
2. Celia - Presentation
3. Michael Rodriguez - Github and ETL
4. Samantha Borresch - Dashboard and Note Taking

# Project Topic
Based on nearly two decades worth of air quality data, can we determine the top 5 overall polluted states and can we use these findings to predict their future AQI levels?

## Research Questions
1. What are the top 5 most overall polluted states based on historic data?
2. What are the top 5 most polluted states for each four air pollutants based on historic data?
3. Can we predict the next 10-years of pollution levels for the top 5 most polluted states based on historic data?

## Why We Selected Topic
All members live in the greater Northern Utah area and have an interest in air quality and pollution, as this is a common issue among locals.

## Data Source
A CSV file scraped from the US EPA database with over 1.4 million data points that spans over 16-years of major air pollutant metrics.
- https://www.kaggle.com/datasets/sogun3/uspollution

# Data Exploration
## Information on air pollution
- https://datasetsearch.research.google.com/search?query=pollution&docid=L2cvMTFqOWJtNnFzMA%3D%3D
- https://www.airnow.gov/aqi/aqi-basics/

## Four Pollutants
1. Nitrogen Dioxide (NO2) - is the indicator for overall level of air pollution emitted by motor vehicles, coal, oil, and other fossil fuels. High levels of NO2 are damaging to ecosystems, nature, and health.
2. Ozone (O3) - a gas in the atmosphere that absorbs UV rays from the sun to protect living organisms such as plants, animals and humans. Ground-level pollutants in high numbers negatively impacts the ecosystems, nature, and health.
3. Sulphur Dioxide (SO2) - gases emitted by the burning of materials that include sulfur, such as fossil fuels. High levels of SO2 are damaging to ecosystems, nature, and health.
4. Carbon Monoxide (CO) - is a colorless and odorless gas that is harmfuled when inhaled. The higher the CO level the more harmful it is.

## AQI
Air Quality Index (AQI) is a scale of 0 to 500 and the higher the AQI value the greater the level of air pollution and health concern. 
  - Green = Good = 0 to 50 = little to no risk
  - Yellow = Moderate = 51 to 100 = acceptable
  - Orange = Unhealth for Sensitive Groups = 101 to 150 = may expereince health effects
  - Red = Unhealthy = 151 to 200 = may experience health effects
  - Purple = Very Unhealthy = 201 to 300 = increased risk for health effects
  - Maroon = Haszardous = 301+ = emergency health condition warning
  
## Top Major AQI Factors
1. O3 = ground-level ozone
2. CO
3. SO2
4. NO2

## Data Source Metrics
- Row Number - unique identifier
- State Code - state id by US EPA
- County Code - county id by US EPA
- Site Num - unique code for each address
- Address - for monitoring site
- State - for monitoring site
- County - for monitoring site
- City - for monitoring site
- Date Local - date of monitoring
- NO2 Units - units of measure = parts per billion (ppb)
- NO2 Mean - concentration of pollution within a given day
- NO2 1st Max Value - max value for pollutant concentration in a given day
- NO2 1st Max Hour - max level of pollutant at military hour
- NO2 AQI - calculate air quality index within a given day
- O3 Units - units of measure = parts per million (ppm)
- O3 Mean - concentration of pollution within a given day
- O3 1st Max Value - max value for pollutant concentration in a given day
- O3 1st Max Hour - max level of pollutant at military hour
- O3 AQI - calculate air quality index within a given day
- SO2 Units - units of measure = parts per billion (ppb)
- SO2 Mean - concentration of pollution within a given day
- SO2 1st Max Value - max value for pollutant concentration in a given day
- SO2 1st Max Hour - max level of pollutant at military hour
- SO2 AQI - calculate air quality index within a given day
- CO Units - units of measure = parts per million (ppm)
- CO Mean - concentration of pollution within a given day
- CO 1st Max Value - max value for pollutant concentration in a given day
- CO 1st Max Hour - max level of pollutant at military hour
- CO AQI - calculate air quality index within a given day

We have decided to only keep the following columns: state code, state, city, date local, NO2 AQI, SO2 AQI, CO AWI and O3 AQI.
We have decided to only keep the following rows: those records for top 5 most overall polluted state and top 5 most polluted state for each individual pollutant.

# Database/ETL - Michael
- Remove Null and/or N/A values
- Use Jupyter Notebook to determine the top 5 overall polluted states based on AQI for each pollutant for all 16-years. We utilize the CO AQI, SO2 AQI, NO2 AQI, O3 AQI, Site Num, and Date Local. Take an average of all four pollutants AQI data and group by Site Num and Date Local.
- Use Jupyter Notebook to determine the top 5 polluted states for each pollutant. Utilizing CO AQI, SO2 AQI, NO2 AQI and O3 AQI.
- Remove all irrelevant data records.
- Create new file
- Upload to Github for McKaye machine learning

# Machine Learning Model - McKaye
1. A predictive model
2. Uses linear historical data

# Dashboard - Sam
1. Trend line of top 5 states overall pollution levels for 16-years of historic data.
2. Index of top 5 most polluted states levels of each major air pollutants (Nitrogen Dioxide, Sulphur Dioxide, Carbon Monoxide and Ozone).
3. Geographical heat map showing air quality levels based on top 5 polluted states (using AQI color coding see link https://www.airnow.gov/aqi/aqi-basics/)
4. Trend line to determine future pollution levels for top 5 states.

# Presentation - Celia
- Working on a power point.
- Adding some tableau content.

![image](https://user-images.githubusercontent.com/108438270/204967470-63002131-eca7-4528-be25-696ed49130f4.png)

