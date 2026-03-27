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

## Requirements
```
python>=3.8
pandas
numpy
scikit-learn
xgboost
tensorflow
shap
matplotlib
seaborn
google-cloud-bigquery
```

## Usage
1. Request access to MIMIC-III via PhysioNet
2. Set up Google BigQuery credentials
3. Run `AKI_Prediction_MIMIC3.ipynb`

## Key Insights
- Creatinine features dominate (as expected from AKI definition)
- Traditional ML ≈ LSTM performance (endpoint more predictive than trajectory)
- GridSearchCV improved XGBoost performance
- SHAP validated clinical logic

## Limitations
- Single-center data (MIMIC-III = one hospital)
- Retrospective analysis
- Data leakage (48h data used to predict 48h outcome)
- Missing medication and vital sign data

## Future Work
- Predict AKI earlier (at admission) using only baseline features
- External validation on other hospital datasets
- Include medications and vital signs
- Subgroup analysis (diabetic, septic patients)

## Project Structure
```
.
├── AKI_Prediction_MIMIC3.ipynb    # Main notebook
├── AKI_Prediction_Slides.pdf       # Presentation
├── README.md                       # This file
└── requirements.txt                # Dependencies
```
