## Lead Scorring Logistic Regression

The analysis and logistic regression model building and implementation were performed for a company called **X Education** in order to identify the leads that are more likely to get converted into customers.


The following steps were performed during the course of the analysis and ML model building:
1. Data sourcing, EDA, pre-processing.
2. Model building.
3. Model evaluation.



### 1. Data Sourcing, EDA, Pre-Processing
#### 1.1 Data Sourcing
 
The leads data set with 9240 rows and 37 columns came from X Education. No duplicate rows were found in the data set.

#### 1.2 Data Cleaning
 
Some categorical columns contained the value Select, which is as good as NaN, as it indicates that the user didn't choose any of the options in the drop-down menu of a question. Therefore, Select was replaced with a NaN.

Some columns had a large amount of missing values. A threshold of 40% was chosen for the missing data. After removing these columns, 29 remained.

In most of the categorical columns, the most occurring value was chosen in order to impute the missing values. In the column Specialization, the difference between the value counts was not big, so instead of assigning the most occurring value, the missing values were grouped into Unknown category.

Some of the categorical columns were highly imbalanced. The columns, where one value took 90% or more, were removed. 12 columns were left.

As the columns TotalVisits and Page Views Per Visit had outliers, the missing values were replaced with the medians for those columns.

The columns Lead Source, Last Activity, Specialization and Last Notable Activity had too many categories. Some of these categories had very few observations. A new category Other was created in order to store the categories having less than 500 observations.

#### 1.3 EDA
 
Univariate and bivariate analyses were conducted and here are the acquired insights:
 
1. The leads mostly originate from landing a page submission or through the API.
2. The three main sources of leads are: Google, Direct Traffic, Olark Chat.
3. Email Opened and SMS Sent are the most occurring last activities.
4. Out of known specializations, the ones connected to management are more popular with the leads.
5. Most of the leads are unemployed.
6. Around 70% of the people don't want a free copy of 'Mastering The Interview'.
7. The most occurring last notable activity is Modified, with Email Opened and SMS Sent being second and third respectively.
8. In the column Lead Origin, much more leads that originated from the lead add forms got converted than not. Lead add form can be a good indicator of a lead becoming converted.
9. The percentage of converted leads is much higher than non-converted among the leads that were referred to X Education. Being referred can be a good indicator of a future conversion.
10. Most leads among working professionals got converted, which can be explained by their motivation to get better career prospects at the place of their current employment. Lead being a working professional can be a good indicator of a lead becoming converted.
11. Last Notable Activity and Last Activity columns are almost the same, therefore, one of them can be dropped.


#### 1.4 Pre-processing
 
Dummy variables were created for the categorical columns.
The train-test split was conducted.
The numerical variables of the train set were standardized.
A correlation matrix was plotted, some of the variables were highly correlated.

### 2. Model Building
 
RFE was used to select 15 features for the model.
A logistic regression model was built using statsmodels.api.
The multicollinearity and significance of the variables were checked using the VIF scores and p-values. If a variable was insignificant or had high multicollinearity, it was removed and the process was repeated. In the end, 9 features were left in the final model.


### 3. Model Evaluation
 
After checking the accuracy, sensitivity and specificity for different probability cutoffs, the final cutoff of 0.36 was chosen, which gave 0.794 Accuracy score, 0.802 Sensitivity and 0.789 Specificity.
 
After standardizing the numerical variables of the test set, the predictions on the test set were made. The model was performing well on the test set, giving 0.785 Accuracy score, 0.799 Sensitivity score and 0.777 Specificity score.
