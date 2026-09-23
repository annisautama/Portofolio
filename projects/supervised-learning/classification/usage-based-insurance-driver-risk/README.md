# Usage-Based Insurance Driver Risk

### Telematics-Based Driver Risk Classification for Usage-Based Insurance

An end-to-end supervised machine learning project that transforms
driving behavior and contextual telematics data into driver risk
classification for Usage-Based Insurance (UBI) decision support.

---

## Business Problem

Traditional auto insurance relies heavily on historical and
policy-level information.

Usage-Based Insurance (UBI) introduces a different approach:
driver risk can be assessed using observed driving behavior.

This project investigates whether telematics-derived behavioral
features can be used to classify drivers into different risk tiers.

The system is designed as a decision-support prototype for:

- Driver risk segmentation
- UBI analytics
- Safety intervention
- Portfolio risk monitoring
- Insurance underwriting research

The model does NOT automatically determine an insurance premium.

---

## Problem Statement

Given driving behavior and contextual variables:

> Can we classify a driver into an appropriate risk category?

Target:

    0 → Low Risk
    1 → Medium Risk
    2 → High Risk
    3 → Very High Risk

---

## Business Workflow

Raw Driving Data
        │
        ▼
Data Validation
        │
        ▼
Trip-Level Features
        │
        ▼
Driver-Level Aggregation
        │
        ▼
Temporal Train / Validation / Test
        │
        ▼
Supervised Classification
        │
        ▼
Probability Calibration
        │
        ▼
Driver Risk Score
        │
        ▼
UBI Decision Support

---

## Dataset

The primary dataset is based on publicly available driving-risk
data from the POLIDriving dataset used in the Distracted Driving
Risk Detection Challenge.

The dataset contains labeled driving observations across four
risk categories.

This repository treats the dataset as a public driving-risk
dataset for UBI-oriented modeling.

It is NOT proprietary insurance telematics data.

---

## Why UBI?

Usage-Based Insurance can use telematics information such as:

- Mileage
- GPS/location
- Driving time
- Speed
- Rapid acceleration
- Hard braking
- Hard cornering
- Other driving behavior

These variables can be transformed into behavioral risk indicators.

---

## Machine Learning Approach

### Models

Baseline:

- Logistic Regression
- Decision Tree

Tree-based:

- Random Forest
- XGBoost
- LightGBM
- CatBoost

---

## Feature Engineering

Examples:

### Speed

- Average speed
- Maximum speed
- Speed variance
- Speed percentile

### Braking

- Hard braking count
- Hard braking rate
- Braking severity

### Acceleration

- Harsh acceleration count
- Harsh acceleration rate

### Driving Context

- Night driving ratio
- Urban driving ratio
- Weather risk
- Traffic exposure

### Driver-Level Aggregation

Trip-level features are aggregated into driver-level features:

- Mean
- Median
- Standard deviation
- 90th percentile
- Event frequency
- Exposure-normalized event rate

---

## Important Design Principle

The model must avoid using future information to predict
current or future risk.

Therefore:

    Past driving behavior
            ↓
       Observation Window
            ↓
        Risk Prediction
            ↓
       Future Outcome

This prevents temporal leakage.

---

## Evaluation

Because this is a multiclass risk classification problem,
accuracy is not the only metric.

Metrics include:

- Macro F1
- Weighted F1
- Precision
- Recall
- Balanced Accuracy
- Multiclass ROC-AUC
- Confusion Matrix
- Calibration

Macro F1 is emphasized because each risk class should be evaluated
independently rather than allowing the majority class to dominate
the evaluation.

---

## Probability Calibration

The model should provide probabilities rather than only a hard
risk label.

Example:

    LOW        0.08
    MEDIUM     0.21
    HIGH       0.54
    VERY HIGH  0.17

Predicted Risk:

    HIGH

This enables downstream risk segmentation and human review.

---

## Explainability

SHAP is used to investigate:

- Which driving behaviors influence risk predictions?
- Which features contribute to high-risk predictions?
- How does speed affect model output?
- How does harsh braking affect risk?
- Which contextual variables influence predictions?

SHAP values describe model behavior.

They should not be interpreted as proof that a feature
causes an accident.

---

## Example Output

Example:

    Driver ID: D00129

    Risk:
    HIGH

    Probability:

    Low        0.04
    Medium     0.19
    High       0.61
    Very High  0.16

    Main contributing features:

    - High hard-braking frequency
    - High speed variability
    - High night-driving ratio
    - High harsh-acceleration frequency

The values above are illustrative.

---

## Project Structure

```text
notebooks/
    01_data_ingestion
    02_data_quality
    03_eda_driver_behavior
    04_feature_engineering
    05_temporal_dataset
    06_baseline_models
    07_model_comparison
    08_hyperparameter_tuning
    09_probability_calibration
    10_threshold_risk_segmentation
    11_model_explainability
    12_final_evaluation

