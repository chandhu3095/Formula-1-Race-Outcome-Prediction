# 🏎️ Formula 1 Race Outcome Prediction — Machine Learning Pipeline

## 📌 Project Overview

This project builds an **end-to-end machine learning pipeline** to predict a Formula 1 driver’s **finishing position** using historical race data from the modern F1 era (2015–2024).

Formula 1 race outcomes are influenced by multiple interacting factors such as qualifying performance, lap pace consistency, pit stop strategy, driver experience, and track characteristics.  
The goal of this project is to model these factors together and produce **accurate and explainable predictions**.

In addition to machine learning modeling, the project includes **interactive Power BI dashboards** to translate predictions into business- and strategy-focused insights.

---

## 🎯 Problem Statement

Predict the **finishing position of a Formula 1 driver** in a race using historical data, while ensuring:

- Strong predictive performance
- Clear interpretability of model decisions
- Practical insights into race strategy and performance

This is framed as a **regression problem**, where the target is a numeric, ordered finishing position.

---

## 📊 Dataset

The dataset is sourced from publicly available Formula 1 historical data (Kaggle) and consists of multiple relational tables.

### Key data sources:
- Race results (finishing position, laps completed, points)
- Qualifying data (grid position, qualifying rank)
- Lap times (lap-level performance consistency)
- Pit stop data (number of stops, timing)
- Driver and constructor metadata
- Race metadata (track, season, race details)

### Time range:
- **2015 – 2024** (modern Formula 1 era)

The raw datasets were merged, cleaned, and filtered to ensure consistency and relevance for modern race dynamics.

---

## 🔍 Exploratory Data Analysis (EDA)

EDA was intentionally kept **light and focused**, as the dataset is structured and domain-driven.

Key exploratory analyses include:
- Distribution of finishing positions
- Qualifying position vs finishing position
- Pit stop count vs finishing position
- Lap pace consistency vs finishing position

These checks validated domain assumptions and supported feature selection.

---

## 🛠️ Feature Engineering

Raw race data was transformed into **model-ready features**, including:

- **Qualifying performance**
  - Qualifying position
  - Qualifying vs career average performance

- **Lap pace metrics**
  - Average lap time
  - Fastest lap time

- **Pit stop strategy**
  - Number of pit stops
  - First pit lap (for pit strategy modeling)

- **Driver experience**
  - Career race count
  - Career average finishing position

- **Track characteristics**
  - Track-level average finishing position (difficulty proxy)

Target variable:
- **Finishing Position** (regression target)

Missing values were handled carefully, and only reliable race entries were used for training.

---

## 🤖 Modeling Approach

This is a **supervised regression problem**.

### Models used:
1. **Random Forest Regressor**
   - Baseline model
   - Strong non-linear performance
   - Robust to noise

2. **XGBoost Regressor**
   - Final production model
   - Better generalization and lower error
   - Efficient handling of complex feature interactions

The model learns patterns such as:
- Strong qualifying positions improving race outcomes
- Lap pace consistency being more important than single fast laps
- Excessive pit stops negatively impacting finishing position

---

## 📈 Model Evaluation

Model performance was evaluated using:

- **Mean Absolute Error (MAE)**
- **Root Mean Squared Error (RMSE)**
- **Positional Accuracy**
  - Predictions within ±1 finishing position
  - Predictions within ±2 finishing positions

These metrics are intuitive and directly interpretable in a racing context.

---

## 🔍 Explainability (SHAP)

To ensure transparency, **SHAP (SHapley Additive Explanations)** was used.

SHAP provides:
- Feature-level contribution for each prediction
- Directional impact (positive or negative)
- Global and driver-specific explanations

Key insights:
- Qualifying position is the strongest predictor
- Lap pace consistency significantly impacts outcomes
- Pit stop behavior can have positive or negative effects depending on context

This prevents the model from being treated as a black box.

---

## 📊 Power BI Dashboards

Interactive dashboards were built to translate model outputs into actionable insights:

1. **Race Performance Overview**
   - Actual vs predicted finishing positions
   - Driver and race-level analysis

2. **Driver Explainability**
   - Feature influence on predictions
   - Driver-specific performance patterns

3. **Pit Stop Strategy & Impact**
   - Pit timing vs race outcome
   - Strategy effectiveness across tracks and teams

---

## 🗂️ Project Structure

```
├── data/
│   ├── raw/                # Raw datasets from Kaggle
│   └── processed/          # Cleaned and engineered data
│
├── notebooks/
│   └── f1_ml_pipeline.ipynb   # End-to-end ML workflow
│
├── models/
│   ├── rf_model_baseline.pkl  # Random Forest baseline model
│   └── xgb_race_model.json   # Final XGBoost model
│
├── powerbi/
│   └── dashboards.pbix       # Power BI dashboards
│
├── README.md
```


---

## 🧰 Tools & Technologies

- **Python** (Pandas, NumPy)
- **Scikit-learn**
- **XGBoost**
- **SHAP**
- **Matplotlib / Plotly**
- **Power BI**

---

## ✅ Key Takeaways

- Built a complete ML pipeline from raw data to explainable predictions
- Applied domain-driven feature engineering
- Used advanced evaluation techniques beyond standard regression metrics
- Combined machine learning with business intelligence for storytelling

---

## 🔗 Dataset Source

Formula 1 Racing (1950–2024):  
https://www.kaggle.com/datasets/melissamonfared/formula-1

---

## 📬 Feedback

Feedback, suggestions, and improvements are welcome.


