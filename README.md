# Click-Through-Rate-Prediction-Analysis
Welcome to the CTR prediction project repository. This project focuses on predicting ad click-through rate using various regression and tree-based models in R, with a focus on model tuning, feature selection, and interpretability.

## Project Overview

Objective: Predict user click-through rate (CTR) from advertising metadata.

Tools Used: R, caret, ggplot2, fastDummies, xgboost, randomForest, gbm

Dataset: Includes 28 independent variables (numeric and categorical) and CTR as the target.

## Repository Contents

PAC_FINAL2.Rmd - Main RMarkdown source file for analysis

PAC_BKIM.html - Knit HTML output for the full report

images/ - Folder with plots used in README and report

## Data Cleaning and Feature Engineering

Median/mode imputation for missing values

Dummy variable creation for 8 categorical features

Removed highly correlated predictors (|r| > 0.85)

Feature selection via Stepwise Regression and VIF

## Modeling Approaches

### Model

Train RMSE

Test RMSE

Decision Tree

0.116

0.144

Tuned Decision Tree

0.095

0.129

Random Forest

0.110

0.129

Bagging

0.113

0.133

GBM

0.090

0.120

XGBoost (final)

0.008

0.220

## Final Model: Tuned XGBoost

Selected 5 important features: targeting_score, visual_appeal, contextual_relevance, headline_length, cta_strength

Reduced overfitting using early_stopping_rounds and hyperparameter tuning (eta, depth, lambda, alpha)

## Key Visualizations

### Feature Importance
RMSE by Model
CTR vs Targeting Score



## Key Insights

Tree-based models outperformed linear models due to categorical richness

XGBoost demonstrated strongest fit but needed tuning to reduce overfitting

Feature engineering and selection significantly improved model accuracy

## What I Learned

Hands-on experience tuning GBM/XGBoost using caret

Data preparation workflow with dummy encoding and VIF filtering

Communicating modeling trade-offs using visualization and RMSE comparison

## How to View

HTML Report Preview

Clone and knit PAC_FINAL2.Rmd using RStudio
