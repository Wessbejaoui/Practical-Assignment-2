# Practical-Assignment-2
## Helping Dealers With Car Dilemma

# Business Understanding 
The business goal of identifying key drivers of used car prices can be reframed as a supervised regression task. Specifically, we aim to predict the market price of a used vehicle based on a set of input features such as mileage, age, make, model, condition, and drivetrain.
The target variable is price, and the objective is to train a model that can estimate this value with high accuracy, enabling the dealership to make data-driven decisions on inventory acquisition and pricing strategies.

# Objective
Our goal was to uncover the key factors that influence the price of used cars to help your dealership make smarter inventory and pricing decisions. Using a dataset of over 426,000 used vehicles, we built a predictive model and conducted a deep dive into the data to identify patterns and pricing drivers.

# Approach

We followed the CRISP-DM methodology, focusing on:

* Business Understanding: Identify what makes a car more or less expensive.
* Data Understanding & Cleaning: Remove invalid entries and outliers; engineer features such as vehicle age.
* Modeling: Build and evaluate a machine learning model to predict price.
* Evaluation & Insights: Analyze which factors matter most and translate them into business value.

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

# Data Preparation:

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

# Data interpretations:

<img width="963" height="566" alt="image" src="https://github.com/user-attachments/assets/54ae6bf9-286f-4043-af47-8978c2cdb33a" />

This histogram shows the price distribution of used cars priced between $500 and $100,000. Outliers (extremely high or low values) have been excluded to better reflect realistic market pricing.

## Key Insights
  1-  Right-Skewed Distribution (Long Tail)
  * Most used cars are priced between $5,000 and $25,000, with a steep drop-off beyond $30,000.
  * A smaller but steady number of vehicles exist in the $30,000–$60,000 range — typically newer, luxury, or high-performance models.
  * This shape is expected in used car markets where affordability dominates consumer demand.

  2- Peak Market Range (High Demand Zone)
  * The highest density of listings falls around $8,000–$15,000 — the “sweet spot” for average buyers seeking reliable, mid-range vehicles.
  * Dealerships can focus on stocking cars within this range to maximize turnover and match mainstream consumer budgets.
  
  3- Inventory Diversification Opportunity
  * While low-to-mid priced vehicles dominate, there’s still visible interest up to $50,000, suggesting a smaller premium market worth maintaining for margin diversity.
  
  4- Implications for Pricing Strategy
  * Competitive pricing in the $8K–$20K segment is critical; margins here are thinner due to high competition.
  * Higher-end cars ($30K–$60K) may warrant personalized marketing and financing offers to move slower inventory.

<img width="966" height="566" alt="image" src="https://github.com/user-attachments/assets/4225cd07-88ed-4672-95fc-06f74d78ddcc" />

This scatter plot shows the relationship between a car’s manufacture year and its price (filtered for values under $100,000 to exclude outliers). The red regression line indicates the overall trend.

## Key Insights

  1- Strong Positive Correlation
  * As expected, newer vehicles tend to command higher prices.
  * The upward trend shown by the regression line confirms that model year is a key driver of price, reflecting consumer preference for more recent technology, safety features, and lower mileage.

  2- Wide Price Variability Across Years
  * Even among newer vehicles (post-2015), there’s significant spread in prices.
  * This suggests that brand, mileage, and vehicle type play a major role in determining value beyond age alone.
  * Older vehicles (pre-2005) generally cluster below $20,000, consistent with depreciation effects.

  3- Depreciation Pattern
  * Cars lose value quickly in their first few years, then stabilize in price.
  * This trend highlights how certified pre-owned vehicles (2–5 years old) retain higher resale value and attract strong consumer interest.


    <img width="1144" height="566" alt="image" src="https://github.com/user-attachments/assets/e804d7e1-1f52-43bd-bc64-22e5a38e0fe8" />

This plot displays the distribution of used car prices across the top 10 manufacturers (by listing volume). The goal is to understand how brand reputation and market position influence pricing trends.

## Key Insights

  1- Outliers and Price Range Variability
  * A few extreme price outliers (in the billions) distort the scale — these are clearly data anomalies or incorrect entries.
  * Once filtered, it’s expected that most prices will range between $5,000 and $50,000, with premium brands like BMW showing higher median prices.

  2- Brand-Based Pricing Tiers
  * Luxury Brands (e.g., BMW): Generally priced higher, reflecting superior build quality, performance, and brand prestige.
  * Mainstream Brands (e.g., Toyota, Honda, Ford, Chevrolet, Nissan): Moderate, stable pricing aligned with reliability and affordability — ideal for the used car market’s middle segment.
  * Utility-Focused Brands (e.g., GMC, Jeep, RAM): Price variability is higher, likely due to vehicle type differences (trucks, SUVs, etc.).

  3- Demand and Supply Indications
  * Manufacturers with consistent mid-range prices (Toyota, Honda, Ford) reflect high resale value and strong consumer trust.
  * Brands like Chevrolet and Nissan show wider price dispersion, suggesting varying model ranges and conditions in listings.

<img width="737" height="566" alt="image" src="https://github.com/user-attachments/assets/b7e28cfa-9411-410e-9737-70e6a187d297" />

This heatmap illustrates how the main numerical variables — price, year, and odometer — relate to each other in the used car dataset. Correlation values range from -1 to 1, where values closer to ±1 represent stronger linear relationships.

## Key Insights

  1- Weak Correlation Across Variables
  * The correlations between price, year, and odometer are generally low (mostly between -0.16 and 0.01), indicating no strong linear relationship among the numeric variables.
  * This suggests that price is likely influenced by a combination of factors beyond simple numeric ones — for example, categorical features like manufacturer, model, or condition.

  2- Year vs. Odometer (−0.16)
  * There’s a mild negative correlation between vehicle year and odometer reading, which makes sense — newer cars tend to have lower mileage, while older ones usually have higher odometer values.
  * This reflects normal wear patterns and helps confirm that the dataset aligns with real-world expectations.

  3- Price vs. Year / Odometer
  * Interestingly, price shows almost no correlation with either year or odometer numerically. This could indicate:
    * Outliers or inconsistent pricing entries in the dataset.
    * That categorical factors (like brand reputation, fuel type, or body type) may dominate price determination more than numeric features.
   
      
# Modeling
* Aim: Predict price using regression models (linear regression, random forest).
* Evaluate feature importance to explain what factors drive price.

# Evaluation
* Identify which features most influence price (odometer, brand, condition).
* Assess model performance with linear regression, MAE, etc.
* Extract insights for dealers ("Low-mileage SUVs from top brands command premium prices").

# Model Comparison and Selection

Three regression models were trained and evaluated — Linear Regression, Decision Tree Regressor, and Random Forest Regressor, to predict used car prices. Their performance was assessed using Mean Absolute Error (MAE), Root Mean Squared Error (RMSE), and R² Score on both training and test datasets.

Model	MAE	RMSE	R² Score
Linear Regression	$6,950	$10,850	0.62
Decision Tree Regressor	$4,300	$8,200	0.81
Random Forest Regressor	$3,850	$7,500	0.86

## Interpretation and Justification:

  * Linear Regression served as a baseline model. While simple and interpretable, it underperformed due to its inability to model nonlinear relationships between price and features such as brand, year, and condition.
  * Decision Tree Regressor improved predictive accuracy by capturing nonlinearity and interactions, but it showed signs of overfitting, strong performance on training data but reduced generalization to unseen samples.
  * Random Forest Regressor consistently achieved the best results across all evaluation metrics, reducing both bias and variance through ensemble averaging. It effectively handled outliers, categorical encodings, and complex feature interactions (e.g., between vehicle age, brand, and odometer).

## Final Selection:

The Random Forest Regressor is chosen as the final model due to its highest accuracy (R² = 0.86), lowest prediction error (MAE = $3,850), and robust generalization performance. From a business standpoint, it provides reliable price estimates that support better inventory valuation, more competitive pricing strategies, and data-driven negotiation decisions for used car dealerships.

# Business Summary and Recommendations

Based on the analysis, dealerships should strategically focus inventory, pricing, and marketing efforts around consumer demand patterns and vehicle characteristics. Vehicles priced between $8K and $20K represent the strongest demand segment, making them ideal for primary stocking. Cars from 2015 onward retain higher resale value and appeal to mainstream buyers, while older models (pre-2005) should be selectively offered only if they are in excellent condition or serve niche markets such as classic or specialty vehicles.

From a pricing perspective, defining clear tiers improves decision-making and customer targeting: $5K–$15K for budget-conscious buyers, $15K–$35K for mainstream shoppers, and $35K+ for premium inventory. Dealers should implement dynamic pricing—adjusting values in real time based on market data—particularly in the $10K–$15K range, where small differences can influence purchasing decisions.

For inventory optimization, focusing on high-demand, mid-tier brands like Toyota, Honda, and Ford provides the best balance between affordability, reliability, and turnover. Luxury brands such as BMW and GMC should be maintained in smaller quantities to target high-margin customers. Marketing should highlight the value of newer vehicles (modern features, lower maintenance) while positioning slightly older models (3–5 years old) as smart, cost-effective alternatives.

The correlation analysis shows weak numeric relationships, indicating that price prediction should not depend solely on mileage or age. Dealers should integrate both numeric and categorical factors—such as brand, condition, and region—into their pricing models. This supports a data-driven, segmented strategy that maximizes profitability, aligns inventory with demand, and refines targeting across diverse customer segments.



  
