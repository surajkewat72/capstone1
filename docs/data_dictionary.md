# Data Dictionary: Retail Transaction Dataset

This document defines the schema and provides context for each field in the dataset used for the Retail Analytics Capstone.

## 📋 Core Columns

### 1. Customer ID
- **Description:** A unique alphanumeric identifier assigned to each individual customer.
- **Data Type:** `String / Integer`
- **Business Rule:** Used for customer segmentation, churn analysis, and tracking lifetime value (LTV).

### 2. Purchase Date
- **Description:** The precise date and time when the transaction was processed.
- **Data Type:** `DateTime`
- **Business Rule:** Essential for identifying seasonal trends, peak shopping hours, and time-series forecasting.

### 3. Product Category
- **Description:** The category of the item purchased (e.g., Electronics, Clothing, Books, Groceries).
- **Data Type:** `String`
- **Business Rule:** Captures what was sold to identify top-performing product segments.

### 4. Quantity
- **Description:** The total number of units of a specific product purchased in a single transaction line item.
- **Data Type:** `Integer`
- **Business Rule:** Negative values or extreme outliers were removed as invalid entries during ETL.

### 5. Product Price
- **Description:** The unit price of the product.
- **Data Type:** `Float`
- **Business Rule:** Standardized to local currency. Extreme outliers were handled using the IQR method.

### 6. Payment Method
- **Description:** Medium of exchange used by the customer (e.g., Cash, Credit Card, Crypto, PayPal).
- **Data Type:** `String`
- **Business Rule:** Crucial for analyzing checkout efficiency and optimizing payment gateway processing fees.

### 7. Customer Age
- **Description:** The age of the purchasing customer.
- **Data Type:** `Integer`
- **Business Rule:** Demographic identifier. Missing values were imputed using the median age.

### 8. Gender
- **Description:** The gender identity of the purchasing customer.
- **Data Type:** `String`
- **Business Rule:** Demographic identifier used for checking purchasing behavior variances.

### 9. Calculated_Revenue
- **Description:** Derived field calculated as `(Quantity * Product Price)`.
- **Data Type:** `Float`
- **Business Rule:** The primary metric acting as the single source of truth for all downstream financial aggregations and KPI calculations.

### 10. Churn
- **Description:** Binary indicator of customer retention failure.
- **Data Type:** `Boolean / Integer`
- **Business Rule:** `1` indicates the customer has churned, `0` indicates an active customer.

---
*Last Updated: April 2026*
