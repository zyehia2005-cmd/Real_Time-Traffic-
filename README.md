
# 🚦 Real-Time Traffic Data Engineering Project   

## 📚 Table of Contents
- [🧩 Overview](#-overview)
- [🏗️ Architecture](#-architecture)
- [🧱 Data Model (Silver Layer)](#-data-model-silver-layer)
- [🔗 Relationships (Star Schema)](#-relationships-star-schema)
- [🧹 Data Cleaning Highlights](#-data-cleaning-highlights)
- [⚙️ Tools and Technologies](#️-tools-and-technologies)
- [🚀 Project Workflow](#-project-workflow)
- [📊 Star Schema Diagram](#-star-schema-diagram)
- [📂 Scripts](#-scripts)
- [🖼 Assets](#-assets)
- [🧠 Key Learnings](#-key-learnings)
- [👥 Contributors](#-contributors)
- [🏁 Next Steps](#-next-steps)

---

## 🧩 Overview

This is an **end-to-end Data Engineering project** for **UK Traffic Data** built using the  
**Bronze → Silver → Gold** architecture with Python, SQL Server, and Power BI.

---

## 🏗️ Architecture

Pipeline Flow:

`Raw Data → Bronze Layer → Silver Layer → Gold Layer → Power BI`

### 📌 Architecture Diagram 

[![Architecture](Assets/Data%20Architecture.jpg)](Assets/Data%20Architecture.jpg)

### 📌 Workflow Diagram 

[![Workflow](Assets/Data%20Work%20Flow.jpg)](Assets/Data%20Work%20Flow.jpg)

---

## 🧱 Data Model (Silver Layer)

| Table | Description | Key Column |
|-------|-------------|------------|
| Traffic | Fact table | Traffic_id |
| Road | Road information | Road_id |
| Region | UK regions | Region_id |
| LocalAuthority | Local authority details | Local_authority_id |
| Location | Coordinates | Location_id |
| Date | Date dimension | Date_id |

---

## 🔗 Relationships (Star Schema)

| Foreign Key | References | Purpose |
|-------------|------------|----------|
| Traffic.Road_id | Road.Road_id | Road mapping |
| Traffic.Region_id | Region.Region_id | Region mapping |
| Traffic.Local_authority_id | LocalAuthority.Local_authority_id | Authority mapping |
| Traffic.Location_id | Location.Location_id | Geo mapping |
| Traffic.Date_id | Date.Date_id | Time dimension |

---

## 🧹 Data Cleaning Highlights

- Removed duplicates  
- Added surrogate keys  
- Validated datatypes  
- Ensured FK relationships  
- Prepared clean CSVs for SQL Server  

---

## ⚙️ Tools and Technologies

| Tool | Purpose |
|------|----------|
| Python | Data cleaning |
| SQL Server | Storage + schema |
| Power BI | Reporting |
| GitHub | Versioning |

---

## 🚀 Project Workflow

1. Import raw data → Bronze  
2. Clean + normalize → Silver  
3. Load to SQL Server  
4. Visualize in Power BI  

---

## 📊 Star Schema Diagram
![Star Schema](Assets/Star%20Schema.png)



---

## 📂 Scripts

- **Cleaning Notebook:**  
  [`Scripts/DEPI_Pro_Data_Cleaning_.ipynb`](Scripts/DEPI_Pro_Data_Cleaning_.ipynb)

- **Data Insertion:**  
  [`Scripts/Data Insertion`](Scripts/Data%20Insertion)

- **SQL Schema Design:**  
  [`Scripts/Schema Design .SQL`](Scripts/Schema%20Design%20.SQL)

---

## 🖼 Assets

- [`Assets/Data Architecture.jpg`](Assets/Data%20Architecture.jpg)  
- [`Assets/Data Work Flow.jpg`](Assets/Data%20Work%20Flow.jpg)  
- [`Assets/Star Schema.png`](Assets/Star%20Schema.png)

---

## 🧠 Key Learnings

- Multi-layer pipeline  
- Handling large datasets  
- Star schema modeling  
- BI-ready data structure  

---

## 👥 Contributors

| Name | Role |
|------|------|
| Osama Hegazy | SQL + Cleaning |
| Mohamed Nasr Aldin | Data cleaning |
| Sherif Gmal | SQL modeling |
| Ahmed Salama | Power BI |
| Zakaria Yehia | Power BI |
| Sara Hisham | Power BI |
| Yousef Ahmed | Power BI |

---

## 🏁 Next Steps

- Add Airflow / ADF  
- Add incremental refresh  
- Add monitoring  
