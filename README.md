# US_Pollution-Project

# Group Members
1. McKaye Peterson
2. Celia
3. Michael Rodriguez
4. Samantha Borresch

# Roles
1. McKaye Peterson   Machine Learning Model
2. Celia - Presentation
3. Michael Rodriguez   Github and ETL
4. Samantha Borresch   Visualizations

# Project
Based on nearly two decades worth of air quality data, can we determine the top 5 most polluted states and predict their future air quality?

# Research Questions
1. What are the top 5 most overall polluted states based on historic data?
2. What are the top 5 most polluted states for each four air pollutants based on historic data?
3. Can we predict the next 10-years of pollution levels for the top 5 most polluted states based on historic data?

# Why We Selected Topic
All members live in the greater Northern Utah area and have an interest in air quality and pollution, as this is a common issue among locals.

# Data Source
A CSV file scraped from the US EPA database with over 1.4 million data points that spans over 16-years of major air pollutant metrics.
- https://www.kaggle.com/datasets/sogun3/uspollution

Information on air pollution
- https://datasetsearch.research.google.com/search?query=pollution&docid=L2cvMTFqOWJtNnFzMA%3D%3D
- https://www.airnow.gov/aqi/aqi-basics/
- 


# Four Pollutants
1. Nitrogen Dioxide (NO2)   is the indicator for overall level of air pollution emitted by motor vehicles

# Data Source Metrics
- Row Number   unique identifier
- State Code   state id by US EPA
- County Code   county id by US EPA
- Site Num   unique code for each address
- Address   for monitoring site
- State   for monitoring site
- County   for monitoring site
- City   for monitoring site
- Date Local   date of monitoring
- NO2 Units   units of measure = parts per billion (ppb)
- NO2 Mean   concentration of pollution within a given day
- NO2 1st Max Value   max value for pollutant concentration in a given day
- NO2 1st Max Hour   max level of pollutant at military hour
- NO2 AQI   calculate air quality index within a given day
- O3 Units 
- O3 Mean
- O3 1st Max Value
- O3 1st Max Hour
- O3 AQI
- SO2 Units
- SO2 Mean
- SO2 1st Max Value
- SO2 AQI
- CO Units
- CO Mean
- CO 1st Max Value
- CO 1st Max Hour
- CO AQI

# ETL   Michael
- Goal: Keep all 28 metrics but decrease data points to make machine learning.
- Remove Null and/or N/A values
- Use Jupyter Notebook to determine the top 5 overall polluted states based on AQI for each pollutant for all 16-years. We utilize the CO AQI, SO2 AQI, NO2 AQI, O3 AQI, Site Num, and Date Local. Take an average of all four pollutants AQI data and group by Site Num and Date Local.
- Use Jupyter Notebook to determine the top 5 polluted states for each pollutant. Utilizing CO AQI, SO2 AQI, NO2 AQI and O3 AQI.
- Remove all irrelevant data records.
- Create new file
- Upload to Github for McKaye machine learning

# Machine Learning Model - McKaye
1. A predictive model
2. Uses linear historical data

# Visualizations (Tableau Story Board)   Sam
1. Trend line of top 5 cities/states overall pollution levels for 16-years of historic data.
2. Top 5 most polluted cities/states levels of each major air pollutants (Nitrogen Dioxide, Sulphur Dioxide, Carbon Monoxide and Ozone).
3. Geographical heat map showing air quality levels based on historic data.
4. How should we display the models  predictions for air quality?

# Presentation - Celia