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

## Exploratory Data Analysis (EDA)
**Summary statistics and Data visualization**
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


- Distribution of attrition across departments and job roles Using **bar-chart and Heat-map**.
- Relation between gender and Employee Attrition
- Relationship between attrition and factors such as job satisfaction, income, and work conditions
- Comparison of numerical feature distributions between employees who stayed and those who left
- Identification of high-risk employee segments
- Relationship between Department and Employee Attrition using **seaborn**
- The total number of employees in each department was calculated and visualized using **pie-chart in Matplotlib**, **Research & Development** was recorded with **#960 employees** having the highest number of employee and **attrition rate of 65.4%**
- Visualized Relation between Total Working Years, the Working Years at the Company and the Years Since Last Promotion of Former Employees using **scatter-plot in Seanorn**.
- Correlation between features
    <img width="1057" height="685" alt="image" src="https://github.com/user-attachments/assets/e6456fdb-5db6-4c10-8b70-d9147eddc431" />
    
**Summary of Key Insights from the correlation Heatmap**

The correlation heatmap reveals strong relationships among tenure-related variables and between compensation and job level, while job satisfaction and overtime remain weakly correlated with income and experience. This indicates that attrition risk is influenced more by engagement and career dynamics than by salary alone.

## Machine Learning Modeling
**This project applies supervised machine learning (classification) to predict employee attrition.**

## Data Preprocessing
**Key preprocessing steps included:**
-Encoding categorical variables (including the target vector) using Label Encoding
- Separating features and target variable 
- Handling class imbalance using SMOTE (Synthetic Minority Oversampling Technique)
- Scaling numerical features
**(Feature scaling was applied using StandardScaler to support SMOTE and ensure preprocessing consistency, although the final model (Random Forest) is not sensitive to feature scaling.)**

  **These steps ensured the data was suitable for both analysis and machine learning modeling.**

### Modeling workflow:

  - Train-test data split
  - Features selection - Removing some irrelevant input variables (features) that does not contribute the most to predicting the target variable [e.g, 'StandardHours', 'EmployeeNumber', 'Over18' etc]
  - Handling imbalanced classes using SMOTE
  - Model training using a **Random Forest Classifier**
  - Model evaluation using performance metrics

## Evaluation Metrics

  - **Model Accuracy Score: 90.28%** -
The Model Accuracy is High (above 80%) → The model can reliably predict employee attrition.

 **Classification Report**
    

      Classification Report:
                   precision    recall  f1-score   support
    
               0       0.89      0.93      0.91       250
               1       0.92      0.88      0.90       244
    
        accuracy                           0.90       494
       macro avg       0.90      0.90      0.90       494
    weighted avg       0.90      0.90      0.90       494


**Confusion matrix analysis**

<img width="539" height="453" alt="image" src="https://github.com/user-attachments/assets/34db64ac-a2ab-443c-b704-d8233d269d1c" />


 **Key Insights from the confusion matrix**
 
True Negatives (232):
231 employees were correctly predicted as "Stayed" (Class 0).
✅ This is good; the model correctly identifies most employees who won't leave.

False Positives (18):
19 employees were predicted to leave but actually stayed.
⚠️ A slight misclassification, but not too bad.

False Negatives (0):
No employees who actually left were misclassified.
✅ This is excellent! The model is detecting all employees at risk of attrition (Class 1).

True Positives (125):
125 employees were correctly predicted as "Left".
✅ The model is successfully recognizing employees who actually left.
These metrics help assess the model’s ability to correctly identify employees at risk of leaving.

