# LiveDrift – Drift-Aware Stock Predictor

**Status:** *This project is currently in active development. Components will be implemented incrementally.*

## Overview
**LiveDrift** is a real-time machine learning system designed to forecast short-term stock market trends while actively monitoring for model drift. The system automatically triggers retraining when performance degrades due to shifting market conditions.

Key features:
- Multiple data sources including market prices, sentiment analysis, and ESG scores.
- Automated ETL and model training pipelines with **Apache Airflow**.
- Drift detection using **Evidently AI** with retraining triggers.
- Real-time inference service powered by **FastAPI**, containerized in Docker.
- Observability and monitoring with **Prometheus & Grafana**.
- Web demo for live predictions and visualizations.

---

##  System Architecture

<a >
  <img src="/System-Architecture.png" alt="Demo" width="700">
</a>

### 1. Data Sources
- **yfinance** – Stock prices & technical indicators.
- **Financial Modeling Prep API** – Stock news sentiment scores.
- **Finnhub API** – ESG scores and market insights.

### 2. Data Warehouse
- Centralized storage in **Amazon S3 or GCP Buckets ** for raw and processed datasets.

### 3. Data Processing & Feature Engineering
- Data preprocessing for missing values, normalization or standardization, and transformations.
- Technical Analysis (TA) feature pipeline.

### 4. Model Training
- **XGBoost** (for speed & interpretability) for the prototype will later move to an LSTM Neural Network.
- Evaluation and registration in the **Model Registry**.
- Lime to explain Predictions(Later Addition)

### 5. Drift Monitoring
- **Evidently AI** checks model performance and data distribution on regular intervals.
- Drift above threshold triggers retraining via Airflow.

### 6. Serving & Observability
- **FastAPI** inference service (Dockerized, deployable to AWS Lambda or GCP Cloud Run)  
- Optional **Streamlit** live demo for end-user interaction  
- **Prometheus** collects metrics and logs, visualized in **Grafana**, including:

  - **Model Metrics** – Prediction latency, prediction throughput, accuracy over time, drift detection results  
  - **Pipeline Metrics** – ETL job runtimes, data freshness, retraining frequency  
  - **System Metrics** – CPU/memory utilization, container uptime, API request/response rates, error counts(Maybe)



### 7. Automation
- **Apache Airflow** schedules and orchestrates:
  - ETL pipeline
  - Model training
  - Drift checks and retraining triggers

---

##  Development Plan

| Phase  | Description |
|--------|-------------|
| **1**  | Get all components working individually (Jupyter Notebooks) |
| **2**  | Setup complete Airflow pipelines |
| **3**  | Implement monitoring & observability |
| **4**  | Build web demo interface |
| **5**  | Deploy full system to production |

---


