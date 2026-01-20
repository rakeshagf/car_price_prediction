# Car Price Prediction leveraging CRISP-DM framework and regression models  

# Notebook link: 
https://github.com/rakeshagf/car_price_prediction/blob/main/carprice_prediction.ipynb

# Problem
The goal of this project is to understand what factors make a car more or less expensive. As a result of analysis, we need to provide clear recommendations to client -- a used car dealership -- as to what consumers value in a used car.

# Data
In this application, dataset (original dataset from Kaggle contained information on 3 million used cars) contains information on 426K cars (file size - approx 50mb).
This repo contains the zip version of datasetin data/ folder as github (free version) didn't allow upload of file size greater than 25mb. This dataset is same as provided in the practical assignment. 
Before running the notebook, zip format dataset will need extraction from zip file and and resulting vehicles.csv need to placed in data folder only.

## Summary of Key Findings 

## Model Performance Overview:
Our analysis compared three regression models—Polynomial Linear Regression, Ridge Regression, and Lasso Regression—all utilizing polynomial features of degree 2. The performance metrics (Mean Absolute Error (MAE) and Mean Squared Error (MSE)) for each model on both training and test datasets are summarized below:

| Model             | Dataset | MAE         | MSE          |
| :---------------- | :------ | :---------- | :----------- |
| Linear Regression | Train   | 4747.50     | 4.97e+07     |
| Linear Regression | Test    | 4801.22     | 5.15e+07     |
| Ridge             | Train   | 4747.47     | 4.97e+07     |
| Ridge             | Test    | 4801.37     | 5.15e+07     |
| Lasso             | Train   | 5327.20     | 5.81e+07     |
| Lasso             | Test    | 5351.03     | 5.89e+07     |

Both **Polynomial Linear Regression** and **Ridge Regression** demonstrated very similar and superior predictive accuracy, achieving the lowest MAE and MSE values on both training and test sets. This indicates their strong ability to capture the underlying patterns in the data and generalize well to unseen car data. The `alpha` value for the best Ridge model was very small (`1e-05`), suggesting that only a minimal amount of regularization was needed, which aligns with its close performance to the unregularized Linear Regression model.

**Lasso Regression**, while also performing reasonably well, showed slightly higher MAE and MSE. Its primary benefit lies in feature selection by driving the coefficients of less influential features to exactly zero, thus simplifying the model and allowing further tuning of model. However, for pure predictive accuracy in this context, it was marginally outperformed by the other two models.

**Conclusion:** Given the similar high performance and the added benefit of regularization for robustness, **Ridge Regression is the recommended model** for predicting used car prices.

### Key Drivers of Used Car Prices (from Ridge Regression Coefficient Analysis):

Analyzing the coefficients of the Ridge Regression model, we can identify the most influential factors determining a used car's price:

*   **Year and Odometer:** These remain the most critical predictors. Newer cars with lower mileage command premium prices, and the rate of depreciation accelerates with age and use.
*   **Manufacturer and Model:** The specific manufacturer and model specifications are highly influential. 
*   **Drivetrain and Transmission:** Certain drivetrain and transmission configurations are more valued depending on the car's age.
*   **Fuel Type:** Fuel gas type significantly impact price, with influence varying with the year.
*   **Vehicle Type:** Truck and Pickup type demonstrate strong positive correlations with price, particularly in newer models.


## Dealership Recommendations
Based on the insights from our modeling, here are actionable recommendations for optimizing operations:

1.  **Strategic Inventory Acquisition:**
    *   **Prioritize Newer, Lower-Mileage Vehicles:** Actively seek to acquire cars from recent years with low odometer readings, as these offer the highest profit potential and are most appealing to buyers.
    *   **Focus on High-Value Manufacturer-Model Combinations:** Identify and target the acquisition of specific brands and models that consistently show strong market demand and higher prices.

2.  **Targeted Marketing and Sales:**
    *   **Highlight Key Value-Driving Features:** In all marketing materials, emphasize the most impactful features such as the car's recent year, low mileage, desirable manufacturer, specific model, and favored configurations (e.g., specific drivetrain, fuel type, or vehicle type like trucks/pickups).
    *   **Personalize Pitches:** Equip sales staff with insights on how specific car features contribute to its value, allowing them to better articulate benefits to customers based on model-identified drivers.

3.  **Continuous Improvement:**
    *   **Integrate Feedback Loop:** Continuously feed new sales data back into the model to refine its predictions and ensure it adapts to evolving market trends and buyer preferences.
    *   **Expand Data Collection (Future):** Consider collecting more granular data on vehicle options, trim levels, or regional micro-market trends to potentially enhance predictive accuracy further.

By systematically applying these data-driven recommendations, the dealership can make more informed decisions across its operations, leading to increased profitability and a more competitive market position.
