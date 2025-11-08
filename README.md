# 🚦 Real-Time Traffic Data Engineering Project

---

## 📚 Table of Contents
- [🧩 Overview](#-overview)
- [🏗️ Architecture](#-architecture)
- [🧱 Data Model (Silver Layer)](#-data-model-silver-layer)
- [🔗 Relationships (Star Schema)](#-relationships-star-schema)
- [🧹 Data Cleaning Highlights](#-data-cleaning-highlights)
- [⚙️ Tools and Technologies](#️-tools-and-technologies)
- [🚀 Project Workflow](#-project-workflow)
- [📊 Star Schema Diagram](#-star-schema-diagram)
- [🧠 Key Learnings](#-key-learnings)
- [👥 Contributors](#-contributors)
- [🏁 Next Steps](#-next-steps)

---

## 🧩 Overview

This is an **end-to-end data engineering project** for **UK Traffic Data**.  
The goal is to build a **modern data pipeline** that collects, cleans, transforms, and prepares data for analysis and visualization using a multi-layer architecture:

> **Bronze → Silver → Gold**

The project ensures **data quality**, **scalability**, and **analytical efficiency** using **Python**, **SQL Server**, and **Power BI**.

---

## 🏗️ Architecture

**Pipeline Flow:**  
`Raw Data → Bronze Layer → Silver Layer → Gold Layer → Power BI Dashboard`

### 🔸 Bronze Layer
- Raw ingestion layer.  
- Stores data as received from the source with minimal modification.  
- Data loaded using **Python (Pandas)**.

### 🔸 Silver Layer
- Cleaned and structured layer.  
- Includes **normalized tables** with proper **surrogate keys (IDs)** for relationships.  
- Duplicates removed, datatypes validated, and relationships defined.  
- Acts as the **main analytical data model**.

### 🔸 Gold Layer
- Aggregated and **business-ready data** for dashboards.  
- *(In this project, the Power BI team handles this layer).*

---

## 🧱 Data Model (Silver Layer)

| **Table**          | **Description**                                          | **Key Columns**           |
| ------------------ | -------------------------------------------------------- | ------------------------- |
| **Traffic**        | Fact table containing traffic volume and vehicle counts. | `Traffic_id` (PK)         |
| **Road**           | Road information (type, junctions, length).              | `Road_id` (PK)            |
| **Region**         | Regional data including ONS codes.                       | `region_id` (PK)          |
| **LocalAuthority** | Details of local authorities.                            | `local_authority_id` (PK) |
| **Location**       | Coordinates and mapping of count points.                 | `Location_id` (PK)        |
| **Date**           | Date dimension (used for time-based analysis).           | `Date_id` (PK)            |

Each table is connected through **foreign keys** to form a **Star Schema** for optimized querying and BI analysis.

---

## 🔗 Relationships (Star Schema)

| **Foreign Key**              | **References**                      | **Purpose**                                      |
| ---------------------------- | ----------------------------------- | ------------------------------------------------ |
| `Traffic.Road_id`            | `Road.Road_id`                      | Links traffic data to specific road information. |
| `Traffic.Region_id`          | `Region.Region_id`                  | Associates each record with its region.          |
| `Traffic.Local_authority_id` | `LocalAuthority.Local_authority_id` | Connects traffic data to its managing authority. |
| `Traffic.Location_id`        | `Location.Location_id`              | Maps traffic counts to geographic coordinates.   |
| `Traffic.Date_id`            | `Date.Date_id`                      | Enables time-based analysis and trends.          |

> Together, these relationships create a **clean, analytical Star Schema**, ideal for Power BI or other reporting tools.

---

## 🧹 Data Cleaning Highlights

- 🧽 Removed duplicated rows from all tables.  
- 🔑 Added **Surrogate Keys (IDs)** for tables without natural unique identifiers.  
- 🔗 Ensured consistent relationships between `Traffic`, `Location`, `Region`, and `Date` tables.  
- 🧾 Verified referential integrity using SQL constraints.  
- 📁 Prepared clean CSVs ready for **BULK INSERT** into SQL Server.

---

## ⚙️ Tools and Technologies

| Tool | Purpose |
|------|----------|
| 🐍 **Python (Pandas, NumPy)** | Data cleaning and preparation |
| 🗄️ **SQL Server** | Database storage and schema design |
| 📊 **Power BI** | Visualization and reporting |
| 💻 **GitHub** | Version control and collaboration |

---

## 🚀 Project Workflow

1. **Data Extraction** – Loaded raw data into the **Bronze layer** using Python.  
2. **Transformation** – Cleaned, normalized, and created **surrogate keys** in the Silver layer.  
3. **Loading** – Used **BULK INSERT** to load cleaned CSVs into SQL Server.  
4. **Analysis** – Prepared the data for **Power BI** visualization (Gold layer).

---

## 📊 Star Schema Diagram

> *(Add your ERD image here, e.g. `/assets/ERD.png`)*

---

## 🧠 Key Learnings

- 🧩 **Multi-Layer Data Architecture (Bronze → Silver → Gold)**  
  Structured the pipeline for clarity, scalability, and maintainability.

- ⚡ **Efficient Handling of Large Datasets**  
  Optimized performance for loading, cleaning, and transforming CSVs.

- 🔑 **Use of Surrogate Keys for Data Consistency**  
  Ensured proper table relationships when natural keys were missing.

- 🧱 **Designing a BI-Ready Data Model**  
  Built a schema ready for Power BI and other analytical tools.

---

## 👥 Contributors

| Name | Role |
|------|------|
| **Osama Hegazy** | Data cleaning, SQL modeling, documentation |
| **Mohamed Nasr Aldin** | Data cleaning and transformation |
| **Sherif Gmal** | SQL design and documentation |
| **Ahmed Salama Soliman** | Dashboard and visualization layer |
| **Zakaria Yehia Ahmed** | Dashboard and visualization layer |
| **Sara Hisham Ahmed Mohamed** | Dashboard and visualization layer |
| **Yousef Ahmed Mohamed Ibrahiem** | Dashboard and visualization layer |
---

## 🏁 Next Steps

- ⚙️ Automate ETL using **Airflow** or **Azure Data Factory**.  
- 🔁 Implement **incremental data updates**.  
- 🧪 Add **monitoring and data quality checks**.

---
