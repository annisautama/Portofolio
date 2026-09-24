🚕 Urban Mobility Geospatial Clustering
Discovering Mobility Hubs and Travel Patterns from NYC Taxi Trips

An end-to-end unsupervised machine learning project that uses geospatial clustering to discover hidden urban mobility patterns across New York City.

The project transforms millions of taxi trips into interpretable geographic mobility segments using spatial feature engineering, density-based clustering, cluster validation, and interactive geospatial visualization.

🎯 Project Overview

Urban transportation systems generate enormous amounts of spatial and temporal data.

However, raw trip records do not directly tell us:

Which areas behave as major mobility hubs?

Which neighborhoods have similar mobility patterns?

Where do airport-oriented trips concentrate?

Which areas are highly active during commuting hours?

Which locations behave differently from surrounding areas?

How do mobility patterns change between weekdays and weekends?

This project addresses these questions using unsupervised learning and geospatial analytics.

Instead of clustering individual passengers, we cluster taxi zones based on their mobility behavior.

The result is a geographic segmentation of NYC into interpretable mobility archetypes.

🔎 Research Question

Can unsupervised machine learning identify meaningful urban mobility archetypes from taxi trip activity?

Supporting questions:

Which taxi zones act as major mobility hubs?

Which zones have similar temporal and trip characteristics?

Can density-based clustering discover spatially concentrated mobility patterns?

How stable are the discovered clusters?

What distinguishes one mobility archetype from another?

🧠 Analytical Approach
NYC TLC Trip Records
        │
        ▼
Data Quality & Cleaning
        │
        ▼
Taxi Zone Aggregation
        │
        ▼
Spatial + Temporal Feature Engineering
        │
        ├── Trip volume
        ├── Trip distance
        ├── Trip duration
        ├── Average fare
        ├── Peak-hour activity
        ├── Weekend activity
        ├── Airport activity
        └── Origin/Destination connectivity
        │
        ▼
Feature Scaling
        │
        ▼
Dimensionality Reduction
        │
        ▼
Multiple Clustering Algorithms
        │
        ├── K-Means
        ├── DBSCAN
        └── HDBSCAN
        │
        ▼
Cluster Validation
        │
        ├── Silhouette Score
        ├── Davies-Bouldin Index
        ├── Cluster Stability
        └── Spatial Interpretability
        │
        ▼
Cluster Profiling
        │
        ▼
Mobility Archetypes
        │
        ▼
Interactive Geospatial Visualization

🗺️ Dataset

This project uses the official NYC Taxi & Limousine Commission (TLC) Trip Record Data.

The TLC trip records contain fields such as:

pickup/drop-off date and time

pickup/drop-off taxi zone

trip distance

passenger count

fare information

payment type

rate type

The TLC also provides a Taxi Zone Lookup Table and geographic taxi-zone boundaries.

Source:

NYC TLC Trip Record Data

NYC TLC Data

The analysis uses taxi-zone-level aggregates rather than attempting to expose individual passenger behavior.

📊 Unit of Analysis

The primary unit of analysis is:

Taxi Zone × Time Period

rather than individual taxi trips.

This reduces the computational burden and makes the clustering problem meaningful from a geographic perspective.

Example:

Zone 1
├── total_trips
├── avg_trip_distance
├── avg_trip_duration
├── avg_fare
├── peak_hour_share
├── weekend_share
├── airport_trip_share
└── connectivity_score

🧩 Feature Engineering

The project creates several groups of features.

1. Mobility Intensity
total_trips
trips_per_hour
unique_destinations
unique_origins

2. Trip Characteristics
avg_trip_distance
median_trip_distance
avg_trip_duration
avg_fare
avg_speed

3. Temporal Behavior
morning_peak_share
evening_peak_share
night_share
weekend_share
weekday_share

4. Spatial Connectivity
destination_diversity
origin_diversity
inbound_trip_share
outbound_trip_share

5. Airport Mobility

Airport-oriented activity is represented using taxi-zone information rather than manually assigning individual coordinates.

🤖 Clustering Strategy

Three clustering approaches are evaluated.

K-Means

Used as a baseline because it provides simple and interpretable centroid-based segmentation.

DBSCAN

Used to identify dense geographic/behavioral groups while allowing noise points.

HDBSCAN

Used as the primary density-based method because mobility zones may contain clusters with different densities.

The goal is not to maximize a single metric blindly.

A useful clustering solution should be:

statistically reasonable

spatially coherent

stable

interpretable

useful for downstream mobility analysis

📐 Cluster Validation

The following metrics are considered:

Silhouette Score

Measures how separated observations are from neighboring clusters.

Higher values generally indicate better separation.

Davies-Bouldin Index

Measures similarity between clusters.

Lower values generally indicate better separation.

Stability Analysis

The clustering is repeated under different random samples / parameter settings to evaluate whether the resulting mobility segments remain reasonably consistent.

Spatial Interpretability

A statistically valid cluster that produces geographically meaningless patterns is not automatically considered useful.

🗺️ Expected Mobility Archetypes

The final names are assigned only after examining the actual cluster profiles.

Possible examples include:

High-Intensity Urban Hub
Airport-Oriented Zone
Commuter Corridor
Residential Mobility Zone
Nightlife / Evening Activity Zone
Peripheral Low-Intensity Zone


These are analytical labels, not predefined classes.

📈 Example Output

The final analysis produces:

Mobility Cluster Map
                 NYC Mobility Landscape

             🟦 🟦 🟦
          🟦 🟦 🟦 🟦

       🟩 🟩 🟩
     🟩 🟩 🟨 🟨

          🟨 🟨
             🟥 🟥

                🟪


Each color represents a discovered mobility archetype.

💡 Business / Urban Analytics Questions

The resulting clusters can support questions such as:

Where are the highest-intensity mobility hubs?

Which zones have strong commuting patterns?

Which zones exhibit unusual night-time activity?

Which zones are strongly connected to airport activity?

Which zones have high trip volume but relatively short trips?

Which zones have low volume but high average trip distance?

The model is therefore treated as an exploratory decision-support tool, not as a system that automatically determines transportation policy.

🛠️ Tech Stack
Data

Python

Pandas

NumPy

PyArrow

NYC TLC Trip Records

Machine Learning

Scikit-learn

HDBSCAN

SciPy

Geospatial

GeoPandas

Shapely

Folium

Contextily

Visualization

Matplotlib

Seaborn

Plotly

Folium

Deployment

Streamlit

Docker

📁 Project Structure
urban-mobility-geospatial-clustering/
│
├── README.md
├── requirements.txt
│
├── data/
│
├── notebooks/
│   ├── 01_data_acquisition.ipynb
│   ├── 02_data_cleaning_eda.ipynb
│   ├── 03_spatial_feature_engineering.ipynb
│   ├── 04_geospatial_clustering.ipynb
│   ├── 05_cluster_profiling.ipynb
│   └── 06_mobility_insights.ipynb
│
├── src/
│   ├── config.py
│   ├── data_loader.py
│   ├── preprocessing.py
│   ├── features.py
│   ├── clustering.py
│   └── visualization.py
│
├── outputs/
│   ├── figures/
│   ├── maps/
│   └── tables/
│
└── app/
    └── streamlit_app.py

🚀 How to Run

Clone the repository:

git clone https://github.com/YOUR_USERNAME/urban-mobility-geospatial-clustering.git

cd urban-mobility-geospatial-clustering


Create a virtual environment:

python -m venv .venv


Activate it.

macOS/Linux:

source .venv/bin/activate


Windows:

.venv\Scripts\activate


Install dependencies:

pip install -r requirements.txt


Then run the notebooks sequentially:

01_data_acquisition
        ↓
02_data_cleaning_eda
        ↓
03_spatial_feature_engineering
        ↓
04_geospatial_clustering
        ↓
05_cluster_profiling
        ↓
06_mobility_insights

📌 Reproducibility

The project separates:

raw data

processed data

feature engineering

modeling

visualization

Raw TLC files are not committed to GitHub because of their size.

Instead, the repository contains the code required to reproduce the analysis from the official source data.

⚠️ Data Limitations

TLC notes that the trip records are submitted by technology providers / bases and that TLC does not guarantee the accuracy or completeness of every record.

Therefore:

results should be interpreted as patterns in the published trip records

clusters should not be treated as exact representations of all NYC mobility

taxi activity is not equivalent to total transportation activity

spatial clusters depend on the selected period and feature definitions

🎯 What This Project Demonstrates

This project demonstrates practical skills in:

Python

SQL-style aggregation logic

large-scale data processing

data cleaning

feature engineering

unsupervised learning

K-Means

DBSCAN

HDBSCAN

dimensionality reduction

geospatial analytics

cluster validation

interactive visualization

reproducible ML workflows

communicating ML results to non-technical stakeholders

👤 Author

Annisa Utama berliana

Data Scientist / Machine Learning Enthusiast

Focus areas:

Machine Learning
Geospatial Analytics
Unsupervised Learning
Data Products
Python

📜 License

This project is provided for educational and portfolio purposes.

The underlying trip data remains subject to the terms and policies of the NYC Taxi & Limousine Commission.
