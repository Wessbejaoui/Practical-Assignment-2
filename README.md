# Practical-Assignment-2
## Helping Dealers With Car Dilemma

# Business Understanding 
The business goal of identifying key drivers of used car prices can be reframed as a supervised regression task. Specifically, we aim to predict the market price of a used vehicle based on a set of input features such as mileage, age, make, model, condition, and drivetrain.
The target variable is price, and the objective is to train a model that can estimate this value with high accuracy, enabling the dealership to make data-driven decisions on inventory acquisition and pricing strategies.

# Data Understanding

  Structure & Content:
*  The dataset has 426,880 records and 18 columns.
*  The data includes a mix of numeric features (price, odometer, year) and categorical variables (e.g., manufacturer, condition, transmission).
*  Target variable: Price

  Data Quality Assessment:
* Missing Values:
    * Substantial missing data in critical fields like condition (174K missing), cylinders (177K), VIN, and drive.
    * Lighter missingness in fuel, transmission, title_status, odometer, and year.
* Outliers and Irregularities:
    * Price ranges from 0 to nearly $3.7 billion — clear need for outlier filtering.
    * Year ranges from 1900 to 2022 — some may be vintage or erroneous.
    * Odometer shows a max of 10 million miles — likely errors or edge cases.

* Inconsistencies in Categorical Data:
    * High cardinality in model (~30K unique), which may be too granular for modeling.
    * Some categorical features (drive, fuel, condition) have manageable value counts.


The dataset has key variables such as:
* Target variable: Price
* Useful factors: Year, manufacturer, model, condition, cylinders, odometer, fuel, transmission, type, etc.

Missing data is notable in fields like:
* Condition, cylinders, VIN, size, and paint color.
* Some rows are nearly empty (likely noisy or unhelpful).

# Data Preparation

Data Cleaning & Filtering
* Drop rows missing key fields: year, odometer, manufacturer, etc.
* Remove outliers:
  * Price outside the $500–$100,000 range
  * Odometer under 1,000 or over 300,000
  * Vehicles older than 100 years

Feature Engineering
* Create a new feature: age = 2025 - year
* Remove unused or irrelevant fields: id, region, VIN, paint_color, state

Data Transformation
* Separate features (X) and target (y)
* Use StandardScaler for numeric features and OneHotEncoder for categorical features through ColumnTransformer
    * Training set: 94,439 rows
    * Test set: 23,610 rows

# Modeling
* Aim: Predict price using regression models (linear regression, random forest).
* Evaluate feature importance to explain what factors drive price.

# Evaluation
* Identify which features most influence price (odometer, brand, condition).
* Assess model performance with linear regression, MAE, etc.
* Extract insights for dealers ("Low-mileage SUVs from top brands command premium prices").

# Deployment

# Used Car Price Analysis: Insights & Recommendations
Prepared For: Used Car Dealership Partners

Prepared By: Wassim Bejaoui

Date: 08/12/2025

# Objective
Our goal was to uncover the key factors that influence the price of used cars to help your dealership make smarter inventory and pricing decisions. Using a dataset of over 426,000 used vehicles, we built a predictive model and conducted a deep dive into the data to identify patterns and pricing drivers.

# Approach

We followed the CRISP-DM methodology, focusing on:

* Business Understanding: Identify what makes a car more or less expensive.

* Data Understanding & Cleaning: Remove invalid entries and outliers; engineer features such as vehicle age.

* Modeling: Build and evaluate a machine learning model to predict price.

* Evaluation & Insights: Analyze which factors matter most and translate them into business value

  # Key Findings
* Condition & Wear: Age and odometer reading are the strongest predictors of price.

* Newer cars and those with lower mileage command a higher value.

* Brand & Model: Vehicles from brands like Toyota, Honda, and Ford retain value well.

* Even within brands, certain models stand out for their resale strength.

* Type & Features: SUVs and trucks consistently sell for more than sedans or coupes.

* 4WD/AWD drive systems boost price, especially in trucks and larger vehicles.

* Other Factors: Condition descriptions (“excellent”, “like new”) significantly increase price.

* Transmission type and fuel type have a moderate impact but are less critical.

<img width="800" height="600" alt="image" src="https://github.com/user-attachments/assets/fe85ca85-7c27-4456-85fd-e42a5f6638ac" />

<img width="800" height="600" alt="image" src="https://github.com/user-attachments/assets/94c42eae-d83a-46a7-947d-75cdd661e409" />

<img width="800" height="600" alt="image" src="https://github.com/user-attachments/assets/07d56a14-d382-4971-8fba-f1bdede3b923" />


