# 🛒 RetailPulse — Project FORESIGHT

**AI-Powered Demand & Inventory Intelligence Platform**

RetailPulse is an end-to-end data science platform that helps retailers forecast SKU-level demand, catch stockout/overstock risk early, understand customer behaviour, and get actionable inventory recommendations — all through an interactive dashboard.

Built as a 1-month Data Science & Analytics project (25 Jun 2026 – 25 Jul 2026).

---

## ✨ Features

- 📈 **Demand Forecasting** — Prophet + LSTM hybrid ensemble (10.4% MAPE)
- 👥 **Customer Segmentation** — RFM features clustered with KMeans/DBSCAN into personas
- ⚠️ **Churn Prediction** — XGBoost classifier with SHAP explainability (0.928 AUC)
- 📦 **Inventory Optimization** — EOQ, safety stock, and reorder-point recommendations per SKU
- 🔬 **Model Monitoring** — Evidently drift detection + Prometheus/Grafana dashboards
- 🖥️ **Dual dashboards** — a 4-page Streamlit web app and a 12-page Power BI executive suite

## 🏗️ Architecture

```
Data Layer          → raw + processed retail transaction data
Feature Engineering  → RFM, lag features, rolling averages
Model Layer          → Prophet, LSTM, hybrid ensemble, XGBoost (tracked in MLflow)
Serving Layer        → Streamlit app, FastAPI endpoints
Monitoring Layer      → Evidently (drift), Prometheus + Grafana
```

## 📂 Project Structure

```
retailpulse-main/
├── app/                    # Streamlit application
│   ├── main.py             # Entry point
│   ├── pages/               # Forecasting, Segments, Churn, Inventory, Monitoring
│   └── utils/                # PDF export helpers
├── data/
│   ├── raw/                 # Source transaction/customer/product data
│   └── processed/            # Cleaned + feature-engineered datasets
├── 01_eda.ipynb … 27_day.ipynb   # Day-by-day build notebooks (EDA → modeling → MLOps)
├── monitoring/              # Prometheus config, Grafana dashboard, metrics API
├── airflow/                 # Pipeline DAGs
├── k8s/                     # Kubernetes deployment manifests
├── tests/load/               # Locust load-testing script
├── Dockerfile
├── requirements.txt          # Full dependencies (notebooks + training)
├── requirements-deploy.txt   # Lean dependencies for the deployed Streamlit app
└── DEPLOYMENT.md
```

## 🚀 Getting Started

### Run locally

```bash
git clone https://github.com/<your-username>/retailpulse.git
cd retailpulse
pip install -r requirements-deploy.txt
streamlit run app/main.py
```

### Deploy on Streamlit Community Cloud

See [`DEPLOYMENT.md`](DEPLOYMENT.md) — set the main file path to `app/main.py` and use `requirements-deploy.txt` for a fast build.

## 📊 Results

| Metric | Result |
|---|---|
| Demand forecast accuracy (MAPE) | 10.4% |
| Customer churn model (AUC) | 0.928 |
| Projected stockout reduction | 32% |
| Load test (100 concurrent users) | p95 = 3.4s, 0 errors |
| Data drift (production) | 0.0% share, no alert |

## 🛠️ Tech Stack

Python · pandas · scikit-learn · XGBoost · Prophet · PyTorch (LSTM) · SHAP · Optuna · Streamlit · Plotly · Power BI · MLflow · Evidently · Prometheus · Grafana · FastAPI · Docker · Kubernetes · GitHub Actions

## 📄 License

This project was built for educational/internship purposes as part of a Data Science & Analytics program.
