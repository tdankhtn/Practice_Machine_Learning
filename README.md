# Travel Insurance Prediction

## Table of Contents
- [Introduction](#introduction)
- [Dataset Description](#dataset-descriptiont)
- [Installation](#installation)
- [Data Analysis](#data-analysis)
- [Feature Engineering](#feature-engineering)
- [Model Training and Evaluation](#model-training-and-evaluation)
- [Results](#results)

## Introduction
This notebook performs a classification task aimed at predicting customer travel insurance purchases. The main objective is to predict "Churn rate," a marketing metric that describes the number of customers who leave a business over a specific time period. Each user is assigned a prediction value that estimates their churn status at any given time, based on the provided attributes.

## Dataset Description
The dataset contains the following attributes, used to predict whether a customer will purchase travel insurance:

- **Age**: Age Of The Customer
- **Employment Type**: The Sector In Which Customer Is Employed
- **GraduateOrNot**: Whether The Customer Is College Graduate Or Not
- **AnnualIncome**: The Yearly Income Of The Customer In Indian Rupees[Rounded To Nearest 50 Thousand Rupees]
- **FamilyMembers**: Number Of Members In Customer's Family
- **ChronicDisease**: Whether The Customer Suffers From Any Major Disease Or Conditions Like Diabetes/High BP or Asthama,etc.
- **FrequentFlyer**: Derived Data Based On Customer's History Of Booking Air Tickets On Atleast 4 Different Instances In The Last 2 Years[2017-2019].
- **EverTravelledAbroad**: Has The Customer Ever Travelled To A Foreign Country[Not Necessarily Using The Company's Services]
- **TravelInsurance**: Did The Customer Buy Travel Insurance Package During Introductory Offering Held In The Year 2019.

## Installation
To run this notebook, you need to install the following Python libraries:
- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`
- `scikit-learn (sklearn)`
- `imblearn (for SMOTE)`
- `ydata-profiling (for data analysis)`

You can install them using pip:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn imblearn ydata-profiling
```

## Data Analysis
The notebook performs initial data analysis, including:
- Identifying numerical and categorical columns.
- Checking for missing values in each column.
- Displaying basic statistical summaries of numerical columns to understand data distribution.
- Using ydata-profiling to generate a detailed data report, including statistics and warnings.

## Feature Engineering
To prepare the data for machine learning models, the following feature engineering steps are applied:
- Categorical columns are converted into numerical codes.
- The SMOTE oversampling technique is applied to balance the dataset, addressing imbalanced data cases.

## Model Training and Evaluation
The project uses the following machine learning models:
- Random Forest Classifier: An ensemble decision tree model.
- Logistic Regression: A linear classification model.
Both models are trained using GridSearchCV to find the best hyperparameters, ensuring optimal performance. The hyperparameters searched include:
- Random Forest: n_estimators, max_depth, min_samples_split, min_samples_leaf, max_features, bootstrap.
- Logistic Regression: C (inverse of regularization strength), penalty (l1 or l2), solver (lbfgs, liblinear, etc.).

Models are evaluated based on performance metrics such as accuracy_score, precision_score, recall_score, and f1_score, specifically f1_weighted for GridSearchCV.

## Results
- The best Random Forest model found optimal parameters such as max_depth=10, max_features='log2', min_samples_leaf=2, n_estimators=10.
- The best Logistic Regression model found C=10, penalty='l2', and solver='lbfgs'.

The notebook performs data splitting into training and testing sets (80/20 ratio) after applying SMOTE.
- Training set size: (2043, 8)
- Testing set size: (511, 8)

Detailed performance metrics for each model (e.g., accuracy, precision, recall, F1-score) are calculated after model training.