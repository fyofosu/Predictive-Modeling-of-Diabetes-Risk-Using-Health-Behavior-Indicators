# Predictive-Modeling-of-Diabetes-Risk-Using-Health-Behavior-Indicators
End-to-end diabetes risk prediction project using balanced and imbalanced datasets. Features data cleaning, model tuning, feature selection, and SHAP interpretability, with comparative evaluation of Logistic Regression, Random Forest, and XGBoost models.
# Overview

This project applies machine learning to predict diabetes risk using health behavior indicators from the CDC BRFSS 2015 dataset. The goal is to develop an interpretable, scalable, and clinically meaningful Clinical Decision Support (CDS) system that identifies high-risk individuals early.

Multiple models were evaluated on both balanced and real-world imbalanced datasets, followed by SMOTE resampling, hyperparameter tuning, and SHAP explainability.

# Project Objectives

Build predictive models for diabetes risk using behavioral, clinical, and socioeconomic variables.

Compare baseline performance on balanced and imbalanced datasets.

Apply SMOTE to address class imbalance and measure its effect.

Tune models using GridSearchCV for optimized performance.

Use SHAP to interpret model predictions and highlight clinically relevant features.

Lay the foundation for a transparent Clinical Decision Support System.

# Dataset Description

Source: CDC Behavioral Risk Factor Surveillance System (BRFSS 2015)
Size: 400,000+ U.S. adult responses 

Diabetes_Risk_Prediction_Presen…

Datasets Used

Balanced Binary Dataset: 50/50 split (diabetes vs no diabetes)

Imbalanced Binary Dataset: real-world distribution

Feature Categories:

Clinical: BMI, HighBP, HighChol

Behavioral: Smoking, Physical Activity, Fruits/Veggies, Alcohol

Socioeconomic: Education, Income

Self-reported health: GenHlth, PhysHlth, MentHlth

These features are strongly associated with diabetes risk in existing literature and clinical practice.

# Exploratory Data Analysis (EDA)

Key findings from initial EDA:

No missing values in the cleaned dataset.

Balanced dataset = 50/50 distribution; Imbalanced dataset reflects real-world majority-negative class.

Higher BMI, poor general health, high BP, and high cholesterol correlate with increased diabetes risk.

Behavioral factors (diet, smoking, activity) show meaningful separation between diabetic and non-diabetic groups.

Strong positive correlations: BMI, HighBP, HighChol.

Negative correlations: Physical Activity, Fruit/Veg intake.


Diabetes_Risk_Prediction_Presen…

# Methodology
1. Data Preparation

Loaded and previewed datasets.

Encoded categorical variables.

Performed 80/20 train-test split using stratified sampling.

Created baseline models for both balanced and imbalanced datasets.

2. Models Used

Logistic Regression

Random Forest

XGBoost

3. Handling Imbalance

SMOTE applied only to training data.

Models retrained on SMOTE-resampled data and tested on the original imbalanced test set.

4. Evaluation Metrics

Accuracy

Precision

Recall

F1-score

ROC-AUC

5. Hyperparameter Tuning

GridSearchCV used to tune LR, RF, and XGBoost hyperparameters.

Improvements seen in calibration, stability, and discrimination.

6. Explainability (SHAP)

SHAP reveals how high/low feature values influence predictions.

Red = high value, *blue = low value.

Positive SHAP values push predictions toward diabetes; negative values reduce risk.


Diabetes_Risk_Prediction_Presen…

# Results Summary
Balanced Dataset Results

Logistic Regression: strong baseline interpretability.

Random Forest: improved recall for positive cases.

XGBoost: highest AUC and F1-score.

Imbalanced Dataset (Baseline)

High accuracy but very low recall for diabetes class.

Models tend to predict “No Diabetes” due to imbalance.

After SMOTE

Recall improves significantly, especially for Logistic Regression (0.16 → 0.76).

Accuracy decreases slightly (expected when sensitivity increases).

AUC remains stable, meaning model discrimination stays strong.

ROC Curve Comparison

XGBoost (AUC = 0.820) → best generalization on real-world data.

Logistic Regression (AUC = 0.818) → stable and consistent.

Random Forest (AUC = 0.815) → slight decline due to overfitting SMOTE data.


Diabetes_Risk_Prediction_Presen…

# Model Interpretability (SHAP)

SHAP results show the top contributors to diabetes prediction:

General Health (GenHlth)

High Blood Pressure (HighBP)

Age

BMI

High Cholesterol (HighChol)

Diet (Fruit/Veg intake)

Smoking

These align with clinical knowledge and research findings, increasing trust in the model for CDS applications.

# Code Included in Repository

The notebook contains:

EDA

Balanced dataset baseline modeling

Imbalanced dataset baseline modeling

SMOTE resampling pipeline

Hyperparameter tuning

SHAP explainability

Performance visualizations (ROC curves, confusion matrices, comparison charts)

# Future Work

Explore advanced ML models (CatBoost, LightGBM).

Add clinical variables for improved accuracy.

Use ADASYN or SMOTE-ENN for enhanced resampling.

Conduct fairness analysis across demographic subgroups.

Deploy a prototype CDS dashboard with interactive SHAP explanations.

Validate predictions with clinicians and real-world patient data.
