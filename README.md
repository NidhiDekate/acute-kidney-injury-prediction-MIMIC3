# Acute Kidney Injury (AKI) Prediction using MIMIC-III

Predicting AKI in ICU patients using traditional ML and deep learning models on MIMIC-III clinical data.

## Overview
This project develops and compares 5 different models for early AKI detection:
- Logistic Regression
- Random Forest
- XGBoost (with GridSearchCV)
- Ensemble (Voting Classifier)
- LSTM (temporal sequence model)

**Result:** All models achieved >0.95 AUC, with Ensemble performing best (AUC=1.000).

## Dataset
- **Source:** MIMIC-III Clinical Database (accessed via Google BigQuery)
- **Cohort:** 10,866 ICU patients with ≥2 creatinine measurements in 48h
- **Target:** AKI defined as creatinine ≥1.5x baseline within 48h

## Key Features
- **Feature Engineering:** Demographics, creatinine trajectory, lab values (sodium, potassium, BUN, etc.)
- **Hyperparameter Tuning:** GridSearchCV on XGBoost (27 combinations)
- **Interpretability:** SHAP analysis for model transparency
- **Deep Learning:** LSTM architecture for temporal pattern learning

## Models & Performance

| Model | ROC-AUC |
|-------|---------|
| Logistic Regression | 1.000 |
| Random Forest | 1.000 |
| XGBoost | 1.000 |
| Ensemble | 1.000 |
| LSTM | 0.997 |

*Note: Near-perfect scores suggest possible data leakage (using 48h data to predict 48h outcome). See limitations.*
