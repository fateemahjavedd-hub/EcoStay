# 🌿 EcoStay — Energy Efficiency Optimization System

> **Predicting hotel energy consumption using booking demand and building efficiency data**

---

## 📌 Project Overview

EcoStay is a machine learning system that predicts how much energy a hotel building needs based on two inputs:
- **Who is coming** — from hotel booking data
- **What the building looks like** — from energy efficiency data

Hotels waste enormous energy running heating and cooling at full power regardless of how many guests are staying. EcoStay fixes this by predicting the right amount of energy based on actual occupancy predictions.

---

## 🎯 Objectives (As Per Assignment Requirements)

| # | Objective | Status |
|---|-----------|--------|
| 1 | Predict hotel occupancy levels from booking data | ✅ Done |
| 2 | Predict heating and cooling loads from building data | ✅ Done |
| 3 | Link both models through occupancy level | ✅ Done |
| 4 | Build interactive product prototype | ✅ Done |
| 5 | Write final report | ✅ Done |

---

## 🗂️ Project Structure

```
ecostay/
│
├── app.py                          ← Streamlit dashboard (main app)
├── requirements.txt                ← All Python packages needed
├── README.md                       ← This file
│
├── data/
│   ├── hotel_bookings.csv          ← Dataset 1 (Hotel Booking Demand)
│   └── energy_efficiency_data.csv  ← Dataset 2 (ENB2012 Energy Efficiency)
│
├── notebooks/
│   ├── 01_hotel_eda.ipynb          ← Hotel data EDA
│   ├── 02_energy_eda.ipynb         ← Energy data EDA
│   ├── 03_clustering.ipynb         ← KMeans occupancy segmentation
│   └── 04_model_training.ipynb     ← Model training and evaluation
│
├── models/
│   ├── demand_model.pkl            ← Trained Random Forest model
│   ├── energy_model.pkl            ← Trained Linear Regression model
│   ├── energy_scaler.pkl           ← StandardScaler for energy features
│   ├── cluster_scaler.pkl          ← StandardScaler for clustering
│   ├── kmeans.pkl                  ← Trained KMeans model
│   └── segment_multipliers.json    ← Occupancy multipliers per segment
│
└── report/
    └── EcoStay_Report.docx         ← Final project report
```

---

## 📊 Datasets Used

### Dataset 1 — Hotel Booking Demand
- **Source:** [Kaggle — jessemostipak/hotel-booking-demand](https://www.kaggle.com/datasets/jessemostipak/hotel-booking-demand)
- **Authors:** Nuno Antonio, Ana Almeida, Luis Nunes (2019)
- **Size:** 119,390 rows × 32 columns
- **Purpose:** Predict occupancy level (Low / Moderate / High / Peak)

### Dataset 2 — Energy Efficiency (ENB2012)
- **Source:** [Kaggle — Energy Efficiency Dataset](https://www.kaggle.com/datasets/elikplim/eergy-efficiency-dataset)
- **Authors:** Angeliki Xifara & Athanasios Tsanas, University of Oxford (2012)
- **Size:** 768 rows × 10 columns
- **Purpose:** Predict Heating Load and Cooling Load (kWh)

---

## 🤖 Machine Learning Models

### Model 1 — Demand Prediction
| Model | Accuracy |
|-------|----------|
| Linear Regression (baseline) | ~58% |
| **Random Forest (selected)** | **~84%** |

### Model 2 — Energy Prediction
| Model | R² Score | RMSE (Heating) | RMSE (Cooling) |
|-------|----------|----------------|----------------|
| **Linear Regression (Multi-Output)** | **0.88+** | **~2.1 kWh** | **~2.4 kWh** |

---

## 🔗 Model Integration

```
Hotel Booking Inputs          Building Inputs
(month, guests, nights)  +   (surface, wall, height, glazing)
         ↓                              ↓
  Random Forest              Multi-Output Linear Regression
  predicts SEGMENT           predicts BASE ENERGY
  (Low/Moderate/High/Peak)   (Heating kWh + Cooling kWh)
         ↓                              ↓
              FINAL ENERGY = Base Energy × Occupancy Multiplier
              CARBON (kg CO₂) = Final Energy × 0.233
```

---

## 🚀 How to Run

### Option 1 — Run Locally

```bash
# Step 1: Clone or download this project
cd ecostay

# Step 2: Install all required packages
pip install -r requirements.txt

# Step 3: Add your datasets to the data/ folder

# Step 4: Train models (run notebooks 01 to 04 in order)
jupyter notebook

# Step 5: Launch the dashboard
streamlit run app.py
```

### Option 2 — Run in Google Colab
Upload the notebook files to Google Colab and run cells in order. Upload both CSV files when prompted.

### Option 3 — Live Dashboard
👉 **[Click here to open EcoStay Dashboard](https://ecostay-energy.streamlit.app)**

> Note: Dashboard loads in 30-60 seconds on first open (free tier cold start)

---

## 🛠️ Tools and Technologies

| Tool | Purpose |
|------|---------|
| Python 3.10 | Core programming language |
| Google Colab | Development environment |
| Pandas | Data loading and manipulation |
| NumPy | Numerical calculations |
| Matplotlib / Seaborn | Data visualization and EDA graphs |
| Scikit-learn | Machine learning models and preprocessing |
| KMeans | Occupancy segmentation (unsupervised) |
| Random Forest | Demand prediction (supervised) |
| Linear Regression | Energy prediction (supervised) |
| Streamlit | Interactive dashboard |
| Joblib | Saving and loading trained models |
| Plotly | Interactive charts in dashboard |

---

## 📋 Assignment Requirements Coverage

| Requirement | Covered |
|-------------|---------|
| Missing value handling | ✅ Cell 6-7 |
| Categorical encoding (Label Encoding) | ✅ Cell 7 |
| Feature selection | ✅ Cell 8 |
| Feature scaling (StandardScaler) | ✅ Cell 8-9 |
| Monthly booking trends (EDA) | ✅ Graph 1 |
| Distribution of guests (EDA) | ✅ Graph 2 |
| Heating/cooling correlations (EDA) | ✅ Graph 3-4 |
| Model 1 — Linear Regression | ✅ Cell 12 |
| Model 1 — Random Forest | ✅ Cell 13 |
| Model 2 — Linear Regression | ✅ Cell 14 |
| Linking variable (occupancy level) | ✅ Cell 15 |
| Final Energy = Predicted × Occupancy | ✅ Cell 15-16 |
| Product prototype | ✅ Cell 17 + app.py |
| Final report (~2000 words) | ✅ report/ folder |

---

## 📝 Final Report Sections

1. Introduction — Energy challenges in hotels
2. Product Design — Datasets, target users, system requirements
3. Product Development — Models, tools, methodology
4. Project Management — Timeline, risks, real-world applications

---

## 👥 Authors

**Project:** EcoStay — Energy Efficiency Optimization System
**Assignment:** Energy Efficiency Optimization using Hotel Booking Demand Prediction
**Tool:** Python, Google Colab, Streamlit

---

## 📚 References

- Antonio, N., Almeida, A., Nunes, L. (2019). Hotel Booking Demand Datasets. *Data in Brief*, 22, 41–49.
- Tsanas, A., Xifara, A. (2012). Accurate quantitative estimation of energy performance of residential buildings. *Energy and Buildings*, 49, 560–567.
- Pedregosa, F. et al. (2011). Scikit-learn: Machine Learning in Python. *JMLR*, 12, 2825–2830.
- European Environment Agency (2023). CO₂ Emission Factor: 0.233 kg CO₂ per kWh.
