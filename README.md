# 📡 Telco Customer Churn — Business Intelligence Dashboard

A fully self-contained Python business intelligence project that combines **data cleaning**, **machine learning-based churn prediction**, and an **interactive Dash dashboard** — all in a single file (`app.py`).

---

## 📌 Project Overview

Customer churn is one of the most costly problems in the telecommunications industry. Acquiring a new customer costs 5–25× more than retaining an existing one. This project uses the publicly available **Telco Customer Churn dataset** to:

- **Analyse** churn patterns across contract types, payment methods, and tenure groups.
- **Predict** which customers are at risk of churning using a **Random Forest classifier**.
- **Visualise** key business metrics through an interactive, three-section dashboard.

The dashboard is structured into three actionable sections:
| Section | Purpose |
|---------|---------|
| (A) Executive Overview | Top KPIs and high-level churn landscape |
| (B) Customer & Segment Analysis | Churn drivers by contract type, tenure, payment method |
| (C) Risk, Opportunity & Action | Highest-risk segment, growth opportunity, retention recommendations |

---

## 🚀 How to Run

### Prerequisites
- Python 3.9 or later
- The dataset CSV file (see [Dataset](#-dataset) section below)

### Steps

1. **Clone / download** this repository into a local folder.

2. **Place the dataset** — download `WA_Fn-UseC_-Telco-Customer-Churn.csv` from Kaggle (link below) and rename it to:
   ```
   telco_customer_churn.csv
   ```
   Place it in the **same directory** as `app.py`.

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Run the application:**
   ```bash
   python app.py
   ```

5. **Open your browser** at:
   ```
   http://127.0.0.1:8050
   ```

> The terminal will print model performance metrics (accuracy, AUC) and the top 10 feature importances before the dashboard launches.

---

## 🤖 Model Used

### Random Forest Classifier (Primary)
- **Library:** `scikit-learn`
- **Estimators:** 200 trees, max depth 10
- **Training split:** 80% train / 20% test, stratified by churn label
- **Evaluation metrics:** Accuracy, AUC-ROC

### Logistic Regression (Benchmark)
- Used as a baseline model for comparison; results shown in the Executive Overview table.

### Feature Engineering
- All categorical variables are label-encoded prior to model training.
- Features are standardised with `StandardScaler` for Logistic Regression.
- `TotalCharges` blanks (for new customers) are imputed with `0`.
- `customerID` is dropped as it carries no predictive signal.

---

## 📊 Key KPIs Tracked

| KPI | Description |
|-----|-------------|
| Overall Churn Rate | % of customers who left |
| MRR at Risk | Sum of monthly charges from churned customers |
| Average Customer Tenure | Mean tenure in months across all customers |
| Churn Rate by Contract Type | Month-to-month vs One Year vs Two Year |
| Churn Rate by Payment Method | Electronic check, mailed check, bank transfer, credit card |
| Churn Rate by Tenure Bucket | 0–12 mo, 13–24 mo, …, 61–72 mo |

---

## 📁 Project Structure

```
.
├── app.py                        # Main application (all-in-one)
├── requirements.txt              # Python dependencies
├── README.md                     # This file
├── Telco_Churn_Report.docx       # Project report (Word document)
└── telco_customer_churn.csv      # Dataset (download separately — see below)
```

---

## 📂 Dataset

**Source:** Kaggle — IBM Sample Dataset  
**URL:** [https://www.kaggle.com/datasets/blastchar/telco-customer-churn](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)  
**File name (original):** `WA_Fn-UseC_-Telco-Customer-Churn.csv`  
**Rename to:** `telco_customer_churn.csv`

The dataset contains 7,043 telecom customers with 21 features including demographics, account information, subscribed services, and whether the customer churned.

---

## 📄 License

This project is for educational and analytical purposes. The dataset is subject to [Kaggle's terms of use](https://www.kaggle.com/terms).
