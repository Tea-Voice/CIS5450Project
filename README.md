# CIS5450Project
This is the repository for CIS5450 course project for Spring 2026


## CIS 5450 Project Proposal: 
# Predictive Modeling for DoorDash ETA Marketplace 
Targeting Delivery Latency and Supply-Demand Dynamics using DoorDash Data


# Group Members & Responsibilities
Mingtian Chen: Lead Architect (Feature Engineering, Model Selection).
Shidian Tian: Data Engineer (ETL pipeline, handling nulls/outliers).
Linchong Hu: Insights Lead (EDA, Visualizing supply/demand curves).
Wenyu Yang: Statistical Lead (Hypothesis testing, P-value calculation, final interpretation).

# Data Source
Kaggle Dataset Link: https://www.kaggle.com/datasets/dharun4772/doordash-eta-prediction?resource=download 
We will use a publicly available DoorDash delivery dataset (historical_data.csv) containing approximately 197,000 records. Each row represents a delivery order with structured features including timestamps, order details, store information, and marketplace conditions (e.g., number of available and busy dashers).
The dataset satisfies the project requirements:
It is publicly available and legal to use
It contains well over 50,000 rows after cleaning
It includes a rich set of structured features suitable for analysis and modeling

# Objective and Value Proposition
The goal of this project is to understand and predict delivery times in a food delivery marketplace setting.
More specifically, we want to answer:
What factors most influence delivery time?
How do supply-demand conditions (e.g., busy dashers, outstanding orders) affect delays?
Can we build a model that reasonably predicts delivery duration at the time an order is placed?
This problem is interesting because delivery time estimation is critical to user experience in real-world platforms like DoorDash or Uber Eats. By analyzing this dataset, we can explore how operational and marketplace factors impact performance.

# Modeling Plan
Our primary task is a regression problem, where the target variable is:
Delivery duration (in seconds)
 (calculated from created_at to actual_delivery_time)
Duration = actual_delivery_time - created_at
We plan to:
Start with a baseline linear regression model
Then experiment with a tree-based model such as Random Forest
We will incorporate features such as:
Time-based features (hour of day, day of week)
Order complexity (number of items, subtotal, etc.)
Store characteristics (category)
Marketplace conditions (busy dashers, outstanding orders)
Precomputed duration estimates provided in the dataset
We will evaluate model performance using metrics such as RMSE and MAE.
We will split the dataset into training and test sets (e.g., 80/20) and use cross-validation where appropriate to ensure robust evaluation.
Phase
Model
Purpose
Baseline
OLS Linear Regression
Establish a performance floor and check for feature collinearity.
Advanced
XGBoost / LightGBM
Capture non-linear relationships and handle categorical features (Store Category) efficiently.
Refinement
Random Forest
Use Feature Importance plots to rank which factors (e.g., "Busy Dashers") actually drive delays.


# Hypothesis Testing
We plan to test several hypotheses related to delivery performance.
Example hypotheses:
Effect of marketplace congestion
H0: Marketplace congestion (e.g., high number of busy dashers) does not affect delivery time
H1: Higher congestion leads to longer delivery times
Effect of peak hours
H0: Orders placed during peak hours do not take longer than non-peak hours
H1: Peak-hour orders have longer delivery times
Effect of order complexity
H0: Order size/complexity does not affect delivery duration
H1: Larger or more complex orders take longer
We will use statistical tests such as t-tests and, if appropriate, simulation-based methods covered in class to evaluate these hypotheses.

# Anticipated Obstacles & Challenges
We expect a few challenges:
Handling missing or noisy data (e.g., invalid timestamps or price values)
Feature engineering, especially for time-based and marketplace variables
Dealing with skewed distributions in delivery times
Ensuring that our model does not overfit given the number of features
We will address these by careful data cleaning, exploratory analysis, and model validation.

