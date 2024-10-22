# Waze_Predictive_Model_Project

### Project Overview
#### Hopefully you are now seeing this README file. Some strange rendering issues with how the file was saved had caused a blank page to be displayed.
#### The goal of this project was to gain insight into how many users discontinued using the Waze app (user churn), and what factors contributed to them churning. Waze is a popular transportation app used by motorists to facilitate route navigation, obtain traffic conditions, and access other related information. The project evaluates the predictions made by three (3) machine-learning models; binary logistic regression, decision tree, and random forest. The data used contains app usage information from a sample of 14,999 Waze users, and is fictitious data.
#### This project is based on one of the projects from the Google Advanced Data Analytics Certificate Courses, which I completed online through Coursera . It emulates the PACE (Plan, Analyze, Construct, Execute) analytical framework taught during the Certificate. The project layout also follows the 6 courses of the Certificate: 1). Project Proposal, 2). Data Cleaning and Manipulation, 3). EDA and Visualizations, 4). Statistical Analysis, 5), Regression Analysis, and 6). Machine Learning. Note that Course 7 is the Capstone Project which is coming soon in a separate repository.

### Business Understanding 

#### Waze leadership wanted to know what factors drive user churn. Knowing these factors allows the business to develop initiatives aimed at increasing user retention, and therefore promoting business growth and sustainability.

### Data Understanding 

#### A sample dataset of 14,999 users with 10 columns of data points and behavioral information was utilized in this project. The data contains information from the past month. Seven hundred (700) rows of data were dropped due to missing values in the retained/churned (label) column, and outliers were accounted for, most being transformed to values equaling the 95th percentile of that value's range (note a few other outliers were transformed to the 75th and 50th percentile).

### Jupyter Notebook Workflow.
### This is an outline of the steps completed in the project notebook.
Step | Sub-Step | Task |
|---|---|---|
| 1 | | Project Planning |
| | 1a | Imports and Data Loading.
| 2 | | Data Cleaning and EDA.
| | 2a | Data Cleaning |
| 3 | | Visualizations, Further EDA, and Outliers |
| | 3a | Variable Distributions |
| | 3b | Variable Relationships |
| | 3c | Handling Outliers |
| 4 | | Hypothesis Testing |
| 5 | | Build a Binomial Logistic Regression Model |
| | 5a | Checking for Outliers |
| | 5b | More Feature Engineering |
| | 5c | Determine Whether Assumptions Have Been Met |
| | 5d | Build and Evaluate the Model |
| 6 | | Tree-based Modeling - Decision Tree |
| | 6a | Build the Decision Tree Model |
| | 6b | Model Evaluation |
| 7 | | Tree-based Modeling - Random Forest
| | 7a | Additional Feature Engineering |
| | 7b | Construct and Evaluate Random Forest Model WITHOUT Outliers |
| | 7c | Construct and Evaluate Random Forest Model WITH Outliers |


### Data Dictionary 
### 1. Input Variables

Column | Type | Description |
|---|---|---|
| label | obj | Binary target variable (“retained” vs “churned”) for whether a user has churned during the month. | 
| sessions | int | The number of occurrences of a user opening the app during the month. |
| drives | int | An occurrence of driving at least 1 km during the month. |
| device | obj | The type of device a user starts a session with ("Android" or "iPhone"). |
| total_sessions | float | A model estimate of the total number of sessions since a user has onboarded. |
| n_days_after_onboarding | int | The number of days since a user signed up for the app. |
| total_navigations_fav1 | int | Total navigations since onboarding to the user's favorite place 1. |
| total_navigations_fav2 | int | Total navigations since onboarding to the user's favorite place 2. |
| driven_km_drives | float | Total kilometers driven during the month. |
| duration_minutes_drives | float | Total duration driven in minutes during the month. |
| activity_days | int | Number of days the user opens the app during the month. | 
| driving_days | int | Number of days the user drives (at least 1 km) during the month. |

### 2. Engineered Variables
*Column 3 "Step" indicates the step, or location, of where the variable was engineered in the Jupyter notebook.
Column | Type | Step | Description
|---|---|---|---|
| 1. 'km_per_driving_day' | float | 3b | The mean number of kilometers a user drove per day, computed by dividing 'driven_km_drives' by 'driving_days' |
| 2. 'percent_sessions_in_last_month' | float | 3b | The percentage of a user's total sessions that occurred within the last month, computed by dividing 'sessions' by 'total_sessions' |
| 3. 'professional_driver' | obj | 5b| Binary variable: 1 for users who drove 60 or more times in the last month AND drove on 15 or more days in the last month, 0 for all other users |
| 4. 'total_sessions_per_day' | float | 7a | The mean number of sessions per day since the user began using the app, computed by dividing 'total_sessions' by 'n_days_after_onboarding' |
| 5. 'km_per_hour' | float | 7a | The number of kilometers the user drove per hour in the last month, computed by dividing the quotient of 'driven_km_drives' and 'duration_minutes_drives', by 60 |
| 6. 'km_per_drive | float | 7a | The mean number of kilometers a user drove per drive during the past month, computed by dividing 'driven_km_drives' by 'drives' |
| 7. 'percent_of_sessions_to_favorite' | float | 7a | The percentage of a users total sessions that the user drove to their first and second favorite destination, computed by dividing the sum of 'total_navigations_fav1' and 'total_navigations_fav2' by 'total_sessions' |

### Visualizations

#### Below is a list of visualizations completed using Python.

| Type | Visualization |
|---|---|
| 1. Boxplot | Distribution of 'sessions' |
| 2. Histogram | Distribution of 'sessions' |
| 3. Boxplot | Distribution of 'drives' |
| 4. Histogram | Distribution of 'drives' |
| 5. Boxplot | Distribution of 'total_sessions' |
| 6. Histogram | Distribution of 'total_sessions' |
| 7. Boxplot | Distribution of 'nbr_days_after_onboarding' |
| 8. Histogram | Distribution of 'nbr_days_after_onboarding' |
| 9. Boxplot | Distribution of 'driven_km_drives' |
| 10. Histogram | Distribution of 'driven_km_drives' |
| 11. Boxplot | Distribution of 'duration_minutes_drives' |
| 12. Histogram | Distribution of 'duration_minutes_drives' |
| 13. Boxplot | Distribution of 'activity_days' |
| 14. Histogram | Distribution of 'activity_days' |
| 15. Boxplot | Distribution of 'driving days' |
| 16. Histogram | Distribution of 'driving_days' |
| 17. Pie Chart | Users by device |
| 18. Pie Chart | Count of retained vs. churned |
| 19. Histogram | 'driving_days' vs. 'activity_days' |
| 20. Scatterplot | 'driving_days' vs. 'activity_days' |
| 21. Histogram | Retention by 'device' |
| 22. Histogram | Churn rate by mean 'km_per_driving_day' |
| 23. Histogram | Churn rate per 'driving_days' |
| 24. Histogram | Distribution of 'percent_sessions_in_last_month' |
| 25. Histogram | Distribution of 'n_days_after_onboarding' for users >= 42% sessions in last month |


### Modeling and Evaluation 

#### Three models were developed: binomial logistic regression, decision tree, and random forest. Below are the metrics at the last iteration of the notebook (Note that most values were rounded to 3 decimal places for viewing ease):
                                     
| Model |	F1	| Precision	| Recall | Accuracy |
|---|---|---|---|---|
| Logistic Regr | 0.156 | 0.542 | 0.091 | 0.825 |
| Decision Tree	| 0.260	| 0.268	| 0.276	| 0.733 |
| Random Forest no Outliers | 0.103 | 0.517 | 0.057 | 0.823 | 
| Random Forest with outliers | 0.102 | 0.500 | 0.057 | 0.822 |                        	

#### Decision tree appears to be the champion model. As we see above, the random forest model with outliers performed slightly worse than the model with the outliers adjusted, which is surprising.

### Conclusion
#### It was determined that 17% of Waze users churned in the last month. The most notable fact that correlates with this churn is that the users who drove longer, farther, and more often, stopped using the app. 
#### The tree-based model is the best predictor of churn so far, having good f1 and recall scores. It was recommended that more granular data be obtained, and that these 3 models not be used in a production environment, but should be used for further data exploration and model development.

