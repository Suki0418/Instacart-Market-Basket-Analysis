# Instacart-Market-Basket-Analysis
 Analyzing Instacart’s dataset of 3M+ grocery orders to (a) predict products likely to be reordered, (b) identify product combinations, (c) suggest cross-selling strategies, and (d) improve store layouts.

# 1. Dataset Overview
 1.1 Dataset Link: https://www.kaggle.com/competitions/instacart-market-basket-analysis 
 1.2 Dataset Descriptions: An anonymized relational dataset of 3M+ grocery orders from 200,000+ Instacart users, detailing 4–100 orders per user with product sequences and order timing information.
 1.3 File Descriptions: 
 
 (1) aisles.csv
 - aisle_id
 - aisle
 
 (2) departments.xlsx
 - department_id
 - department
 
 (3) order_products_train.xlsx & order_products_prior.xlsx (order-product level)
 These files specify which products were purchased in each order. order_products_prior.xlsx contains previous order contents for all customers. 
 - order_id
 - product_id
 - add_to_cart_order: The sequence in which the product was added to the cart.
 - reordered: The customer has a previous order that contains the product. Note that some orders will have no reordered items.  You may predict an explicit 'None' value for orders with no reordered items. (1 = reordered, 0 = not reordered)

 * order_products_prior give the order information of all users in the history.
 - Feature Engineering: Create customer-level, product-level, and user-product interaction features
 - Identify frequently bought product combinations using techniques like association rule mining (e.g., Apriori algorithm).
 
 * order_products_train give the current order information of some users.
 - Model Training & Evaluation
 - Test Predictions 
 
 (4) orders.xlsx (order-level)
 This file tells to which set (prior, train, test) an order belongs. You are predicting reordered items only for the test set orders. 
 - order_id
 - user_id
 - eval_set: which set an order belongs (prior, train, test)
   * The test rows in the orders dataset are for customers' most recent orders where the products they purchased are unknown. These rows act as your target set for prediction (Kaggle competition goal: to predict products likely to be reordered).
 - order_number (primary key): order sequence number for this user (1 = first, n = nth)
 - order_dow: the day of week - 0:'Monday', 1:'Tuesday', 2:'Wednesday', 3:'Thursday', 4:'Friday', 5:'Saturday', 6:'Sunday'
 - order_hour_of_day: 0-23
 - days_since_prior_order
 (5) products.xlsx
 - product_id
 - product_name
 - aisle_id
 - department_id
 (6) sample_submission.xlsx (for the Kaggle competition goal: to predict products likely to be reordered)
 - order_id
 - products: product_id(s)  
