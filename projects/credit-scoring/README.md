Credit Risk Loss Modeling & Profitability Optimization
<p align="center"> <b>From Risk Modeling → Credit Strategy → Bottom-Line Impact</b> </p> <p align="center"> <img src="https://img.shields.io/badge/Python-3.x-blue?logo=python" /> <img src="https://img.shields.io/badge/Credit%20Risk-PD%20%7C%20LGD%20%7C%20EAD-orange" /> <img src="https://img.shields.io/badge/Modeling-Scikit--Learn%20%7C%20XGBoost-green" /> <img src="https://img.shields.io/badge/Analytics-Profitability-purple" /> </p>
🚀 Professional Impact
<table> <tr> <td align="center" width="50%">
Cost of Credit
<h1>11.00% → 8.24%</h1>

<b>▼ 2.76 percentage points</b>

</td> <td align="center" width="50%">
WO / ANR
<h1>8.80% → 6.10%</h1>

<b>▼ 2.70 percentage points</b>

</td> </tr> </table>

Professional impact: Developed and deployed an advanced loss
modeling framework that supported a reduction in Cost of Credit
from 11.0% to 8.24% and WO/ANR from 8.8% to 6.1%.

This portfolio project reconstructs the analytical framework behind
the initiative using simulated/anonymized data.

🎯 Business Objective

Credit risk modeling should go beyond predictive performance.

The objective of this project is to connect:

Risk Model → Credit Decision → Portfolio Loss → Financial Impact

The central business question:

How can PD, LGD, and EAD modeling be translated into credit
policy decisions and ultimately improve portfolio economics?

🧩 End-to-End Architecture
<p align="center">
                         CUSTOMER DATA
                              │
                              ▼
                   ┌────────────────────┐
                   │ DATA PREPARATION   │
                   │                    │
                   │ Cleaning           │
                   │ Feature Engineering│
                   │ Segmentation       │
                   └─────────┬──────────┘
                             │
             ┌───────────────┼───────────────┐
             ▼               ▼               ▼
       ┌──────────┐    ┌──────────┐    ┌──────────┐
       │    PD    │    │   LGD    │    │   EAD    │
       │  MODEL   │    │  MODEL   │    │  MODEL   │
       └────┬─────┘    └────┬─────┘    └────┬─────┘
            │               │               │
            └───────────────┼───────────────┘
                            ▼
                   ┌─────────────────┐
                   │ EXPECTED LOSS   │
                   │                 │
                   │   PD × LGD × EAD│
                   └────────┬────────┘
                            │
                            ▼
                   ┌─────────────────┐
                   │ CUT-OFF         │
                   │ SIMULATION      │
                   │                 │
                   │ Score / PD      │
                   │ Approval Rate   │
                   └────────┬────────┘
                            │
              ┌─────────────┼─────────────┐
              ▼             ▼             ▼
          ┌───────┐     ┌───────┐     ┌───────┐
          │  WO   │     │  ANR  │     │  CoC  │
          └───┬───┘     └───┬───┘     └───┬───┘
              │             │             │
              └─────────────┼─────────────┘
                            ▼
                  ┌────────────────────┐
                  │   PROFITABILITY    │
                  │                    │
                  │ Revenue            │
                  │ Funding Cost       │
                  │ Credit Loss        │
                  │ Operating Cost     │
                  └────────────────────┘

</p>
📊 Risk Modeling Framework
01 — Probability of Default

Estimate the probability that an account defaults within the
defined performance window.

Key components

Feature engineering

Risk segmentation

Logistic / tree-based modeling

Discrimination analysis

Calibration

Score-to-PD transformation

02 — Loss Given Default

Estimate the proportion of exposure that is not recovered after
default.

LGD = 1 − Recovery Rate


The framework incorporates recovery behavior and loss assumptions
to estimate account-level LGD.

03 — Exposure at Default

Estimate exposure at the point of default.

For revolving products:

EAD = Current Balance
    + CCF × Undrawn Amount

04 — Expected Loss

The three risk components are combined:

                ┌─────┐
                │ PD  │
                └──┬──┘
                   │
                   ×
                   │
                ┌──▼──┐
                │ LGD │
                └──┬──┘
                   │
                   ×
                   │
                ┌──▼──┐
                │ EAD │
                └──┬──┘
                   │
                   ▼
            EXPECTED LOSS


Expected Loss = PD × LGD × EAD

🎚️ Credit Cut-off Simulation

Model outputs are translated into credit policy scenarios.

For each potential cut-off:

Metric	Description
Approval Rate	Percentage of applications approved
Bad Rate	Observed / expected default rate
WO / ANR	Write-off relative to average net receivables
Expected Loss	Expected credit loss
Revenue	Expected portfolio revenue
CoC	Cost of Credit
Profitability	Expected economic contribution

The simulation allows the relationship between risk appetite,
portfolio growth, credit losses, and profitability to be explored.

💰 From Risk Model to Economics
                    RISK
                     │
          ┌──────────┼──────────┐
          ▼          ▼          ▼
         PD         LGD        EAD
          │          │          │
          └──────────┼──────────┘
                     ▼
              EXPECTED LOSS
                     │
                     ▼
              CREDIT POLICY
                     │
                     ▼
             PORTFOLIO MIX
                     │
        ┌────────────┼────────────┐
        ▼            ▼            ▼
       WO           CoC        Revenue
        │            │            │
        └────────────┼────────────┘
                     ▼
                PROFITABILITY


This is the core principle of the project:

A credit model creates business value when its risk predictions
can be translated into economically meaningful decisions.

📈 Professional Impact
Cost of Credit
BEFORE                         AFTER

  11.00%          ─────────►    8.24%

                         -2.76 pp

WO / ANR
BEFORE                         AFTER

   8.80%          ─────────►    6.10%

                         -2.70 pp


The professional implementation demonstrated how loss modeling
and credit strategy could be connected to measurable portfolio
outcomes.

🧠 What This Project Demonstrates
<table> <tr> <td>Risk Modeling</td> <td>PD / LGD / EAD</td> </tr> <tr> <td>Credit Analytics</td> <td>Score & Cut-off Simulation</td> </tr> <tr> <td>Portfolio Risk</td> <td>Expected Loss / WO / ANR</td> </tr> <tr> <td>Financial Analytics</td> <td>CoC / Revenue / Profitability</td> </tr> <tr> <td>Data Science</td> <td>Feature Engineering / Model Development</td> </tr> <tr> <td>Business Translation</td> <td>Risk Model → Credit Decision → Economics</td> </tr> </table>
🛠️ Technology
<p align="center">

Python · Pandas · NumPy · Scikit-learn · XGBoost
· Matplotlib · Seaborn · Jupyter · Git

</p>
📁 Repository Structure
credit_score/
│
├── 📂 docs/
│   ├── architecture.drawio
│   ├── methodology.md
│   └── assumptions.md
│
├── 📂 notebooks/
│   ├── 01_data_exploration.ipynb
│   ├── 02_feature_engineering.ipynb
│   ├── 03_pd_modeling.ipynb
│   ├── 04_lgd_modeling.ipynb
│   ├── 05_ead_modeling.ipynb
│   ├── 06_cutoff_simulation.ipynb
│   └── 07_profitability_simulation.ipynb
│
├── 📂 src/
│   ├── models/
│   ├── features/
│   ├── simulation/
│   └── utils/
│
├── 📂 outputs/
│   ├── figures/
│   └── model_results/
│
└── README.md

🔬 Project Roadmap
[x] Business Problem Definition
[x] Risk Framework Design
[ ] Data Preparation
[ ] PD Modeling
[ ] LGD Modeling
[ ] EAD Modeling
[ ] Expected Loss Framework
[ ] Cut-off Simulation
[ ] WO / ANR Analysis
[ ] CoC Simulation
[ ] Profitability Analysis
[ ] Sensitivity Analysis
[ ] Final Case Study

⚠️ Disclaimer

This repository is a portfolio reconstruction of a professional
credit risk modeling use case.

Production data, proprietary model parameters, confidential business
logic, and company-specific information are not included.

The portfolio implementation uses simulated and/or anonymized data
for demonstration purposes.

<p align="center"> <b>Risk Modeling → Credit Decision → Portfolio Economics</b> </p>
