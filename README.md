
# Customer Churn Analysis and Prediction

## Problem Statement

A telecom company is experiencing high customer churn and wants to focus on retention, which is more cost-effective than acquiring new customers. The business aims to:
(1) identify factors driving churn, 
(2) predict at-risk customers, and 
(3) recommend actions to improve retention.

## Dataset 
Telco Customer Churn dataset (Source: Kaggle)
Features: 

-- Demographics: Gender, SeniorCitizen, Dependents.

-- Services: Internet, Phone, Online Security, Backup, Tech Support, Streaming.

-- Billing/Contract: Contract type, Payment method, Monthly & Total Charges.

-- Target: Churn (Yes / No).

## Data Cleaning 

-- Converted TotalCharges from string → numeric.

-- Filled missing values (new customers had tenure = 0 → TotalCharges = 0).

-- Removed duplicates.

-- Added derived features:

    1. RPU (Revenue Per User) = TotalCharges / tenure

    2. NumServices = count of add-on services subscribed.

    3. TenureGroup = grouped customers into 0–12, 12–24, … months.

Clean dataset saved as Cleaned_Telco_Churn.csv for further analysis
