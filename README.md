# Factors-Influencing-Food-Delivery-Times-A-Predictive-Analysis-Using-Linear-Regression-

This project focuses on predicting food delivery times by analyzing various factors such as delivery distance, weather conditions, traffic levels, time of day, vehicle type, preparation time, and courier experience. Using real-world data, it aims to optimize delivery operations, improve efficiency, and enhance decision-making for food delivery services. By identifying key variables influencing delivery times, the project offers valuable insights for logistics management, helping businesses streamline operations, reduce delays, and improve customer satisfaction.

---

## Components

### Section 1: Data Import and Initial Exploration
- Data Import: The dataset Food_Delivery_Times.csv was loaded into the R environment using read.csv.
- Initial Exploration: The first 40 rows of the dataset were printed using head() to get a preview. The structure of the dataset was examined with str() to understand the types of variables and their data formats.

### Section 2: One-Hot Encoding of Categorical Features
- Categorical Variable Conversion: Categorical variables (Weather, Traffic_Level, Time_of_Day, Vehicle_Type) were converted into factors.
- One-Hot Encoding: The dummyVars function from the caret package was used to convert categorical variables into one-hot encoded features (binary columns). The result was combined with the original numeric features (such as Order_ID, Distance_km, Preparation_Time_min, etc.).
- Final Dataset Preparation: The original categorical columns were optionally removed to create a final dataset (fdt_final) that only contains one-hot encoded columns and numeric variables.

### Section 3: Handling Missing Values and Empty Strings
- Missing Values Check: The is.na() function was used to check for missing values in the dataset.
- Missing Data Removal: Rows with missing values in the Courier_Experience_yrs column were removed.
- Empty String Check: The number of empty strings in the dataset was counted to assess the presence of empty values.

### Section 4: Developing the Initial Linear Model for Price Prediction with Feature Selection and Residual Analysis
- Linear Model Fitting: A linear regression model was created to predict Delivery_Time_min based on all available features.
- Residual Analysis: The residuals (differences between actual and predicted values) and fitted values were plotted to assess the model fit. A horizontal line at zero was added to the plot for clarity.

### Section 5: Checking for Multicollinearity
- Variance Inflation Factor (VIF): The vif() function from the car package was used to calculate the VIF for each predictor in the model to check for multicollinearity. High VIF values indicated potential multicollinearity issues.
- Alias Check: The alias() function identified redundant variables with perfect multicollinearity (variables that can be expressed as linear combinations of others).
- Removal of Multicollinear Variables: The variable Vehicle_Type.Scooter was removed from the model due to high multicollinearity.

### Section 6: Refining the Linear Model with Stepwise Regression and Multicollinearity Check
- Stepwise Regression: A stepwise regression model was fitted using stepAIC() to find the best model by adding or removing predictors based on the AIC criterion.
- Residual Analysis: Residual plots were generated to assess the fit of the stepwise regression model.
- Multicollinearity Check: The VIF values for the stepwise model were calculated to ensure that multicollinearity was minimized. Variables with VIF values above a threshold were considered for removal.

### Section 7: Outlier Removal and Final Linear Model with Residual Analysis
- Outlier Detection: The residuals from the model were analyzed using the interquartile range (IQR) method to identify outliers. Residuals outside the range of Q1 - 1.5 * IQR to Q3 + 1.5 * IQR were treated as outliers.
- Outlier Removal: Outliers were removed from the dataset, and a new model was fitted without the outliers.
- Final Model: A final linear regression model was created using the cleaned data, and its summary was reviewed.
- Data Export: The cleaned dataset with the predictors used in the final model was saved to a CSV file.

### Section 8: Generating Predictions
- Predictions on Cleaned Data: The model without outliers was used to generate predictions on the cleaned dataset.
- Comparison of Actual vs. Predicted Values: A data frame was created to compare the actual Delivery_Time_min values with the predicted values.
- New Data Predictions: Predictions were made on new data points with specified features (e.g., Distance_km, Preparation_Time_min, etc.). The model generated predictions for each of the new data instances.


