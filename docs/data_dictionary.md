# Data Dictionary: Retail Transaction Dataset

This document defines the schema and provides context for each field in the dataset used for the Retail Analytics Capstone.

## 📋 Core Columns

### 1. CustomerID
- **Description:** A unique alphanumeric identifier assigned to each individual customer.
- **Data Type:** `String / Integer`
- **Business Rule:** Used for customer segmentation, churn analysis, and tracking lifetime value.

### 2. Product
- **Description:** The name, SKU, or category of the item purchased.
- **Data Type:** `String`
- **Business Rule:** Captures what was sold. Inconsistent naming conventions in raw data may require standardizing.

### 3. Quantity
- **Description:** The total number of units of a specific product purchased in a single transaction line item.
- **Data Type:** `Integer`
- **Business Rule:** Must be greater than zero. High values should be checked for bulk/wholesale behavior.

### 4. Price
- **Description:** The unit price of the product before any discounts or taxes.
- **Data Type:** `Float / Decimal`
- **Business Rule:** Standardized to the local currency (e.g., USD).

### 5. TransactionDate
- **Description:** The precise date and time when the transaction was processed.
- **Data Type:** `DateTime`
- **Business Rule:** Essential for identifying seasonal trends, peak shopping hours, and day-of-week performance.

### 6. Location
- **Description:** The geographical identifier for where the transaction occurred (e.g., Store ID, City, or Region).
- **Data Type:** `String`
- **Business Rule:** Enables regional performance benchmarking and logistical optimization analysis.

### 7. Discount
- **Description:** The reduction applied to the original price, either as a percentage or a flat amount.
- **Data Type:** `Float`
- **Business Rule:** Negative values or values exceeding the item price should be treated as data entry errors.

### 8. TotalAmount
- **Description:** The final net amount paid by the customer for the specific line item or transaction.
- **Data Type:** `Float`
- **Business Rule:** Derived field typically calculated as `(Quantity * Price) - Discount`. This is the primary metric for revenue analysis.

---
*Last Updated: 2026-04-25*
