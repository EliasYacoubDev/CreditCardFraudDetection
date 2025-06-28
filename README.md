# Credit Card Fraud Detection

This project applies machine learning to detect fraudulent credit card transactions using the popular [Kaggle Credit Card Fraud dataset](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud).

## Project Overview

- Highly imbalanced data: only ~0.17% of transactions are fraud
- Features V1 to V28 are anonymized PCA components
- Amount and Time included
- Binary target: Class (1 = fraud, 0 = non-fraud)

We performed:
- Exploratory Data Analysis (EDA)
  - Class imbalance visualization
  - Distribution of amounts and times
  - Boxplots to explore features
  - Correlation heatmaps
- Feature engineering
  - Scaled `Amount` using StandardScaler
  - Removed `Time` for model building
  - Preserved the original `Amount` column for Power BI visualization
- Train/test split using stratification
- Baseline Logistic Regression
  - High ROC AUC but poor precision/recall on fraud class
- Random Forest Classifier
  - Much better performance on fraud detection
  - Tuned to `class_weight=balanced`
  - Feature importances extracted
  - Retrained on reduced features

## Results

- **Best model**: Random Forest on reduced features
  - Accuracy: ~99.9%
  - Fraud class recall: 0.77
  - ROC AUC: 0.95
  - Confusion matrix showed most frauds detected with minimal false positives
- Feature importances highlighted V4, V10, V14, and V17 as top contributors
- Predictions exported for Power BI

## Power BI Dashboard

We built an interactive Power BI report to explore:
- Overall fraud rate
- Fraud rate by transaction amount
- Average fraud probability by amount
- Distribution of fraud probabilities
- High-risk transactions table with probability > 0.7
- All visuals built on top of exported predictions
