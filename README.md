# 🏎️ Formula 1 Race Outcome Prediction — Machine Learning Pipeline

[![CI - F1 Race Prediction API](https://github.com/chandhu3095/F1-Race-Prediction-API/actions/workflows/ci.yml/badge.svg)](https://github.com/chandhu3095/F1-Race-Prediction-API/actions)

An end-to-end machine learning project that predicts Formula 1 driver finishing positions using historical race data (2015–2024). The project extends a Jupyter Notebook ML workflow into a **FastAPI REST API**, with automated testing, Docker containerization, continuous integration, and public deployment.

**Live API:** [F1 Race Prediction API](https://f1-race-prediction-api.onrender.com)  
**Interactive API Documentation:** [Swagger UI](https://f1-race-prediction-api.onrender.com/docs)  
**GitHub Repository:** [F1-Race-Prediction-API](https://github.com/chandhu3095/F1-Race-Prediction-API)  
**GitHub Actions:** [Workflow Runs](https://github.com/chandhu3095/F1-Race-Prediction-API/actions)

---

## 📌 Project Overview

Formula 1 race outcomes are influenced by qualifying performance, lap pace, pit-stop strategy, driver experience, and track characteristics.

This project uses historical Formula 1 data to build, evaluate, interpret, and deploy regression models for predicting driver finishing positions.

### Key Features

- Data cleaning, validation, exploratory data analysis (EDA), and feature engineering.
- Random Forest baseline and XGBoost regression models.
- Model evaluation using MAE, RMSE, and positional error analysis.
- SHAP-based model explainability.
- FastAPI REST API for serving predictions.
- Pydantic request validation and structured responses.
- Automated API testing with pytest.
- Docker containerization.
- GitHub Actions continuous integration (CI).
- Public deployment on Render.

## 🎯 Problem Statement

Predict a Formula 1 driver's finishing position using engineered features derived from historical race data.

The task is formulated as a **supervised regression problem**, where the target variable is the driver's numerical finishing position.

**Current scope:** The deployed API performs inference for historical, completed races. It is not yet a true pre-race forecasting or live race prediction system.

## 📊 Dataset

**Dataset Source:** [Formula 1 Racing Dataset — Kaggle](https://www.kaggle.com/datasets/melissamonfared/formula-1)

- **Time Range:** 2015–2024
- **Modeling Records:** 3,345 driver-race records
- **Data Format:** Multiple relational CSV datasets

### Data Sources

- Race results
- Qualifying results
- Lap times
- Pit stops
- Driver and constructor information
- Circuit and race metadata

The data preparation process includes cleaning, validation, filtering, merging relevant tables, exploratory analysis, and feature engineering.

## 🔍 Exploratory Data Analysis (EDA)

EDA was used to investigate race performance patterns and support feature selection.

Key analyses included:

- Distribution of finishing positions.
- Qualifying position versus finishing position.
- Pit-stop count versus finishing position.
- Lap-time metrics and race performance.
- Relationships between driver experience and finishing position.

## 🛠️ Feature Engineering

The deployed XGBoost model uses nine features:

| Feature | Description |
|---|---|
| `qual_pos` | Driver's qualifying position |
| `pit_count` | Number of pit stops |
| `laps_completed` | Number of laps completed |
| `avg_lap_sec` | Average lap time in seconds |
| `fastest_lap_sec` | Fastest lap time in seconds |
| `career_avg_finish` | Historical average finishing position |
| `career_race_count` | Number of previous races |
| `qual_vs_career` | Qualifying performance relative to career average |
| `track_avg_finish` | Historical average finishing position associated with the track |

The API's feature service prepares these features from the historical datasets before passing them to the trained model.

## 🤖 Modeling Approach

Two regression models were evaluated.

### 1. Random Forest Regressor

- Used as the baseline model.
- Captures nonlinear relationships between features and finishing position.
- Provides a benchmark for model comparison.

### 2. XGBoost Regressor

- Selected as the final deployed model.
- Captures complex relationships between engineered features.
- Saved in JSON format for inference through the API.

## 📈 Model Evaluation

Model performance was evaluated using Mean Absolute Error (MAE), Root Mean Squared Error (RMSE), and positional error analysis.

| Metric | XGBoost Result |
|---|---:|
| Mean Absolute Error (MAE) | 2.06 positions |
| Root Mean Squared Error (RMSE) | 2.73 positions |
| Predictions within ±1 position | 46.34% |
| Predictions within ±2 positions | 68.91% |

These results describe performance on the evaluated test set and do not guarantee accuracy on future races.

## 🔍 Model Explainability — SHAP

SHAP (SHapley Additive exPlanations) was used in the notebook to investigate feature contributions and interpret model predictions.

It supports:

- Understanding feature contributions to individual predictions.
- Comparing the influence of model features.
- Improving the interpretability of model outputs.

## 🏗️ Application Architecture

```text
Client
  |
  | POST /predict
  v
FastAPI Application
  |
  v
Pydantic Request Validation
  |
  v
FeatureService
  |
  | Build 9 model features
  v
ModelService
  |
  | XGBoost inference
  v
Prediction Response
