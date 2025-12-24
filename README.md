# IBM Customer Churn Prediction – End-to-End Machine Learning Project

## Project Overview

This project focuses on predicting customer churn using the **IBM Telco Customer Churn dataset**.  
The objective is to identify customers who are likely to churn and provide actionable insights that help businesses **reduce churn proactively**.

The project was implemented following **machine learning best practices**, starting from a professional folder structure, moving through exploratory data analysis, preprocessing, modeling, and ending with business-oriented evaluation and explainability.

---

## Business Objective

- Problem Type: **Supervised Classification**
- Target Variable: `Churn Value`
  - `0` → Not Churned
  - `1` → Churned
- Main Goal:
  - Identify **potential churned customers**
  - Prioritize **recall** to capture as many churned customers as possible
  - Support data-driven customer retention strategies

---

## Project Folder Structure

ibm-customer-churn-prediction/  
├── data/  
│ ├── raw/  
│ │ └── telco_customer_churn.xlsx  
│ └── processed/  
│ ├── X_train.npy  
│ ├── X_test.npy  
│ ├── y_train.npy  
│ └── y_test.npy  
│  
├── notebooks/  
│ ├── 01_data_exploration.ipynb  
│ ├── 02_preprocessing.ipynb  
│ ├── 03_modeling.ipynb  
│ └── 04_evaluation.ipynb  
│  
├── src/  
│ ├── **init**.py  
│ ├── data_preprocessing.py  
│ ├── feature_engineering.py  
│ ├── model_training.py  
│ └── model_evaluation.py  
│  
├── models/  
│ └── churn_model.pkl  
│  
├── reports/  
│ ├── figures/
│  
├── README.md  
└── .gitignore

This structure separates **exploration (notebooks)** from **reusable and production-ready code (`src/`)**, following industry best practices.

---

## Notebooks Summary

### 01_data_exploration.ipynb

- Performed exploratory data analysis to understand customer behavior and churn patterns
- Identified class imbalance, requiring metrics beyond accuracy
- Removed non-informative features (e.g., constant columns)
- Observed that churned customers generally pay higher monthly charges
- Highlighted non-binary categorical features requiring careful encoding

---

### 02_preprocessing.ipynb

- Defined numerical and categorical features
- Handled missing values using appropriate imputation strategies
- Scaled numerical features and encoded categorical variables
- Refactored preprocessing logic into reusable Python modules under `src/`

---

### 03_modeling.ipynb

- Trained multiple supervised classification models using a unified preprocessing pipeline
- Models evaluated:
  - Logistic Regression
  - Random Forest
  - XGBoost
- Evaluation metric: **ROC-AUC**, chosen due to class imbalance

Model Performance:

| Model               | ROC-AUC |
| ------------------- | ------- |
| Logistic Regression | 0.84    |
| Random Forest       | 0.83    |
| XGBoost             | 0.82    |

Logistic Regression achieved the best performance and was selected for further evaluation due to its interpretability and stability.

---

### 04_evaluation.ipynb

- Focused on aligning the model with real business goals
- Optimized the classification threshold using the Precision–Recall trade-off
- Selected a custom threshold of **0.3** to maximize recall
- Performed model explainability using Logistic Regression coefficients

Top churn drivers:

- No dependents
- Month-to-month contracts
- Fiber optic internet service

Top churn-reducing factors:

- No internet service
- No online security
- No streaming TV service

---

## `src/` Module Overview

- `data_preprocessing.py`: builds preprocessing pipelines (imputation, scaling, encoding)
- `feature_engineering.py`: handles feature selection and target extraction
- `model_training.py`: trains Logistic Regression model using pipelines
- `model_evaluation.py`: evaluates models, applies custom thresholds, and computes metrics

These modules ensure **reusability, maintainability, and reproducibility** across notebooks.

---
