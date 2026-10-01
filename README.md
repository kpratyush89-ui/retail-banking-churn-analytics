# Retail Banking Customer Churn & Root Cause Analytics

## Executive Summary
This project analyzes customer attrition across a 10,000-customer retail banking portfolio. By combining descriptive cohort analytics, predictive modeling (XGBoost), and SHAP-based interpretability, this framework identifies critical account balance at risk and pinpoints actionable operational drivers of churn for executive decision-making.

## Key Insights & Root Cause Drivers
- **Product Over-Saturation:** Accounts holding 3 or 4 products display an attrition rate exceeding 80%, indicating friction or uncompetitive fee structures in multi-product bundles.
- **Activity & Demographic Vulnerability:** Inactive account holders aged 40+ represent the highest concentration of total capital loss.
- **Geographic Disparities:** Specific regional branches exhibit higher baseline churn, requiring localized retention incentives.

## Modeling & Performance Metrics
- **Algorithm:** XGBoost Classifier with imbalanced class handling (`scale_pos_weight`)
- **Interpretability:** SHAP (SHapley Additive exPlanations) TreeExplainer
- **Evaluation:** ROC-AUC ~0.86, evaluated on a 20% stratified holdout set

## Business Financial Impact
- **Risk Scoring:** Generates individual customer attrition probabilities ($P_{\text{churn}}$).
- **Capital at Risk:** Computes expected portfolio loss ($\text{Balance} \times P_{\text{churn}}$) to prioritize retention outreach on high-net-worth accounts.

## Repository Structure
```text
├── Retail_Banking_Churn_Analytics.ipynb  # End-to-end data processing, model, and SHAP code
├── Churn_Modelling.csv                   # Raw customer portfolio dataset
├── processed_churn_predictions.csv       # Predictions and risk scores for Power BI/Tableau
└── high_risk_action_list.csv             # Target list of high-risk customers ($P >= 0.65$)
