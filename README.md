# BOM DelayRadar ✈️
> **Interactive Machine-Learning Flight Delay Predictor & Data Explorer for Mumbai (BOM) Departures (2024)**

[![GitHub Pages](https://img.shields.io/badge/Live_Demo-GitHub_Pages-2ea44f?style=for-the-badge&logo=github)](https://yaswanth-codeai.github.io/bom-delay-radar/)
[![License](https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge)](LICENSE)
[![Zero Dependencies](https://img.shields.io/badge/Dependencies-0_Runtime-blueviolet?style=for-the-badge)](#tech-stack)

---

## 🛫 Overview

**BOM DelayRadar** is an interactive web-based data visualization and machine learning tool designed to predict and analyze departure flight delays out of **Chhatrapati Shivaji Maharaj International Airport (BOM), Mumbai**.

Built using real-world data from **22,886 departures in 2024**, it pairs an in-depth exploratory analytics dashboard with an embedded, client-side gradient-boosted decision tree ensemble that evaluates delay risks in real time without sending any data over the network.

🔗 **Live Demo:** [https://yaswanth-codeai.github.io/bom-delay-radar/](https://yaswanth-codeai.github.io/bom-delay-radar/)

---

## ✨ Key Features

### 1. 🎯 Real-Time In-Browser ML Predictor
- **Zero Latency & 100% Client-Side:** Evaluates a compact 13-feature gradient boosted tree ensemble directly inside JavaScript.
- **Probabilistic Risk Gauge:** Outputs the exact probability of departing $\ge 15$ minutes late, alongside expected delay duration in minutes.
- **Counterfactual Guidance (*"What would change the answer?"*):** Automatically identifies actionable optimizations (e.g., rescheduling from rush hour to 13:00, flying during lower airport traffic).
- **24-Hour Departure Hour Sweep:** Instantly graphs the safest departure hour for your chosen destination and airline profile.

### 2. 📊 Multi-Dimensional Data Explorer
- **Synchronized Global Filters:** Filter across all 22,886 flights by Month, Airline Type (Indian vs. Foreign carriers), Route (Domestic vs. International), and Weather conditions.
- **Dynamic KPIs:** Real-time updates for flight counts, delay rates, average delay length, and peak vs. off-peak performance.
- **Temporal & Congestion Charts:** Interactive bar charts analyzing delay rate by departure hour, month, and airport traffic level.
- **Interactive Route Network Maps:**
  - Scalable vector graphics (SVG) world projection with curved geodesic flight paths.
  - Dedicated high-resolution close-up map of the Indian domestic network with Natural Earth boundary paths.
  - Color-coded delay intensity and proportional flight volume circles with keyboard accessibility.
- **Hour $\times$ Weekday Heat Map:** 168-cell matrix showing delay hotspots across every hour and day of the week.

### 3. 🔬 Transparent Machine Learning Benchmarks
- **Honest Calendar-Split Validation:** Trained strictly on January–September 2024 (17,132 flights) and evaluated on unseen October–December 2024 departures (5,754 flights) to mirror production reality and prevent data leakage.
- **Model Comparison:** Full benchmark table comparing Baseline, Logistic Regression, Random Forest, Gradient Boosting, and a Stacked Ensemble.
- **Diagnostics:** Confusion matrix, empirical risk calibration bands, permutation feature importance, and feature ablation studies.

---

## 🧠 Model & Methodology Summary

| Metric | Stacked Ensemble (Full) | Compact In-Browser GB |
| :--- | :---: | :---: |
| **Accuracy** | 84.48% | **85.12%** |
| **Precision** | 80.48% | **83.07%** |
| **Recall** | 76.67% | **75.12%** |
| **F1-Score** | 0.7853 | **0.7890** |
| **ROC-AUC** | 0.8954 | **0.8983** |
| **Delay MAE** | — | **$\pm$ 5.77 mins** |

### Top Predictive Drivers
1. **Airport Traffic Pressure (`BOM_Hourly_Traffic` $\times$ `Is_Peak_Hour`):** By far the largest determinant of flight delays. At traffic levels 1–2, delay rate is $\approx 13\%$; at saturation (level 9–10), it exceeds $70\%$.
2. **Scheduled Time of Day:** Double daily peak hours (07:00–09:00 and 18:00–20:00).
3. **Weather Dynamics:** Heavy rain and thunderstorm conditions during monsoon months (June–September) significantly amplify delay variance.

---

## 🛠️ Tech Stack

- **Frontend:** Semantic HTML5, Custom CSS3 (variables, light/dark mode support, responsive grid, accessible contrasts), Vanilla JavaScript.
- **Visualizations:** Pure native SVG (world and India maps derived from public domain Natural Earth vectors), CSS meter charts.
- **Machine Learning Training Pipeline:** Python, `scikit-learn`, `numpy`, `pandas`.
- **Inference Engine:** Custom tree traversal compiler exported directly into client-side JS arrays (zero dependencies, no external APIs, fully functional offline).

---

## 🚀 Local Quickstart

No dependencies or build steps are required.

1. **Clone the repository:**
   ```bash
   git clone https://github.com/Yaswanth-codeai/bom-delay-radar.git
   cd bom-delay-radar
   ```

2. **Run locally:**
   - Simply double click `index.html` to open it in your browser, or:
   - Run a lightweight HTTP server:
     ```bash
     python -m http.server 8000
     ```
   - Open [http://localhost:8000](http://localhost:8000) in your browser.

---

## 📄 License

This project is open-source under the [MIT License](LICENSE).
