# # SaaS Pulse: AI-Powered Product Analytics Suite 🚀

![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)
![Streamlit](https://img.shields.io/badge/Streamlit-App-FF4B4B.svg)
![Polars](https://img.shields.io/badge/Polars-Fast_Data-orange.svg)
![Machine Learning](https://img.shields.io/badge/Scikit--Learn-Random_Forest-yellow.svg)

## 📌 Overview
**SaaS Pulse** is an end-to-end interactive web application designed for Product Managers and Executives. It transforms raw subscription transaction data into actionable business intelligence. 

Instead of relying on basic vanity metrics, this tool calculates high-level financial health indicators—like **Net Revenue Retention (NRR)** and **Margin-Adjusted Payback Periods**—and uses Machine Learning to proactively identify cohorts at risk of churn.

## ✨ Key Features
* **⚡ High-Performance Data Engine:** Replaced Pandas with **Polars** for lightning-fast, multi-threaded cohort aggregations.
* **📈 Net Revenue Retention (NRR) Matrix:** Visualizes expansion revenue vs. churn over the customer lifecycle using a perceptually uniform (Viridis) heatmap.
* **💰 Unit Economics Engine:** Calculates the true break-even point by comparing Customer Acquisition Cost (CAC) against Margin-Adjusted Cumulative Lifetime Value (CLV).
* **🤖 Predictive Churn Radar:** Integrates a Scikit-Learn `RandomForestClassifier` to assign a real-time churn probability score to every user based on their engagement and spending history.
* **🎯 Actionable UI:** Includes dynamic risk-threshold sliders and a one-click CSV export for seamless handoffs to Customer Success teams.

## 🛠️ Tech Stack
* **Frontend/UI:** Streamlit
* **Data Processing:** Polars, Numpy
* **Visualizations:** Plotly Express
* **Machine Learning:** Scikit-Learn

## 📊 Dashboard Navigation - [SaaS Pulse](https://www.loom.com/share/ce34e4464e16452a8d2ad1362d0787e5?t=1)
- **NRR Heatmap:** Tracks how cohorts expand or contract over time. Values > 100% indicate successful upsells/upgrades outpacing churn.
- **Margin Adjusted Payback:** A dual-line chart plotting raw CLV and Margin-Adjusted CLV against a static Average CAC line to find the exact payback month.
- **Churn Risk Radar:** Adjust the ML sensitivity slider (e.g., 75% risk) to instantly filter and export a list of users highly likely to cancel their subscriptions.

## 📂 Project Structure
```text
├── app.py                  # Main Streamlit application and UI logic
├── data_generator.py       # Script to generate synthetic B2B SaaS data (Expansion, CAC, COGS)
├── customers.csv           # Generated metadata (Segments, CAC, COGS)
├── subscriptions.csv       # Generated transaction ledger
├── churn_data.csv          # Generated historical churn labels for ML training
└── README.md               # Project documentation
```



## Running in Google Colab (or Juptyer Notebooks)
If you are developing or running this project within a **Google Colab environment**, use pyngrok to expose the Streamlit port:
```text
import os
from pyngrok import ngrok

# Authenticate and open tunnel
!ngrok config add-authtoken YOUR_NGROK_TOKEN

os.system("streamlit run app.py --server.port 8501 &"

public_url = ngrok.connect(8501)
print(f"App Live At: {public_url.public_url}")

