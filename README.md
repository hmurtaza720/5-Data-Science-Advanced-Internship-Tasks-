# 🧠 Advanced Data Science Projects

![Python](https://img.shields.io/badge/Python-3.10-blue?style=flat&logo=python)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?style=flat&logo=jupyter)
![XGBoost](https://img.shields.io/badge/XGBoost-Forecasting-red?style=flat)
![Streamlit](https://img.shields.io/badge/Streamlit-Dashboard-red?style=flat&logo=streamlit)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=flat)

---

## 📌 About

A collection of **5 advanced end-to-end Data Science projects** covering real-world problem domains including banking, retail, energy, and business intelligence. Each project goes beyond basic modeling — incorporating **Explainable AI (SHAP)**, **unsupervised clustering**, **multi-model time series forecasting**, **business cost optimization**, and an **interactive Streamlit dashboard**.

---

## 📂 Repository Structure

```
📦 Advanced-Data-Science-Projects
 ┣ 📓 Task1_Term_Deposit_Prediction.ipynb
 ┣ 📓 Task2_Customer_Segmentation.ipynb
 ┣ 📓 Task3_Energy_Forecasting.ipynb
 ┣ 📓 Task4_Loan_Default_Risk.ipynb
 ┣ 📓 Task5_Streamlit_Dashboard.ipynb
 ┗ 📄 README.md
```

---

## 🗂️ Projects Overview

| # | Project | Type | Key Techniques | Dataset |
|---|---------|------|---------------|---------|
| 1 | Term Deposit Subscription Prediction | Classification + XAI | Logistic Regression, Random Forest, SHAP | Bank Marketing (UCI) |
| 2 | Customer Segmentation | Unsupervised Learning | K-Means, PCA, t-SNE | Mall Customers (Kaggle) |
| 3 | Energy Consumption Forecasting | Time Series | ARIMA, Prophet, XGBoost | Household Power (UCI) |
| 4 | Loan Default Risk Optimization | Classification + Cost Analysis | Logistic Regression, CatBoost, Threshold Tuning | Home Credit (Kaggle) |
| 5 | Interactive Business Dashboard | BI Dashboard | Streamlit, Plotly, KPI Analysis | Global Superstore (Kaggle) |

---

## 📓 Project Details

---

### 🏦 Project 1 — Term Deposit Subscription Prediction

**Objective:** Predict whether a bank customer will subscribe to a term deposit after a marketing campaign call.

**Approach:**
- Replaced `unknown` values and applied One-Hot Encoding to all categorical features
- Trained Logistic Regression and Random Forest classifiers with `class_weight='balanced'`
- Evaluated using Confusion Matrix, F1-Score, and ROC-AUC Curve
- Applied **SHAP TreeExplainer** to explain 5 individual predictions — showing which features pushed each prediction toward or against subscription

**Key Insights:**
- Call duration is the #1 predictor — longer calls (5+ min) strongly signal subscription intent
- Customers with a previous successful campaign outcome convert at the highest rate
- SHAP global summary reveals `nr.employed` and `euribor3m` as macro-level drivers

**Results:** Random Forest AUC ~0.94 | F1-Score ~0.60

---

### 🛍️ Project 2 — Customer Segmentation Using Unsupervised Learning

**Objective:** Cluster mall customers based on income and spending behavior, then propose marketing strategies per segment.

**Approach:**
- Used the Elbow Method and Silhouette Score to identify the optimal K=5 clusters
- Applied K-Means and visualized clusters in 2D using both PCA and t-SNE
- Profiled each cluster by income, spending score, and age

**Key Insights:**

| Cluster | Profile | Recommended Strategy |
|---------|---------|---------------------|
| 0 | Low Income, Low Spend | Budget deals, coupons |
| 1 | High Income, Low Spend | Premium exclusives, VIP |
| 2 | Mid Income, Mid Spend | Cross-sell, loyalty points |
| 3 | Low Income, High Spend | Flash sales, BNPL options |
| 4 | High Income, High Spend ⭐ | Max investment — VIP concierge |

**Results:** Silhouette Score confirms well-separated clusters across all 5 groups

---

### ⚡ Project 3 — Energy Consumption Time Series Forecasting

**Objective:** Forecast hourly household power consumption 7 days ahead using three different modeling approaches.

**Approach:**
- Resampled raw minute-level data to hourly averages
- Engineered time features: hour, day of week, month, weekend flag, lag features (1h, 24h, 168h), rolling averages
- Trained and compared ARIMA (2,0,2), Facebook Prophet, and XGBoost Regressor
- Plotted Actual vs Forecasted values for all three models side by side

**Key Insights:**
- XGBoost achieves the lowest MAE and RMSE by leveraging lag and rolling features
- Prophet decomposition confirms strong daily and weekly seasonality
- Energy peaks at 7–9 AM and 6–10 PM daily; weekends show slightly higher usage

**Results:**

| Model | Relative Performance |
|-------|---------------------|
| ARIMA | Baseline — good for stationary short-horizon series |
| Prophet | Medium — best for interpretable seasonal decomposition |
| XGBoost | **Best** — lowest error with engineered time features |

---

### 💳 Project 4 — Loan Default Risk with Business Cost Optimization

**Objective:** Predict loan default probability and optimize the decision threshold to minimize total business cost.

**Approach:**
- Engineered features: Age in years, Employment years, Credit-to-Income ratio, Annuity-to-Income ratio
- Trained Logistic Regression and CatBoost with class imbalance handling
- Defined business cost matrix: FN costs $10,000 (loan loss), FP costs $1,000 (lost revenue)
- Swept thresholds 0.05–0.95 to find the optimal decision point maximizing net financial benefit

**Key Insights:**
- EXT_SOURCE risk scores dominate feature importance — more predictive than all demographics combined
- Default threshold (0.50) is not optimal — the cost-optimized threshold significantly improves net benefit
- Credit-to-income ratio > 5× is a strong default signal

**Results:** CatBoost AUC ~0.78 | Threshold optimization delivers measurable reduction in loan losses vs default 0.50 cutoff

---

### 📊 Project 5 — Interactive Business Dashboard (Streamlit)

**Objective:** Build a fully interactive BI dashboard for analyzing Global Superstore sales, profit, and customer performance.

**Approach:**
- Full EDA with Matplotlib and Seaborn in the notebook
- Generated a complete `app.py` Streamlit dashboard with Plotly interactive charts
- Sidebar filters: Region, Category, Sub-Category, Year, Segment
- KPI cards: Total Sales, Total Profit, Orders, Profit Margin %, Average Order Value
- Charts: Monthly trend, category breakdown, region comparison, profit by sub-category, top 5 customers, discount vs profit scatter

**Key Insights:**
- Discounts above 20% consistently produce losses, especially in Furniture
- Technology leads in revenue; some Sub-Categories (Tables, Bookcases) are loss-making
- Top 5 customers represent a disproportionately high share of total revenue

**How to run:**
```bash
pip install streamlit plotly pandas
streamlit run app.py
```

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| **Python 3.10** | Core language |
| **Pandas & NumPy** | Data manipulation |
| **Matplotlib & Seaborn** | Static visualizations |
| **Scikit-learn** | ML models, clustering, PCA |
| **SHAP** | Explainable AI — individual prediction explanations |
| **Statsmodels** | ARIMA time series modeling |
| **Prophet** | Seasonal time series forecasting |
| **XGBoost** | Gradient boosted ML forecasting |
| **CatBoost** | Gradient boosted classification |
| **Streamlit** | Interactive BI dashboard |
| **Plotly** | Interactive charts in dashboard |
| **Google Colab** | Cloud notebook environment |

---

## 🚀 How to Run Any Notebook

### Google Colab (Recommended)
1. Go to [colab.research.google.com](https://colab.research.google.com)
2. Click **File → Open Notebook → GitHub**
3. Paste this repository URL and select any notebook
4. Click **Runtime → Run All**

### Local Setup
```bash
git clone https://github.com/YOUR_USERNAME/Advanced-Data-Science-Projects.git
cd Advanced-Data-Science-Projects
pip install pandas numpy matplotlib seaborn scikit-learn shap prophet xgboost catboost streamlit plotly statsmodels
jupyter notebook
```

---

## 📥 Dataset Sources

| Project | Dataset | How to Get |
|---------|---------|-----------|
| Project 1 | Bank Marketing (UCI) | Auto-downloads in notebook |
| Project 2 | Mall Customers | Auto-downloads / synthetic fallback |
| Project 3 | Household Power Consumption (UCI) | Auto-downloads / synthetic fallback |
| Project 4 | Home Credit Default Risk | [Kaggle](https://www.kaggle.com/c/home-credit-default-risk) — upload `application_train.csv` or use synthetic fallback |
| Project 5 | Global Superstore | Auto-downloads / synthetic fallback |

> All notebooks include a **synthetic fallback dataset** that auto-generates if the download fails — so every notebook runs without any manual setup.

---

## 📊 Results Summary

| Project | Best Model | Best Metric |
|---------|-----------|-------------|
| Project 1 | Random Forest | AUC ~0.94, F1 ~0.60 |
| Project 2 | K-Means (K=5) | Strong silhouette separation |
| Project 3 | XGBoost | Lowest MAE & RMSE |
| Project 4 | CatBoost | AUC ~0.78 + cost-optimized threshold |
| Project 5 | Streamlit Dashboard | 9 interactive charts + 5 KPI cards |
