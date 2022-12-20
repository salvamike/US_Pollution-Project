# US Pollution Project
![Screenshot](https://github.com/salvamike/US_Pollution-Project/blob/main/ETL%20%26%20Machine%20Learning/US_AQI_Map.png)

## Group Members
1. McKaye Peterson
2. Celia Carranza
3. Michael Rodriguez
4. Samantha Borresch

## Roles
1. McKaye Peterson - Machine Learning Model
2. Celia - Presentation
3. Michael Rodriguez - Github & HTML
4. Samantha Borresch - README, Database, ETL & Tableau Dashboard

# Project Topic
Based on a decade of air quality data from 2012-2022, can we determine the top 5 most overall polluted cilties and top 5 overall least polluted cities and can we use these findings to predict the 2023 AQI levels?

## Research Questions
1. What are the top 5 most overall polluted cities based on AQI data?
2. What are the top 5 most overall least polluted cities based on AQI data?
2. Can we predict the next year of pollution levels for these cities?

## Why We Selected Topic?
All members live in the greater Northern Utah area and have an interest in air quality and pollution, as this is a common issue among locals.

# Data Exploration
## Data Source
The data source includes 11 seperate CSV files provided by the United States Environmental Protection Agency (EPA). Each file is the data for each fiscal year.

Link: https://aqs.epa.gov/aqsweb/airdata/download_files.html#Annual

## Data Source Metrics
- CBSA: Metropolitan area
- CBSA: Metropolitan area unique identifier code
- Year: Year data was collected
- Days with AQI: Count of how many days each CBSA collected AQI data
- Good Days: Count of how many good days that CBSA had in one fiscal year
- Moderate Days: Count of how many moderate days that CBSA had in one fiscal year
- Unhealthy for Sensitive Groups Days: Count of how many unhealthy for sensitive group days that CBSA had in one fiscal year
- Unhealthy Days: Count of how many unhealthy days that CBSA had in one fiscal year
- Very Unhealthy Days: Count of how many very unhealthy days that CBSA had in one fiscal year
- Hazardous Days: Count of how many hazardous days that CBSA had in one fiscal year
- Max AQI: The highest AQI value for that CBSA within one fical year
- 90th Percentile AQI: The 90th percentile AQI score for that CBSA within one fiscal year
- Median AQI: The middle collected value for AQI data for that CBSA within one fiscal year
- Days CO: Count of days with high levels of carbon monoxide
- Days NO2: Count of days with high levels of nitrogen dioxide
- Days Ozone: Count of days with high levels of ground-level ozone
- Days PM2.5: Count of days with high levels of particle pollutions
- Days PM10: Count of days with extreme levels of particle pollutions

## What is AQI?
Air Quality Index (AQI) is a scale of 0 to 500 and the higher the AQI value the greater the level of air pollution and health concern. 
  - Green = Good = 0 to 50 = little to no risk
  - Yellow = Moderate = 51 to 100 = acceptable
  - Orange = Unhealth for Sensitive Groups = 101 to 150 = may expereince health effects
  - Red = Unhealthy = 151 to 200 = may experience health effects
  - Purple = Very Unhealthy = 201 to 300 = increased risk for health effects
  - Maroon = Haszardous = 301+ = emergency health condition warning
 
 Link: https://www.airnow.gov/aqi/aqi-basics/

# Database & ETL - Samantha
## Process
1. Create ERD for database
2.Create databse in Postgresql
3. Create tables for each data source (x11)
4. Import data to each of the data sources (x11)
5. Create a "Master" table and join the sources
6. Create [script](https://github.com/salvamike/US_Pollution-Project/blob/main/Second%20Attempt/ETL_Script_2.ipynb) in Jupyter Notebook
7. Import Pandas, Psycopg, and SQLAlchemy libraries
8. Create engine instance
9. Connect Postgresql "Master" table to Pandas
10. Read in "Master" table
11. Display "Master" table
12. Determine top 5 worst AQI cities
13. Determine top 5 best AQI cities

## Files
- [ERD Visual](https://github.com/salvamike/US_Pollution-Project/blob/main/Second%20Attempt/Entity_Relationship_Diagram_ERD.png)
- [Master Table Script](https://github.com/salvamike/US_Pollution-Project/blob/main/Second%20Attempt/PostgreSQL_Database_Script.txt)
- [ETL Script](https://github.com/salvamike/US_Pollution-Project/blob/main/Second%20Attempt/ETL_Script_2.ipynb)

# Machine Learning Model - McKaye
1. A predictive model
2. Uses linear historical data
- Features are the variables used to make a prediction. Target is the predicted outcome.

## Features: 
- City
- Median AQI for that city which is combined data from NO2 AQI, CO2 AQI, SO2 AQI, CO AQI
- Date by year (in order to see how the pollution has progressed over time)
Inspect the relationship between year, median aqi (Air Quality Index), and the city over the course of 10 years.

## Target: 
- The target VARIABLE is pollution levels, meaning that the goal of the linear regression model is to predict future pollution levels based on historical pollution levels in a given area.
- Independent variable is on the x axis and the dependent variable is on the y axis
Package to use: SKlearn.linear_model import LinearRegression
* Inspect the relationship between state and pollution levels

 Supervised learning model: create a model, train the model, and then create predictions.
* Our database = csv file contained 10 years (2012-2022) of pollution data across the united states.
* Once the ETL process has been completed on the dataset, the we can read in the file to the machine learning model and begin the process.

## Provisional Machine Learning Model
- Our process will include the following:
- Reading in the ETL Dataset
- Then, splitting the data into training and testing
- Note: The data will be split by its features and target, which are mentioned above
1. Train the model using the training data. 
2. Calculate the balanced accuracy score from sklearn.metrics.
3. Print the confusion matrix from sklearn.metrics.
4. Generate a classication report using the `imbalanced_classification_report` from imbalanced-learn.
5. For the Balanced Random Forest Classifier onely, print the feature importance sorted in descending order (most important feature to least important) along with the feature score
We will Use a random state of 1 for each algorithm to ensure consistency between tests

## Machine Learning Model Goal:
- This machine learning process will help us predict the future pollutant levels of the cities (both the least polluted cities and most polluted cities from our data set) based on previous 10 years. 

### Output labels for this dataset will be:
target column values = 
1. predicted AQI for the city in 2023

## Machine Learning Model 2 Segment Deliverable
Description of preliminary data preprocessing
- data preprocessing included finding a combined average of all the pollutants for each city. This required retrieving the average for the added up counties. From there, we were able to get the states average pollutant levels from that year. Then, we combined the ten years of data (represented by ten different .csv files) to create a single database.
Description of preliminary feature engineering and preliminary feature election, including their decision-making process
- Feature engineering includes relabeling the column with the combined AQI to be the target, or the dependent variable
- The categorical variable is the state
- The date will be relabeled to be the independent variable
Description of how data was split into training and testing sets
1. seperate the data into its features and targets
Explanation of model choice, including limitations and benefits
- We will be using sklearn.model_selection to train_test_split
- Then using BalancedRandomForestClassifier, the data will be resampled
- Next, we will output the balanced accuracy score and the confusion matrix
- Benefits include sensitivity, but is limited by potentially misidentifying pollutant levels.

# Github & HTML - Michael

# Tableau Dashboard - Samantha
1. Story board of all visualizations
2. Interactive "US AQI Heat Map"
3. Interactive bar graph of "Top 5 Worst AQI Cities"
4. Interactive bar graph of "Top 5 Best AQI Cities"
5. Images of "Top 5 Worst AQI Cities Linear Relationships" between "Year" and "Median AQI" value
6. Images of "Top 5 Best AQI Cities Linear Relationships" between "Year" and "Median AQI" value

Link to Tableau Public Dashboard: https://public.tableau.com/app/profile/samantha.borresch/viz/US_Pollution_Project/StoryBoard?publish=yes

# Presentation - Celia
- Creator and Presenter
- Working on Google slides: https://docs.google.com/presentation/d/e/2PACX-1vQz5z_8KfzVfRJkGl4SMdeCbaSOQ0b11xDZOm145ADsOy3D2FwUkeqv7C79ZSXO35Yei33GxuNHah0O/pub?start=true&loop=false&delayms=3000

![image](https://user-images.githubusercontent.com/108438270/204967470-63002131-eca7-4528-be25-696ed49130f4.png)
