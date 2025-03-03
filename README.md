# Delivery Time Prediction for Porter - Intra-City Logistics

This project focuses on predicting delivery times for orders placed through **Porter**, India's largest marketplace for intra-city logistics. Porter serves over 5 million customers and works with a wide range of restaurants to deliver items directly to customers. The goal of this project is to build a robust regression model that can accurately estimate delivery times based on various features such as order details, restaurant information, and delivery partner availability.

---

## **Table of Contents**
1. [Project Overview](#project-overview)
2. [Context](#context)
3. [Dataset](#dataset)
4. [Data Dictionary](#data-dictionary)
5. [Features](#features)
6. [Methodology](#methodology)
7. [Results](#results)
8. [Installation](#installation)
9. [Usage](#usage)
10. [Tools Used](#tools-used)
11. [Contributing](#contributing)
12. [License](#license)
13. [FAQs](#faqs)
14. [Acknowledgments](#acknowledgments)

---

## **Project Overview**
The project involves:
- **Exploratory Data Analysis (EDA)** to understand the dataset and identify trends.
- **Data preprocessing**, including handling missing values, encoding categorical variables, and removing outliers.
- Building and training a **Neural Network (NN)** model using TensorFlow/Keras.
- Comparing the NN model's performance with **XGBoost** and **Linear Regression**.
- Evaluating models using **Mean Absolute Error (MAE)** and **R² scores**.

---

## **Context**
**Porter** is India's largest marketplace for intra-city logistics, operating in the country's $40 billion intra-city logistics market. The company aims to improve the lives of over 1,50,000+ driver-partners by providing them with consistent earnings and independence. Porter has serviced over 5 million customers and works with a wide range of restaurants to deliver food and other items directly to customers.

To enhance customer experience, Porter wants to provide accurate delivery time estimates to customers based on:
- **What they are ordering** (e.g., item details, subtotal).
- **Where the order is placed** (e.g., market ID, store location).
- **Delivery partner availability** (e.g., on-shift partners, busy partners).

This project uses a dataset containing the necessary features to train a regression model for delivery time estimation.

---

## **Dataset**
The dataset contains information about orders, including:
- **Order details**: `created_at`, `actual_delivery_time`, `subtotal`, `min_item_price`, `max_item_price`, etc.
- **Store details**: `store_id`, `store_primary_category`, `market_id`, etc.
- **Delivery logistics**: `total_onshift_partners`, `total_busy_partners`, `total_outstanding_orders`, etc.

The dataset is stored in a CSV file named `dataset.csv`.

---

## **Data Dictionary**
Each row in the dataset corresponds to one unique delivery. The columns represent the following features:
- **market_id**: Integer ID for the market where the restaurant is located.
- **created_at**: Timestamp at which the order was placed.
- **actual_delivery_time**: Timestamp when the order was delivered.
- **store_primary_category**: Category of the restaurant (e.g., fast food, fine dining).
- **order_protocol**: Integer code representing how the order was placed (e.g., through Porter, call to restaurant, pre-booked, third-party, etc.).
- **total_items**: Total number of items in the order.
- **subtotal**: Final price of the order.
- **num_distinct_items**: Number of distinct items in the order.
- **min_item_price**: Price of the cheapest item in the order.
- **max_item_price**: Price of the costliest item in the order.
- **total_onshift_partners**: Number of delivery partners on duty at the time the order was placed.
- **total_busy_partners**: Number of delivery partners attending to other tasks.
- **total_outstanding_orders**: Total number of orders to be fulfilled at the moment.

---

## **Features**
Key features used in the model:
- **Temporal features**: `day_of_week`, `hour_o`, `minute_o`, etc.
- **Order details**: `subtotal`, `min_item_price`, `max_item_price`.
- **Delivery logistics**: `total_onshift_partners`.
- **Target variable**: `time_taken` (delivery time in minutes).

---

## **Methodology**
1. **Data Preprocessing**:
   - Converted date columns to datetime format.
   - Extracted temporal features (e.g., day of the week, hour of the day).
   - Handled missing values and removed outliers.
   - Applied target encoding to categorical variables.

2. **Exploratory Data Analysis (EDA)**:
   - Visualized the distribution of delivery times.
   - Analyzed order frequencies by hour, day, and market.
   - Explored correlations between features and removed highly correlated columns.

3. **Model Building**:
   - Built a Neural Network model with multiple dense layers, batch normalization, and leaky ReLU activations.
   - Used advanced techniques like learning rate scheduling and early stopping.
   - Trained and evaluated the model using MAE and R².

4. **Comparison with Other Models**:
   - Compared the NN model's performance with XGBoost and Linear Regression.

---

## **Results**
### **Neural Network Model**
- **MAE**: 0.2326
- **R² Score**: 0.9837

### **XGBoost Model**
- **MAE**: 0.8675
- **R² Score**: 0.9814

### **Linear Regression Model**
- **MAE**: 1.0256
- **R² Score**: 0.9951

The **Neural Network model** demonstrated the best performance, with the lowest MAE and a high R² score, indicating strong predictive accuracy and generalization.
---
