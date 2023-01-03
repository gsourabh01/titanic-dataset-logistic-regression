# titanic-dataset-logistic-regression
We are going to build a Logistic Regression model using a training set of samples listing passengers who survived or did not survive the Titanic disaster. Then we check the performance of the model on a test dataset to evaluate how well the model is able to predict whether these passengers of the test dataset survived or not.

Let's get started:
 Step 1: Import Libraries
 Step 2: Read Datasets
 Step 3: Datasets Overview
         Training Dataset Overview:
         Test Dataset Overview
         In order to prevent data leakage, we need to prepare each of the Training and Test datasets separately. But first of all we concatenate the actual target values from df_submission to the test dataset.
         
 Step 3.1: Datasets Basic Information:
           Training Dataset Basic Information:
           Test Dataset Basic Information:
 Step 3.2: Datasets Numerical Columns Description:
           Training Dataset Numerical Columns Description:
           Test Dataset Numerical Columns Description:
 Step 3.3: Datasets Object Columns Description:
           Training Dataset Object Columns Description:
           Test Dataset Object Columns Description:
 Step 4: Deal with Missing Data in Training Dataset
         Next, we define a function that shows the distribution of missing values for each feature in the form of a graph. In this way, depending on the amount of missing values, we can decide how to deal with missing values in each feature:
 Step 4.1: Discover Missing Data in Training Dataset:
 Step 4.2: Age Missing Data Imputation
           Next, we will try to complete Age feature according to other features:
           We plot boxplots of Age versus the dataset categorical features. We also plot countplots of categorical features in parallel. We want to see that Age has different data distribution according to the categories of which of the features, so that we can use them to impute the missing data in Age.
           From the graphs above, it can be seen that Age has a different median value according to the different categories of Pcalss. There is also a large amount of samples in each category of PCalss. It seems that the missing values in Age can be imputed according to the median value of those samples with the same Pclass category. To be sure, we also check the correlation of features with Age.
           As can be seen, Pclass has the largest absolute value of correlation with Age. Therefore, we made sure that we can impute the missing values in Age with the median value of Age of samples with the same Pclass category.
          Age Missing Data Imputation:
Step 4.3: Embarked Missing Data Imputation:
          The percentage of missing data in Embarked:
Step 4.4: Drop Cabin:
          The percentage of missing data in Cabin:
          Most of the data of Cabin is missing. Therefore, this feature will not bring much information to the model and imputing it will bring a lot of noise. Therefore, we drop this feature:
          Now, the training dataset is cleared of any missing data:

Step 5: Deal with Missing Data in Test Dataset
Step 5.1: Discover Missing Data in Test Dataset:
Step 5.2: Age Missing Data Imputation:
          Similar to what was stated in training dataset cleaning, the missing values in Age again will be imputed according to the median of the age values of samples with the same Pcalss category:
Step 5.3: Fare Missing Data Imputation:
          The percentage of missing data in Fare:
          Since the number of missing values in Fare is very small compared to the total number of training dataset samples, we fill these missing values with the Median value of Fare:
Step 5.4: Drop Cabin:
          The percentage of missing data in Cabin:
          Again most of the data of Cabin is missing. Therefore, we drop this feature from test dataset:
          The test dataset was cleared of any missing data as well:

Step 6: Feature Subset Selection:
Step 6.1: Drop PassengerId & Name:
          Unique Values in PassengerId & Name:
          As can be seen, values of PassengerId & Name features are all unique and therefore these features act as identifiers and lack valuable information for the model. So we drop them from both datasets:
Step 6.2: Drop Ticket
          Let's check Ticket unique values:
          Since Ticket contains 681 unique values, and this number of values is very high compared to the number of dataset samples, it is better to drop this feature as well:

Step 7: EDA
Step 7.1: Target vs. Categorical Features Bivariate Analysis
Step 7.2: Target vs. Numerical Features Bivariate Analysis
Step 8: Categorical Features Encoding 
        Training Dataset Basic Information after Data Cleaning:
        We implement dummy encoding on categorical columns:
        Training Dataset Basic Information after Dummy Encoding:
        Test Dataset Basic Information after Dummy Encoding:
Step 9: Correlation Analysis
        Conclusion:
        Pcalss & Sex are the most important features in target estimation.
Step 10: Build Logistic Regression Model
Step 10.1: Determine Features & Target Variables
Step 10.2:  Train Logistic Regression Model
Step 11: Model Evaluation
Step 11.1: Predict X-test
Step 11.2: Plot Confusion Matrix
Step 11.3: Classification Report
Step 11.4: Calculate Performance Metrics
           Base Model Performance Metrics:
Step 11.5: Plot Curves
Step 11.5.1: Plot Precision-Recall Curve
Step 11.5.2: Plot ROC Curve
Step 12: Tune Logistic Regression Hyperparameters
         We try to find those hyperparameters values that are going to make our model boost out. It is possible to search the hyperparameter space for the best cross validation score using GridSearchCV. The grid search provided by GridSearchCV generates candidates from a grid of parameter values and choose the optimal values based on the desired metric:
Step 12.1: Define Base Estimator
Step 12.2: Create Param Grid
           The choice of the solver depends on the penalty chosen. Supported penalties by solvers are:
           Therefore, different combinations of solver and penalty should be considered:
Step 12.3: Create Grid Search Object
           We considered a Stratified 5-Folds Cross-validator for finding the optimal hyperparameters.
Step 12.4: Fit Grid Search Object on Training Data
Step 12.5: Choose Best Estimator Hyperparameters
Step 13: Final Model Evaluation
Step 13.1: Predict X-test
Step 13.2: Plot Final Model Confusion Matrix
Step 13.3: Final Model Classification Report
Step 13.4: Determine Final Model Performance Metrics
Step 13.5: Plot Final Model Curves
Step 13.5.1: Plot Final Model Precision-Recall Curve
Step 13.5.2: Plot Final Model ROC Curve
Step 14: Conclusion:
         Comparison of the Base Model to the Final Model:
         As can be seen, the performance of the model improves after tuning the hyperparameters.
Step 15: Submit Predicted Data:
