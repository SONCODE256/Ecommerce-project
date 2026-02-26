# Ecommerce-project
eCommerce Analytics Project — SQL-based analysis on retail sales data to answer business questions (traffic, bounce rate, revenue, orders) using CTEs, joins, and time filters. Includes clean queries, notes, and reproducible outputs.
## 📌 Project Overview

This repository is an **eCommerce Analytics project using SQL** to analyze performance across the full customer journey — from **traffic acquisition** to **user behavior** and finally **conversion & revenue**.

The project answers **10 real-world business questions** and produces metrics such as:

- **Visits, pageviews, and transactions** by month  
- **Bounce rate** and **conversion rate** by traffic source  
- **Revenue trends** by week/month, including **cumulative revenue**  
- **Revenue contribution** by device category (desktop, mobile, etc.)  
- **Purchaser vs. non-purchaser behavior** comparisons  
- **Cross-sell insights** (products also purchased together)  
- **Product-level funnel/cohort map**: *view → add_to_cart → purchase*  

The goal is to practice a complete analytics workflow: choosing the right tables/columns, joining data correctly, filtering time periods, calculating KPIs, and writing clean, reproducible SQL.

---

## 🚀 What You Will Gain

By completing this project, you will gain:

### ✅ Strong SQL Analytics Skills
- Write clean, structured queries using **CTEs**
- Apply correct **date filtering** and time grouping (**weekly / monthly**)
- Calculate key KPI formulas (**rates, ratios, contributions**)
- Build **cumulative metrics** (running totals)

### ✅ End-to-End Funnel & Cohort Thinking
- Measure performance across the funnel: **view → add_to_cart → purchase**
- Compute product-level **add_to_cart_rate** and **purchase_rate**
- Understand user behavior differences (**purchasers vs non-purchasers**)

### ✅ Business Insight & Decision Support
- Identify high-performing **traffic sources** and **devices**
- Evaluate **volume vs. efficiency** (traffic vs conversion)
- Discover cross-sell patterns for recommendation ideas

### ✅ Portfolio-Ready Deliverable
- A well-structured GitHub repo showcasing real eCommerce KPI analysis
- Clear, interview-ready examples: funnel analysis, revenue trends, and segmentation
## 📂 Dataset

This project uses **Google Analytics 360 Sample (Google Merchandise Store)** exported to **BigQuery**.  
The dataset contains **session-level data** with nested structures for **hits**, **eCommerce actions**, and **product details**.

### 🔎 Key Concepts
- **Session-level metrics** are stored in `totals` (visits, pageviews, transactions, bounces, hits).
- **Traffic attribution** comes from `trafficSource.source`.
- **Device segmentation** comes from `device.deviceCategory`.
- **Product & funnel events** (view → add_to_cart → purchase) come from `hits.eCommerceAction` and `hits.product`.

---

## 🧾 Table / Fields Description (Core Columns Used)

> Below are the main fields used across the 10 queries in this project.

| Field Name | Data Type | Description |
|-----------|----------|-------------|
| `fullVisitorId` | STRING | Unique visitor ID. |
| `date` | STRING | Session date in `YYYYMMDD` format. |
| `totals` | RECORD | Aggregate values across the session. |
| `totals.bounces` | INTEGER | Total bounces (1 if bounced session, otherwise NULL). |
| `totals.hits` | INTEGER | Total number of hits within the session. |
| `totals.pageviews` | INTEGER | Total number of pageviews within the session. |
| `totals.visits` | INTEGER | Number of sessions (1 for valid sessions, NULL if no interaction events). |
| `totals.transactions` | INTEGER | Total number of eCommerce transactions within the session. |
| `trafficSource.source` | STRING | Traffic source (search engine, referral hostname, or `utm_source`). |
| `hits` | RECORD (REPEATED) | Repeated record containing hit-level data. |
| `hits.eCommerceAction` | RECORD | eCommerce events collected during the session (hit-level). |
| `hits.eCommerceAction.action_type` | STRING | Action type: product list click (1), product detail view (2), add to cart (3), remove from cart (4), checkout (5), purchase (6), refund (7), checkout options (8),unknown (0)  | 
| `hits.product` | RECORD | Product-level data for enhanced eCommerce hits. |
| `hits.product.productQuantity` | INTEGER | Quantity of the product purchased. |
| `hits.product.productRevenue` | INTEGER | Product revenue (stored in micros; divide by `1e6` to get standard currency). |
| `hits.product.productSKU` | STRING | Product SKU. |
| `hits.product.v2ProductName` | STRING | Product name. |
| `device.deviceCategory` | STRING | Device category (Mobile, Tablet, Desktop). |
## 📁 Project Structure

```text
ecommerce-analytics-sql/
├── README.md
├── queries/
│   ├── q01_monthly_visits_pageviews_transactions_jan_mar_2017.sql
│   ├── q02_bounce_rate_by_traffic_source_jul_2017.sql
│   ├── q03_revenue_by_source_week_month_jun_2017.sql
│   ├── q04_conversion_rate_by_traffic_source_2017.sql
│   ├── q05_avg_pageviews_purchasers_vs_nonpurchasers_jun_jul_2017.sql
│   ├── q06_avg_transactions_per_purchasing_user_jul_2017.sql
│   ├── q07_revenue_contribution_by_device.sql
│   ├── q08_also_bought_products_youtube_mens_vintage_henley_jul_2017.sql
│   ├── q09_product_level_funnel_view_addtocart_purchase_jan_mar_2017.sql
│   └── q10_weekly_and_cumulative_revenue_may_jul_2017.sql
├── docs/
│   ├── data_dictionary.md
│   └── notes.md
└── outputs/
    ├── screenshots/
    └── sample_results.csv
