# US Pollution Project
![Screenshot](https://github.com/salvamike/US_Pollution-Project/blob/main/ETL%20%26%20Machine%20Learning/US_AQI_Map.png)

# Introduction
## Team Roles
1. McKaye Peterson - Machine Learning Model
2. Celia - Presentation
3. Michael Rodriguez - Github & HTML
4. Samantha Borresch - README, Database, ETL & Tableau Dashboard

## Project Topic
The United States air quality index (AQI) conversation is a regular topic among news reporters, research topics, and headlines. Living in cities with a lower AQI value, on a 0 to 500 scale, promotes healthy living and minimal respitory issues. In comparison, cities with a higher AQI value may cause respitory issues, infections, and lower quality of living. Understanding how AQI is calculated and the factors that effect the AQI value are beneficial for preserving a good quality of life. This topic raises a question, can we predict AQI? Could this help the general public better understand AQI and assist in their choice of locality? Using government funded AQI data from the United States Environmental Protection Agency (EPA), can we begin to understand how AQI performs over time and make comparable predictions based on selected inputs?

## Research Questions
1. What are the top 5 overall worst AQI cities?
2. What are the top 5 overall best AQI cities?
3. Can we build a machine learning model that predicts an AQI value comparable to the actual AQI value for each year for each top 5 city using "MedianAQI" and "Year" inputs?

## Why We Selected Topic?
All members live in the greater Northern Utah area and we have an interest in AQI, as this is a common issue among locals.

# Data Exploration
## Data Source
The data source includes 11 seperate CSV files provided by the United States Environmental Protection Agency (EPA). Each file holds AQI data for each fiscal year.

Link to the data sources: https://github.com/salvamike/US_Pollution-Project/tree/main/Data_Sources

Link to the EPA: https://aqs.epa.gov/aqsweb/airdata/download_files.html#Annual

## Data Source Metrics
- **CBSA**: Metropolitan area
- **CBSA**: Metropolitan area unique identifier code
- **Year**: Year data was collected
- **Days with AQI**: Count of how many days each CBSA collected AQI data
- **Good Days**: Count of how many good days that CBSA had in one fiscal year
- **Moderate Days**: Count of how many moderate days that CBSA had in one fiscal year
- **Unhealthy for Sensitive Groups Days**: Count of how many unhealthy for sensitive group days that CBSA had in one fiscal year
- **Unhealthy Days**: Count of how many unhealthy days that CBSA had in one fiscal year
- **Very Unhealthy Days**: Count of how many very unhealthy days that CBSA had in one fiscal year
- **Hazardous Days**: Count of how many hazardous days that CBSA had in one fiscal year
- **Max AQI**: The highest AQI value for that CBSA within one fical year
- **90th Percentile AQI**: The 90th percentile AQI score for that CBSA within one fiscal year
- **Median AQI**: The middle collected value for AQI data for that CBSA within one fiscal year
- **Days CO**: Count of days with high levels of carbon monoxide
- **Days NO2**: Count of days with high levels of nitrogen dioxide
- **Days Ozone**: Count of days with high levels of ground-level ozone
- **Days PM2.5**: Count of days with high levels of particle pollutions
- **Days PM10**: Count of days with extreme levels of particle pollutions

## What is AQI?
Air Quality Index (AQI) is a scale of 0 to 500 and the higher the AQI value the greater the level of air pollution and health concern. 
  - **Green** = Good = 0 to 50 = little to no risk
  - **Yellow** = Moderate = 51 to 100 = acceptable
  - **Orange** = Unhealth for Sensitive Groups = 101 to 150 = may expereince health effects
  - **Red** = Unhealthy = 151 to 200 = may experience health effects
  - **Purple** = Very Unhealthy = 201 to 300 = increased risk for health effects
  - **Maroon** = Haszardous = 301+ = emergency health condition warning
 
 Link to understanding AQI: https://www.airnow.gov/aqi/aqi-basics/

## Database & ETL - Samantha
### Process
1. Create Entity Relationship Diagram [(ERD)](https://github.com/salvamike/US_Pollution-Project/blob/main/ETL%20%26%20Machine%20Learning/Entity_Relationship_Diagram_ERD.png) for database
2. Create static database in PostgreSQL
3. Create [tables](https://github.com/salvamike/US_Pollution-Project/blob/main/ETL%20%26%20Machine%20Learning/PostgreSQL_Database_Script.txt) for each 11 CSV file
4. Import [data](https://github.com/salvamike/US_Pollution-Project/tree/main/Data_Sources) to each of the tables
5. Create a "Master" table and join the tables
6. Create [ETL script](https://github.com/salvamike/US_Pollution-Project/blob/main/ETL%20%26%20Machine%20Learning/ETL_Script_2.ipynb) in Jupyter Notebook that will interface with the database
7. Import Pandas, Psycopg, and SQLAlchemy libraries
8. Create engine instance
9. Connect Postgresql "Master" table to Pandas
10. Connect "Master" table from PostgreSQL using SQLAlchemy
11. Display "Master" table
12. Determine top 5 worst AQI cities using groupby on dataframe
13. Determine top 5 best AQI cities using groupby on dataframe
14. Save [files](https://github.com/salvamike/US_Pollution-Project/tree/main/ETL%20%26%20Machine%20Learning) and push to Github

# Analysis Phase
## Machine Learning Model - McKaye
We will be using a predictive based machine learning model that uses linear historical data for the analysis phase of this project. The features are the variables used to make a predictions and the target is the predicted outcome.

## Features: 
- City
- Median AQI for that city which is combined data from NO2 AQI, CO2 AQI, SO2 AQI, CO AQI
- Date by year (in order to see how the pollution has progressed over time)

Inspect the relationship between year, median aqi (Air Quality Index), and the city over the course of 11 years.

## Target: 
- The target VARIABLE is pollution levels, meaning that the goal of the linear regression model is to predict future pollution levels based on historical pollution levels in a given area.
- Independent variable is on the x axis and the dependent variable is on the y axis
Package to use: SKlearn.linear_model import LinearRegression

Inspect the relationship between state and pollution levels.

## Supervised Learning Model
- Create a model, train the model, and then create predictions.
- Our database = csv file contained 11 years (2012-2022) of pollution data across the united states.
- Once the ETL process has been completed on the dataset, the we can read in the file to the machine learning model and begin the process.

## Provisional Machine Learning Model
Our process will include the following:
- Reading in the ETL Dataset
- Splitting the data into training and testing (the data will be split by its features and target, which are mentioned above)
- Train the model using the training data. 
- Calculate the balanced accuracy score from sklearn.metrics.
- Print the confusion matrix from sklearn.metrics.
- Generate a classication report using the `imbalanced_classification_report` from imbalanced-learn.
- For the Balanced Random Forest Classifier onely, print the feature importance sorted in descending order (most important feature to least important) along with the feature score
- We will Use a random state of 1 for each algorithm to ensure consistency between tests

## Machine Learning Model Goal
Can we build a machine learning model that predicts an AQI value comparable to the actual AQI value for each year for each top 5 city using "MedianAQI" and "Year" inputs?

## Machine Learning Model 2 Segment Deliverable
Description of preliminary data preprocessing:
- Data preprocessing included finding a combined average of all the pollutants for each city. This required retrieving the average for the added up counties. From there, we were able to get the states average pollutant levels from that year. Then, we combined the ten years of data (represented by ten different .csv files) to create a single database.
Description of preliminary feature engineering and preliminary feature election, including their decision-making process
- Feature engineering includes relabeling the column with the combined AQI to be the target, or the dependent variable
- The categorical variable is the state
- The date will be relabeled to be the independent variable

Description of how data was split into training and testing sets:
- seperate the data into its features and targets
Explanation of model choice, including limitations and benefits
- We will be using sklearn.model_selection to train_test_split
- Then using BalancedRandomForestClassifier, the data will be resampled
- Next, we will output the balanced accuracy score and the confusion matrix
- Benefits include sensitivity, but is limited by potentially misidentifying pollutant levels.

# Github & HTML - Michael

# Tableau Dashboard - Samantha
## What is included?
1. Story board of all visualizations
2. Interactive "US AQI Heat Map"
3. Interactive bar graph of "Top 5 Worst AQI Cities"
4. Interactive bar graph of "Top 5 Best AQI Cities"
5. Images of "Top 5 Worst AQI Cities Linear Relationships" between "Year" and "Median AQI" value
6. Images of "Top 5 Best AQI Cities Linear Relationships" between "Year" and "Median AQI" value
7. Images of "Top 5 Worst Predicted vs Actual AQI Line Graph"
8. Images of "Top 5 Best Predicted vs Actual AQI Line Graph"

Link to Tableau Public Dashboard: https://public.tableau.com/app/profile/samantha.borresch/viz/US_Pollution_Project/StoryBoard?publish=yes

# Presentation - Celia
- Creator and Presenter
- Working on Google slides: https://docs.google.com/presentation/d/e/2PACX-1vQz5z_8KfzVfRJkGl4SMdeCbaSOQ0b11xDZOm145ADsOy3D2FwUkeqv7C79ZSXO35Yei33GxuNHah0O/pub?start=true&loop=false&delayms=3000
