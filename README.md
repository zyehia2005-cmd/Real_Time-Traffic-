#🚦 Real-Time Traffic Data Engineering Project

🧩 Overview

This is an end-to-end data engineering project for UK Traffic Data.
The goal is to build a modern data pipeline that collects, cleans, transforms, and prepares data for analysis and visualization using a multi-layer architecture:
Bronze → Silver → Gold

The project ensures data quality, scalability, and analytical efficiency using Python, SQL Server, and Power BI.

=======================================================================================================================================================================
🏗️ Architecture

Raw Data  →  Bronze Layer  →  Silver Layer  →  Gold Layer  →  Power BI Dashboard

🔸 Bronze Layer

Raw ingestion layer.

Stores data as received from the source with minimal modification.

Data loaded using Python (Pandas).

🔸 Silver Layer

Cleaned and structured layer.

Includes normalized tables with proper Surrogate Keys (IDs) for relationships.

Duplicates removed, datatypes validated, and relationships defined.

Acts as the main analytical data model.

🔸 Gold Layer

Aggregated and business-ready data for dashboards.

(In this project, Power BI team handles this layer.)

======================================================================================================================================================================
🧱 Data Model (Silver Layer)

Table           	      Description	                                                    Key Columns
____________________________________________________________________________________________________________________
Traffic	          |    Fact table containing traffic volume and vehicle counts	 |    Traffic_id           (PK)
Road	            |    Road information (type, junctions, length)	               |    Road_id              (PK)
Region	          |    Regional data including ONS codes	                       |    region_id            (PK)
LocalAuthority    |    Details of local authorities	                             |    local_authority_id   (PK)
Location	        |    Coordinates and mapping of count points	                 |    Location_id          (PK)
Date	            |    Date dimension (used for time-based analysis)	           |    Date_id              (PK)
__________________|______________________________________________________________|__________________________________
Each table is linked through foreign keys to form a Star Schema.
======================================================================================================================================================================

🧹 Data Cleaning Highlights

-> Removed duplicated rows from all tables.

-> Added Surrogate Keys (IDs) for tables without natural unique identifiers.

-> Ensured consistent relationships between Traffic, Location, Region, and Date tables.

-> Verified referential integrity using SQL constraints.

-> Prepared clean CSVs ready for BULK INSERT into SQL Server.

======================================================================================================================================================================
⚙️ Tools and Technologies

Python (Pandas, NumPy) - for data cleaning and preparation

SQL Server - for database storage and schema design

Power BI - for visualization and reporting

GitHub - for version control and collaboration
======================================================================================================================================================================
🚀 Project Workflow

Data Extraction: Loaded raw data into the Bronze layer using Python.

Transformation: Cleaned, normalized, and created surrogate keys in Silver layer.

Loading: Used BULK INSERT to load the cleaned CSVs into SQL Server.

Analysis: Prepared the data for Power BI visualization (Gold layer).
======================================================================================================================================================================
📊 Star Schema Diagram

(Include an image or screenshot of your ERD here)
Example:
/assets/ERD.png
======================================================================================================================================================================
🧠 Key Learnings

Importance of multi-layer architecture (Bronze/Silver/Gold)

Handling large CSV data efficiently

Using surrogate keys to maintain relational integrity

Building a scalable and query-optimized model for BI tools
======================================================================================================================================================================
👥 Contributors

Osama Hegazy, Mohamed Nasr Aldin, Sherif Gmal – Data cleaning, SQL modelling, and documentation

Team Members – Power BI dashboards and visualization layer
======================================================================================================================================================================
🏁 Next Steps

Automate ETL using Airflow or Azure Data Factory

Implement incremental data updates

Add monitoring and data quality checks

