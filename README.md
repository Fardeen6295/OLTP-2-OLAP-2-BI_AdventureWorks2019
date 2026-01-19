# Azure Hybrid Data Lakehouse Implementation

This is a complete solution of Many Business Data Situation where they have data on On Prem SQL Server and they want to build a Data Warehouse but at the same time want the cost to be as low as possible. This Solution Load data incrementally via Synapse Data Ingestion, Transform the Data In Notebooks with Pyspark and then Create Lake House Database.

* Designed a scalable ETL pipeline migrating OLTP data from On-Prem SQL Server to Azure Data Lake Gen2 using Azure Data Factory and Self-Hosted Integration Runtime (SHIR).
* Implemented Medallion Architecture (Bronze/Silver/Gold) using Azure Databricks (PySpark) to clean and transform raw data.
* Engineered complex SCD Type 2 (Slowly Changing Dimensions) logic to track historical changes in Master Data, ensuring 100% referential integrity.
* Optimized storage costs and query performance by utilizing Synapse Serverless SQL Pools and Parquet/Delta formats.
* Developed interactive Power BI Dashboards with Incremental Refresh policies to visualize Sales Performance and Commission Efficiency.

<br />

#### This is the End Result of the Project, After Completing the Data Engineering in Azure and Data Anslysis in Power BI and UI Design in FIgma, this is the outcome of all work. A Enterprise Grade Dashboard built on Lakehouse Architecture
<br />
<img width="1898" height="1019" alt="Screenshot 2026-01-16 152411" src="https://github.com/user-attachments/assets/ef2691a3-14d6-4c59-989c-932f3c1eb3b4" />
<br />


#### This is the Parent Pipelone which is built on MEDALLION Architecture
<br />
<img width="1400" height="986" alt="Screenshot 2026-01-19 153036" src="https://github.com/user-attachments/assets/7fc9a7c8-0b4b-4bd6-8a70-4705d464cdb3" />
<br />


#### This is the Bronze Layer Ingesting 67 Tables from On-Prem SQL Server Database to Azure Cloud Data Lake in Parquet format Incrementally with metadata approach and SHIR along with Java Runtime

<br />
<img width="1555" height="924" alt="Screenshot 2026-01-12 154637" src="https://github.com/user-attachments/assets/ddf4997e-38bf-4244-a7e6-b3a07b7f61c2" />
<br />

#### I used Notebook to Transform Bronze Layer Data and Upsert that Processed data in Lake Database of Synapse Server SQL Pool, this layer always perocess new and modified data cause bronze layer is transient in nature

<br />
<img width="1033" height="902" alt="Screenshot 2026-01-12 154648" src="https://github.com/user-attachments/assets/c8c28b3a-871d-414c-b50a-448cfb1e16b3" />
<br />

#### This is the Gold Layer which creates the Star Schema Dimentional Data Model which is designed for the Business Requirement which is currently focused on Sales person performance but can be used to create other business purpose as well like marketing, Products, Vendors etc, but currently it is only build in terms of Sales Person Performance and Commission Calculation for Variable Pay. We Have one notebook for each table of the Dimentional Data Model

<br />
<img width="1369" height="921" alt="Screenshot 2026-01-12 154658" src="https://github.com/user-attachments/assets/8f2c4a83-1af5-4c5a-96de-380a19905dab" />
<br />

#### Once we had the Dimentional Data Model Warehouse ready, We can use Serverless SQL Endpoint to connect to the Lake database tables which are basically metadata layer in top of actual delta lake table sitting in data lake. The advantange of it are 
* Cost way cheaper as copared to Dedicated SQL Pool as storage cost is very high whether you use it or not.
* It is based on Lakehouse Architecture hence cost of storage is very cheap
* Performance and Behaviour is exactly like SQL Database, thanks to Delta lake tables and delta_log
* You Only pay for the Query you do that is $5/Per TB of Data Processed. 

<br />
<img width="591" height="644" alt="image" src="https://github.com/user-attachments/assets/3e3dc88e-a1d1-47a4-b219-474f85f71f3f" />
<br />


#### After All these Data Engineering work is done, we move to Data Analysis Work with Power BI and DAX. Below is the Link for PBIX file for your reference.
* https://drive.google.com/drive/u/1/folders/1MMvDNeYqz5Py0Qm_Gb00S-rsGXDBP0e0

<br />

#### We use DAX to create the skeleton of Dashboard and check its resulta and cross verify the number with SQL queries in azure to make sure that numbers are correct and reliable.
<br />
<img width="1910" height="1070" alt="Screenshot 2026-01-15 234802" src="https://github.com/user-attachments/assets/9e6118d4-d016-4109-aa34-55126d2ec80b" />
<br />

### I architected an end-to-end Hybrid Data Lakehouse solution using Azure Synapse, Azure Data Factory, Azure Data Lake Store Gen2, Delta Lake and used Power BI, DAX, Figma for Metrics creations and Reporting result to Business for data orientated actions.

# Thnak You, If you came so Far.

