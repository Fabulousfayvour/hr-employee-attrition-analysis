# HR Attrition Analysis & Prediction

## People Analytics | Machine Learning Classification
---
## Introduction

Employee attrition is a critical challenge for organizations, impacting productivity, hiring costs, and overall business performance. This project analyzes an HR dataset to uncover key drivers of employee attrition and builds a machine learning model to predict the likelihood of an employee leaving the organization.

## Purpose of the Analysis

**The objectives of this project are to:**

- Understand patterns and factors contributing to employee attrition
- Identify key employee attributes linked to higher attrition rates
- Build and evaluate a machine learning model to predict attrition
- Provide actionable, data-driven recommendations for HR decision-making

## Dataset Overview

**The dataset contains employee-level HR information, including:**

- Demographics (e.g., age, gender)
- Job-related features (department, role, job level)
- Compensation and benefits
- Work conditions and satisfaction indicators
- Attrition status (target variable)
  
**The target variable Attrition indicates whether an employee left the company (Yes) or stayed (No).**

## Data Exploration
**After importation, the dataset was examined with the following steps:**
  - Displaying the first 10 rows - `df.head(10)`
  - Checked the data shape, given count of 1,470 rows and 35 columns - `df.shape`
  - Got information about the whole data using: `df.info()`
  - Analaysing the statistical descriptiom of the numerical variables using: `df.describe()`

## Data Cleaning and Preparation
- Checking and handling missing values -- Zero null values were found.
- Handling duplicate records -- The dataset recorded no duplicates.

## Data Preprocessing
**Key preprocessing steps included:**
-Encoding categorical variables (including the target vector) using Label Encoding
- Separating features and target variable 
- Handling class imbalance using SMOTE (Synthetic Minority Oversampling Technique)
- Scaling numerical features
**(Feature scaling was applied using StandardScaler to support SMOTE and ensure preprocessing consistency, although the final model (Random Forest) is not sensitive to feature scaling.)**

  **These steps ensured the data was suitable for both analysis and machine learning modeling.**

## Exploratory Data Analysis (EDA)
**EDA was performed to uncover trends and patterns related to attrition, including:**

- **Attrition overview:**
  
   |No |1233|
   | ----- | ----- |
   |Yes|237|

- Attrition Rate is 16.12%
- Distribution of attrition across departments and gender.
  
  |Department           |Gender| Attrition|    |
  | ---- | ---- | ---- | ---- |
  |Human Resources|         Female|No|         14|
  |               |                |Yes|        6|
  |                |        Male|    No|       37|
  |                |              |  Yes|       6|
  |Research & Development|  Female|  No|      336|
  |                     |         |Yes|       43|
  |                      |Male   | No|       492|
  |                       |       |Yes |       90|
  |Sales                  | Female|  No|      151|
  |                       |        |Yes|      38|
  |                       | Male|    No |     203|
  |                      |        |Yes|       54|


- Distribution of attrition across departments and job roles
- Relationship between attrition and factors such as job satisfaction, income, and work conditions
- Comparison of numerical feature distributions between employees who stayed and those who left
- Identification of high-risk employee segments
- Relationship between Department and Employee Attrition using **seaborn**
- The total number of employees in each department was calculated and visualized using **pie-chart in Matplotlib**

Visualizations and summary statistics were used to support insights.

