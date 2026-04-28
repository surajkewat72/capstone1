# Portfolio Case Study: Retail Analytics & Business Intelligence

*This document serves as a portfolio-ready case study summarizing the NST DVA Capstone 2 project.*

## 1. Problem Statement and Stakeholder Context

**Context:** The global retail sector is shifting heavily towards digital, omni-channel experiences. Despite having access to millions of data points, this specific retail organization was struggling to transition from descriptive spreadsheet reporting to dynamic, prescriptive decision-making. 

**Stakeholders:** This project serves C-Suite and Executive Leadership (e.g., CEO, Chief Revenue Officer, Head of Supply Chain) who require high-level, reliable insights without drowning in technical jargon.

**The Challenge:** Management lacked clear visibility into which product categories drove the most revenue, how different customer demographics spent, and the efficiency of their checkout processes. This "analysis paralysis" led to suboptimal inventory purchasing and inefficient capital allocation in marketing. 

**The Goal:** Optimize inventory purchasing and targeted marketing by understanding what products sell, to whom, and how they pay, in order to increase overall net margins without acquiring new customers.

## 2. Dataset Source and Scope

- **Source:** The analysis is based on a synthetic, highly realistic retail transaction dataset representative of standard Kaggle retail data (`ecommerce_customer_data_custom_ratios.csv`).
- **Scope:** 
  - **Volume:** ~9,400 transaction records across 14 columns.
  - **Timeframe:** 12-month historical transactional period.
  - **Key Variables:** Customer Demographics (Age, Gender), Purchase Details (Product Category, Quantity, Price, Date), and Payment Mechanics (Payment Method).

## 3. Cleaning and Transformation Summary

A robust ETL (Extract, Transform, Load) pipeline was built using Python and Pandas to ensure high data integrity:

- **Missing Values:** Rows missing critical identifiers like `Customer ID` were dropped to maintain the validity of Lifetime Value (LTV) calculations. Missing `Customer Age` values were imputed using the median.
- **Outlier Detection:** The Interquartile Range (IQR) method was deployed to detect anomalies in financial metrics (`Product Price` and `Quantity`). Extreme outliers were removed to prevent skewing the Average Order Value (AOV).
- **Standardization:** Text columns (`Product Category` and `Payment Method`) were standardized to lowercase and stripped of whitespaces to ensure accurate aggregations.
- **Feature Engineering:** Created a derived `Calculated_Revenue` field (`Quantity` * `Product Price`) to serve as the single source of truth for all downstream financial calculations.

## 4. KPI Framework

The analysis was driven by four primary Key Performance Indicators (KPIs):

1. **Total Revenue:** Gross sales across all categories (Sum of `Calculated_Revenue`). The ultimate indicator of top-line growth.
2. **Average Order Value (AOV):** Average amount spent per transaction (`Total Revenue` / `Count of Unique Transactions`). Critical for evaluating cross-selling strategies.
3. **Category Penetration:** Revenue contributed by a specific category as a percentage of total revenue. Identifies the "cash cow" products.
4. **Customer Lifetime Value (LTV) Proxy:** Total historical spending per unique customer. Identifies the most valuable "VIP" customers.

## 5. Key Insights

Through Exploratory Data Analysis (EDA) and Statistical testing, we uncovered several actionable insights:

1. **Massive Digital Dependency:** Over 70% of gross revenue flows through just two digital payment gateways (Credit Card and PayPal), making checkout infrastructure the most critical technical dependency.
2. **The Power User Multiplier:** While the Top 10 VIP customers contribute a mere 0.61% of total revenue (indicating high mass-market stability), they average $4,368 per customer—**5.7x higher** than the baseline average.
3. **Category Concentration:** The 'Books' and 'Clothing' verticals are the undisputed cash cows, driving 60% of all sales, whereas 'Groceries' is a low-performing drag on margins.
4. **Gender Parity in Spending:** Statistical Independent Two-Sample T-Tests confirmed that male and female customers have statistically identical Average Order Values, invalidating any assumptions that gendered marketing campaigns would yield a higher basket size.
5. **Q4 Supply Chain Pressure:** Time-series analysis revealed exponential revenue growth in Q4, demanding that inventory procurement be finalized by late Q3.

## 6. Tableau Dashboard

To provide stakeholders with a self-serve analytics tool, a dynamic Tableau dashboard was developed.

- **Executive View:** Displays high-level KPIs (Total Revenue, AOV).
- **Operational View:** Features time-series trend lines, category performance bar charts, and demographic breakdowns.
- **Interactivity:** Allows users to slice data dynamically by Date Range, Region, and Product Category.

**Live Link:** [View the Interactive Retail Sales Dashboard](https://public.tableau.com/app/profile/suraj.kewat/viz/RetailSalesDashboard_17773605413330/RetailSalesDashboard?publish=yes)

*(Note: See `tableau/screenshots/dashboard_overview.png` in the repository for a visual overview).*

## 7. Recommendations and Expected Impact

Based on the insights, we delivered three highly actionable, data-backed business recommendations:

1. **Optimize Payment Gateways**
   - **Action:** Leverage the massive, proven transaction volume (70%) flowing through Credit Cards and PayPal to renegotiate processing fees with the gateway providers.
   - **Expected Impact:** An immediate 0.4% to 0.7% increase in net profit margins on the majority of revenue without altering product or marketing strategies.
2. **Launch an Automated VIP Loyalty Tier**
   - **Action:** Implement a loyalty program where any customer crossing a $1,500 LTV threshold receives free expedited shipping and early access to new lines.
   - **Expected Impact:** Increases the purchase frequency and retention of the most profitable 5% of the customer base, estimated to boost total revenue by 4% to 6%.
3. **Reallocate Marketing Budgets**
   - **Action:** Halt gender-specific AOV optimization campaigns. Reallocate spending towards the highest-performing "Books" and "Clothing" channels as primary acquisition funnels.
   - **Expected Impact:** Drastically lowers blended Customer Acquisition Cost (CAC) by focusing only on proven acquisition channels.
