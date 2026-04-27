# Heart Disease Prediction Model Using BRFSS 2015 Dataset

**Course:** Data Mining (BCSE208L) | DA2 and DA3 Analysis  
**Authors:** Divyanshu Sharma (23BDS1155) and Saumyarup Guha (23BDS1128)

---

## Overview

This project builds and evaluates multiple machine learning classifiers to predict heart disease risk using the CDC Behavioral Risk Factor Surveillance System (BRFSS) 2015 survey data. The dataset contains 22 health indicator features across 253,680 respondents.

<img src="BRFSS%202015%20Data%20Processing-2026-04-05-103839.png" width="600" alt="BRFSS 2015 Data Processing Workflow">

---

## Dataset

- **Source:** [Kaggle - Heart Disease Health Indicators BRFSS 2015](https://www.kaggle.com/datasets/alexteboul/heart-disease-health-indicators-dataset)
- **File:** `heart_disease_health_indicators_BRFSS2015.csv`
- **Rows:** 253,680 | **Columns:** 22
- **Target:** `HeartDiseaseorAttack` (binary: 0 = No, 1 = Yes)
- **Class imbalance:** ~9.4% positive cases

---

## Workflow

1. Exploratory Data Analysis (EDA) - distributions, correlations, class balance
2. Preprocessing - type conversion, outlier capping (Winsorization), feature selection via Information Gain
3. Train/test split - stratified 80/20
4. Class imbalance handling - ROSE oversampling
5. Model training - 5 classifiers + 1 hybrid ensemble
6. Evaluation - confusion matrices, ROC curves, AUC, F1, Recall, Precision

---

## Models

| Model | Notes |
|---|---|
| Logistic Regression | Interpretable baseline |
| Random Forest | Ensemble, handles non-linearity |
| XGBoost | Gradient boosting with early stopping |
| Naive Bayes | Probabilistic baseline |
| KNN | Distance-based, trained on scaled features |
| Hybrid (NB + XGBoost) | Stacked ensemble with logistic meta-learner |

---

## Key Risk Factors

| Rank | Feature | Significance |
|---|---|---|
| 1 | GenHlth | Self-rated general health, strongest predictor |
| 2 | Age | Risk rises sharply after age group 7 (50-54 yrs) |
| 3 | HighBP | Leading modifiable CVD risk factor |
| 4 | DiffWalk | Signals cardiovascular or metabolic compromise |
| 5 | Diabetes | 2-4x higher CVD risk |
| 6 | BMI | Amplifies metabolic risk pathways |
| 7 | HighChol | Contributes to atherosclerosis |
| 8 | PhysHlth | Reflects cumulative disease burden |

---

## Requirements

Install R packages before knitting:

```r
install.packages(c(
  "tidyverse", "scales", "corrplot", "gridExtra", "ggthemes",
  "caret", "ROSE", "randomForest", "xgboost", "e1071",
  "pROC", "knitr", "kableExtra", "FSelector", "naivebayes"
))
```

---

## Usage

1. Clone the repository
2. Place `heart_disease_health_indicators_BRFSS2015.csv` in the project root
3. Open `heart_disease_analysis.Rmd` in RStudio
4. Knit to HTML or PDF

---

## Files

```
.
+-- heart_disease_analysis.Rmd         # Main analysis notebook
+-- heart_disease_health_indicators_BRFSS2015.csv  # Dataset
+-- brfss_heart_disease_workflow.svg   # Workflow diagram
+-- BRFSS 2015 Data Processing-2026-04-05-103839.png
+-- Mini_Project_Review1.pdf           # Project review slides
```
