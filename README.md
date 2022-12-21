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

## Technologies Used
- Github
- CSV Files
- Quick Database Diagrams
- Python
- PostgreSQL
- Jupyter Notebook
- Pandas
- Psycopg2
- SQLalchemy
- Numpy
- Matplotlib
- Seaborn
- SKLearn
- Linear Regression
- Tableau
- HTML
- CSS
- Google Slides
- Google Docs

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

## Provisional/Final Machine Learning Model
Our process will include the following:
- Reading in the ETL Dataset
- Splitting the data into training and testing (the data will be split by its features and target, which are the year and median aqi)
- Train the model using the training data. 
- Calculate the balanced accuracy score from sklearn.metrics.
- Check the distribution of the model
- Begin working with the actual dataset in order to visualize predicted aqi and actual aqi for each top 5 polluted city and state
- We will Use a random state of 1 for each algorithm to ensure consistency between tests

## Machine Learning Model Goal
Can we build a machine learning model that predicts an AQI value comparable to the actual AQI value for each year for each top 5 city using "MedianAQI" and "Year" inputs?

## Machine Learning Model 2 Segment Deliverable
Description of preliminary data preprocessing:
- Data preprocessing included retreiving all eleven files and combining them into one dataframe. From there the dataset was sorted by worst and best aqi levels. 
Description of preliminary feature engineering and preliminary feature election, including their decision-making process
- Feature engineering includes relabeling the column with the combined AQI to be the target, or the dependent variable
- The categorical variable is the state
- The date will be relabeled to be the independent variable

Description of how data was split into training and testing sets:
- Seperate the data into its features and targets (Years and Median AQI)
- Used from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=1)
Explanation of model choice, including limitations and benefits
- We will be using sklearn.model_selection to train_test_split
- Then we will perform the analysis on the training set using the sklearn linear regression model
- Next, we will output the coeffecients. We only had two variables so the data doesn't seem to be too accurate
- Benefits for using this model include sensitivity, but is limited by potentially misidentifying pollutant levels.

## Deliverable 4 Machine learning model
Description of feature engineering and the feature selection, including the team's decision-making process
- We wanted to view the trend in data from the past ten years and see how the machine learning model would do to predict the data based on actual results
Description of how model was trained. 
- Model was trained by splitting the data into test and train sets for both X and Y which are the year and median AQI respectively.
Description and explanation of model’s confusion matrix, including final accuracy score and statistical analysis
- Explanation: MAE is a measure of the average error between the predictions and intended targets, thus we want to minimise this value. So 2.5 shows that the model is not too far off from the actual dataset.
- The Mean Squared Error measures how close a regression line is to a set of data points.
- The RMSE is the square root of the variance of the residuals. It indicates the absolute fit of the model to the data–how close the observed data points are to the model's predicted values.
Problem we are solving
- Our goal is to train a linear regression model to see if the air quality reality is comparable to the predicted.
Future statistical analysis:
- Running statistical tests to see the relation between the datapoints instead of just viewing and interpreting them visually.

# Github & HTML - Michael

# Tableau Dashboard - Samantha
## What is included?
1. Story board of all visualizations
2. Introduction of project topic
3. Interactive "US AQI Heat Map"
4. Interactive bar graph of "Top 5 Worst AQI Cities"
5. Interactive bar graph of "Top 5 Best AQI Cities"
6. Images of "Top 5 Worst AQI Cities Linear Relationships" between "Year" and "Median AQI" value
7. Images of "Top 5 Best AQI Cities Linear Relationships" between "Year" and "Median AQI" value
8. Images of "Top 5 Worst Predicted vs Actual AQI Line Graph"
9. Images of "Top 5 Best Predicted vs Actual AQI Line Graph"

Link to Tableau Public Dashboard: https://public.tableau.com/app/profile/samantha.borresch/viz/US_Pollution_Project/StoryBoard?publish=yes

# Presentation - Celia
Link to Google slides: https://docs.google.com/presentation/d/e/2PACX-1vQz5z_8KfzVfRJkGl4SMdeCbaSOQ0b11xDZOm145ADsOy3D2FwUkeqv7C79ZSXO35Yei33GxuNHah0O/pub?start=true&loop=false&delayms=3000

Link to Speaker Notes: https://docs.google.com/document/d/1dG2VEaVGcyk6v6gsNtsJJ7isXpXbI_ZLk1OziUVK4Xo/edit

# Results
## Findings
### Weak Relationship Between Variables
![Screenshot](https://github.com/salvamike/US_Pollution-Project/blob/main/ETL%20%26%20Machine%20Learning/Bakersfield%2C%20CA.png)

According to the "Top 5 Best - Linear Relationships" and the "Top 5 Worst - Linear Relationships" sections of our [dashboard](https://public.tableau.com/app/profile/samantha.borresch/viz/US_Pollution_Project/StoryBoard?publish=yes), there is a weak relationship between our variables "Year" and "MedianAQI" for each city. An example of "Bakersfield, CA" above domonstrates that each of the line graphs is set up the same for the top 5 best and worst cities. The x-axis is "Year" and the y-axis is "MedianAQI". Each point on the graph represents the "MedianAQI" for that corresponding "Year". The blue line is a autogenerated trend line based on the data. The blue shading is the confidence intervals for each graph. The confidence interval illustrates a level of uncertainty. The seaborn import during the machine learning model process has a 95% confidence interval by default. This mean anthything within the 95% interval is likely to be true and anything outside the confidence interval is likely to be false. To have a "strong" relationship each point should lie close to the trend line and be within the confidence interval. However, many points do not straddle the trend line and some lie outside the confidence interval, which are likely to be extreme outliers. **Therefore, this data shows that a weak relationship exists between our chosen variables and a lack of accuracy in predicting AQI**. In addition most of the trend lines are negative weak meaning they are sloping down and the points are not close to the trend line. A negative relationship illustrates a negative linear relationship between "MedianAQI" and "Year". Essentialy, as "Year" increases "MedianAQI" has an inverse relationship, of decreasing.

### Predicted vs Actual AQI Disconnect
![Screenshot](https://github.com/salvamike/US_Pollution-Project/blob/main/ETL%20%26%20Machine%20Learning/Bakersfield.png)

According to the "Top 5 Worst Predicted vs Actual" and the "Top 5 Best Predicted vs Actual" sections of our [dashboard](https://public.tableau.com/app/profile/samantha.borresch/viz/US_Pollution_Project/StoryBoard?publish=yes), our machine learning model was unsucessful in predicting AQI. Each top 5 best and worst city has their own graph where the x-axis is "Year" and the y-axis is "MedianAQI". There are two lines to show the accuracy of the "PredictedAQI" provided by the machine learning model and the "MedianAQI" provided by the EPA data. The "Predicted" line is yellow with an x at each data point that represents "PredictedAQI" and the "Actual" line is blue with a dot over each data point that represents "MedianAQI". All 10 of our cities illustrated a disconnect between the "Acutal" and "Predicted". This demonstrates that AQI cannot be predicted simply alone by "Year" and "MedianAQI". This also leads us to our largest limitation for the project, not having enough variables to build and teach our machine learning model to predict AQI more accurately. **Although we cannot draw accuracy from these graphs we can hypothesize what causes positive and negative spikes in the "Actual" line that could be used to perfect the model in future research projects**. See the next finding "Hypotheses for Volatitlity" to see other possibly assumptions to why "Actual" and "Predicted" are vastly different, seperate from lack of variables limitation.

### Hypotheses for Volatility 
- **Wild Fire Spread**: these are unpredictable and negatively effect many city's AQI
- **Covid-19 Relocations**: the mass movement of people across the US could be cause for extreme positive/negative spikes in certain cities
- **Droughts**: such as lack of rain fall causing wild fires during summer or bodies of water drying up, which cause an increase in particles in the air.
- **Factory/Plants/Mills/etc.**: can all effect AQI by their emissions

## Limitations
### Limited Variables
When building out our project we tested if we could predict each year's "PredictedAQI" based simply upon the historic "MedianAQI" and "Year" data collected by the EPA. However, we determined that "PredictedAQI" can not be predicted accurately on historic "MedianAQI" and "Year" values alone. There is a weak relationship between "Year" and "MedianAQI" for all top 5 cities, as shown in the visuals on the "Top 5 Best - Linear Relationships" and the "Top 5 Worst - Linear Relationships" sections of our [dashboard](https://public.tableau.com/app/profile/samantha.borresch/viz/US_Pollution_Project/StoryBoard?publish=yes) . Therefore more dependent variables, such as weather patterns, wind movements, emissions, etc. need to be added to the machine learning formula to improve the predictive accuracy rate of the indepenent variable "MedianAQI".

### Time Limits
We believe that if more time was alloted to do data exploration and analysis, that this project would prove a better accuracy rate in "PredictedAQI" for the top 5 best and worst cities. A project with this count of deliverables and it's highly technical nature, proves difficult for many teams albeit an unfamiliar team and 4-weeks. Regardless of the time limit for this project, we believe we demonstrated many skills learned throughout this boot camp and are proud of what we accomplished.

### Technical Skill
During conversation between the team, all of the members were newer to the subject of data analytics, computer programming, and machine learning. With only 6-months to prepare for a project of this calliber, technical skill is a huge caveat to performance. We all had basic working skills for each section of the project and demonstrated at our best, the knowledge we have obtained. With more practice on technical skills a more refined foundation of this project may have improved our predictive ability.

## Recommendation for Future Analysis
### Use More Variables
As indicated in the above paragraph "Limited Variables", it could prove beneficial to add additional variables to our machine learning model formula to improve the predictive ability of AQI for the top 5 best and worst cities.

### Research Other AQI Studies
After finishing our project, high level researching demonstrated many other AQI studies and foundations focusing on predicting AQI and its effects on humans, animals, and the earth. According to IQAir, a Swiss technology company with a mission to improve air quality, there are many quantitative and qualitative variables that effect AQI, of which the variables themselves are hard to predict (IQAir, 2022). There are also many different techniquest that can be used to make predictions. For this reason, futher preliminary research to obtain secondary data and information could prove beneficial in building a more accurate machine learning model in the future.

Reference: IQAir. (2022, November 16). First in Air Quality. IQAir. Retrieved December 20, 2022, from https://www.iqair.com/us/newsroom/can-air-pollution-be-predicted 

## What We Would Have Done Differently
### Further Clean Records in ETL
![Screenshot](https://github.com/salvamike/US_Pollution-Project/blob/main/ETL%20%26%20Machine%20Learning/Danville.png)

After running the ETL process and identifying the top 5 best and worst AQI cities, we realized that some of the top 5 cities had fewer records than other cities. For example, when we visualized the linear regresstion relationship between "Year" and "MedianAQI" for "Danville, VA" we noticed there were only two AQI data points ranging from 2021 to 2022. We determined that if we removed records for cities that had fewer than 11 years of AQI data points, that the data would be more sound and compared equally. 

### Polish Visualizations
![Screenshot](https://github.com/salvamike/US_Pollution-Project/blob/main/ETL%20%26%20Machine%20Learning/Jamestown.png)

During the machine learning model, we built a multiline regression graph that illustrated each top 5 city's "PredictedAQI" and actual "MedianAQI" values. Once visualized, some of the visualizations had different formats for the axis "Year". For example, the above visualization shows "Jamestown, ND" and the x-axis ("Year") is in decimal format compared to the other visualizations being in whole numbers. This is also a product of the above paragraph, "Further Clean Records in ETL". If this step would have been done, the visualizations would have the same count of "Years" and the x-axis identical.


