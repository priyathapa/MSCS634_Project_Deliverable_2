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

# Dataset, Modeling Process, and Evaluation Results

## Dataset Summary

This project uses the **Gym Members Exercise Dataset**, which contains information about gym members, including demographic characteristics, body measurements, heart-rate data, workout habits, hydration levels, and calories burned during exercise. The dataset contains over 900 observations and includes both numerical and categorical features.

Examples of numerical variables include age, weight, height, maximum heart rate, average heart rate, resting heart rate, session duration, fat percentage, water intake, workout frequency, BMI, and calories burned. The categorical variables include gender and workout type.

The target variable for this regression analysis was **Calories_Burned**, a continuous numerical variable representing the estimated number of calories burned during a workout session. Because the target variable is continuous, regression modeling was an appropriate machine learning technique for this project.

---

## Modeling Process

The regression modeling process followed a structured machine learning workflow.

The dataset was first inspected to verify its structure and confirm that there were no missing or duplicate values that could negatively affect model performance. Feature engineering was then performed to create additional variables that better represented workout intensity, body composition, hydration, and exercise volume. The engineered features included Heart_Rate_Increase, Heart_Rate_Intensity, Workout_Load, Weekly_Workout_Hours, Lean_Body_Mass, Fat_Mass, Water_Per_Kg, and BMI_Category. These features were created only from existing predictor variables, ensuring that the target variable was never used during feature engineering and preventing data leakage.

After feature engineering, the target variable (Calories_Burned) was separated from the predictor variables. Categorical variables such as Gender, Workout_Type, and BMI_Category were converted into numerical values using one-hot encoding so they could be processed by the regression models. The dataset was then divided into an 80% training set and a 20% testing set using a fixed random state to ensure reproducibility.

Since the predictor variables were measured on different numerical scales, feature standardization was performed using StandardScaler. Standardization was particularly important for Ridge Regression because its regularization penalty depends on the magnitude of model coefficients.

Two regression models were developed and compared:

- **Multiple Linear Regression**, which served as the baseline model for predicting calories burned using multiple predictor variables.
- **Ridge Regression**, which extends linear regression by applying L2 regularization to improve model stability and reduce the effects of multicollinearity.

Both models were trained using the same training dataset and evaluated using the same testing dataset to ensure a fair comparison.

To further evaluate how well the models generalized to unseen data, **5-fold cross-validation** was performed. Feature scaling and model training were implemented within Scikit-learn pipelines so that preprocessing occurred independently within each training fold, preventing data leakage during cross-validation.

---

## Evaluation Results

Model performance was evaluated using four regression metrics: **R-squared (R²), Mean Squared Error (MSE), Root Mean Squared Error (RMSE), and Mean Absolute Error (MAE).**

On the holdout testing dataset, both Multiple Linear Regression and Ridge Regression achieved excellent predictive performance. Each model obtained an **R-squared value of approximately 0.9854**, indicating that they explained about **98.5% of the variation in calories burned**. The models also produced low MSE, RMSE, and MAE values, demonstrating that their predictions closely matched the actual calorie values.

Five-fold cross-validation produced nearly identical results. Both models achieved a **mean cross-validation R-squared of approximately 0.9843** with very small standard deviations, indicating consistent performance across different subsets of the dataset. Multiple Linear Regression achieved a slightly lower average cross-validation RMSE, while Ridge Regression produced slightly more consistent RMSE values across the validation folds. However, these differences were extremely small and did not represent a meaningful difference in predictive performance.

Overall, both regression models demonstrated excellent predictive accuracy, strong generalization ability, and stable performance. Based on the cross-validation results, **Multiple Linear Regression was selected as the best-performing model**, although both models produced nearly identical results and proved to be highly effective for predicting calories burned using the available fitness and workout-related features.
