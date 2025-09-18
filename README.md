## Project Overview: ETL & Predictive Inventory Dashboard

This project develops an end-to-end pipeline for analyzing and predict retail inventory performance using transactional data. The workflow is structured into several main stages:

### 1. Data Wrangling (ETL)

* Imported raw transaction data (`retail_store_inventory.csv`) using Pandas.
* Performed data quality checks:

  * Detected missing values and duplicates.
  * Validated business rules such as `Inventory Level ≥ 0`, `Discount ≤ 100`, and `Units Sold ≤ Inventory Level`.
* Verified consistency between Product ID–Category and Store ID–Region mappings.
* Normalized identifiers by generating composite keys (`product_id_new`, `store_id_new`).
* Converted data types for proper storage (dates, strings, integers, and floats).

### 2. Transformation & Feature Engineering

* Generated new analytical fields such as Revenue (`Units Sold * Price`), Utilization Rate, Stockout Flag, and Forecast Error.
* Structured the data into fact and dimension tables to support star-schema design for BI dashboards.

### 3. Loading into PostgreSQL

* Used SQLAlchemy and psycopg2 to establish a connection with PostgreSQL.
* Uploaded the processed tables (`fact_inventory`, `dim_product`, `dim_store`, `dim_date`) into a centralized data mart.
  <img width="872" height="956" alt="schema inventory" src="https://github.com/user-attachments/assets/c5d944d1-092e-4daf-bac6-462baf3c3278" />


### 4. Predictive Modeling

* Applied time-series forecasting with Facebook Prophet to predict future demand.
* Performed customer and product segmentation using K-Means clustering.
* Evaluated forecast accuracy with MAE and RMSE metrics.
* Visualized actual vs predicted vs future demand trends to assess forecast reliability.

### 5. Dashboard Preparation

* Exported cleaned and enriched data for Power BI dashboard integration.
* Dashboard includes KPIs, trend analysis, sales vs demand conversion funnel, clustering insights, and forecasting accuracy evaluation.

## Preview Dashboard

### Sales & Inventory Performance

<img width="1188" height="671" alt="image" src="https://github.com/user-attachments/assets/083c466c-189b-4dc2-89fb-16c42548ce15" />
Baik, berikut versi **README** yang sudah saya ubah ke bahasa Inggris dan tanpa emotikon:

## Description

This dashboard is designed to analyze **sales and inventory performance** based on key KPIs, sales distribution by category and region, forecast accuracy, and sales trends over time.

It provides descriptive, diagnostic, and prescriptive insights to support decision-making in sales and inventory management.

## Analysis & Insights

### 1. Key KPIs

* **Revenue:** Target achieved at **688.12K**.
* **Stockout %:** No stockouts occurred (0%).
* **Utilization Rate:** Only **0.49** compared to the target of **0.80**, indicating underutilization of capacity.

### 2. Units Sold vs Units Ordered

* All categories (Furniture, Groceries, Clothing, Toys, Electronics) show that **units ordered are higher than units sold**.
* **Insight:** Indicates potential **over-ordering** or inaccurate demand estimation.

### 3. Forecast Accuracy

* Forecast error is consistently around **12K** across categories.
* **Insight:** Forecasting methods need improvement to better align with actual demand.

### 4. Regional Sales Distribution

* **East:** Strong in Groceries and Furniture.
* **North:** Dominated by Furniture and Electronics.
* **South:** Mainly Furniture.
* **West:** More evenly distributed (Clothing, Furniture, Toys).
* **Insight:** Consumer preferences differ by region, suggesting a need for region-specific sales and marketing strategies.

### 5. Trends (2022–2024)

* **Units sold** remain higher than both inventory level and demand forecast.
* A sharp decline is observed in early 2024 across all indicators.
* **Insight:** Further investigation is needed to determine whether this is due to seasonality or a real performance drop.
  
## Conclusion

* Revenue target is achieved and stock levels are sufficient, but **utilization rate and forecast accuracy need improvement**.
* Sales distribution varies across regions, providing opportunities for regional sales strategies.
* Continuous monitoring of 2024 trends is necessary to mitigate potential risks.

---
### Profitability & Market Factors

<img width="1190" height="672" alt="image" src="https://github.com/user-attachments/assets/1aef83bd-66d3-4bfa-afc7-36aa4f0fa162" />

