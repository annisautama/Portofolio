# 🏭 Predictive Maintenance Classification

### Predict machine failure before it becomes production downtime.

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Scikit Learn](https://img.shields.io/badge/Scikit--Learn-Machine_Learning-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-Gradient_Boosting-189FDD?style=for-the-badge)
![SHAP](https://img.shields.io/badge/SHAP-Explainable_AI-FF6B35?style=for-the-badge)
![Streamlit](https://img.shields.io/badge/Streamlit-Deployment-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-Containerized-2496ED?style=for-the-badge&logo=docker&logoColor=white)

---

## 🚨 Business Problem

Unexpected machine failures can cause:

- 🏭 Production downtime
- 💰 Unexpected maintenance costs
- 🔧 Emergency repairs
- ⏱️ Production delays
- 📉 Reduced operational efficiency

Traditional maintenance often follows this pattern:

```text
Machine Running
      │
      ▼
Machine Problem
      │
      ▼
❌ Machine Failure
      │
      ▼
Emergency Maintenance
      │
      ▼
Production Downtime
```

### What if we could detect the risk earlier?

This project develops a **Machine Learning-based Predictive Maintenance System** that analyzes machine operating conditions and predicts the probability of machine failure before it happens.

---

# 🎯 Project Objective

The primary objective is to develop a **binary classification model** that predicts whether a machine is likely to experience failure based on its operating conditions.

```text
              MACHINE
                 │
                 ▼
        Sensor Measurements
                 │
                 ▼
        Feature Engineering
                 │
                 ▼
        Machine Learning Model
                 │
                 ▼
        Failure Probability
                 │
        ┌────────┴────────┐
        ▼                 ▼
    🟢 LOW RISK       🔴 HIGH RISK
        │                 │
        ▼                 ▼
   Keep Monitoring   Schedule Maintenance
```

### Prediction Target

| Value | Meaning |
|---|---|
| `0` | Normal Operation |
| `1` | Potential Machine Failure |

> **Goal:** Transform raw machine sensor data into an actionable maintenance risk assessment.

---

# 💡 Why Predictive Maintenance?

Instead of waiting for a machine to fail, organizations can use machine learning to identify machines that require attention.

```text
TRADITIONAL MAINTENANCE

Failure
   ↓
Repair
   ↓
Downtime
   ↓
Cost
```

```text
PREDICTIVE MAINTENANCE

Sensor Data
   ↓
ML Prediction
   ↓
Failure Risk
   ↓
Preventive Action
   ↓
Potentially Reduced Downtime
```

The model is designed as a **decision-support system** for maintenance planning.

---

# 📊 Dataset

This project uses the **AI4I 2020 Predictive Maintenance Dataset**.

The dataset contains machine operating measurements including:

| Feature | Description |
|---|---|
| `Type` | Product quality/type |
| `Air temperature [K]` | Air temperature |
| `Process temperature [K]` | Process temperature |
| `Rotational speed [rpm]` | Machine rotational speed |
| `Torque [Nm]` | Machine torque |
| `Tool wear [min]` | Tool usage/wear |
| `Machine failure` | Target variable |

### Target

```text
Machine failure
```

---

# 🔬 End-to-End Machine Learning Pipeline

```text
┌──────────────────────────┐
│       RAW DATA           │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│   DATA VALIDATION        │
│                          │
│ • Missing Values         │
│ • Duplicates             │
│ • Data Types             │
│ • Target Validation      │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│ EXPLORATORY DATA ANALYSIS│
│                          │
│ • Distributions          │
│ • Correlations           │
│ • Failure Patterns       │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│   FEATURE ENGINEERING    │
│                          │
│ • Temperature Difference │
│ • Temperature Ratio      │
│ • Machine Load Proxy     │
│ • Tool Wear Risk         │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│    PREPROCESSING         │
│                          │
│ • Encoding               │
│ • Scaling                │
│ • Train/Test Split       │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│    MODEL COMPARISON      │
│                          │
│ • Logistic Regression    │
│ • Decision Tree           │
│ • Random Forest          │
│ • Gradient Boosting      │
│ • XGBoost                │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│ HYPERPARAMETER TUNING    │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│      FINAL MODEL         │
└────────────┬─────────────┘
             │
       ┌─────┴─────┐
       ▼           ▼
   SHAP / XAI   Threshold
   Analysis     Optimization
       │           │
       └─────┬─────┘
             ▼
┌──────────────────────────┐
│  PREDICTION APPLICATION  │
│                          │
│       Streamlit          │
└──────────────────────────┘
```

---

# ⚙️ Feature Engineering

The project creates additional features to help the model capture relationships between machine operating conditions.

### 🌡️ Temperature Difference

```text
Temperature Difference
=
Process Temperature
-
Air Temperature
```

This feature helps represent the thermal condition of the machine.

### ⚙️ Machine Load Proxy

```text
Machine Load
=
Torque × Rotational Speed
```

This provides an additional representation of machine operating load.

### 🛠️ Tool Wear Risk

Tool wear is transformed into risk-oriented features.

```text
Normal Wear
     │
     ▼
Moderate Wear
     │
     ▼
High Wear
     │
     ▼
Potential Risk
```

---

# 🤖 Machine Learning Models

Several classification algorithms are evaluated.

| Model | Purpose |
|---|---|
| Dummy Classifier | Baseline |
| Logistic Regression | Linear baseline |
| Decision Tree | Non-linear interpretable model |
| Random Forest | Ensemble learning |
| Gradient Boosting | Boosting benchmark |
| XGBoost | Advanced gradient boosting |

The models are compared using multiple classification metrics rather than relying only on accuracy.

---

# 🏆 Model Performance

> ⚠️ Performance values will be generated from the actual experiments. No results are fabricated.

| Metric | Final Model |
|---|---:|
| Precision | `XX.XX%` |
| Recall | `XX.XX%` |
| F1 Score | `XX.XX%` |
| ROC-AUC | `XX.XX%` |
| PR-AUC | `XX.XX%` |

### Why multiple metrics?

Predictive maintenance is an **imbalanced classification problem**, where machine failures are typically much less frequent than normal operations.

Therefore, the project evaluates:

- Precision
- Recall
- F1 Score
- ROC-AUC
- PR-AUC
- Confusion Matrix

---

# 🎯 Threshold Optimization

The default classification threshold of `0.50` is not necessarily the optimal business threshold.

The project evaluates multiple probability thresholds:

```text
0.10 ── 0.20 ── 0.30 ── 0.40 ── 0.50 ── 0.60 ── 0.70 ── 0.80
```

The objective is to balance:

```text
False Negative
      VS
False Positive
```

### Why is this important?

A false negative could mean:

```text
Model Prediction
       ↓
    NORMAL
       ↓
Actual Machine Failure
       ↓
Unexpected Downtime
```

While a false positive could mean:

```text
Model Prediction
       ↓
   HIGH RISK
       ↓
Actual Machine Normal
       ↓
Additional Inspection
```

In a real manufacturing environment, the optimal threshold should be selected based on the relative cost of these outcomes.

---

# 🔍 Explainable AI

A machine learning system should not only answer:

> **"Will the machine fail?"**

It should also help answer:

> **"Why does the model think the machine is at risk?"**

This project uses **SHAP** and feature importance techniques to analyze model behavior.

Example:

```text
Machine Failure Risk
       │
       ▼
     78%
       │
       ├── Tool Wear          ██████████
       ├── Torque             ████████
       ├── Temperature Diff.  ██████
       └── RPM                ████
```

This makes the model more interpretable and useful as a maintenance decision-support system.

---

# 🖥️ Interactive Streamlit Dashboard

The final model is exposed through an interactive web application.

### Machine Input

```text
┌─────────────────────────────────────────┐
│       🏭 MACHINE PARAMETERS              │
├─────────────────────────────────────────┤
│                                         │
│ Product Type        [ M ▼ ]             │
│                                         │
│ Air Temperature     [ 300.5 ] K         │
│                                         │
│ Process Temperature [ 310.2 ] K         │
│                                         │
│ Rotational Speed    [ 1500 ] RPM        │
│                                         │
│ Torque              [ 45.0 ] Nm         │
│                                         │
│ Tool Wear           [ 180 ] min         │
│                                         │
│       [ 🔮 PREDICT FAILURE ]            │
└─────────────────────────────────────────┘
```

### Prediction Result

```text
┌─────────────────────────────────────────┐
│         MACHINE RISK ASSESSMENT         │
├─────────────────────────────────────────┤
│                                         │
│             ⚠️ HIGH RISK                │
│                                         │
│                73.2%                    │
│           Failure Probability           │
│                                         │
│ Recommended Action:                     │
│ Schedule maintenance inspection         │
│                                         │
└─────────────────────────────────────────┘
```

> `73.2%` above is only an example of how the dashboard will look. The actual value will come from the trained model.

---

# 🚦 Risk Classification

The application converts model probability into an easier-to-understand risk level.

```text
0%              40%              70%             100%
│────────────────│────────────────│────────────────│
      🟢 LOW           🟡 MEDIUM         🔴 HIGH
```

| Probability | Risk Level | Suggested Action |
|---:|---|---|
| `< 40%` | 🟢 Low | Continue monitoring |
| `40–70%` | 🟡 Medium | Schedule inspection |
| `> 70%` | 🔴 High | Prioritize maintenance |

> These thresholds are configurable and should ultimately be calibrated using real operational and maintenance costs.

---

# 💼 Business Impact

The system is designed to support:

### 🏭 Production

Identify machines that may require attention before unexpected downtime.

### 🔧 Maintenance

Help maintenance teams prioritize machines for inspection.

### 💰 Cost Control

Potentially reduce emergency maintenance and unplanned downtime.

### 📦 Resource Planning

Support technician and spare-part planning.

### 📈 Decision Making

Transform raw sensor measurements into actionable risk information.

---

# 🧪 Model Validation

The project includes:

- ✅ Train/Test Split
- ✅ Stratified Sampling
- ✅ Cross-Validation
- ✅ Baseline Model
- ✅ Model Comparison
- ✅ Hyperparameter Tuning
- ✅ Confusion Matrix
- ✅ ROC Curve
- ✅ Precision-Recall Curve
- ✅ Threshold Optimization
- ✅ Feature Importance
- ✅ SHAP Explainability

---

# 📁 Project Structure

```text
predictive-maintenance-classification/
│
├── 📄 README.md
├── 📄 requirements.txt
├── 📄 setup.py
├── 🐳 Dockerfile
├── 🐳 docker-compose.yml
├── 📄 .gitignore
│
├── 📂 data/
│   ├── raw/
│   │   └── ai4i2020.csv
│   └── processed/
│
├── 📂 notebooks/
│   ├── 01_data_loading_validation.ipynb
│   ├── 02_exploratory_data_analysis.ipynb
│   ├── 03_data_preprocessing.ipynb
│   ├── 04_feature_engineering.ipynb
│   ├── 05_baseline_models.ipynb
│   ├── 06_model_comparison.ipynb
│   ├── 07_hyperparameter_tuning.ipynb
│   ├── 08_model_evaluation.ipynb
│   ├── 09_shap_explainability.ipynb
│   └── 10_final_model_pipeline.ipynb
│
├── 📂 src/
│   ├── __init__.py
│   ├── config.py
│   ├── data_loader.py
│   ├── preprocessing.py
│   ├── features.py
│   ├── models.py
│   ├── train.py
│   ├── evaluate.py
│   ├── threshold.py
│   └── predict.py
│
├── 📂 models/
│   └── final_model.joblib
│
├── 📂 reports/
│   ├── figures/
│   ├── model_comparison.csv
│   └── final_metrics.json
│
├── 📂 app/
│   └── app.py
│
├── 📂 tests/
│   ├── test_data.py
│   ├── test_features.py
│   └── test_prediction.py
│
└── 📂 .github/
    └── workflows/
        └── tests.yml
```

---

# 🧰 Tech Stack

| Category | Technologies |
|---|---|
| Programming | Python |
| Data Processing | Pandas, NumPy |
| Visualization | Matplotlib, Seaborn |
| Machine Learning | Scikit-learn, XGBoost |
| Explainable AI | SHAP |
| Deployment | Streamlit |
| Model Serialization | Joblib |
| Testing | Pytest |
| Containerization | Docker |
| Version Control | Git, GitHub |
| CI/CD | GitHub Actions |

---

# 🚀 Getting Started

## 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/predictive-maintenance-classification.git

cd predictive-maintenance-classification
```

## 2. Create Virtual Environment

### Windows

```bash
python -m venv .venv

.venv\Scripts\activate
```

### macOS / Linux

```bash
python -m venv .venv

source .venv/bin/activate
```

## 3. Install Dependencies

```bash
pip install -r requirements.txt
```

## 4. Run Jupyter Notebook

```bash
jupyter notebook
```

Run notebooks sequentially:

```text
01 → 02 → 03 → 04 → 05
              ↓
06 → 07 → 08 → 09 → 10
```

## 5. Run Streamlit Application

```bash
streamlit run app/app.py
```

---

# 🐳 Docker

Build the image:

```bash
docker build -t predictive-maintenance .
```

Run the application:

```bash
docker run -p 8501:8501 predictive-maintenance
```

---

# 🧪 Run Tests

```bash
pytest
```

Tests cover:

- Dataset loading
- Target validation
- Feature engineering
- Prediction pipeline

---

# 📚 Project Notebooks

| Notebook | Focus |
|---|---|
| `01_data_loading_validation` | Dataset loading & validation |
| `02_exploratory_data_analysis` | EDA & visualization |
| `03_data_preprocessing` | Cleaning & preprocessing |
| `04_feature_engineering` | Domain-based feature creation |
| `05_baseline_models` | Baseline classification |
| `06_model_comparison` | Model benchmarking |
| `07_hyperparameter_tuning` | Model optimization |
| `08_model_evaluation` | Final evaluation |
| `09_shap_explainability` | Explainable AI |
| `10_final_model_pipeline` | Final ML pipeline |

---

# 🔮 Future Improvements

### Version 2

- 📡 Real-time sensor streaming
- 📈 Time-series modeling
- 🚨 Anomaly detection
- 📊 Model monitoring
- 🔄 Data drift detection

### Version 3

- MLflow experiment tracking
- REST API
- Cloud deployment
- Automated model retraining
- Maintenance scheduling optimization

### Advanced Modeling

```text
LSTM
Transformer
Temporal CNN
Autoencoder
Survival Analysis
Time-to-Failure Prediction
```

---

# ⚠️ Limitations

This project uses a public predictive maintenance dataset.

Therefore:

- The dataset may not represent every real manufacturing environment.
- Model performance may change when applied to real industrial sensor data.
- Probability estimates should be calibrated before operational use.
- Maintenance decisions should involve domain experts.
- Risk thresholds should be determined using actual business costs.

This project should therefore be considered a **proof-of-concept decision-support system**, rather than a production safety system.

---

# ⭐ Portfolio Highlights

This project demonstrates an end-to-end Machine Learning workflow:

```text
DATA
 │
 ▼
EDA
 │
 ▼
FEATURE ENGINEERING
 │
 ▼
MACHINE LEARNING
 │
 ▼
MODEL OPTIMIZATION
 │
 ▼
EVALUATION
 │
 ▼
EXPLAINABLE AI
 │
 ▼
DEPLOYMENT
 │
 ▼
BUSINESS DECISION
```

### Key Skills Demonstrated

- 📊 Exploratory Data Analysis
- ⚙️ Feature Engineering
- 🤖 Binary Classification
- ⚖️ Imbalanced Classification
- 🏆 Model Selection
- 🎯 Hyperparameter Optimization
- 📈 Threshold Optimization
- 🔍 Explainable AI
- 🧪 Model Testing
- 🚀 Streamlit Deployment
- 🐳 Docker
- ⚙️ CI/CD Fundamentals

---

# 👨‍💻 Author

## Annisa Utama Berliana

Interested in:

`Machine Learning` · `Predictive Analytics` · `Explainable AI` · `MLOps` · `Data-driven Decision Making` . `Agentic AI` . `AI Engineering` . `Deep Learning`

---

## ⭐ If You Find This Project Interesting

Feel free to explore the notebooks, experiment with the models, and extend the system to other predictive maintenance scenarios.

> **Built with Python, Machine Learning, and a focus on solving real-world problems.**
