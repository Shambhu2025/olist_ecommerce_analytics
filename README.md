# E-Commerce Customer Intelligence & Logistics Prediction

## Overview
An end-to-end data analytics and machine learning pipeline built on the Olist Brazilian E-Commerce dataset (100,000+ relational transactions). This project utilizes an in-memory SQL engine (DuckDB) and Python to execute complex data wrangling, customer segmentation, and predictive logistics modeling.

## 🛠️ Tech Stack & Techniques
* **Data Engineering & Analysis:** SQL (DuckDB), Python (Pandas)
* **Machine Learning:** Scikit-Learn (K-Means Clustering, Random Forest Classifier)
* **Advanced SQL Used:** Multi-table `INNER JOIN`s, Common Table Expressions (CTEs), Window Functions (`NTILE`), Aggregations.

## 📊 Key Project Phases

### 1. Relational Data Wrangling (SQL)
* Designed a "Master View" architecture by joining 8 distinct relational tables (Orders, Customers, Products, Payments, Reviews, etc.).
* Mitigated Cartesian explosion (fan-out) traps during 1-to-Many joins using localized CTEs and `COUNT(DISTINCT)` aggregations.

### 2. Customer Segmentation via RFM (SQL + K-Means)
* Engineered Recency, Frequency, and Monetary (RFM) features directly in SQL using Window Functions to rank 96,000+ customers.
* Passed extracted SQL features into a Python `StandardScaler` and applied **K-Means Clustering** to discover 4 distinct buyer personas (e.g., High-Value "Whales" vs. Churned Customers).

### 3. Predictive Logistics Modeling (Random Forest)
* Built a binary classification model to predict late package deliveries.
* Handled a severe class imbalance (93% on-time, 7% late) using targeted class weights, achieving a **69% recall rate** for delayed shipments.
* Extracted **Feature Importances** to prove that package weight and freight distance were the primary drivers of supply chain failures.

## 💡 Business Recommendations
Based on the modeling outputs, I recommend the following operational changes:
1. **Dynamic Shipping Buffers:** Dynamically add 2-3 days to estimated delivery dates at checkout for items with high package weights to manage customer expectations.
2. **VIP Retention:** Transition the K-Means "Whale" segment away from generic discount codes and into a VIP loyalty tier with guaranteed expedited shipping to protect high-margin revenue.
3. **Targeted Win-Backs:** Automate highly personalized discount campaigns for the "At-Risk" cluster before they permanently churn.

## 🚀 How to Run the Project
1. The full analysis is available in the Jupyter Notebook located in the `notebooks/` directory.
2. Datasets are sourced from the [Olist Kaggle Repository](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce).
3. The notebook utilizes `duckdb` to run SQL natively in memory, requiring no local PostgreSQL server setup.

## 📈 Visualizations
images/rfm_cluster.png
images/feature_importance.png
