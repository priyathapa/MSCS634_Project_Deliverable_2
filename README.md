# MSCS634_Project_Deliverable_2

## Regression Modeling and Performance Evaluation

## Project Overview

This project is the second deliverable for **MSCS 634: Data Mining**. The purpose of this phase was to build, evaluate, and compare regression models that predict the number of calories burned during a workout.

The project builds upon the data preparation and exploratory analysis completed in Deliverable 1. In this deliverable, the cleaned Gym Members Exercise Dataset was used to perform feature engineering, prepare the data for machine learning, train multiple regression models, evaluate model performance, apply cross-validation, and create visualizations that compare the models.

Two regression models were developed:

- Multiple Linear Regression
- Ridge Regression

The models were evaluated using both a holdout testing dataset and 5-fold cross-validation to determine how accurately they predicted calories burned and how well they generalized to unseen data.

---

## Dataset Summary

The project uses the **Gym Members Exercise Dataset** from Kaggle.

The dataset contains more than 900 observations describing gym members, their physical characteristics, workout habits, heart-rate measurements, hydration levels, body composition, and calories burned.

The dataset includes both numerical and categorical variables.

### Numerical Features

Examples of numerical variables include:

- Age
- Weight in kilograms
- Height in meters
- Maximum heart rate
- Average heart rate
- Resting heart rate
- Session duration in hours
- Fat percentage
- Water intake in liters
- Workout frequency in days per week
- Experience level
- Body Mass Index
- Calories burned

### Categorical Features

Examples of categorical variables include:

- Gender
- Workout type

The target variable selected for regression modeling was:

```text
Calories_Burned

This variable represents the estimated number of calories burned during a workout session.
The dataset was appropriate for regression analysis because Calories_Burned is a continuous numerical variable, and the dataset contains several physiological, demographic, and workout-related variables that may influence calorie expenditure.

### Project Objectives

The main objectives of this deliverable were to:

- Perform feature engineering to create useful predictors.
- Prepare numerical and categorical data for regression modeling.
- Build at least two regression models.
- Evaluate model performance using several regression metrics.
- Compare model performance using tables and visualizations.
- Apply cross-validation to assess model generalization.
- Identify the best-performing model.
- Summarize meaningful findings and challenges.


### Project Flow




