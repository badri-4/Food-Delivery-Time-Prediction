# Food Delivery Time Prediction

This repository contains the code and documentation for predicting delivery time for a food delivery app. The goal of this project is to create regression models that accurately predict the delivery time (in minutes) based on various features in the dataset.

## Project Overview

Food delivery services bring food to customers, and the delivery time can significantly impact customer satisfaction. This project aims to predict the delivery time for orders placed through a food delivery app by analyzing and modeling the available data.

## Dataset

The dataset used in this project is sourced from Kaggle: [Food Delivery Dataset](https://www.kaggle.com/datasets/gauravmalik26/food-delivery-dataset). The data includes information about delivery personnel, order details, and environmental conditions.

**Dataset Features:**

- **Continuous Variables:** Delivery_person_Age, Delivery_person_Ratings, distance
- **Discrete Variables:** Vehicle_condition, order_preparation_time, multiple_deliveries
- **Categorical Variables:** Weatherconditions, Road_traffic_density, Type_of_order, Type_of_vehicle, Festival, City

## Data Cleaning and Preparation

The data cleaning process involved the following steps:

1. Removed string parts from the `Weatherconditions` & `Time_taken(min)` columns.
2. Converted quantitative data types to `float` and date columns to `datetime`.
3. Created new variables:
   - **Distance:** Calculated from geographic coordinates.
   - **Order Preparation Time:** Derived from `order_placed` and `order_picked` timestamps.
4. Imputed missing data using `sklearn`’s `SimpleImputer`:
   - Categorical data imputed with the mode.
   - Numerical data imputed with the median.

## Exploratory Data Analysis (EDA)

During the EDA phase, we visualized the distribution of the target variable `Time_taken(min)` and examined its relationship with continuous, discrete, and categorical variables. We observed the following key points:

- Most deliveries occur during road traffic jams, with motorcycles, in metropolitan cities, and on non-festival days.
- The delivery time is influenced by `Multiple Deliveries`, `Weather Condition`, `Road Traffic`, `City`, `Festival`, and `Type of Vehicle`.
- No strong linear correlation was found between continuous variables and the target variable.

## Feature Selection

To prevent overfitting and enhance model performance, feature selection was performed using the following methods:

1. **Random Forest Importance**
2. **Lasso Regression**
3. **Fisher’s Score**
4. **Mutual Information**

Based on these methods, the following features were selected for modeling:

- Delivery_person_Age
- Delivery_person_Ratings
- Vehicle_condition
- multiple_deliveries
- Jam
- Low
- festival

## Modeling

Several regression models were built and evaluated, including:

1. **Multiple Linear Regression**
2. **Decision Trees**
3. **Random Forest**

### Model Performance

- **Linear Regression:** Train MSE: 45.39, Test MSE: 45.86
- **Decision Tree:** Train MSE: 29.69, Test MSE: 40.75
- **Pruned Decision Tree:** Train MSE: 34.50, Test MSE: 35.44
- **Random Forest:** Train MSE: 29.89, Test MSE: 39.38
- **Cross-Validated Random Forest:** Train MSE: 34.16, Test MSE: 35.17

The Random Forest model with cross-validation yielded the best performance, with a test MSE of 35.17, corresponding to an RMSE of approximately 6 minutes.

## Conclusion

The Random Forest model achieved the lowest test MSE, indicating an average prediction error of about 6 minutes. This level of accuracy is crucial for improving the operational efficiency of food delivery services. Further optimization is necessary to reduce this error margin and enhance the model's predictive power.

## Links

- [Dataset](https://www.kaggle.com/datasets/gauravmalik26/food-delivery-dataset)
