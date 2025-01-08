# Factors-Influencing-Food-Delivery-Times-A-Predictive-Analysis-Using-Linear-Regression-

This project focuses on predicting food delivery times by analyzing various factors such as delivery distance, weather conditions, traffic levels, time of day, vehicle type, preparation time, and courier experience. Using real-world data, it aims to optimize delivery operations, improve efficiency, and enhance decision-making for food delivery services. By identifying key variables influencing delivery times, the project offers valuable insights for logistics management, helping businesses streamline operations, reduce delays, and improve customer satisfaction.

---

## Components

### Section 1: Data Import and Initial Exploration
- Data Import: The dataset Food_Delivery_Times.csv was loaded into the R environment using read.csv.
- Initial Exploration: The first 40 rows of the dataset were printed using head() to get a preview. The structure of the dataset was examined with str() to understand the types of variables and their data formats.

![1](https://github.com/user-attachments/assets/9a308ce6-ecc6-4433-b725-323f585204b0)


### Section 2: One-Hot Encoding of Categorical Features
- Categorical Variable Conversion: Categorical variables (Weather, Traffic_Level, Time_of_Day, Vehicle_Type) were converted into factors.
- One-Hot Encoding: The dummyVars function from the caret package was used to convert categorical variables into one-hot encoded features (binary columns). The result was combined with the original numeric features (such as Order_ID, Distance_km, Preparation_Time_min, etc.).
- Final Dataset Preparation: The original categorical columns were optionally removed to create a final dataset (fdt_final) that only contains one-hot encoded columns and numeric variables.

![2](https://github.com/user-attachments/assets/6abd8cf2-d0fc-4436-aa5b-119276544088)


### Section 3: Handling Missing Values and Empty Strings
- Missing Values Check: The is.na() function was used to check for missing values in the dataset.
- Missing Data Removal: Rows with missing values in the Courier_Experience_yrs column were removed.
- Empty String Check: The number of empty strings in the dataset was counted to assess the presence of empty values.

### Section 4: Developing the Initial Linear Model for Price Prediction with Feature Selection and Residual Analysis
- Linear Model Fitting: A linear regression model was created to predict Delivery_Time_min based on all available features.
- Residual Analysis: The residuals (differences between actual and predicted values) and fitted values were plotted to assess the model fit. A horizontal line at zero was added to the plot for clarity.

![3](https://github.com/user-attachments/assets/8a6825c4-01cf-4474-8610-d6aca0cbb0e6)

![4](https://github.com/user-attachments/assets/8392d6be-1e25-4ca0-a765-ccb147ced5d2)

### Section 5: Checking for Multicollinearity
- Variance Inflation Factor (VIF): The vif() function from the car package was used to calculate the VIF for each predictor in the model to check for multicollinearity. High VIF values indicated potential multicollinearity issues.
- Alias Check: The alias() function identified redundant variables with perfect multicollinearity (variables that can be expressed as linear combinations of others).
- Removal of Multicollinear Variables: The variable Vehicle_Type.Scooter was removed from the model due to high multicollinearity.

### Section 6: Refining the Linear Model with Stepwise Regression and Multicollinearity Check
- Stepwise Regression: A stepwise regression model was fitted using stepAIC() to find the best model by adding or removing predictors based on the AIC criterion.

![5](https://github.com/user-attachments/assets/b95847e5-9d42-467d-869e-f8c7dc14ff53)


- Residual Analysis: Residual plots were generated to assess the fit of the stepwise regression model.

![6](https://github.com/user-attachments/assets/613590ad-bb86-4261-9ae5-db780e53cbf5)


- Multicollinearity Check: The VIF values for the stepwise model were calculated to ensure that multicollinearity was minimized. Variables with VIF values above a threshold were considered for removal.

### Section 7: Outlier Removal and Final Linear Model with Residual Analysis
- Outlier Detection: The residuals from the model were analyzed using the interquartile range (IQR) method to identify outliers. Residuals outside the range of Q1 - 1.5 * IQR to Q3 + 1.5 * IQR were treated as outliers.
- Outlier Removal: Outliers were removed from the dataset, and a new model was fitted without the outliers.
- Final Model: A final linear regression model was created using the cleaned data, and its summary was reviewed.

![7](https://github.com/user-attachments/assets/44261c2a-0d79-4a69-b992-c7b192a5e6e2)


- Data Export: The cleaned dataset with the predictors used in the final model was saved to a CSV file.
- Residual Analysis: Residual plots were generated to assess the fit of the final linear model.

![8](https://github.com/user-attachments/assets/6dbe9f12-69b0-48f1-a3fd-07587081c44e)


### Section 8: Generating Predictions
- Predictions on Cleaned Data: The model without outliers was used to generate predictions on the cleaned dataset.
  
![9](https://github.com/user-attachments/assets/036de0bc-e946-4293-8d0e-e106c88a3415)

- Comparison of Actual vs. Predicted Values: A data frame was created to compare the actual Delivery_Time_min values with the predicted values.

![10](https://github.com/user-attachments/assets/d1cb78c2-96f6-40d8-b736-d0406b4a19ec)

- New Data Predictions: Predictions were made on new data points with specified features (e.g., Distance_km, Preparation_Time_min, etc.). The model generated predictions for each of the new data instances.
![11](https://github.com/user-attachments/assets/3bc5689e-f48b-4747-bfb7-acdb2a35e67a)

![12](https://github.com/user-attachments/assets/fb20a327-46f7-4a24-8337-e151722558b8)

