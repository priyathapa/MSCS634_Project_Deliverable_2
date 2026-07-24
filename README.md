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

- # Dataset, Modeling Process, and Evaluation Results

## Dataset Summary

This project uses the **Gym Members Exercise Dataset**, which contains information about gym members, including demographic characteristics, body measurements, heart-rate data, workout habits, hydration levels, body composition, and the estimated number of calories burned during exercise. The dataset contains over 900 observations and includes a combination of numerical and categorical variables, making it suitable for predictive modeling.

The numerical features include variables such as age, weight, height, maximum heart rate, average heart rate, resting heart rate, session duration, body fat percentage, water intake, workout frequency, experience level, BMI, and calories burned. The categorical variables include gender and workout type.

The target variable selected for this project was **`Calories_Burned`**, a continuous numerical variable representing the estimated calories burned during a workout session. Since the objective was to predict a continuous value, regression modeling was the appropriate machine learning approach.

---

## Modeling Process

The modeling process followed a structured machine learning workflow beginning with data preparation and ending with model evaluation.

The dataset was first inspected to verify its structure, review the available features, and confirm that no missing values or duplicate records would negatively affect model performance. After verifying the quality of the dataset, feature engineering was performed to create additional variables that could improve the predictive ability of the regression models.

Several new features were created to better represent workout intensity, exercise volume, body composition, and hydration. These engineered features included **Heart_Rate_Increase, Heart_Rate_Intensity, Workout_Load, Weekly_Workout_Hours, Lean_Body_Mass, Fat_Mass, Water_Per_Kg,** and **BMI_Category**. Each engineered feature was derived only from existing predictor variables, ensuring that the target variable was never used during feature creation and preventing data leakage.

Following feature engineering, the target variable (**Calories_Burned**) was separated from the predictor variables. Categorical features such as **Gender**, **Workout Type**, and **BMI Category** were converted into numerical representations using one-hot encoding so they could be processed by the regression algorithms.

The dataset was then divided into an **80% training set** and a **20% testing set** using a fixed random state to ensure reproducible results. Because the predictor variables were measured on different numerical scales, feature standardization was performed using **StandardScaler**. Standardization was particularly important for Ridge Regression because the regularization penalty depends on the magnitude of the model coefficients.

Two regression models were developed and compared:

- **Multiple Linear Regression**, which served as the baseline model for predicting calories burned using multiple predictor variables.
- **Ridge Regression**, which extends linear regression by applying L2 regularization to improve model stability and reduce the effects of multicollinearity.

Both models were trained using the same training dataset and evaluated using the same testing dataset to ensure a fair and consistent comparison.

To further assess model reliability, **5-fold cross-validation** was performed. During cross-validation, the dataset was divided into five subsets, with each subset serving as the validation set once while the remaining subsets were used for training. Feature scaling and model training were performed within Scikit-learn pipelines to prevent data leakage during the cross-validation process.

---

## Evaluation Results

The performance of both regression models was evaluated using four commonly used regression metrics: **R-squared (R²), Mean Squared Error (MSE), Root Mean Squared Error (RMSE),** and **Mean Absolute Error (MAE).**

On the holdout testing dataset, both models achieved excellent predictive performance. Multiple Linear Regression produced an **R² value of 0.9854**, while Ridge Regression achieved the same **R² value of 0.9854**, indicating that both models explained approximately **98.5% of the variation in calories burned**. The RMSE values were approximately **34.86 calories** for both models, demonstrating that the average prediction error was relatively small compared to the overall range of calories burned in the dataset.

To verify that the models generalized well beyond a single train-test split, **5-fold cross-validation** was performed. Both models achieved a **mean cross-validation R² of 0.9843** with very small standard deviations, indicating highly consistent performance across different subsets of the data. Multiple Linear Regression achieved a slightly lower mean cross-validation RMSE, while Ridge Regression demonstrated slightly more consistent RMSE values across the validation folds. However, these differences were minimal and did not represent a meaningful difference in predictive performance.

Overall, both regression models demonstrated excellent predictive accuracy, strong generalization capability, and stable performance. Based on the cross-validation results, **Multiple Linear Regression was selected as the best-performing model**, although the performance difference between the two models was extremely small. These results indicate that the engineered fitness, physiological, and workout-related features were highly effective predictors of calories burned.
