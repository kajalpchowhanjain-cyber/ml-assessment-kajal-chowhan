B1. Problem Formulation
(a) Answer
The objective is to predict the number of items sold for each store under different promotional strategies. Therefore, the target variable is **items_sold**.

The candidate input features include store attributes (store size, location type), promotion type, temporal features (month, weekend, festival), and competition density.

This is a **supervised learning regression problem**, as the goal is to predict a continuous numerical value (items sold) based on historical data.
-----------------------------------------------------------------------------------------------------------------------------------------------------
(b) Answer
Using total sales revenue as the target variable can be misleading because it is influenced by price variations, discounts, and promotional strategies. In contrast, items sold directly reflects customer demand and purchasing behavior.

This illustrates the broader principle that the target variable in a machine learning problem should align closely with the business objective and should not be distorted by external factors that may introduce noise or bias.
-----------------------------------------------------------------------------------------------------------------------------------------------------
(c) Answer
Instead of using a single global model, a better approach would be to segment stores based on location or customer behavior and build separate models for each segment. Alternatively, a hierarchical or multi-level model can be used to capture store-specific variations.

This approach accounts for differences in customer demographics, competition, and purchasing patterns across locations, leading to more accurate and meaningful predictions.
-----------------------------------------------------------------------------------------------------------------------------------------------------
B2. Data and EDA Strategy
(a) Answer
The data from the four tables—transactions, store attributes, promotion details, and calendar—would be joined using common keys such as store_id and transaction_date.

The final dataset would have a grain of one row per store per time period (e.g., per day or per month). Aggregations such as total items sold, average basket size, and total transactions would be computed before modeling.

This structured dataset would then combine all relevant features required for predictive modeling.
-----------------------------------------------------------------------------------------------------------------------------------------------------
(b) Answer
Exploratory Data Analysis would include:

1. Distribution of items sold to understand overall sales patterns.
2. Sales by promotion type to identify which promotions perform best.
3. Time series analysis of sales to detect trends and seasonality.
4. Correlation analysis between features and items sold to identify important predictors.

These analyses would guide feature engineering decisions, such as creating seasonal indicators or selecting the most relevant variables for modeling.
-----------------------------------------------------------------------------------------------------------------------------------------------------
(c) Answer
The imbalance where 80% of transactions occur without promotions can bias the model towards predicting non-promotional outcomes more accurately while underperforming on promotional cases.

To address this, techniques such as resampling, assigning higher weights to promotional data, or building separate models for promotional and non-promotional scenarios can be used to ensure balanced learning.
-----------------------------------------------------------------------------------------------------------------------------------------------------
B3. Model Evaluation and Deployment
(a) Answer
The data should be split using a time-based approach, where earlier data is used for training and more recent data is used for testing. A random split is inappropriate because it can lead to data leakage from future observations into the training set.

Evaluation metrics such as RMSE and MAE should be used. RMSE penalizes larger errors more heavily, while MAE provides an average magnitude of errors. Together, they give a comprehensive view of model performance in predicting items sold.
-----------------------------------------------------------------------------------------------------------------------------------------------------
(b) Answer
Feature importance can be used to understand why the model recommends different promotions for the same store across different months. By analyzing which features have the highest importance, we can identify whether factors such as seasonality, customer behavior, or competition are influencing the decision.

For example, a higher importance of festival-related features may explain why a certain promotion performs better in December compared to March. This explanation can be communicated to the marketing team to build trust in the model's recommendations.
-----------------------------------------------------------------------------------------------------------------------------------------------------
(c) Answer
The trained model can be saved using serialization techniques such as joblib or pickle. Each month, new data would be preprocessed using the same pipeline and passed to the model to generate predictions for all stores.

Monitoring should include tracking prediction errors over time and comparing actual vs predicted values. If performance degrades significantly, it may indicate data drift or changes in customer behavior, requiring the model to be retrained with updated data.
