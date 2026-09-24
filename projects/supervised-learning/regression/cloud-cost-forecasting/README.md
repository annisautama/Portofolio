☁️ Cloud Cost Forecasting

End-to-end machine learning system for forecasting cloud infrastructure costs, detecting unusual spending, and estimating future cost uncertainty.












📌 Project Overview

Cloud infrastructure costs can change rapidly as workloads, compute usage, storage, and network traffic change.

This project builds an end-to-end machine learning pipeline to:

Forecast future cloud infrastructure costs.

Identify unusual spending patterns.

Estimate prediction uncertainty.

Expose the model through an API.

Track experiments with MLflow.

Provide a simple monitoring dashboard.

The project is designed to demonstrate production-oriented machine learning rather than a standalone regression notebook.

🎯 Business Problem

A cloud engineering team wants to answer:

"How much are we likely to spend over the next 7 days?"

The system receives historical infrastructure metrics such as:

CPU utilization

Memory utilization

Storage usage

Network traffic

Number of running instances

Instance type

Workload type

Deployment activity

Historical cloud cost

Calendar features

The model predicts:

Expected cost
Prediction interval
Cost anomaly

🧠 Machine Learning Problem

The primary task is a supervised regression problem.

Target
daily_cloud_cost


For forecasting:

next_1_day_cost
next_7_day_cost
next_30_day_cost

Features
cpu_utilization
memory_utilization
storage_gb
network_gb
instance_count
deployment_count
hour
day_of_week
is_weekend
is_month_end
lag_1
lag_7
rolling_mean_7
rolling_std_7

🏗️ Architecture
                ┌─────────────────────┐
                │ Cloud Usage Dataset │
                └──────────┬──────────┘
                           │
                           ▼
                ┌─────────────────────┐
                │ Data Validation      │
                └──────────┬──────────┘
                           │
                           ▼
                ┌─────────────────────┐
                │ Feature Engineering │
                └──────────┬──────────┘
                           │
              ┌────────────┴────────────┐
              ▼                         ▼
       Baseline Models           XGBoost Model
              │                         │
              └────────────┬────────────┘
                           ▼
                   Model Evaluation
                           │
                           ▼
                     MLflow Tracking
                           │
                           ▼
                     Model Registry
                           │
                 ┌─────────┴─────────┐
                 ▼                   ▼
              FastAPI             Streamlit
                 │                   │
                 └─────────┬─────────┘
                           ▼
                   Cloud Cost Insights

📊 Dataset

The repository initially uses a synthetic cloud infrastructure dataset so that the project can be reproduced without exposing private billing information.

The synthetic dataset simulates:

compute workload

memory utilization

storage

network usage

instance count

deployment activity

daily cloud cost

The project can later be adapted to AWS Cost and Usage Report data.

🔬 Modeling Strategy

The project compares several approaches.

Baseline
Previous-day cost
7-day moving average
Linear Regression

Machine Learning
Random Forest
XGBoost

Evaluation
MAE
RMSE
MAPE
R²


The validation strategy is time-aware.

Random train/test splitting is intentionally avoided because future observations should not influence past observations.

📈 Example Output

Example prediction:

Cloud Cost Forecast
────────────────────────────

Current daily cost       $842.31

Forecast

Tomorrow                 $861.20
Next 7 days             $6,174.40
Next 30 days           $26,410.80

90% Prediction Interval

$5,820 — $6,590


Example anomaly:

⚠️ Cost Anomaly Detected

Expected cost:      $820
Observed cost:    $1,430

Deviation:         +74.4%

Potential drivers:
- CPU utilization increased
- Instance count increased
- Network traffic increased

🧪 Experiment Tracking

MLflow is used to track:

model parameters

validation metrics

model artifacts

experiment runs

model versions

Example:

Experiment: cloud-cost-forecasting

Model: XGBoost

MAE: 7.24
RMSE: 10.91
MAPE: 6.82%
R²: 0.91

🚀 Quick Start
1. Clone
git clone https://github.com/YOUR_USERNAME/cloud-cost-forecasting.git

cd cloud-cost-forecasting

2. Create environment
python -m venv .venv


Linux/macOS:

source .venv/bin/activate


Windows:

.venv\Scripts\activate

3. Install dependencies
pip install -r requirements.txt

4. Generate dataset
python -m src.data.generate_data

5. Build features
python -m src.features.build_features

6. Train model
python -m src.models.train

7. Run API
uvicorn api.main:app --reload


Open:

http://127.0.0.1:8000/docs

8. Run dashboard
streamlit run app/streamlit_app.py

📓 Notebook Workflow

The notebooks are intentionally ordered as a complete ML workflow.

01_generate_data
        ↓
02_eda
        ↓
03_feature_engineering
        ↓
04_baseline_model
        ↓
05_xgboost_model
        ↓
06_model_evaluation
        ↓
07_forecasting
        ↓
08_prediction_interval

🧠 Key ML Concepts Demonstrated

Regression

Time-series validation

Feature engineering

Lag features

Rolling statistics

Gradient boosting

Model comparison

Error analysis

Prediction intervals

Anomaly detection

Experiment tracking

Model registry

REST API

Docker

CI testing

🔮 Future Improvements

Potential production improvements:

AWS Cost and Usage Report integration

AWS Cost Explorer integration

Real-time cost ingestion

Feature store

Automated model retraining

Data drift monitoring

Model drift monitoring

Cloud deployment

Cost optimization recommendations

LLM-generated cost explanations

👨‍💻 Author

YOUR NAME

Data Scientist / Machine Learning Engineer

Interested in:

Machine Learning
Applied Statistics
Forecasting
MLOps
Production ML Systems

📄 License

MIT License
