# HR Attrition Analysis & Prediction

## People Analytics | Machine Learning Classification
---

### TABLE OF CONTENTS
- [Introduction](#introduction)
- [Purpose of the Analysis](#purpose-of-the-analysis)
- [Dataset Overview](#dataset-overview)
- [Data Exploration](#data-exploration)
- [Data Cleaning and Preparation](#data-cleaning-and-preparation)
- [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
- [Machine Learning Modeling](#machine-learning-modeling)
- [Data Preprocessing](#data-preprocessing)
- [Modeling workflow](#modeling-workflow)
- [Evaluation Metrics](#evaluation-metrics)


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
---
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


## Key Insights and Findings
#### **Top Drivers of Attrition**
  - Departments /  Job roles
  - Gender
  - Education level
  - Age
  - Stock level
  - Carreer And Job duration
  
  1. Department and Job Role Drivers:
       - Employee attrition is most concentrated in the Research & Development **(65.4%)** and Sales **(30.3%)** departments.
      - Specific job roles with consistently higher attrition include Laboratory Technician,  Sales Executive, Research Scientist, and Sales Representative.
      - These roles are largely operational and customer-facing, indicating higher workload and performance pressure.
  **Insight:**
  Attrition risk is role-driven rather than evenly distributed across the organization.
  2. Gender Distribution:
      - Male employees account for a higher proportion of attrition **(63.3%)** compared to female employees **(36.7%).**
  **Insight:**
  While gender alone is not a causal factor, the disparity suggests role concentration and workload exposure may differ across genders.
  3. Education Level Impact:
      - Attrition is more prevalent among employees with mid-level qualifications (Master’s degree), followed by Doctorate and Bachelor’s degree holders.
  **Insight:**
  Highly educated employees may experience misalignment between expectations, career growth, and actual job roles.
  4. Career Stage and Job Duration:
       - Attrition is significantly higher among early-career employees, particularly those with 0–5 years of experience.
       - Early exits are strongly associated with Job Level 1, indicating challenges with onboarding, role clarity, or career progression.
  **Insight:**
  Early-stage attrition represents the most critical retention risk and cost to the organization.
  5. Engagement and Work Conditions:
        - Employees with lower job satisfaction and engagement levels are more likely to leave.
        - Single (unmarried) employees show higher attrition rates.
        - Employees without stock options experience higher attrition.
  **Insight:**
  Retention is influenced more by engagement, incentives, and perceived value than by tenure or performance alone.

**Modeling and Predictive Performance**
  - Addressing class imbalance using SMOTE improved the model’s ability to detect attrition cases.
  - The final classification model demonstrates strong predictive performance based on the classification report and evaluation metrics.
  **Insight:**    
  Predictive modeling can effectively support early identification of high-risk employees.

## **Recommendations**
1. Target High-Risk Departments and Roles
    - Implement role-specific retention strategies for Sales and R&D functions.
    - Introduce workload balancing, role rotation, and clearer performance expectations for high-pressure roles.

2. Strengthen Early-Career Retention
    - Improve onboarding programs with structured mentorship for Job Level 1 employees.
    - Define clear career progression paths within the first 12–24 months of employment.
    - Conduct early engagement check-ins for employees within their first 6 months.

3. Align Career Growth with Education Level
    - Offer growth opportunities, advanced projects, or leadership tracks for highly educated employees.
    - Ensure role responsibilities match employee qualifications to reduce dissatisfaction and early exits.

4. Improve Engagement and Incentive Programs
    - Invest in engagement initiatives such as flexible work policies, recognition programs, and manager effectiveness training.
    - Expand access to stock options or performance-based incentives, especially for high-performing employees.

5. Use Predictive Analytics for Proactive HR Decisions
    - Integrate the attrition prediction model into HR dashboards to flag at-risk employees early.
    - Combine model outputs with satisfaction surveys and manager feedback to guide targeted interventions.

     ### **Summary**

This analysis highlights that employee attrition is driven primarily by role pressure, gender distribution, early-career challenges, engagement levels, and incentive structures. By combining exploratory data analysis with machine learning, the organization can proactively identify at-risk employees and implement targeted retention strategies to reduce turnover and associated costs.


