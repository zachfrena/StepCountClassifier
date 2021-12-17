# Classifying step count: Fitness and Health Tracking with Garmin Smartwatch

## 1. Question/Topic being investigated
The topic I investigated was how effectively fitness and health outcomes can be predicted when provided metrics surrounding daily fitness activities. My reason for choosing this topic is that physical health and exercise has been a big part of my life and regular activity can have both immediate and long-term benefits. Being able to glean insight through data-centric processes is something of great interest to me and this project helped optimize my own physical health.
The 5,000 step-per-day benchmark has been proven to assess an individual's general physical activity level. The Garmin Smartwatch (i.e. the data collection device) can accurately measure steps taken throughout the day, however it also has the ability to collect large amounts of data during activities and workouts (e.g. reps, sets, max heart rate, etc.).

## 2. Plan of attack
The goal of this project was to build, train, and test a model that accurately predicts whether an individual will reach their daily step goal (i.e. achieve > 5,700 steps/day) when only provided samples of their daily activity. The Garmin Fenix 6 Pro was the wearable device used-- it allows a user to track overall health metrics and log exercises and activities. The device owner has the ability to select from 30-40 different default activities (hiking, swimming, jogging, climbing, etc.), and there is the opportunity to add custom ones as well.

<img src=https://github.com/ensf611-fall-2021/ml-project-zachfrena/blob/main/images/garmin_activity_select.JPG width = "600">


The data from this project was collected from my personal Garmin device through the Garmin Connect App (a online tool for tracking, analyzing, visualizing and sharing health and fitness activities). The final dataset contains activities/exercises collected during the period of 11 months (Jan-Nov 2021). While there are many detailed reports and insights generated through the Connect App, it was clear that a more customized dataset was required for analysis. 

<img src=https://github.com/ensf611-fall-2021/ml-project-zachfrena/blob/main/images/garmin_connect_dashboard.JPG width = "600"> 

The following reports were pulled from the Connect App between Jan 1st - Nov 12th 2021: Logged physical activities, Step Count (daily) and Total Calories (daily).

After combining the datasets into a feature matrix, the target vector (i.e. predicted outcome) is defined as the daily step count. This problem can be treated as either a regression (e.g. predict the number of steps) or classification task (e.g. predict whether you will surpass your step threshold value). In this project I treated it as a classification task, however I am very interested in exploring regression in the future!

## 3. Dataset, models, framework, components
As previously mentioned, the final dataset is comprised of multiple reports that logged physical activity and health metrics. Each sample in this dataset represents a single activity that was recorded using the Garmin Smartwatch. Features for each activity include Activity Name, Exercise Duration, Average Heart Rate, etc. 
The models used in the analysis are identified as the following Scikit-learn classifiers: 
- LogisticRegression() 
- SVC() 
- BernoulliNB() 
- RandomForestClassifier() 
- GradientBoostingClassifier(). 

The analysis is in the form of a Jupyter Notebook-- this makes it easy to walk through each step and see what the code is doing. 


After loading the data, the following steps were performed:
1. Inspect data with pandas and seaborn.
2. Preprocess any non-numerical data using OneHotEncoder.
3. Create training and test sets with train_test_split().
4. Compare the various classification models using 7-fold cross-validation.
5. Hyperparameter tuning using grid search with 7-fold cross-validation.
7. Retrain the best model using the optimal hyperparameters.
8. Evaluate best model on test data including precision, recall and confusion matrix.

## Conclusion:

When plotting the correlation matrix, I noticed that there was a possibility we would run into a `multicollinearity` scenario. This would ultimately reduce the stability of the coefficient estimates, which weakens the power of the classification model. It would have been a good idea to identify and isolate all independent variables that are statistically significant, and only keep those for training purposes. For any pair of features that had a correlation value higher than 85%, I could have deleted one of them. Another method to combat this issue would be to use a dimension reduction algorithm such as Principle Component Analysis (PCA). I feel that having additional data points would have made the entire process more refined and the model would perform much better when trained on additional samples.

The topic I set out to investigate was how effectively fitness and health outcomes can be predicted when provided metrics surrounding daily fitness activities. I was very excited to use my own personal fitness data for this, as my physical health and exercise has been a big part of my life. I was able to uncover some very interesting results through this project and the models developed are explainable and interpretable. Using cross validation and grid search procedures, an optimal logistic regression model with an accuracy of 0.75 was chosen as the final classifier. 

I'm happy to conclude that I can predict (and further optimize) my own physical health and well-being using machine-learning techniques and tools.
