# Sales Dashboard using Microsoft Fabric

An end-to-end sales analytics project built on **Microsoft Fabric**, following the **Medallion Architecture** (Bronze → Silver → Gold) to transform raw sales data into a clean, business-ready Power BI dashboard.

This project was built as a hands-on learning exercise to understand Microsoft Fabric's Lakehouse, Data Engineering, and Warehouse capabilities from scratch.

---

## 🎯 Project Objective

To build a complete data pipeline in Microsoft Fabric — from raw data ingestion to a published, interactive sales dashboard — while learning core Fabric concepts like Lakehouses, Delta tables, Warehouses, and the Medallion Architecture.

---

## 🛠 Tools & Technologies

- Microsoft Fabric (Lakehouse, Warehouse, Pipelines, Notebooks)
- Delta Lake / Delta Tables
- Power Query / Dataflows
- SQL (Warehouse queries)
- Power BI (Report & Dashboard)

---

## 🏗 Project Architecture (Medallion Architecture)

```
Raw Dataset (CSV/Excel)
        │
        ▼
   Bronze Layer   →  Raw data ingested as-is, converted to Delta format
        │
        ▼
   Silver Layer   →  Cleaned, validated, and standardized data
        │
        ▼
   Gold Layer     →  Business-ready, aggregated data (fact & dimension tables)
        │
        ▼
   Warehouse      →  Gold data loaded for SQL-based reporting
        │
        ▼
   Power BI       →  Published interactive sales dashboard
```

---

## 📌 Step-by-Step Workflow

### 1. Workspace & Lakehouse Setup
- Created a new Workspace in Microsoft Fabric
- Created a Lakehouse: `Sales_Lakehouse`

### 2. Raw Data Upload
- Uploaded the raw sales dataset (`sales_data.csv`) into the **Files** section of the Lakehouse
- Verified the file structure and column names before processing

### 3. Bronze Layer — Raw to Delta
- Loaded the raw file into a Fabric Notebook / Dataflow
- Converted the raw file into a **Delta table** without transformation
- Saved it as the Bronze table: `bronze_sales`
- Purpose: preserve the original data as a single source of truth

### 4. Silver Layer — Data Cleaning
- Read data from `bronze_sales`
- Applied cleaning steps:
  - Removed duplicates
  - Handled null/missing values
  - Corrected data types (date, numeric, text)
  - Standardized column names
- Saved the cleaned output as: `silver_sales`

### 5. Gold Layer — Business-Ready Data
- Read data from `silver_sales`
- Created **fact and dimension tables** following a star schema:
  - Fact table: `fact_sales`
  - Dimension tables: `dim_product`, `dim_customer`, `dim_date`, `dim_region`
- Applied business logic (aggregations, calculated columns, KPIs)
- Saved as Gold tables

### 6. Warehouse Layer
- Created a Fabric **Warehouse**: `Sales_Warehouse`
- Loaded the Gold tables into the Warehouse using SQL / pipeline
- Validated data using SQL queries (row counts, sample checks)

### 7. Power BI Report & Publish
- Connected Power BI to the Fabric Warehouse (Direct Lake / Import mode)
- Built the sales dashboard with:
  - Sales KPIs (Total Sales, Total Orders, Avg Order Value)
  - Sales trend over time
  - Sales by region/product/customer segment
  - Interactive slicers and filters
- Published the report to the Fabric workspace



## 📁 Repository Structure

```
├── raw_data/
│   └── sales_data.csv
├── notebooks/
│   ├── bronze_layer.ipynb
│   ├── silver_layer.ipynb
│   └── gold_layer.ipynb
├── dashboard_screenshot.png
└── README.md
```

---

## 🔑 Key Learnings

- Understood how Medallion Architecture organizes data into progressive layers of quality
- Learned to convert raw files into Delta tables inside a Fabric Lakehouse
- Practiced building fact/dimension tables and star schema design
- Learned to move Gold data into a Warehouse for SQL-based access
- Connected Power BI to a Fabric Warehouse and published a live report

---

## 👤 Author

**Saloni Kushwah**
GitHub: [salonikushwah27](https://github.com/salonikushwah27)
LinkedIn: [saloni-kushwah-](https://linkedin.com/in/saloni-kushwah-)
