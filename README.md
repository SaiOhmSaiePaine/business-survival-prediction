# Business Survival Prediction (Singapore)

This project predicts whether a newly registered business in Singapore will survive or fail, using public registration data provided by the Accounting and Corporate Regulatory Authority (ACRA) via [data.gov.sg](https://data.gov.sg).

## 📊 Dataset

- **Source**: [ACRA Information on Corporate Entities – data.gov.sg](https://data.gov.sg)
- **Compiled by**: [Lin Thant Soe Wai](https://www.kaggle.com/datasets/linnthantsoewai/acra-information-on-corporate-entities-2019-2025)
- **Time Coverage**: January 2019 – April 2024
- **Scope**: Combined from 27 CSV files (A–Z), over 2 million registered business entities

> ✅ This dataset was compiled from Singapore’s official government registry and published on Kaggle. It provides reliable ground truth for early-stage business analysis in the local economic context.

## 🧠 Problem Statement

> Can we predict whether a business will remain active using only the information available at the time of registration?

The aim is to help:
- Government agencies support at-risk SMEs
- Financial institutions assess early credit risk
- Analysts explore structural survival patterns without relying on financials

---

## 🛠️ Project Highlights

- Cleaned, merged, and engineered features across 27 datasets
- Focused only on fields **available at registration time**:
  - `business_age` (calculated from registration date)
  - `no_of_officers` (team size)
  - `entity_type_description` (e.g., LLP, Pte Ltd)
  - `company_type_description`
  - `primary_ssic_code` (industry)
  - `postal_code` (location proxy)

> ⚠️ Financial data such as revenue, capital, or shareholder information was **not included** — as this project simulates an early-risk scoring tool that works purely on **public registration attributes**.

---

## ⚙️ Modeling Process

- Addressed extreme class imbalance using **SMOTE**
- Created a **balanced test set** (200 active, 200 inactive businesses) for fair recall evaluation
- Trained and compared:
  - Logistic Regression
  - Decision Tree (best performer)
  - Random Forest
  - XGBoost

---

## 📈 Model Results

| Model               | Accuracy | Recall (Failed) | F1-Score (Failed) |
|---------------------|----------|------------------|--------------------|
| Logistic Regression | 77%      | 0.61             | 0.72               |
| Decision Tree       | ✅ **85%**  | ✅ **0.69**         | ✅ **0.82**           |
| Random Forest       | 79%      | 0.58             | 0.73               |
| XGBoost             | 79%      | 0.57             | 0.73               |

---

## 🔍 Interpretation

Top predictive features:
- Fewer officers → higher failure risk
- Younger businesses are more volatile
- Industry classification (SSIC) affects closure likelihood

These findings align with common sense and make the model explainable to policy stakeholders.

---

## 💾 Model Export

The final model is saved using:

```python
import joblib
joblib.dump(tree_model, 'business_survival_model.pkl')
```

---
## 🧪 Setup & Environment

To run this notebook:

1. Clone the repo:
   ```bash
   git clone https://github.com/yourusername/business-survival-prediction](https://github.com/SaiOhmSaiePaine/business-survival-prediction.git
   cd business-survival-prediction
   ```

   ```
   pip install -r requirements.txt
   ```

   ```
   jupyter notebook
   ```
   

---

## Author
** Sai Ohm Saie Paine**  
Data Science | Analytics | Singapore  
📧 Email: saiohmsaiepaine@gmail.com  
🔗 LinkedIn: [linkedin.com/in/sai-ohm-saie-paine-43687b283](https://www.linkedin.com/in/sai-ohm-saie-paine-43687b283)

---
