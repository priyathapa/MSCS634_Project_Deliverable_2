# MSCS 634 Project Deliverable 2
## Regression Modeling and Performance Evaluation

## Project Overview

This project is the second deliverable for **MSCS 634: Data Mining** and focuses on developing and evaluating regression models to predict the number of calories burned during a workout. Building on the data preparation and exploratory analysis completed in Deliverable 1, this phase emphasizes feature engineering, regression modeling, model evaluation, and performance comparison.

The primary goal of this project was to develop predictive models capable of estimating **Calories_Burned** using demographic, physiological, body composition, hydration, and workout-related features. Two regression algorithms—**Multiple Linear Regression** and **Ridge Regression**—were implemented and compared using multiple evaluation metrics and cross-validation techniques to determine which model generalized better to unseen data.

---

# Dataset Summary

The project uses the **Gym Members Exercise Dataset**, which contains information describing gym members, their physical characteristics, workout habits, physiological measurements, and estimated calories burned during exercise.

The dataset contains over **900 observations** and includes both numerical and categorical variables.

### Numerical Features

Examples of numerical variables include:

- Age
- Weight (kg)
- Height (m)
- Maximum Heart Rate (Max_BPM)
- Average Heart Rate (Avg_BPM)
- Resting Heart Rate (Resting_BPM)
- Session Duration (hours)
- Fat Percentage
- Water Intake (liters)
- Workout Frequency (days/week)
- Experience Level
- Body Mass Index (BMI)
- Calories Burned

### Categorical Features

The dataset also contains categorical variables, including:

- Gender
- Workout Type

The target variable for this project is **`Calories_Burned`**, which represents the estimated number of calories burned during a workout session.

Regression modeling was selected because the target variable is continuous, making regression algorithms appropriate for predicting its value based on the available predictor variables.

---

# Project Objectives

The objectives of this project were to:

- Perform feature engineering to create additional variables that improve predictive performance.
- Prepare the dataset for regression modeling through encoding and feature scaling.
- Develop and compare two regression models: Multiple Linear Regression and Ridge Regression.
- Evaluate model performance using R-squared (R²), Mean Squared Error (MSE), Root Mean Squared Error (RMSE), and Mean Absolute Error (MAE).
- Apply 5-fold cross-validation to evaluate each model's ability to generalize to unseen data.
- Compare the models using both numerical evaluation metrics and visualizations.
- Identify the best-performing model and summarize the key findings from the analysis.
