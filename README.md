# Predicting Telecom Churn With AI


![coverphoto.png](https://github.com/jaybee202/mod3_project/blob/master/images/coverphoto.png)

### Items in Repository:

- README.md - a summary of the repository content
- /images - all images
- /data - all data files pertaining to the Telecom Churn  data set and processed data files
- /presentation - PowerPoint and pdf files of the final presentation
- /project_kickoff - Onboarding project documents provided at the start of this project
- /step01_data_cleaning_EDA 
  - /step01a - data assessment and cleaning
  - /step01b - exploratory data analysis 
- /step02_train_test_split_ohe_and_ss 
  - /step02a - data splitting to test and train files
  - /step02b - feature engineering and scaling 
- /step03_model_selection - data modeling with logistic, decision tree, random forrest, K-nearest neighbor, gradient boosting classifier
- /step04_hyperparameter_tuning - Files used to tune our models to find the best parameters on our train data set
- /step05_format_test_data - a file for formating the test data so it matches our train data
- /step06_fitting_test_data - a file for testing our models with the test data and providing evaluation metrics (confusion matrix, roc curve) for model comparisons

### Prompt:
Customer churn, also known as customer turnover, is a major concern in the competitive telecom industry. With the abundance of attractive wireless plans provided by different telecom companies, SyriaTel has faced major challenges retaining their customers. Therefore, they have hired us to create a model that can assess which customers are at risk of canceling their plans “soon”. SyriaTel would like to detect these customers as early as possible to maintain long lasting relationships because when a customer leaves, the company might not recover from the cost of acquiring the customer. 

### Goal:

1.	Analyze data set to identify different feature trends between retained and lost customers
2.	Build a binary classifier to predict whether a customer will cancel their phone plan with SyriaTel



### Results:

- Default random forest and gradient boosting classifier were the top 2 models. 

  ![roc_curve.png](https://github.com/jaybee202/mod3_project/blob/master/images/roc_curve.png)

- Random forest had slightly better evalutation metric scores

  ![confusionmatrix.png](https://github.com/jaybee202/mod3_project/blob/master/images/confusionmatrix.png)

### Methodology:

1.	Assess the data: check for null values and outliers
2.	Feature engineer: create new features that will provide us with more information (one hot encoder was used)
3.	Perform exploratory data analysis to pick up trends from the data
4.	Split data into train and test files
5.	Apply standard scaler to numeric data set
6.	Fit the train data to different vanilla models (Logistic, KNN, Decision Trees, Random Forest, Gradient Boosting Classifier)
7.	Utilize gridsearch to do hyperparameter tuning on train data set
8.	Test the best performing models with test data and compare evaluation scores (focussed on precision)

#### Data description: 

https://github.com/jaybee202/mod3_project/tree/master/data

Telecom Churn Dataset: 3333 rows x 22 columns

- Categorical features:
  - Dependent variable: 
    - churn: 1 for yes, 0 for no 
  - International_plan: 
    - Yes ('x1_yes'), if user has the international plan
    - No, if the user does not have the international plan
  - Voice_mail_plan:
    - Yes ('x2_yes'), if user has the international plan
    - No, if the user does not have the international plan

- Numerical features:

    - Account_length: number of days the user has this account
        - similar distribution between maintain and lost customer 
    - Number_vmail_messages: the number of voicemail messages the user has
        - majority (~72%) have 0 voicemails because most users do not have a voicemail plan

    **Phone usage** (eve - evening, intl - international)

    - total_day_minutes, total_eve_minutes, total_night_minutes, total_intl_minutes
    - total_minutes: total_day_minutes + total_eve_minutes + total_night_minutes + total_intl_minutes
    - total_day_calls, total_eve_calls, total_night_calls, total_intl_calls
    - total_calls: total_day_calls +  total_eve_calls + total_night_calls + total_intl_calls

    **Phone Bill** (USD)

    - total_day_charge, total_eve_charge, total_night_charge, total_intl_charge
    - total_charge: total_day_charge + total_eve_charge + total_night_charge + total_intl_charge



### Exploratory Data Analysis: 

**Figure 1. 84.5% (0 - maintain customer) vs 14.5%  (1 - churn/lost customer) **  

![num_customers.png](https://github.com/jaybee202/mod3_project/blob/master/images/num_cutomers.png)

<br/>

**Figure 2: Lost Customers have higher total minutes**

![phone_usage.png](https://github.com/jaybee202/mod3_project/blob/master/images/phone_usage.png)
<br/>

**Figure 3: Lost Customers have a higher cost**

![phone_bill.png](https://github.com/jaybee202/mod3_project/blob/master/images/phone_bill.png)
<br/>

**Figure 4: More lost customers make over 4 customer service calls**

![customer_service_calls.png](https://github.com/jaybee202/mod3_project/blob/master/images/customer_service_calls.png)
<br/>



### Recommendations:

- Monitor customers that use **over 600 minutes** with a **bill over $60**
- Offer promotions to customers who have made **over four** customer service calls
- Provide a survey to customers when they leave to augment existing data

### Next Steps:

- Improve the current model with additional data from Syriatel to **better predict** customer turnover
- Explore machine learning solutions for Sytriatel’s **customer service department** to mitigate customer attrition
- Conduct a **sentiment analysis** of Syriatel’s customers to discover issues not present in operational databases <br/>



