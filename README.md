# Cloud Incident Intelligence

Machine learning and NLP-based investigation of synthetic cloud infrastructure telemetry and API failure logs to evaluate predictive signal quality, root cause classification feasibility, and data leakage risks in observability systems.

---

# Project Overview

This project explores whether API failure root causes can be reliably predicted using:
- infrastructure metadata
- operational telemetry
- system log data
- NLP-based log intelligence pipelines

The project was intentionally approached as a realistic ML engineering investigation rather than a simple “train model and maximize accuracy” workflow.

Several experiments were conducted to evaluate:
- predictive signal strength
- feature usefulness
- model behavior
- synthetic dataset realism
- leakage-prone operational fields

---

# Dataset

Dataset Used:
- API Failure Intelligence Dataset (AFID)

Dataset Characteristics:
- 220,000+ rows
- 22 columns
- synthetic cloud/API observability data
- distributed systems telemetry
- API error logs
- infrastructure metadata
- operational context fields

Key fields included:
- API metadata
- status codes
- latency metrics
- retry counts
- regions/environments
- log levels
- error messages
- remediation actions
- root cause labels

---

# Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- Jupyter Notebook
- Git/GitHub

---

# Machine Learning Approaches

The following approaches were implemented and evaluated:

## 1. Infrastructure Metadata Baseline

### Features
- API metadata
- latency
- request sizes
- retry counts
- regions
- environments

### Model
- Logistic Regression

### Result
- Near random-chance accuracy (~6–7%)

---

## 2. Operational Context Features

### Additional Features
- HTTP status codes
- error types

### Models
- Logistic Regression
- Random Forest

### Result
- Minimal improvement
- weak predictive signal detected

---

## 3. Leakage Investigation

### Potential Leakage-Prone Fields
- resolution_action
- error_message
- retry success indicators

### Purpose
Evaluate whether post-incident fields artificially inflate model performance.

### Result
Dataset still showed extremely weak predictive relationships.

---

## 4. NLP / Log Intelligence Pipeline

### Implemented
- TF-IDF vectorization on API error logs
- hybrid structured + text ML pipeline

### Model
- Logistic Regression

### Result
Semantic log text also showed minimal predictive power.

---

# Key Findings

This project ultimately demonstrated that:

- model complexity cannot compensate for weak data signal
- synthetic datasets may lack meaningful causal structure
- validating dataset realism is critical in ML engineering
- proper leakage analysis is essential
- rigorous experimentation matters more than chasing inflated metrics

Despite testing multiple feature subsets and ML pipelines, all experiments consistently performed near random-chance accuracy, suggesting limited learnable relationships between the provided features and target labels.

---

# ML Engineering Concepts Demonstrated

- train/test split isolation
- preprocessing pipelines
- ColumnTransformer workflows
- OneHotEncoding
- TF-IDF text vectorization
- Random Forest modeling
- Logistic Regression baselines
- feature subset experimentation
- leakage analysis
- reproducible notebook workflows

---

# Repository Structure

```text
cloud-incident-intelligence/
│
├── data/
│   ├── raw/
│   └── processed/
│
├── notebooks/
│   ├── 01_data_exploration.ipynb
│   └── 02_modeling_baseline.ipynb
│
├── src/
│
├── reports/
│
├── models/
│
├── requirements.txt
├── .gitignore
└── README.md
