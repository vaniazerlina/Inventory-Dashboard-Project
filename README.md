# Project Overview: ETL & Predictive Inventory Dashboard

This project develops an end-to-end pipeline for analyzing and predicting retail inventory performance using transactional data. The workflow is structured into several main stages:

---

## 1. Data Wrangling (ETL)

* Imported raw transaction data (`retail_store_inventory.csv`) using **Pandas**.
* Performed data quality checks:

  * Identified missing values and duplicates.
  * Validated business rules such as `Inventory Level ≥ 0`, `Discount ≤ 100`, and `Units Sold ≤ Inventory Level`.
* Ensured consistency between **Product ID–Category** and **Store ID–Region** mappings.
* Normalized identifiers by generating composite keys (`product_id_new`, `store_id_new`).
* Converted data types for proper storage (dates, strings, integers, floats).

---

## 2. Transformation & Feature Engineering

* Generated new analytical fields such as **Revenue (Units Sold × Price)**, **Utilization Rate**, **Stockout Flag**, and **Forecast Error**.
* Structured data into **fact** and **dimension** tables, enabling a **star-schema** design for BI dashboards.

---

## 3. Loading into PostgreSQL

* Used **SQLAlchemy** and **psycopg2** to establish a connection with PostgreSQL.
* Uploaded processed tables (`fact_inventory`, `dim_product`, `dim_store`, `dim_date`) into a centralized **data mart**.

<p align="center">  
  <img width="450" alt="schema inventory" src="https://github.com/user-attachments/assets/c5d944d1-092e-4daf-bac6-462baf3c3278" />  
</p>  

---

## 4. Predictive Modeling

* Applied **time-series forecasting** using **Facebook Prophet** to predict future demand.
* Performed **customer and product segmentation** with K-Means clustering.
* Evaluated forecasting accuracy using **MAE** and **RMSE**.
* Visualized **actual vs predicted vs forecasted demand** to validate model reliability.

---

## 5. Dashboard Preparation

* Exported cleaned and enriched data for **Power BI dashboard integration**.
* Dashboards provide insights through **KPIs, trend analysis, sales vs demand funnel, segmentation results, and forecast evaluation**.

---

# Dashboard Preview

## A. Sales & Inventory Performance

<p align="center">  
  <img width="1188" height="671" alt="Sales & Inventory Performance" src="https://github.com/user-attachments/assets/083c466c-189b-4dc2-89fb-16c42548ce15" />  
</p>  

### Description

This dashboard focuses on **sales and inventory performance** across revenue targets, stock levels, forecast accuracy, and sales distribution by region and category.

### Insights

1. **Key KPIs**

   * Revenue target achieved (**688.12K**).
   * **Stockout rate 0%**, showing efficient stock management.
   * Utilization rate is **0.49 vs target 0.80**, indicating underutilization.

2. **Units Sold vs Ordered**

   * Units ordered consistently exceed units sold across all categories.
   * Suggests **over-ordering** or **inaccurate demand forecasts**.

3. **Forecast Accuracy**

   * Forecast error is around **12K** across categories.
   * Forecasting methods require refinement.

4. **Regional Sales**

   * East → strong in Groceries & Furniture.
   * North → dominated by Furniture & Electronics.
   * South → mainly Furniture.
   * West → balanced mix (Clothing, Furniture, Toys).

5. **Trend (2022–2024)**

   * Units sold consistently higher than both inventory level and demand forecast.
   * Sharp decline in early 2024 → requires further investigation (seasonality vs actual downturn).

**Conclusion:** Revenue goals are met, but **utilization and forecast accuracy require improvement**. Regional sales strategies should be tailored to consumer preferences.

---

## B. Profitability & Market Factors

<p align="center">  
  <img width="1190" height="672" alt="Profitability & Market Factors" src="https://github.com/user-attachments/assets/1aef83bd-66d3-4bfa-afc7-36aa4f0fa162" />  
</p>  

### Description

This dashboard highlights **profitability analysis** and **market-related external factors** such as weather and holidays.

### Insights

1. **Profit Margin by Category**

   * **Toys** have the highest profit margin.
   * **Groceries and Clothing** show low or negative margins due to competitive pricing or heavy discounts.
   * **Electronics** have thin but positive margins.

2. **Units Sold by Weather Condition**

   * Sales remain stable across Sunny, Cloudy, Snowy, and Rainy conditions.
   * Weather has minimal impact on demand.

3. **Revenue Contribution by Category**

   * Revenue is evenly distributed:

     * Furniture (19.71%), Groceries (19.93%), Clothing (19.93%), Toys (20.17%), Electronics (20.27%).
   * No single category dominates revenue, indicating strong diversification.

4. **Impact of Discounts**

   * Discounts negatively impact profit margins, especially in **Clothing** and **Groceries**.
   * **Toys** still show positive effects despite discounts.

5. **Sales Trend: Holiday vs Non-Holiday**

   * No significant difference between holiday and non-holiday sales.
   * Sales remain stable with only minor seasonal peaks.

**Conclusion:**

* **Toys** are the most profitable category.
* **Groceries & Clothing** require strategies to improve margins.
* **Weather and holidays** have limited influence on demand.
* **Discounts should be managed carefully**, especially for low-margin categories.

---
