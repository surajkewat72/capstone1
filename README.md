# NST DVA Capstone 2 - Project Repository

**Newton School of Technology | Data Visualization & Analytics**  
A 2-week industry simulation capstone using Python, GitHub, and Tableau to convert raw data into actionable business intelligence.



## Quick Start
If you are working locally:

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter notebook
```

If you are working in Google Colab:
- Upload or sync the notebooks from `notebooks/`
- Keep the final `.ipynb` files committed to GitHub
- Export any cleaned datasets into `data/processed/`

## Project Overview

| Field | Details |
|---|---|
| Project Title | Retail Analytics Capstone: Data-Driven Business Intelligence |
| Sector | Retail & E-Commerce |
| Team ID | DVA-B1-T3 |
| Section | B1 |
| Faculty Mentor | NST Faculty Mentor |
| Institute | Newton School of Technology |
| Submission Date | 28 April 2026 |

## Team Members

| Role | Name | GitHub Username |
|---|---|---|
| Project Lead / Final Reporting | Suraj Kewat | surajkewat72 |
| Data / ETL Lead | Aditya Raj Srivastava | |
| Analysis / Stats Lead | Shivank Gupta | |
| Visualization Lead | Siddu | |

## Business Problem

**Context**
The retail business is struggling to transition from descriptive spreadsheet reporting to prescriptive, dynamic decision-making. Management lacks clear visibility into which product categories drive the most revenue, how different customer demographics spend, and how efficient the checkout payment processes are, leading to suboptimal inventory and marketing strategies.

**Core Business Question**
How can we optimize inventory purchasing and targeted marketing by understanding what products sell, to whom, and how they pay, in order to increase overall net margins?

**Decision Supported**
This analysis enables stakeholders to confidently reallocate marketing budgets, renegotiate digital payment gateway fees, and launch targeted VIP loyalty programs to maximize profitability and retention.

## Dataset

| Attribute | Details |
|---|---|
| Source Name | Synthetic Retail Transaction Logs (`ecommerce_customer_data_custom_ratios.csv`) |
| Direct Access Link | Internal Repository (`data/raw/`) |
| Row Count | ~9,400 rows |
| Column Count | 14 columns |
| Time Period Covered | 12 Months |
| Format | CSV |

### Key Columns Used

| Column Name | Description | Role in Analysis |
|---|---|---|
| `Customer ID` | Numerical identifier for the buyer | Used for customer segmentation, churn analysis, and Lifetime Value (LTV). |
| `Product Category` | The category of the item (e.g., Electronics, Clothing) | Used for revenue breakdown and identifying cash cows. |
| `Calculated_Revenue` | Derived field (`Quantity` * `Product Price`) | Primary metric for all financial aggregations and KPI calculations. |
| `Payment Method` | Medium of exchange (Cash, Credit Card, Crypto, PayPal) | Used for analyzing checkout efficiency and fee optimization. |

For full column definitions, see `docs/data_dictionary.md`.

## KPI Framework

| KPI | Definition | Formula / Computation |
|---|---|---|
| Total Revenue | Gross sales across all categories | Sum of `Calculated_Revenue` |
| Average Order Value (AOV) | Average amount spent per transaction | `Total Revenue` / `Count of Unique Transactions` |
| Category Penetration | Revenue contributed by a specific category as a percentage of total revenue | `(Category Revenue / Total Revenue) * 100` |
| Customer Lifetime Value (LTV) Proxy | Total historical spending per unique customer | Sum of `Calculated_Revenue` grouped by `Customer ID` |

Document KPI logic clearly in `notebooks/04_statistical_analysis.ipynb` and `notebooks/05_final_load_prep.ipynb`.

## Tableau Dashboard

| Item | Details |
|---|---|
| Dashboard URL | [Retail Sales Dashboard](https://public.tableau.com/app/profile/suraj.kewat/viz/RetailSalesDashboard_17773605413330/RetailSalesDashboard?publish=yes) |
| Executive View | Top ribbon displaying high-level KPIs (Total Revenue, AOV, New Customers) |
| Operational View | Lower sections featuring time-series trend lines, category performance bar charts, and demographic breakdowns |
| Main Filters | Date Range, Region, Product Category |

Store dashboard screenshots in `tableau/screenshots/` and document the public links in `tableau/dashboard_links.md`.

## Key Insights

1. **Digital Dependency:** Over 70% of gross revenue flows through just two digital payment gateways (Credit Card and PayPal), making checkout infrastructure the most critical technical dependency.
2. **Category Concentration:** The 'Books' and 'Clothing' verticals drive 60% of all sales. They are the core acquisition channels for the business.
3. **Mass-Market Stability:** The Top 10 VIP customers contribute a mere 0.61% of total revenue, meaning the business faces virtually zero revenue concentration risk.
4. **The Power User Multiplier:** The Top 10 spenders average $4,368 per customer—5.7x higher than the baseline average.
5. **Emerging Crypto Market:** Cryptocurrency payments account for an unusually high 10% of revenue, highlighting a niche, highly tech-forward customer demographic.
6. **Age Silos:** The customer base is heavily concentrated in the 35-45 age bracket, indicating a failure to capture the Gen Z (under 25) demographic.
7. **Gender Parity in Spending:** Statistical T-Tests confirm that male and female customers have identical Average Order Values, invalidating the need for gendered AOV optimization campaigns.
8. **Q4 Supply Chain Pressure:** Time-series analysis shows exponential revenue growth in Q4, demanding that inventory procurement and warehouse staffing be finalized by late Q3 to avoid catastrophic holiday stockouts.

## Recommendations

| # | Insight | Recommendation | Expected Impact |
|---|---|---|---|
| 1 | Digital Dependency (70% CC & PayPal) | Leverage massive, proven transaction volume to renegotiate processing fees (e.g., from 2.9% to 2.2%) with gateway providers. | 0.4% to 0.7% immediate increase in net profit margins on 70% of total revenue. |
| 2 | The Power User Multiplier (VIPs spend 5.7x more) | Implement an automated VIP loyalty tier where any customer crossing a $1,500 LTV threshold receives free expedited shipping and early access. | Increases purchase frequency and retention of top 5% spenders, boosting total revenue by estimated 4% to 6%. |
| 3 | Emerging Crypto Market (10% of revenue) | Launch targeted digital campaigns on crypto-centric platforms and release exclusive "Crypto-only" limited apparel drops. | Acquires highly liquid customers at a significantly lower CAC than traditional paid search. |

## Repository Structure

```text
SectionName_TeamID_ProjectName/
|
|-- README.md
|
|-- data/
|   |-- raw/                         # Original dataset (never edited)
|   `-- processed/                   # Cleaned output from ETL pipeline
|
|-- notebooks/
|   |-- 01_extraction.ipynb
|   |-- 02_cleaning.ipynb
|   |-- 03_eda.ipynb
|   |-- 04_statistical_analysis.ipynb
|   `-- 05_final_load_prep.ipynb
|
|-- scripts/
|   `-- etl_pipeline.py
|
|-- tableau/
|   |-- screenshots/
|   `-- dashboard_links.md
|
|-- reports/
|   |-- README.md
|   |-- project_report_template.md
|   `-- presentation_outline.md
|
|-- docs/
|   `-- data_dictionary.md
|
|-- DVA-oriented-Resume/
`-- DVA-focused-Portfolio/
```

## Analytical Pipeline

The project follows a structured 7-step workflow:

1. **Define** - Sector selected, problem statement scoped, mentor approval obtained.
2. **Extract** - Raw dataset sourced and committed to `data/raw/`; data dictionary drafted.
3. **Clean and Transform** - Cleaning pipeline built in `notebooks/02_cleaning.ipynb` and optionally `scripts/etl_pipeline.py`.
4. **Analyze** - EDA and statistical analysis performed in notebooks `03` and `04`.
5. **Visualize** - Interactive Tableau dashboard built and published on Tableau Public.
6. **Recommend** - 3-5 data-backed business recommendations delivered.
7. **Report** - Final project report and presentation deck completed and exported to PDF in `reports/`.






## Contribution Matrix

This table must match evidence in GitHub Insights, PR history, and committed files.

| Team Member | Dataset and Sourcing | ETL and Cleaning | EDA and Analysis | Statistical Analysis | Tableau Dashboard | Report Writing | PPT and Viva |
|---|---|---|---|---|---|---|---|
| Suraj Kewat | Owner | Support | Support | Support | Support | Owner | Owner |
| Aditya Raj Srivastava | Support | Owner | Support | Support | Support | Support | Owner |
| Shivank Gupta | Support | Support | Owner | Owner | Support | Support | Owner |
| Siddu | Support | Support | Support | Support | Owner | Support | Owner |

**Declaration:** We confirm that the above contribution details are accurate and verifiable through GitHub Insights, PR history, and submitted artifacts.

**Date:** 28 April 2026


