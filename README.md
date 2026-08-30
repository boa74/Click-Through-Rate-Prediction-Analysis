# Click-Through-Rate-Prediction-Analysis
Welcome to the CTR Prediction Project repository. This project focuses on predicting ad click-through rate using regression and tree-based models in R, with an emphasis on model comparison, feature selection, overfitting diagnosis, and model tuning.

## Project Overview

- Objective: Predict user click-through rate (CTR) from advertising metadata.

- Tools Used: R, caret, ggplot2, fastDummies, xgboost, randomForest, gbm

- Dataset: Includes 28 independent variables (numeric and categorical) and CTR as the target.

## Repository Contents

- PAC_BKIM.Rmd - Main RMarkdown source file for analysis

- PAC_BKIM.html - Knit HTML output for the full report

- PAC_BKIM.PDF - PDF version of the project report

## Data Cleaning and Feature Engineering

- Applied Median/mode imputation for missing values

- Dummy variable creation for 8 categorical features

- Removed highly correlated predictors `(|r| > 0.85)`

- Applied feature selection using Stepwise Regression and VIF

- Split data into training and testing sets for out-of-sample model evaluation

## Modeling Approaches
Developed and compared multiple regression and tree-based predictive models, including Linear Regression, Polynomial Regression, Ridge Regression, Decision Trees, Random Forest, Bagging, GBM, and XGBoost.

## Model Performance Summary (RMSE)

| Model                 | Train RMSE | Test RMSE | Notes                      |
|-----------------------|------------|-----------|----------------------------|
| Linear Regression     | 0.106      | 0.157     | Baseline model             |
| Polynomial Regression | 0.090      | 0.167     | Slightly better train fit  |
| Ridge Regression      | 0.085      | 0.150     | Reduced overfitting        |
| **Decision Tree**     | 0.116      | 0.144     | Simple tree                |
| **Tuned Tree**        | 0.095      | 0.129     | Cross-validated            |
| Random Forest         | 0.110      | 0.129     | Ensemble, reduced variance |
| Bagging               | 0.113      | 0.133     | Ensemble, simpler          |
| **GBM**               | 0.090      | 0.120     | Better generalization      |
| **XGBoost**           | **0.008**  | **0.220** | Overfitting observed       |

GBM achieved the strongest holdout performance in the initial model comparison, with a test RMSE of 0.120.

Although the initial XGBoost model achieved a very low training RMSE of 0.008, its substantially higher test RMSE of 0.220 indicated overfitting. This train-test performance gap motivated an additional model-refinement stage rather than selecting XGBoost based on training performance alone.

## XGBoost Refinement

To address the overfitting observed in the initial XGBoost model, I reduced the model to five selected predictors:

- targeting_score
- visual_appeal
- contextual_relevance
- headline_length
- cta_strength

I then refined XGBoost using:

- 10-fold cross-validation
- Early stopping
- Learning-rate (eta) tuning
- Maximum tree-depth tuning
- Row and column subsampling
- L1/L2 regularization (alpha, lambda)

The reduced-feature XGBoost model was subsequently evaluated through Kaggle submission and achieved the strongest submission performance among the models evaluated in the project.

**Note:** The RMSE table above represents the initial train/test model comparison. The final XGBoost model was developed in a subsequent refinement stage using feature reduction, regularization, cross-validation, and early stopping.

## Key Visualizations
- Feature Importance
- RMSE by Model
- CTR vs. Targeting Score

## Key Insights

- Tree-based ensemble models generally outperformed the regression-based models in predictive performance.
  
- Train/test RMSE comparison identified substantial overfitting in the initial XGBoost model.
  
- Feature reduction, regularization, cross-validation, and early stopping were used to improve the XGBoost modeling approach.
  
- Model selection should consider out-of-sample performance and generalization rather than training accuracy alone.

## What I Learned

- Developed and compared multiple statistical and machine-learning models using a consistent evaluation metric.
  
- Diagnosed model overfitting through train/test performance comparison.
  
- Applied feature selection, cross-validation, early stopping, and hyperparameter tuning to improve model generalization.
  
- Evaluated trade-offs between model complexity and predictive performance.

## How to View

- Open PAC_BKIM.html to view the complete analysis and results.

- PAC_BKIM.PDF provides a PDF version of the full project report.

- PAC_BKIM.Rmd contains the complete R code and analytical workflow.
