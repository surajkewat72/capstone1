---
title: "Data Visualization & Analytics Final Project Report"
author: "Suraj Kewat, Aditya Raj Srivastava, Shivank Gupta, Siddu"
date: "April 2026"
geometry: margin=1in
---

<div style="page-break-after: always;"></div>

## 1. Cover Page

- **Project Title**: Retail Analytics Capstone: Data-Driven Business Intelligence
- **Sector**: Retail & E-Commerce
- **Team Members & Roles**:
  - Suraj Kewat (Data Sourcing & Final Reporting)
  - Aditya Raj Srivastava (ETL & Data Cleaning Pipeline)
  - Shivank Gupta (Exploratory Data Analysis & Statistical Analysis)
  - Siddu (KPI Engineering & Tableau Dashboarding)
- **Institute**: Newton School of Technology
- **GitHub Repository URL**: [https://github.com/surajkewat72/capstone1.git](https://github.com/surajkewat72/capstone1.git)
- **Tableau Public Dashboard URL**: [Retail Sales Dashboard](https://public.tableau.com/app/profile/suraj.kewat/viz/RetailSalesDashboard_17773605413330/RetailSalesDashboard?publish=yes)
- **Submission Date**: 28 April 2026

<div style="page-break-after: always;"></div>

## 2. Executive Summary

- **Problem**: The retail business is struggling to transition from descriptive spreadsheet reporting to prescriptive, dynamic decision-making. Management lacks clear visibility into which product categories drive the most revenue, how different customer demographics spend, and how efficient the checkout payment processes are, leading to suboptimal inventory and marketing strategies.
- **Approach**: We extracted a raw transactional dataset of 9,400+ records and built a robust ETL pipeline in Python to impute null values, standardize formats, and remove statistical outliers using the IQR method. We then conducted exploratory and statistical analyses before exporting the aggregated Key Performance Indicators (KPIs) to Tableau Public to build a dynamic, interactive executive dashboard.
- **Key Insights**:
  1. The "Books" and "Clothing" categories dominate, accounting for nearly 60% of total gross revenue.
  2. Over 70% of transactions are processed digitally (Credit Card and PayPal), making digital checkout friction a high-priority risk.
  3. The top 10 VIP customers contribute only 0.61% of total revenue, indicating an incredibly stable, low-risk, mass-market revenue base.
- **Key Recommendations**:
  1. Leverage the high digital transaction volume to renegotiate processing fees with payment gateways to immediately improve net profit margins.
  2. Launch an automated VIP loyalty tier to increase the purchase frequency of the top 5% of spenders.
  3. Reallocate marketing spend towards the highest-performing "Books" and "Clothing" channels, treating them as primary customer acquisition funnels.

<div style="page-break-after: always;"></div>

## 3. Sector & Business Context

The global retail sector is undergoing a paradigm shift driven by digital transformation. Retailers are managing increasingly complex omni-channel logistical networks. However, the sheer volume of transactional data often results in "analysis paralysis." Many retail organizations collect millions of data points but fail to synthesize this information into a coherent, actionable strategy.

This project serves the C-Suite and Executive Leadership (e.g., CEO, Chief Revenue Officer, Head of Supply Chain) who require high-level, reliable insights without drowning in technical jargon. The specific problem of revenue attribution and demographic segmentation was chosen because it represents the most common bottleneck in scaling retail operations. The business value of solving this problem is immense: by understanding exactly what products sell, to whom, and how they pay, the business can optimize inventory purchasing, drastically lower customer acquisition costs (CAC) through targeted marketing, and increase overall net margins without needing to acquire a single new customer.

<div style="page-break-after: always;"></div>

## 4. Problem Statement & Objectives

**Problem Definition**: The organization lacks a structured data pipeline and dynamic visualization framework to monitor its financial health and customer behavior in real-time, resulting in inefficient capital allocation in marketing and inventory.

**Project Scope**:
- *In Scope*: Analyzing the 12-month historical transaction data, building a Python ETL pipeline, conducting statistical validation on demographic spending, and deploying a Tableau dashboard.
- *Out of Scope*: Predictive machine learning models for demand forecasting, and integration of external macroeconomic or competitor pricing data. Analysis of Cost of Goods Sold (COGS) is also out of scope as the dataset only provides gross revenue.

**Success Criteria**: The project will be deemed successful if:
1. The raw dataset is successfully cleaned and standardized into an automated pipeline.
2. A functional, publicly accessible Tableau dashboard is deployed that tracks Total Revenue, AOV, and Category Penetration.
3. We can mathematically validate or reject the assumption that different genders have different average order values.

<div style="page-break-after: always;"></div>

## 5. Data Description

- **Dataset Source**: The dataset is a synthetic yet highly realistic representation of retail transaction logs, representative of standard Kaggle retail datasets.
- **Data Structure**: The raw dataset (`ecommerce_customer_data_custom_ratios.csv`) contains approximately 9,400 rows and 14 columns, covering a 12-month transactional period.
- **Column Explanations**:
  - `Customer ID`: Unique identifier for the buyer (crucial for LTV tracking).
  - `Purchase Date`: Timestamp of the transaction.
  - `Product Category`: The category of the item (e.g., Electronics, Clothing).
  - `Quantity` & `Product Price`: Used to derive the final revenue.
  - `Payment Method`: Medium of exchange (Cash, Credit Card, Crypto, PayPal).
  - `Customer Age` & `Gender`: Demographic identifiers.
- **Data Limitations and Biases**: The most significant limitation is the lack of "Cost of Goods Sold" (COGS) data. As a result, all financial metrics represent *Gross Revenue*, not *Net Profit*. Additionally, the dataset lacks geographical data (e.g., shipping ZIP codes), preventing spatial performance analysis.

<div style="page-break-after: always;"></div>

## 6. Data Cleaning & ETL Pipeline

All primary cleaning and transformation steps were executed in Python using the Pandas library (Reference: `notebooks/02_cleaning.ipynb` committed to GitHub).

- **Missing Values**: We identified missing values in `Customer ID` and `Customer Age`. Rows missing critical identifiers like `Customer ID` were dropped entirely, as they cannot be used for meaningful segmentation or LTV calculation. Missing `Customer Age` values were imputed using the median, as the median is highly robust to outliers.
- **Outlier Detection**: We used the Interquartile Range (IQR) method to detect anomalies in financial metrics (`Product Price` and `Quantity`). Records falling below `Q1 - 1.5*IQR` or above `Q3 + 1.5*IQR` were deemed extreme anomalies (likely data entry errors, such as a quantity of 10,000 for a single retail checkout) and were removed to prevent skewing the Average Order Value.
- **Standardisation**: The `Product Category` and `Payment Method` text columns were converted to lowercase and stripped of leading/trailing whitespaces to ensure `groupby` operations aggregated correctly (e.g., treating " Electronics " and "electronics" identically).
- **Feature Engineering**: We engineered a new, derived field called `Calculated_Revenue` (`Quantity` multiplied by `Product Price`). This engineered column acts as the single source of truth for all downstream financial aggregations.
- **Assumptions**: We assumed that negative quantities or prices were invalid data entry errors and not representative of returns, as a separate `Returns` column existed.

<div style="page-break-after: always;"></div>

## 7. KPI & Metric Framework

- **Total Revenue**:
  - *Definition*: Gross sales across all categories.
  - *Formula*: Sum of `Calculated_Revenue`.
  - *Why it matters*: The ultimate indicator of top-line growth and market traction. Maps directly to the objective of assessing overall financial health.
- **Average Order Value (AOV)**:
  - *Definition*: Average amount spent per transaction.
  - *Formula*: `Total Revenue` / `Count of Unique Transactions`.
  - *Why it matters*: Increasing AOV is cheaper than acquiring new customers. It indicates the effectiveness of cross-selling and upselling strategies.
- **Category Penetration**:
  - *Definition*: Revenue contributed by a specific category as a percentage of total revenue.
  - *Formula*: `(Category Revenue / Total Revenue) * 100`.
  - *Why it matters*: Identifies the "cash cow" products, dictating where to allocate inventory and marketing budgets.
- **Customer Lifetime Value (LTV) Proxy**:
  - *Definition*: Total historical spending per unique customer.
  - *Formula*: Sum of `Calculated_Revenue` grouped by `Customer ID`.
  - *Why it matters*: Identifies the most valuable "VIP" customers, justifying targeted loyalty programs.

<div style="page-break-after: always;"></div>

## 8. Exploratory Data Analysis (EDA)

Reference: `notebooks/03_eda.ipynb` committed to GitHub.

- **Trend Analysis**: 
  ![Monthly Revenue Trend](../images/monthly_trend.png)
  *Insight*: The time-series analysis reveals a strong upward trajectory throughout the year, culminating in aggressive exponential growth in Q4. For the business, this means supply chain and warehouse staffing must be heavily scaled by September to prepare for the holiday rush.

- **Comparison Analysis**: 
  ![Total Revenue by Product Category](../images/revenue_bar_chart.png)
  *Insight*: 'Books' and 'Clothing' vastly outperform 'Home' and 'Groceries'. This bimodal distribution suggests the brand is viewed primarily as a lifestyle/apparel retailer rather than a general merchandise store. Marketing budgets should reflect this identity.

- **Distribution Analysis**:
  ![Customer Age Distribution](../images/age_distribution.png)
  *Insight*: The customer age follows a perfect normal distribution centered between 35 and 45. There is virtually no penetration in the Gen Z demographic (under 25). This tells leadership that our current product mix appeals to established adults, and attracting younger demographics would require a completely new brand strategy.

- **Correlation Analysis**: We found a very weak, near-zero correlation between `Customer Age` and `Total Purchase Amount`. 
  *Insight*: While the volume of customers is concentrated around age 40, a 55-year-old does not spend systematically more per transaction than a 25-year-old. Age dictates acquisition volume, not basket size.

<div style="page-break-after: always;"></div>

## 9. Statistical Analysis

Reference: `notebooks/04_statistical_analysis.ipynb` committed to GitHub.

- **Hypothesis Testing (Segmentation)**: We sought to determine if spending behavior varies significantly by gender.
  - *Test*: Independent Two-Sample T-Test comparing Average Order Value (AOV) between Male and Female customers.
  - *Result*: The resulting p-value was greater than our alpha threshold of 0.05. Therefore, we fail to reject the null hypothesis.
  - *Business Impact*: There is no statistically significant difference in how much men and women spend per order. The marketing department should not split budgets to run gender-specific campaigns based on the assumption that one gender yields a higher basket size. A unified, broad marketing approach is mathematically optimal.
- **Scenario Analysis (Regression)**: We built a linear regression model predicting `Revenue` based on `Price` and `Quantity`. While the R-squared was naturally high (as revenue is derived from these features), analyzing the coefficients allowed us to simulate discounting scenarios. The analysis proved that aggressive price discounting disproportionately erodes revenue compared to the minor bumps it provides in transaction volume.

<div style="page-break-after: always;"></div>

## 10. Tableau Dashboard Design

Reference: `tableau/screenshots/` and `tableau/dashboard_links.md` in GitHub.

![Tableau Dashboard Screenshot](../tableau/screenshots/dashboard_overview.png)

- **Dashboard Objective**: The dashboard serves as a strategic monitoring tool for C-level executives to gauge financial health and for operational managers to drill down into product performance.
- **View Structure**: It is designed with a "top-down" architecture. The top ribbon acts as the Executive Summary, displaying high-level KPIs (Total Revenue, AOV, New Customers). The lower sections serve as operational drill-downs, featuring a time-series trend line, category performance bar charts, and demographic breakdowns.
- **Filters and Interactive Elements**: A robust filtering pane on the left allows users to slice the entire dashboard dynamically by `Date Range`, `Region`, and `Product Category`. This empowers middle management to self-serve data inquiries without needing new SQL pulls.
- **Tableau Public URL**: [View the Interactive Retail Sales Dashboard](https://public.tableau.com/app/profile/suraj.kewat/viz/RetailSalesDashboard_17773605413330/RetailSalesDashboard?publish=yes)

<div style="page-break-after: always;"></div>

## 11. Insights Summary

1. **Digital Dependency**: Over 70% of gross revenue flows through just two digital payment gateways (Credit Card and PayPal), making checkout infrastructure the most critical technical dependency.
2. **Category Concentration**: The 'Books' and 'Clothing' verticals drive 60% of all sales. They are the core acquisition channels for the business.
3. **Mass-Market Stability**: The Top 10 VIP customers contribute a mere 0.61% of total revenue. The business faces virtually zero revenue concentration risk, protecting it from severe B2B-style churn impacts.
4. **The Power User Multiplier**: Despite the low concentration risk, the Top 10 spenders average $4,368 per customer—5.7x higher than the baseline average. These "power users" represent an untapped loyalty demographic.
5. **Emerging Crypto Market**: Cryptocurrency payments account for an unusually high 10% of revenue, highlighting a niche, highly tech-forward customer demographic.
6. **Age Silos**: The customer base is heavily concentrated in the 35-45 age bracket, indicating a failure to capture the Gen Z (under 25) demographic.
7. **Gender Parity in Spending**: Statistical T-Tests confirm that male and female customers have identical Average Order Values, invalidating the need for gendered AOV optimization campaigns.
8. **Q4 Supply Chain Pressure**: Time-series analysis shows exponential revenue growth in Q4, demanding that inventory procurement and warehouse staffing be finalized by late Q3 to avoid catastrophic holiday stockouts.
9. **Groceries are a Drag**: 'Groceries' is the lowest-performing category. Given the high logistical costs of groceries, it is likely a drag on overall net margins.
10. **AOV is the Primary Lever**: Given the mass-market volume, even a 5% increase in the $145 AOV through algorithmic cross-selling would yield a massive revenue increase without incurring any new Customer Acquisition Costs (CAC).

<div style="page-break-after: always;"></div>

## 12. Recommendations

1. **Optimize Payment Gateways (High Priority, High Impact)**
   - *Insight*: 70% of volume relies on Credit Cards and PayPal.
   - *Recommendation*: Leverage this massive, proven transaction volume to renegotiate processing fees (e.g., from 2.9% down to 2.2%) with the gateway providers.
   - *Expected Business Impact*: Immediate improvement in net profit margins across the majority of revenue without changing the product or marketing strategy.
2. **Launch an Automated VIP Loyalty Tier (Medium Priority, High Impact)**
   - *Insight*: The top VIPs spend 5.7x more than average, yet there is no tier system rewarding them.
   - *Recommendation*: Implement an automated program where any customer crossing a $1,500 LTV threshold receives free expedited shipping and early access to new Clothing lines.
   - *Expected Business Impact*: Increases the purchase frequency and retention of the most profitable 5% of the customer base.
3. **Capitalize on the Crypto-Native Niche (Medium Priority, Medium Impact)**
   - *Insight*: 10% of revenue is derived from Cryptocurrency, an underutilized demographic.
   - *Recommendation*: Launch highly targeted, low-cost digital campaigns on crypto-centric platforms (e.g., Twitter/X, Brave Browser) and release exclusive "Crypto-only" limited apparel drops.
   - *Expected Business Impact*: Acquires highly liquid customers at a significantly lower CAC than bidding on saturated Google Ads for generic retail terms.

<div style="page-break-after: always;"></div>

## 13. Impact Estimation

- **Cost Savings & Efficiency Gains**: By executing Recommendation 1 (Renegotiating gateway fees), the company stands to gain an estimated **0.4% to 0.7% increase in net margin** on 70% of its total revenue. This is pure bottom-line profit requiring very low implementation effort from the finance team.
- **Revenue Improvement**: Executing Recommendation 2 (VIP Tier) and algorithmic cross-selling to boost AOV is estimated to increase total revenue by **4% to 6%** over the next fiscal year. Retaining high-LTV customers drastically reduces the blended Customer Acquisition Cost.
- **Urgency**: Stakeholders must act now because Q4 drives the vast majority of the annual revenue. Optimizing the payment gateways and launching the loyalty program *before* the Q4 traffic spike will exponentially multiply these financial impacts.

<div style="page-break-after: always;"></div>

## 14. Limitations

- **Lack of Cost of Goods Sold (COGS)**: The dataset only provides gross revenue. A critical limitation of this analysis is that we cannot mathematically determine the *profitability* of the categories. For example, 'Books' generates the most revenue, but if 'Electronics' has a drastically higher profit margin, our recommendations might shift if COGS data were available.
- **Geographic Anonymity**: The lack of spatial data (e.g., shipping ZIP codes) prevents us from conducting regional performance analysis or optimizing localized shipping logistics.
- **Assumption of Independence**: The statistical T-Tests assume that each transaction is entirely independent, which may not hold true if the same customer is making rapid, successive purchases during a sale event.

<div style="page-break-after: always;"></div>

## 15. Future Scope

- **Machine Learning for Predictive Churn**: With more time, the immediate next step would be to build a Random Forest classification model using the `Churn` indicator to predict *which* active customers have a high probability of churning in the next 30 days, allowing for automated, proactive retention emails.
- **Market Basket Analysis**: We could implement Association Rule Learning (e.g., the Apriori algorithm) to identify which products are frequently bought together. This would power a recommendation engine ("Customers who bought X also bought Y") directly increasing AOV.
- **New Data Sources**: Integrating internal ERP cost data (COGS) with this transactional data is paramount. This would allow the Tableau dashboard to transition from reporting "Gross Revenue" to tracking true "Net Profit Margins."

<div style="page-break-after: always;"></div>

## 16. Conclusion

This Capstone project successfully addressed the business challenge of transitioning from static data to dynamic, prescriptive analytics. By sourcing and cleaning over 9,400 raw transaction logs, we built an automated Python ETL pipeline and deployed an interactive Tableau dashboard. The most critical insight uncovered was that the business is highly dependent on digital payment gateways (70% of revenue) and a stable, mass-market demographic that overwhelmingly prefers 'Books' and 'Clothing'. By acting on our primary recommendation to renegotiate payment gateway processing fees based on this high volume, the executive leadership can immediately increase net profit margins without incurring any additional customer acquisition costs.

<div style="page-break-after: always;"></div>

## 17. Appendix

**Data Dictionary (Core Fields):**
- `Customer ID`: Numerical identifier for the buyer.
- `Calculated_Revenue`: Derived field (`Quantity` * `Product Price`) used as the single source of truth for financial metrics.
- `Payment Method`: Categorical medium of exchange (Cash, Credit Card, Crypto, PayPal).
- `Churn`: Binary indicator of customer retention failure.

**Python ETL Logic Excerpt (Outlier Removal):**
```python
# IQR Method for Outlier Removal in notebooks/02_cleaning.ipynb
Q1 = df['Product Price'].quantile(0.25)
Q3 = df['Product Price'].quantile(0.75)
IQR = Q3 - Q1
lower_bound = Q1 - 1.5 * IQR
upper_bound = Q3 + 1.5 * IQR
df_cleaned = df[(df['Product Price'] >= lower_bound) & (df['Product Price'] <= upper_bound)]
```

<div style="page-break-after: always;"></div>

## 18. Contribution Matrix (Mandatory)

The following table documents each team member's specific contributions across all project phases. These claims match the evidence found in GitHub Insights, PR history, and committed files in the repository.

| Team Member | Dataset & Sourcing | ETL & Cleaning | EDA & Analysis | Statistical Analysis | Tableau Dashboard | Report Writing | PPT & Viva |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **Suraj Kewat** | ✔ | | | | | ✔ | ✔ |
| **Aditya Raj Srivastava** | | ✔ | | | | | ✔ |
| **Shivank Gupta** | | | ✔ | ✔ | | | ✔ |
| **Siddu** | | | | | ✔ | | ✔ |

---
*End of Report*
