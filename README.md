# MSCS 634 Project Deliverable 2
## Regression Modeling and Performance Evaluation

## Project Overview

This project is the second deliverable for **MSCS 634: Data Mining** and focuses on developing and evaluating regression models to predict the number of calories burned during a workout. Building on the data preparation and exploratory analysis completed in Deliverable 1, this phase emphasizes feature engineering, regression modeling, model evaluation, and performance comparison.

The primary goal of this project was to develop predictive models capable of estimating **Calories_Burned** using demographic, physiological, body composition, hydration, and workout-related features. Two regression algorithms **Multiple Linear Regression** and **Ridge Regression** were implemented and compared using multiple evaluation metrics and cross-validation techniques to determine which model generalized better to unseen data.

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

# Meaningful Insights and Key Observations

Several important insights were gained from developing and evaluating the regression models.

### Excellent Predictive Performance

Both Multiple Linear Regression and Ridge Regression achieved excellent predictive performance. The models explained approximately **98.5% of the variation in calories burned**, indicating that the selected demographic, physiological, and workout-related features were highly effective predictors of the target variable. The high R-squared values and low prediction errors demonstrate that the dataset contains strong relationships between the predictor variables and calories burned.

### Feature Engineering Improved the Dataset

Feature engineering played an important role in improving the predictive capability of the models. Creating new variables such as **Heart_Rate_Intensity**, **Workout_Load**, **Weekly_Workout_Hours**, **Lean_Body_Mass**, and **Water_Per_Kg** provided more meaningful representations of workout intensity, exercise volume, body composition, and hydration than the original variables alone. These engineered features allowed the regression models to capture relationships that may not have been as apparent using only the original dataset.

### Similar Performance Between Both Models

The evaluation results showed that Multiple Linear Regression and Ridge Regression performed almost identically. While Ridge Regression achieved a slightly lower RMSE on the holdout testing dataset, Multiple Linear Regression achieved a slightly lower average RMSE during 5-fold cross-validation. The differences between the models were extremely small, indicating that both approaches were highly effective for this prediction task.

### Strong Generalization to Unseen Data

The cross-validation results closely matched the holdout testing results, demonstrating that both models generalized well to unseen data. The consistently high R-squared values and low standard deviations across the five validation folds indicate that model performance remained stable regardless of how the dataset was partitioned. This suggests that neither model was overfitting the training data.

### Limited Benefit from Regularization

Although Ridge Regression incorporates L2 regularization to reduce the effects of multicollinearity and overfitting, it did not provide a significant improvement over the standard Multiple Linear Regression model. This suggests that the relationships within the dataset were already strongly linear and that the predictor variables did not introduce enough instability for regularization to produce a substantial performance gain.

### Reliable Prediction Errors

Both models produced relatively low RMSE and MAE values, indicating that their predictions were consistently close to the actual calorie values. Considering the range of calories burned within the dataset, the average prediction error was small, demonstrating that the models were capable of making accurate predictions across different workout sessions and participant characteristics.

### Overall Observation

Overall, the analysis demonstrated that both regression models were highly accurate, stable, and capable of generalizing well to new data. Multiple Linear Regression was selected as the best-performing model because it achieved the slightly lower average cross-validation RMSE while maintaining the same explanatory power as Ridge Regression. However, the difference between the two models was negligible, indicating that either model could be successfully used to predict calories burned with a high degree of accuracy.

# Challenges Encountered and How They Were Addressed

Several challenges were encountered throughout the regression modeling process. Each challenge provided an opportunity to improve the overall quality and reliability of the final models.

### Recreating the Project Environment

One of the first challenges was that the original dataset file from Deliverable 1 was no longer available when work on Deliverable 2 began. Since a new Google Colab notebook was created for this deliverable, the dataset and project environment had to be recreated from scratch.

**Solution:**  
The Gym Members Exercise Dataset was downloaded again from Kaggle and uploaded into Google Colab. The required Python libraries were re-imported, and the dataset was loaded and verified before beginning the regression modeling process.

---

### Selecting Meaningful Engineered Features

Another challenge was deciding which new features would improve the regression models without introducing unnecessary complexity or causing data leakage. Simply creating additional variables does not always improve model performance.

**Solution:**  
New features were carefully designed using existing predictor variables only. Variables such as **Heart_Rate_Intensity**, **Workout_Load**, **Weekly_Workout_Hours**, **Lean_Body_Mass**, and **Water_Per_Kg** were created because they represented meaningful fitness and physiological relationships. The target variable, **Calories_Burned**, was intentionally excluded from feature engineering to prevent data leakage.

---

### Preparing the Dataset for Regression Modeling

The dataset contained categorical variables such as **Gender** and **Workout Type**, which cannot be used directly by regression algorithms.

**Solution:**  
One-hot encoding was applied to convert categorical variables into numerical features. In addition, all predictor variables were standardized using **StandardScaler** so that variables measured on different numerical scales could be compared fairly during model training, particularly for Ridge Regression.

---

### Preventing Data Leakage During Cross-Validation

Cross-validation requires careful preprocessing to ensure that information from the validation data does not influence the training process. Applying feature scaling before cross-validation would have resulted in data leakage and overly optimistic evaluation results.

**Solution:**  
Scikit-learn Pipelines were used to combine feature scaling and model training. This ensured that the scaler was fitted only on the training portion of each fold, while the validation fold remained completely unseen until evaluation.

---

### Comparing Models with Nearly Identical Performance

The evaluation metrics for Multiple Linear Regression and Ridge Regression were extremely similar. Determining which model performed better required more than simply comparing one metric.

**Solution:**  
Model selection was based on multiple evaluation criteria, including R-squared, MSE, RMSE, MAE, and 5-fold cross-validation results. Rather than relying on a single metric, the overall performance, consistency, and generalization ability of each model were considered. Although both models achieved excellent predictive accuracy, Multiple Linear Regression was selected because it produced a slightly lower average RMSE during cross-validation while maintaining the same explanatory power as Ridge Regression.

---

### Interpreting and Presenting Results

Another challenge was organizing the regression results in a way that clearly communicated the performance of each model. With multiple evaluation metrics, cross-validation results, and visualizations, it was important to present the findings in a logical and easy-to-understand format.

**Solution:**  
The notebook was organized into clearly defined sections covering feature engineering, model development, evaluation, cross-validation, visualizations, and final analysis. Tables were used to compare evaluation metrics, while charts such as RMSE comparisons, actual-versus-predicted plots, residual plots, and cross-validation visualizations were included to support the numerical results. Detailed interpretations were added after each major section to explain what the results indicated and how they contributed to the final model selection.

# Conclusion

This deliverable successfully demonstrated the complete regression modeling workflow, from feature engineering and data preparation to model development, evaluation, and cross-validation. Both Multiple Linear Regression and Ridge Regression achieved excellent predictive performance, explaining more than 98% of the variation in calories burned while maintaining strong generalization to unseen data. Overall, the project highlighted the importance of thoughtful feature engineering, proper preprocessing, rigorous model evaluation, and cross-validation when developing reliable machine learning models. The results showed that the available fitness and physiological features can be used to accurately predict calories burned, with Multiple Linear Regression emerging as the preferred model based on its overall performance and consistency.
