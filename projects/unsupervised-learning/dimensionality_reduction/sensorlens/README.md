SensorLens
Understanding High-Dimensional Sensor Data Through Representation Learning

SensorLens is an end-to-end machine learning project for analyzing high-dimensional chemical sensor data using dimensionality reduction, representation learning, clustering, and sensor drift analysis.

The project investigates whether a 128-dimensional sensor representation can be compressed into a much smaller latent space while preserving meaningful structure such as:

gas identity

sensor response patterns

cluster structure

temporal drift

downstream classification performance

Why this project?

High-dimensional sensor systems often contain strongly correlated and redundant measurements.

The challenge is not simply to reduce the number of features.

The real questions are:

How much information can be retained after compression?

Does the latent representation preserve class structure?

Are nonlinear methods better at revealing hidden structure?

Is the learned representation stable across temporal batches?

Can dimensionality reduction improve downstream machine learning efficiency?

Can latent-space analysis reveal sensor drift?

SensorLens treats dimensionality reduction as an analytical problem rather than a visualization-only technique.

Dataset

This project uses the Gas Sensor Array Drift at Different Concentrations dataset from the UCI Machine Learning Repository.

The dataset contains:

13,910 measurements

128 numerical features

16 chemical sensors

6 gas classes

multiple concentration levels

10 temporal batches

approximately 36 months of collection history

Each observation contains eight derived features for each of sixteen sensors, producing a 128-dimensional feature vector.

Source:

UCI Machine Learning Repository

Dataset DOI:

10.24432/C5MK6M

Dataset:

https://archive.ics.uci.edu/dataset/270/gas+sensor+array+drift+dataset+at+different+concentrations

Research Question

Can dimensionality reduction reveal stable and interpretable structure in high-dimensional chemical sensor data while preserving information useful for gas discrimination and exposing temporal sensor drift?

Methods

SensorLens compares three representation-learning strategies.

PCA

Principal Component Analysis provides a linear baseline.

We investigate:

explained variance

cumulative explained variance

loading structure

reconstruction error

downstream classification

UMAP

Uniform Manifold Approximation and Projection is used to investigate nonlinear structure.

We analyze:

local neighborhood structure

class separation

batch structure

embedding stability

Autoencoder

A neural autoencoder learns a nonlinear compressed representation.

Architecture:

128
 ↓
64
 ↓
32
 ↓
16
 ↓
8
 ↓
16
 ↓
32
 ↓
64
 ↓
128


The 8-dimensional bottleneck becomes the learned latent representation.

Experimental Design

The project is divided into several experiments.

Experiment 1
Data quality
      ↓
Experiment 2
Exploratory analysis
      ↓
Experiment 3
Standardization
      ↓
Experiment 4
PCA
      ↓
Experiment 5
UMAP
      ↓
Experiment 6
Autoencoder
      ↓
Experiment 7
Latent clustering
      ↓
Experiment 8
Sensor drift
      ↓
Experiment 9
Downstream evaluation
      ↓
Experiment 10
Final comparison

Evaluation

Dimensionality reduction is evaluated using multiple criteria rather than visualization alone.

Representation quality

explained variance

reconstruction error

trustworthiness

neighborhood preservation

Cluster quality

silhouette score

Davies-Bouldin index

adjusted Rand index

Downstream utility

A classifier is trained using:

Original 128 features
vs
PCA representation
vs
UMAP representation
vs
Autoencoder representation


Metrics:

accuracy

macro F1

balanced accuracy

inference dimensionality

Drift analysis

Representations are compared across temporal batches.

We investigate:

centroid movement

distribution shift

class separation over time

batch-to-batch distance

Key Questions

The final report answers:

Q1

How many dimensions are required to preserve most of the variance?

Q2

Does nonlinear dimensionality reduction reveal structure that PCA misses?

Q3

Does the autoencoder produce a useful compact representation?

Q4

Does compression preserve downstream classification performance?

Q5

Does the latent representation remain stable across temporal batches?

Q6

Which representation is most useful for analysis versus downstream modeling?

Project Structure
sensorlens/
│
├── data/
│   ├── raw/
│   └── processed/
│
├── notebooks/
│   ├── 01_data_understanding.ipynb
│   ├── 02_data_quality_and_eda.ipynb
│   ├── 03_preprocessing.ipynb
│   ├── 04_pca_analysis.ipynb
│   ├── 05_umap_analysis.ipynb
│   ├── 06_autoencoder.ipynb
│   ├── 07_latent_clustering.ipynb
│   ├── 08_drift_analysis.ipynb
│   ├── 09_downstream_evaluation.ipynb
│   └── 10_final_comparison.ipynb
│
├── src/
│   ├── data_loader.py
│   ├── preprocessing.py
│   ├── visualization.py
│   ├── models.py
│   └── evaluation.py
│
└── outputs/
    ├── figures/
    ├── tables/
    └── models/

Reproducibility

Create a virtual environment:

python -m venv .venv


Activate it.

macOS / Linux
source .venv/bin/activate

Windows
.venv\Scripts\activate


Install dependencies:

pip install -r requirements.txt


Start Jupyter:

jupyter lab


Run notebooks sequentially from:

01 → 02 → 03 → ... → 10

Dataset Setup

Download the dataset from UCI and place the batch files inside:

data/raw/


Expected structure:

data/raw/
├── batch1.dat
├── batch2.dat
├── batch3.dat
├── batch4.dat
├── batch5.dat
├── batch6.dat
├── batch7.dat
├── batch8.dat
├── batch9.dat
└── batch10.dat


The dataset is not committed to this repository.

Main Findings

Results are generated automatically by the notebooks.

The final comparison reports:

Method          Dimensions    Reconstruction    Macro F1
---------------------------------------------------------
Original        128            -                 ...
PCA             ...            ...               ...
UMAP            ...            ...               ...
Autoencoder     8              ...               ...


Actual values depend on the executed environment and experiment configuration.

What this project demonstrates

This project demonstrates practical understanding of:

dimensionality reduction

PCA

UMAP

autoencoders

representation learning

unsupervised learning

clustering

anomaly/shift analysis

sensor drift

feature redundancy

model evaluation

reproducible ML experimentation

Limitations

Several limitations should be considered.

The dataset was collected in a controlled experimental environment.

The dataset does not represent every real-world electronic-nose deployment.

UMAP is primarily used here as an exploratory representation method.

Latent-space visualization should not be interpreted as proof of physical causality.

Temporal batch information is used to study distribution shift, not to construct a forecasting model.

Autoencoder representations depend on architecture and optimization settings.

Future Work

Potential extensions include:

contrastive representation learning

domain-adversarial drift correction

variational autoencoders

sensor failure simulation

online drift detection

uncertainty estimation

lightweight edge deployment

representation stability benchmarking

Citation

Vergara, A. (2012). Gas Sensor Array Drift at Different Concentrations. UCI Machine Learning Repository.

DOI: 10.24432/C5MK6M

Dataset license information is provided by UCI.

Author

Built as a machine learning portfolio project focused on high-dimensional representation learning and sensor intelligence.
