# Black Friday

A retail company “ABC Private Limited” wants to understand the customer purchase behaviour (specifically, purchase amount) against various products of different categories. They have shared purchase summary of various customers for selected high volume products from last month.
The data set also contains customer demographics (age, gender, marital status, city_type, stay_in_current_city), product details (product_id and product category) and Total purchase_amount from last month.

Now, they want to build a model to predict the purchase amount of customer against various products which will help them to create personalized offer for customers against different products.

## Approach 1
1. Perform Numerical Encoding of all String Features.
2. Hot Encode Product_Category, may not be One Hot
3. One Hot Encode - City_Category, Age, Stay_In_Current_City_Years,
4. Tried Linear Regression, SGD Regression, Deep Neural Net, XGBoost
5. XGBoost works out best with RMSE = 2908

> Decision Trees does not give best results with one-hot encoding. Lets try XGBoost without one-hot encoding of some categorical variables in Approach 2.

## Approach 2
1. Perform Numerical Encoding of all String Features
2. One hot encode only city variable because it has less cardinality.
3. Replace Null product categories with 0.
4. Worked with XGBoost, performed hyper-parameter optimization using hyperopt.
5. This time XGBoost gives RMSE = 2841

> Lets try feature engineering to create some useful features. 

## Approach 3
1. Perform Numerical Encoding of all String Features
2. One hot encode only city variable because it has less cardinality.
3. Replace Null product categories with 0.
4. Remove samples with purchase that lies in outliers, consider only upto 99.5 percentile.
5. Keep User_ID, Product_ID and label encode them. Replace new Product_ID in test data with -1
6. Find best hyperparameters with hyperopt for xgboost and then train it.
7. This time XGBoost gives RMSE = 2516

> 

## Approach 4