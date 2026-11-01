# Housing Price Prediction Using Machine Learning

## Overview
This project investigates how residential property characteristics relate to housing prices and compares three supervised regression methods: Linear Regression, Decision Tree, and Random Forest.

## Dataset
The included Excel workbook contains 1,124 property records (as reported in the original analysis). Features include floor area, rooms, year built, location, street type, furnishing, property type, and pool status. The target is `Price`. Dataset provenance and permitted reuse should be confirmed before publishing.

## Methods
- Inspect missing values and descriptive statistics.
- Visualize price distribution, correlations, and relationships with area and rooms.
- Split data into training (80%) and holdout testing (20%).
- Use median imputation and scaling for numeric features; mode imputation and one-hot encoding for categorical features.
- Compare Linear Regression, Decision Tree, and Random Forest using RMSE, MAE, and R² on the test set, plus five-fold cross-validation on training data.
- Inspect predictions, residuals, and linear-model coefficients.

## Results
The **original notebook run** reported Linear Regression as the strongest of the three models (R² ≈ 0.944; RMSE ≈ 34,259). The cleaned notebook changes cross-validation to use only the training partition, so rerun it and use the refreshed outputs when reporting final results.

## Run locally
1. Install dependencies: `pip install -r requirements.txt`.
2. Start Jupyter in this project folder: `jupyter notebook`.
3. Open `Housing_Price_Prediction.ipynb` and run all cells in order.
4. The dataset is read from `data/Housing_Price_Dataset.xlsx`.

## Files
- `Housing_Price_Prediction.ipynb`: analysis and modeling.
- `data/Housing_Price_Dataset.xlsx`: input dataset.
- `reports/Housing_Price_Prediction_Report.pdf`: original written report (course references may remain).
- `presentation/Housing_Price_Prediction_Presentation.pptx`: original presentation (course references may remain).

## Limitations
Performance is measured on the supplied dataset and may not generalize to other housing markets. Investigate dataset provenance, possible target leakage, and stability of model coefficients before using this approach in a real-world setting.
