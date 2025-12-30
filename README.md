# 🏎️ Formula 1 Race Outcome Prediction — Machine Learning & Analytics

An end-to-end **machine learning and analytics project** focused on predicting **Formula 1 driver finishing positions** using historical race data, advanced feature engineering, explainable AI (SHAP), and interactive Power BI dashboards.

---

## 📌 Problem Statement

Formula 1 race outcomes are influenced by multiple interacting factors such as:

- Qualifying performance  
- Lap time consistency  
- Pit stop strategy  
- Driver experience  
- Track characteristics  

The objective of this project is to **predict a driver’s finishing position** in a race by learning patterns from historical data, while ensuring the predictions are **accurate, interpretable, and actionable**.

---

## 📊 Dataset

The dataset is sourced from publicly available **Formula 1 historical data** and consists of multiple relational tables.

### Key data sources:
- Race results (finishing position, laps completed, points)
- Qualifying data (grid position, qualifying rank)
- Lap times (lap-level performance)
- Pit stop data (number of pit stops, timing)
- Driver and constructor metadata
- Race metadata (track, season, race name)

**Time range:**  
📅 *2015 – 2024* (modern Formula 1 era)

The raw datasets were merged and filtered to ensure consistency and relevance for modern racing dynamics.

---

## 🛠️ Feature Engineering

Significant feature engineering was performed to convert raw race data into **ML-ready numerical features**.

### Key engineered features include:
- **Qualifying Position (`qual_pos`)**
- **Lap Performance**
  - Average lap time
  - Fastest lap time
- **Pit Stop Metrics**
  - Pit stop count
  - First pit lap
- **Driver Experience**
  - Career average finish
  - Career race count
- **Contextual Features**
  - Qualifying vs career performance gap
  - Track-level average finishing position (track difficulty proxy)

### Target Variable:
- **Finishing Position** (regression target)

---

## 🤖 Modeling Approach

This problem was framed as a **regression task** since finishing position is an **ordered numeric outcome**.

### Models used:
- **Random Forest Regressor** (baseline)
- **XGBoost Regressor** (final model)

XGBoost was chosen as the final model due to:
- Better bias–variance control
- Sequential error correction (boosting)
- Improved performance on tabular data

---

## 📈 Model Evaluation

Model performance was evaluated using:

- **Mean Absolute Error (MAE)**
- **Root Mean Squared Error (RMSE)**
- **Positional Accuracy**
  - Predictions within ±1 position
  - Predictions within ±2 positions

### Interpretation:
- MAE directly represents average finishing position error
- Positional accuracy reflects realistic race prediction quality

---

## 🔍 Model Explainability (SHAP)

To ensure transparency, **SHAP (SHapley Additive Explanations)** was used to explain model predictions.

### SHAP provides:
- Feature-level contribution for each prediction
- Directional impact (positive or negative)
- Global and driver-specific explanations

### Key insights:
- Qualifying position is one of the strongest predictors
- Lap consistency often outweighs raw speed
- Pit stop behavior has context-dependent impact

SHAP ensures the model is **interpretable and trustworthy**, not a black box.

---

## 📊 Power BI Dashboards

To translate model outputs into actionable insights, interactive **Power BI dashboards** were created.

### Dashboards include:
- **Race Performance Overview**
- **Driver Performance & Explainability**
- **Pit Stop Strategy & Impact**

These dashboards allow:
- Driver and race-level filtering
- Comparison of actual vs predicted performance
- Strategic insights into pit stop decisions

---

## 🧠 Key Learnings

- Feature engineering has a greater impact than model choice
- Regression is more suitable than classification for ordered outcomes
- Explainability is essential for real-world ML adoption
- Dashboards bridge the gap between ML models and business decisions

---

## 🧰 Tech Stack

- **Python**
- **Pandas, NumPy**
- **Scikit-learn**
- **XGBoost**
- **SHAP**
- **Power BI**

---
## 📁 Project Structure
'''
├── data/
│ ├── raw/ # Raw Kaggle datasets
│ └── processed/ # Cleaned and feature-engineered data
├── notebooks/
│ └── f1_ml_pipeline.ipynb # End-to-end ML pipeline notebook
├── models/
│ ├── rf_model_baseline.pkl # Random Forest baseline model
│ └── xgb_race_model.json # XGBoost final model
├── powerbi/
│ └── dashboards.pbix # Power BI dashboards
└── README.md # Project documentation
'''
---

## 🚀 Future Enhancements

- Live race prediction using APIs
- Weather and tyre compound features
- Driver head-to-head comparisons
- Real-time dashboard integration

---

## 🙌 Acknowledgements

Dataset sourced from publicly available Formula 1 historical data.

---

## 📬 Contact

If you’d like to discuss this project or opportunities in data science / machine learning, feel free to connect with me on LinkedIn.

---



