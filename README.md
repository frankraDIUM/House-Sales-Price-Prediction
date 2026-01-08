🏠 House Sales Price Prediction

Summary

RealAgents is a real estate company operating in a metropolitan area and selling multiple types of residential properties. Some properties take longer to sell and often require price reductions, reducing competitiveness and increasing holding costs.
The objective of this project was to predict house sale prices based on property characteristics, enabling RealAgents to optimize listing prices and reduce time on the market. 

Using a Baseline vs. Comparison modeling approach, I developed and evaluated two predictive models:

Baseline Model: Linear Regression
Comparison Model: Random Forest Regressor (with hyperparameter tuning)

The Random Forest model demonstrated superior predictive performance and is recommended for deployment.

🧾 Data Overview
The dataset contains historical records of house sales, including:
Property identifiers
Location (city)
Structural characteristics (bedrooms, house type, area)
Market behavior (months listed)
Sale price and sale date

Key Columns
Feature	Description
house_id	Unique identifier for each house
city	Location of the house
sale_price	Final sale price (target variable)
sale_date	Date of last sale
months_listed	Time on market
bedrooms	Number of bedrooms
house_type	Terraced, Semi-detached, Detached
area	House size in square meters


1. Data Cleaning & Preparation

To ensure modeling accuracy, the dataset was cleaned according to predefined business rules:

Cleaning Steps
City: Missing or invalid values replaced with "Unknown"
Sale Price: Rows with missing values removed
Sale Date: Missing values replaced with 2023-01-01
Months Listed: Missing values replaced with column mean (rounded to 1 decimal)
Bedrooms: Missing values replaced with mean (rounded to nearest integer)
House Type: Invalid entries standardized; missing values replaced with mode
Area: Text cleaned, converted to numeric, missing values replaced with mean

The cleaned dataset was stored as clean_data.


2. Exploratory Analysis
Impact of Bedrooms on Sale Price
To test the assumption that bedroom count drives price, average sale price and variance were calculated by bedroom count.

Bedrooms	Avg Price ($)	Variance
2	67,076.4	5.65e+08
3	154,665.1	2.38e+09
4	234,704.6	1.73e+09
5	301,515.9	2.48e+09
6	375,741.3	3.92e+09

📊 Insight:
Sale price increases consistently with the number of bedrooms, confirming it as a major price driver.


3. Modeling Strategy

A Baseline vs. Comparison approach was used:

🔹 Baseline Model — Linear Regression

Simple, interpretable benchmark
Requires feature scaling
Assumes linear relationships

🔹 Comparison Model — Random Forest Regressor

Captures non-linear relationships
Ensemble-based
Tuned using GridSearchCV


4. Model Training & Evaluation
Baseline Model Performance

Model: Linear Regression
Metric: Root Mean Squared Error (RMSE)
RMSE: Higher than comparison model

Predictions stored in base_result.

Comparison Model Performance
Model: Random Forest Regressor

Best Parameters:

max_depth: 8
n_estimators: 100
min_samples_leaf: 5
min_samples_split: 2


RMSE: 14,791.41

Predictions stored in compare_result.

📈 Result:
The Random Forest model significantly outperformed the baseline by better capturing complex interactions between property features.


5. Key Business Insights

Bedrooms are a major driver of sale price
Area and location strongly influence valuation
Time on market provides useful pricing signals
Non-linear feature interactions improve prediction accuracy

6. Final Recommendation

Recommend deploying the Random Forest Regressor for house price prediction.

 Benefits

More accurate listing prices
Reduced time-to-sale
Fewer reactive price reductions
Improved market competitiveness


Skills & Tools Used

Data Cleaning & Validation,
Feature Engineering,
Exploratory Data Analysis (EDA),
Regression Modeling,
Linear Regression,
Random Forest Regression,
Hyperparameter Tuning (GridSearchCV),
Model Evaluation (RMSE),
Python (Pandas, NumPy, Scikit-learn),
Business Insight Communication

Project Outcome (Summary)

This project demonstrates how machine learning-driven pricing strategies can help real estate companies optimize listings, shorten sales cycles, and improve decision-making using historical data.
