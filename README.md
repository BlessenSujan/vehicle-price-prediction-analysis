# Vehicle Price Prediction with Advanced Machine Learning

## Overview
This project presents an advanced machine learning framework for predicting vehicle prices using a large-scale car trader dataset. The workflow includes data cleaning, missing-value handling, outlier removal, feature engineering, encoding, feature selection, dimensionality reduction, model building, and explainability analysis.

The project was designed to compare multiple regression approaches and identify the best-performing model for predicting used car prices.

## Dataset
- Dataset size: **402,005 records**
- Source: Car trader / advert listing dataset
- Target variable: **price**

The dataset contains both numerical and categorical vehicle-related features such as mileage, make, model, body type, fuel type, vehicle condition, and year of registration. :contentReference[oaicite:3]{index=3}

## Project Objectives
- Build a robust regression pipeline for vehicle price prediction
- Apply feature engineering to improve predictive performance
- Compare traditional and advanced machine learning models
- Evaluate models using regression metrics and cross-validation
- Interpret the best-performing model using SHAP and partial dependence plots

## Data Preprocessing
The preprocessing workflow included:
- Dropping irrelevant columns such as `public_reference`
- Handling missing values:
  - `mileage` filled using mean
  - `standard_colour`, `body_type`, and `fuel_type` filled using mode
- Assigning registration year for new vehicles where applicable
- Removing records with invalid or missing registration information
- Removing unrealistic registration years below 1904
- Detecting and removing outliers using the IQR method
- Encoding categorical variables using:
  - One-hot encoding
  - Target encoding

These steps were performed to improve data quality and model reliability. :contentReference[oaicite:4]{index=4}

## Feature Engineering
Several new features were created to improve model performance:
- **Age** = 2024 − year of registration
- **Average mileage per year**
- Polynomial interaction features between **Age** and **mileage**

The project also explored how polynomial features contributed to predictive performance. :contentReference[oaicite:5]{index=5}

## Feature Selection and Dimensionality Reduction
To reduce redundancy and improve generalisation, the following techniques were applied:
- **SelectKBest**
- **RFECV**
- **Sequential Feature Selection (SFS)**
- **Principal Component Analysis (PCA)**

These methods were tested across multiple models to identify the most informative features. The report notes that XGBoost was the best-performing model across the automated feature-selection systems used. :contentReference[oaicite:6]{index=6}

## Models Implemented
The following regression models were built and evaluated:
- Linear Regression
- Random Forest Regressor
- XGBoost Regressor
- Gradient Boosting Regressor
- Voting Ensemble

## Model Performance
### Best model: **XGBoost Regressor**
Key results:
- **RMSE:** 2261.49
- **R²:** 0.9259
- Cross-validation:
  - Train folds ranged from approximately **0.922 to 0.925**
  - Test folds ranged from approximately **0.89 to 0.914**

Best hyperparameters identified:
- `n_estimators = 100`
- `learning_rate = 0.1`
- `max_depth = 3`
- `subsample = 0.8`
- `colsample_bytree = 0.8` 

### Other models
- **Random Forest Regressor:** RMSE 2369.04, R² 0.9167
- **Voting Ensemble:** RMSE 2358.59, R² 0.9194
- **Gradient Boosting Regressor:** RMSE 2999.50, R² 0.8698
- **Linear Regression:** lower performance compared with ensemble models 

## Explainability and Model Interpretation
To improve interpretability, the project included:
- **SHAP** for global and local explanations
- **Permutation importance**
- **Partial Dependence Plots**

The SHAP analysis showed that the most influential features included:
- mileage
- standard model
- age
- standard make
- body type
- fuel type 

## Key Takeaways
- XGBoost delivered the strongest predictive performance among all tested models
- Feature engineering and feature selection significantly improved model quality
- Explainability tools such as SHAP helped identify the main drivers of price prediction
- Ensemble and boosting methods clearly outperformed basic linear regression for this problem

## Tools and Libraries
- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- XGBoost
- SHAP
- Jupyter Notebook

## Repository Structure
```text
README.md
vehicle_price_prediction_advanced_ml.ipynb
requirements.txt
figures/
results/
docs/
