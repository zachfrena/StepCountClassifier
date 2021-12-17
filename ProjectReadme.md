# **Background on your code files**

- My project notebook is called `FinalProject.ipynb`. It uses standard imports and prints out the project flow diagram from mglearn. 

0. Functions are defined for validating, visualizing, printing, various models in the workflow.

1. Data is loaded from CSV, then split into X and y after being cleaned, processed, and visualized.

2. Encoding the non-numerical columns in the feature matrix.

3. Feature Correlation between the various columns in the feature matrix.

4. Create training and test sets using scikit-learn's train_test_split() method.

5. Perform 7-fold cross-validation on list of models (`LogisticRegression()`, `SVC()`, `BernoulliNB()`, `RandomForestClassifier()`, `GradientBoostingClassifier()`) to determine top 3 models based on **average precision**.

6. Hyperparameter tuning the top 3 models using grid search. For each model, print/plot: best parameters, accuracy scores, and a heatmap of grid-search results. 

7. Discuss which model is "the best"-- discuss overfitting, underfitting, accuracy, etc.

8. Retrain the best model using the tuned hyperparameters found in previous grid search. Display F1 score and plot confusion matrix.

9. Determine relative importance of features. Discuss why this is useful and how the model can be interpreted.



# **How to run your code, guide to install any additional packages**

The notebook code should be run **in-order**, and the only issue that may arise is a pandas.read_csv error if the CSV data was removed from the current directory. There are no additional packages to install (mglearn may be new to some users), and all imports are standard for scikit-learn.

# **Results, interpretation and reflection**

**Scattered throughout the notebook are results (intermediate and final), interpretation of data, and personal reflections/discussions.**


As mentioned in the project proposal, the Garmin Fenix 6 Pro is a wearable device that allows a user to track overall health metrics and log exercises and activities. The watch owner has the ability to select from 30-40 different default activities (hiking, swimming, jogging, climbing, etc.), and there is the opportunity to add custom ones as well.

<img src=https://github.com/ensf611-fall-2021/ml-project-zachfrena/blob/main/images/garmin_activity_select.JPG width = "600">


The data from this project was collected from my personal Garmin device through the Garmin Connect App (a online tool for tracking, analyzing, visualizing and sharing health and fitness activities). The final dataset contains activities/exercises collected during the period of 11 months (Jan-Nov 2021). While there are many detailed reports and insights generated through the Connect App, it was clear that a more customized dataset was required for analysis. 

<img src=https://github.com/ensf611-fall-2021/ml-project-zachfrena/blob/main/images/garmin_connect_dashboard.JPG width = "600">


## Where there deviations from proposal? Explain why (or why not).
There was very little deviation from the original project proposal. As discussed, this problem can be treated as either a regression (e.g. predict the number of steps) or classification task (e.g. predict whether you will surpass your step threshold value). In this project I treated it as a classification task, however I am very interested in exploring regression in the future!
I achieved only one of the 2 total stretch goals (I completed the hyperparameter tuning using grid search with 7-fold cross-validation) but was unable to find a better decision threshold due to lack of time. In hindsight, I realize that finding a better decision threshold isn't even critical or important since we don't need to optimize for a high recall score (i.e. there are no real-world downsides/penalties for false negatives). I also added a couple new visualizations that I did not plan out when starting the project: 1) correlation matrix across features, and 2) relative importance of features compared. 


## Things that could have been done better:
When plotting the correlation matrix, I noticed that there was a possibility we would run into a `multicollinearity` scenario. This would ultimately reduce the stability of the coefficient estimates, which weakens the power of the classification model. It would have been a good idea to identify and isolate all independent variables that are statistically significant, and only keep those for training purposes. For any pair of features that had a correlation value higher than 85%, I could have deleted one of them. Another method to combat this issue would be to use a dimension reduction algorithm such as Principle Component Analysis (PCA). While the final accuracy score of 0.75 was impressive, I feel that having additional data points would have made the entire process more refined and the model would perform much better when trained on additional samples.

## Conclusion:
The topic I set out to investigate was how effectively fitness and health outcomes can be predicted when provided metrics surrounding daily fitness activities. I was very excited to use my own personal fitness data for this, as my physical health and exercise has been a big part of my life. I was able to uncover some very interesting results through this project and the models developed are explainable and interpretable. Using cross validation and grid search procedures, an optimal logistic regression model with an accuracy of 0.75 was chosen as the final classifier. 

I'm happy to conclude that I can predict (and further optimize) my own physical health and well-being using machine-learning techniques and tools.
