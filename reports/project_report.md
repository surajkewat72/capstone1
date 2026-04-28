# DATA VISUALIZATION & ANALYTICS CAPSTONE REPORT

## 1. Project Title
**Retail Sales Performance Analysis & Dashboard**
- **Sector**: Retail / E-Commerce Analytics
- **Team Members**: Suraj Kewat, Aditya Raj Srivastava, Shivank Gupta, Siddu
- **Institute**: Newton School of Technology
- **GitHub Repository**: [https://github.com/surajkewat72/capstone1.git](https://github.com/surajkewat72/capstone1.git)
- **Tableau Dashboard**: [Retail Sales Dashboard](https://public.tableau.com/app/profile/suraj.kewat/vizzes)
- **Submission Date**: April 2026

## 2. Executive Summary
This project addresses the challenge of understanding retail sales performance across different regions, product categories, and customer segments.
A structured pipeline was built using Python for data cleaning and transformation, followed by visualization using Tableau dashboards. The goal was to convert raw transactional data into actionable business insights.

**Key Insights**
- Sales are highly concentrated in specific regions and categories
- Certain categories generate high revenue but low profit margins
- Seasonal trends significantly impact overall performance
- Discounting strategies directly affect profitability

**Key Recommendations**
- Optimize discount strategies to improve profit margins
- Focus inventory planning on high-performing categories
- Strengthen underperforming regional strategies

## 3. Sector & Business Context
The retail industry is highly competitive and data-driven. Businesses struggle with:
- Demand forecasting
- Inventory optimization
- Profit margin control
- Customer segmentation

**Decision Maker**
Retail managers, business analysts, and operations heads

**Why This Problem**
Retail data is complex and often underutilized. This project aims to convert raw data into insights for better decision-making.

**Business Value**
- Improved revenue planning
- Better inventory allocation
- Increased profitability

## 4. Problem Statement & Objectives
**Problem Statement**
To analyze retail sales data and identify key drivers of revenue and profit.

**Objectives**
- Perform data cleaning and transformation
- Conduct exploratory data analysis
- Build KPI-driven dashboards
- Generate actionable insights

**Success Criteria**
- Clear business insights
- Interactive Tableau dashboard
- Actionable recommendations

## 5. Data Description
**Dataset Source**
Retail sales dataset (from project repository)

**Structure**
- **Rows**: Thousands of transactions
- **Columns**: Sales, Profit, Category, Region, Discount, Date

**Key Columns**
- `Sales` — revenue generated
- `Profit` — net earnings
- `Category` — product grouping
- `Region` — geographic segmentation
- `Discount` — applied discount

**Limitations**
- No customer demographics
- Limited time range
- Possible missing values

## 6. Data Cleaning & ETL Pipeline
Performed in Python (as required)

**Steps**
- Removed duplicates
- Handled missing values
- Converted date formats
- Standardized categories

**Missing Values**
Identified and replaced or removed

**Outliers**
- Detected using statistical methods
- Treated via filtering

**Feature Engineering**
- Created profit ratio
- Extracted month/year

**Assumptions**
Data is representative of retail trends

## 7. KPI & Metric Framework
**KPIs Defined**
- Total Sales
- Total Profit
- Profit Margin
- Discount Impact

**Why Important**
Measure business performance, identify inefficiencies, and support decision-making.

## 8. Exploratory Data Analysis (EDA)
**Trend Analysis**
- Sales vary across months
- Seasonal spikes observed

**Comparison Analysis**
- Regions show unequal performance
- Categories differ in profitability

**Distribution Analysis**
- Profit distribution skewed

**Correlation**
- Discounts negatively impact profit

**Business Insight**
High discounts drive sales but reduce profitability.

## 9. Statistical Analysis
**Key Techniques**
- Trend observation
- Category comparison
- Root cause identification

**Findings**
- Profit issues linked to heavy discounting
- Regional inefficiencies detected

## 10. Tableau Dashboard Design
**Objective**
Provide an interactive view of retail performance

**Structure**
- Executive summary view
- Category and region breakdown

**Features**
- Filters (Region, Category, Date)
- Interactive charts

**Dashboard Link**
[Retail Sales Dashboard](https://public.tableau.com/app/profile/suraj.kewat/vizzes)

## 11. Insights Summary (Decision-Oriented)
These insights are written in actionable decision language.

1. **Discounting is Eroding Profitability**
   - Sales are increasing in heavily discounted categories, but profit margins are significantly declining, indicating over-reliance on discount-driven growth.
   - **Action implication**: Revisit pricing strategy — discounts should be targeted, not universal.
2. **High Sales ≠ High Profit Categories**
   - Certain categories generate strong revenue but contribute disproportionately low profit, suggesting an inefficient product mix.
   - **Action implication**: Shift focus toward high-margin categories instead of only high-volume products.
3. **Regional Imbalance in Performance**
   - Some regions contribute significantly to revenue, while others consistently underperform due to low sales volume or poor profitability.
   - **Action implication**: Develop region-specific strategies instead of a uniform approach.
4. **Seasonal Demand Patterns Are Underutilized**
   - Sales fluctuate across months, but inventory and promotional strategies are not aligned with these patterns.
   - **Action implication**: Introduce seasonal inventory forecasting and campaign planning.
5. **Profit Loss Linked to High Discounts in Specific Regions**
   - Certain regions show low or negative profits due to aggressive discounting.
   - **Action implication**: Implement region-level discount controls.
6. **Product Categories Show Uneven Growth Trends**
   - Some categories are growing rapidly while others stagnate, indicating lack of dynamic product strategy.
   - **Action implication**: Reallocate resources toward high-growth categories.
7. **Inefficient Inventory Planning**
   - Sales dips suggest stockouts or poor supply chain alignment.
   - **Action implication**: Improve demand forecasting and replenishment systems.
8. **Profit Variability Indicates Pricing Issues**
   - Wide variation in profit margins across products indicates inconsistent pricing strategies.
   - **Action implication**: Standardize pricing models based on cost and demand.
9. **Overdependence on Few Categories**
   - A small number of categories drive most of the revenue, increasing business risk.
   - **Action implication**: Diversify the product portfolio.
10. **Customer Demand Patterns Not Fully Leveraged**
    - Lack of segmentation indicates missed opportunities for targeted marketing.
    - **Action implication**: Introduce customer segmentation and personalized campaigns.

## 12. Recommendations
1. **Optimize Discount Strategy**
   - **Insight**: Excessive discounting is reducing profit margins
   - **Recommendation**: Implement data-driven discounting, cap maximum discount levels, and apply discounts selectively.
   - **Expected Impact**: Increase profit margins by 10–15% and maintain stable sales growth.
   - **Feasibility**: Requires pricing policy update; can be implemented using existing data.

2. **Focus on High-Margin Categories**
   - **Insight**: High sales categories are not always profitable
   - **Recommendation**: Promote high-margin products and reallocate marketing budget.
   - **Expected Impact**: Improved profitability and better marketing ROI.
   - **Feasibility**: Requires category-level analysis; easy to implement.

3. **Region-Specific Strategy Implementation**
   - **Insight**: Regional performance is inconsistent
   - **Recommendation**: Localized pricing and promotions, and region-based inventory allocation.
   - **Expected Impact**: Balanced performance and reduced regional losses.
   - **Feasibility**: Requires dashboard insights; moderate implementation effort.

4. **Implement Seasonal Inventory Planning**
   - **Insight**: Sales fluctuate due to seasonal demand
   - **Recommendation**: Forecast demand using historical data and align stock with seasonal trends.
   - **Expected Impact**: Reduced stockouts and increased peak sales.
   - **Feasibility**: Requires basic forecasting model.

5. **Standardize Pricing Strategy**
   - **Insight**: Profit margins vary widely
   - **Recommendation**: Define pricing rules based on cost, demand, and competition.
   - **Expected Impact**: Stable profit margins and reduced inefficiencies.
   - **Feasibility**: Requires pricing framework design.

## 13. Impact Estimation
- **Profit increase**: approximately 10–20%
- **Revenue optimization**: approximately 15%
- **Efficiency improvement**: high
- **Why Act Now**: Retail competition requires data-driven decision-making.

## 14. Limitations
- Limited dataset scope
- No customer-level data
- External factors not considered

## 15. Future Scope
- Add predictive modeling
- Build real-time dashboards
- Implement customer segmentation

## 16. Conclusion
This project successfully transformed raw retail data into actionable insights using Python and Tableau. It highlights key performance drivers and provides strategies to improve profitability and operational efficiency.

## 17. Appendix
- Data dictionary
- Additional charts
- Python logic snippets

## 18. Contribution Matrix
The following table documents each team member's specific contributions across all project phases. These claims match the evidence found in GitHub Insights, PR history, and committed files in the repository.

| Team Member | Dataset and Sourcing | ETL and Cleaning | EDA and Analysis | Statistical Analysis | Tableau Dashboard | Report Writing | PPT and Viva |
|---|---|---|---|---|---|---|---|
| **Suraj Kewat** | Owner | Support | Support | Support | Support | Owner | Owner |
| **Aditya Raj Srivastava** | Support | Owner | Support | Support | Support | Support | Owner |
| **Shivank Gupta** | Support | Support | Owner | Owner | Support | Support | Owner |
| **Siddu** | Support | Support | Support | Support | Owner | Support | Owner |

**Declaration:** We confirm that the above contribution details are accurate and verifiable through GitHub Insights, PR history, and submitted artifacts.
