# 🚀 Detect Behavior with Sensor Data
> **Capstone AI/ML Project – CIMT College, June 2025**  
> Author: Albert Tchaptchet Womga | Instructor: Priya Virdi  
> [📄 Final Report (PDF)](./reports/Capstone_Report_Albert_Womga.pdf)

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](./LICENSE)
[![Python](https://img.shields.io/badge/python-3.9-blue.svg)](https://www.python.org/)
[![Framework](https://img.shields.io/badge/framework-ScikitLearn%20%7C%20XGBoost%20%7C%20Pandas-blue)]()
[![Status](https://img.shields.io/badge/status-Completed-brightgreen)]()

---

## 🧠 Project Overview

This project tackles the **automated detection of Body-Focused Repetitive Behaviors (BFRBs)** using time-series sensor data from the **Helios wrist-worn device**, developed by the Child Mind Institute.

BFRBs include subtle, compulsive gestures such as:
- Hair pulling
- Skin scratching
- Nail biting

Using IMU (motion), thermopile (temperature), and ToF (proximity) sensor modalities, we classify gestures as **BFRB-like vs non-BFRB** and further identify **gesture subtypes**.

---

## 📦 Dataset

- 📥 Source: [CMI: Detect Behavior with Sensor Data – Kaggle Competition](https://www.kaggle.com/competitions/cmi-detect-behavior-with-sensor-data)
- 🎯 Objective: Classify gestures based on **sensor sequences** of IMU, ToF, and thermal data.
- 👤 Demographics: Age, handedness, body dimensions included as contextual features.
- 🧾 Input shape: Sequences of ~63 timesteps × 300+ features  
- 🔖 Target:  
  - Binary: BFRB-like vs. non-BFRB  
  - Multiclass: 8 BFRB gestures + 1 non-target class

---

## 🧪 Methodology

### ✨ Data Pipeline
- Preprocessing:
  - Filter `Performs gesture` phase
  - Replace `-1` in ToF with NaN
  - Z-score normalization
- Feature Engineering:
  - Time-domain: rolling mean, deltas
  - Frequency-domain: FFT (IMU channels)
  - Statistical summaries: mean, std, RMS, etc.
- Integration of demographic features

### 🔧 Models
- ✅ `Random Forest`: baseline ensemble model
- ✅ `XGBoost`: gradient-boosted trees (final best model)

### 🧮 Evaluation Metric

Final Score = **0.5 × (F1_binary + F1_macro)**  
- `F1_binary`: BFRB vs. non-BFRB
- `F1_macro`: 9-class gesture classification

---

## 📊 Results

| Model         | F1_binary | F1_macro | Final Score |
|---------------|-----------|----------|--------------|
| Random Forest | 0.9681    | 0.6407   | 0.8044       |
| XGBoost       | **0.9801**| **0.6898** | **0.8349**     |

- 🔥 XGBoost outperformed in both binary and multiclass classification.
- 🧠 Recommended for deployment due to its ability to capture subtle behavioral nuances.

---

## 📁 Repo Structure

```bash
Detect-Behavior-with-Sensor-Data/
├── notebooks/
│   └── Detect-Behavior-with-Sensor-Data.ipynb     # Full modeling pipeline
├── reports/
│   └── Capstone_Report_Albert_Womga.pdf           # Formal PDF report
├── requirements.txt                               # Python dependencies
├── README.md
└── LICENSE
