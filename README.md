# 🛒 Retail Analytics Capstone: Data-Driven Business Intelligence

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python&logoColor=white)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Library-Pandas-150458?logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![Tableau](https://img.shields.io/badge/Dashboard-Tableau-E97627?logo=tableau&logoColor=white)](https://public.tableau.com/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)

## 📋 Project Overview
This capstone project provides a comprehensive end-to-end data analytics solution for a retail business. By transforming over **9,400 raw transaction records** into actionable intelligence, the project identifies key revenue drivers, customer behavior patterns, and operational efficiencies. The final output includes a robust Python-based analytical pipeline and an interactive **Tableau Dashboard** for executive decision-making.

---

## 📊 Dataset Description
The analysis utilizes a retail transaction dataset containing details on customer demographics, product categories, and financial metrics.
- **Volume:** 9,400 cleaned records (from a dirty raw source).
- **Core Fields:** `Customer ID`, `Product Category`, `Quantity`, `Price`, `Transaction Date`, `Payment Method`.
- **Data Challenges Addressed:** 
    - Handled missing values (Imputation & Removal).
    - Resolved duplicate entries inflating revenue.
    - Standardized inconsistent categorical naming.
    - Removed statistical outliers using the **Interquartile Range (IQR)** method.

---

## ⚙️ Methodology
The project follows a structured 5-phase analytical framework:

1.  **Phase 1: Extraction & Inspection:** Ingesting raw CSV data and performing initial health checks.
2.  **Phase 2: ETL & Cleaning:** Standardizing data types, handling nulls, and engineering the `Revenue` KPI.
3.  **Phase 3: Exploratory Data Analysis (EDA):** Visualizing trends, regional performance, and product distributions using Seaborn/Matplotlib.
4.  **Phase 4: Statistical Validation:** Performing Independent T-Tests (Hypothesis Testing) and Linear Regression to validate business assumptions.
5.  **Phase 5: Interactive Visualization:** Building a multi-layer Tableau dashboard to track real-time KPIs like AOV and Revenue Growth.

---

## 💡 Key Business Insights
- **Revenue Leadership:** The **Books** and **Clothing** categories dominate the portfolio, contributing to nearly **60% of total revenue**.
- **Digital Payment Dominance:** Over **70% of transactions** are processed via Credit Card or PayPal, indicating a strong preference for digital checkout experiences.
- **Stable Customer Base:** The top 10 customers contribute only **0.61% of revenue**, revealing a highly stable, fragmented model that is not reliant on a few "whales."
- **Statistical Significance:** T-tests confirmed that spending behavior is consistent across demographics (p > 0.05), suggesting that broad, gender-neutral marketing is currently the most cost-effective strategy.

---

## 🚀 Conclusion
This project demonstrates the power of data-driven strategy in retail. By automating the cleaning process and applying rigorous statistical testing, the business can now:
1.  **Optimize Marketing Spend:** Focus on the "Books" and "Clothing" categories.
2.  **Improve Margins:** Renegotiate digital payment gateway fees based on the 70% volume.
3.  **Predict Revenue:** Use the established regression models to forecast future sales based on inventory quantity.

---

## 📂 Project Structure
```text
capstone2/
├── data/
│   ├── raw/                # Original dirty dataset
│   ├── processed/          # Cleaned, ready-to-analyze data
├── notebooks/              # Python analytical pipeline (01-05)
├── tableau/                # Dashboard screenshots and links
├── reports/                # Final comprehensive project report
├── docs/                   # Data dictionary and metadata
└── README.md               # Project overview (this file)
```

---
**Developed by:** [Your Name]  
**Tools:** Python (Pandas, SciPy, Seaborn), Tableau Public, Jupyter Notebook.
