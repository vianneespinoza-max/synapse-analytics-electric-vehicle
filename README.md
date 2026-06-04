# 🚗 Electric Vehicle Analytics with Azure Synapse Analytics

[![Azure Synapse](https://img.shields.io/badge/Azure_Synapse-0078D4?logo=microsoftazure&logoColor=white)](https://azure.microsoft.com/en-us/products/synapse-analytics)
[![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![Power BI](https://img.shields.io/badge/Power_BI-F2C811?logo=powerbi&logoColor=black)](https://powerbi.microsoft.com/)

## 📌 Project Overview

**End-to-end data engineering and analytics project on Azure Synapse Analytics.**

This project implements a complete **Lakehouse architecture** in Microsoft Azure, processing real-world electric vehicle (EV) registration data. The entire pipeline – from raw data ingestion in the **Bronze** layer to a highly optimized **Gold** layer – is fully orchestrated within Azure Synapse Analytics, culminating in an interactive **Power BI** dashboard.

The project covers:
*   **📥 Data Ingestion:** Load raw data from various file formats (CSV, JSON, TSV) into the Bronze layer.
*   **🔄 Data Transformation:** Clean, standardize, and model data in the Silver layer using Spark Notebooks and Serverless SQL.
*   **📈 Data Curation:** Build business-ready aggregations and KPIs in the Gold layer.
*   **☁️ Cloud Orchestration:** Automate all processes with Synapse Pipelines.
*   **📊 Visualization:** A Power BI dashboard connected directly to the Gold layer to visualize key metrics.

---

## 🛠️ Tech Stack

| Category | Technologies |
|----------|-------------|
| **Cloud Platform** | Microsoft Azure, Azure Synapse Analytics |
| **Data Processing** | Serverless SQL Pools, Spark Pools (PySpark) |
| **Orchestration** | Synapse Pipelines |
| **Data Lake** | Azure Data Lake Storage Gen2 |
| **Visualization** | Power BI |
| **Languages** | SQL, Python (PySpark) |

---

## 🏗️ Project Architecture (Medallion / Lakehouse)

The project follows the **Medallion architecture**, organizing data into three quality layers:

1.  **🥉 Bronze Layer (Raw Data):** Raw data is ingested into external tables directly from the Data Lake.
2.  **🥈 Silver Layer (Cleaned Data):** Data is cleaned and standardized. Complex types (e.g., JSON) are parsed. Data quality rules are applied.
3.  **🥇 Gold Layer (Aggregated Data):** Business-ready tables are created, containing aggregations and KPIs (e.g., registrations per year/month, count by vehicle type).

This architecture ensures data quality, reusability, and performance for analytical queries.

### 🔁 Data Flow Diagram

```mermaid
flowchart TD
    A[Raw Data Files<br>CSV, JSON, TSV] --> B[Azure Data Lake Storage Gen2]

    subgraph Azure Synapse Analytics Workspace
        B --> C[Bronze Layer<br>External Tables]
        C --> D{Data Transformation}
        D --> E[Spark Notebooks]
        D --> F[Serverless SQL]
        E & F --> G[Silver Layer<br>Cleaned & Enriched]
        G --> H[Gold Layer<br>Business Aggregations]
    end

    H --> I[Power BI Dashboard]
