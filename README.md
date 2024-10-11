# Tokoyo-Olympic-Analysis-2021-Microsoft Azure
Tokyo Olympics 2021 Analysis Using Microrosft Azure platform

# Microsoft Azure Data Pipeline Project

## Overview

This project demonstrates the development of an end-to-end data pipeline leveraging the Microsoft Azure platform for data ingestion transformation, storage, and analytics. The pipeline processes Tokyo Olympic 2021 data, enabling analysis and visualization through a cloud-native approach. By utilizing Azure services such as Azure Data Factory, Data Lake Storage Gen 2, Databricks, Synapse Analytics, and Tableau, this project outlines a scalable data processing workflow. The goal is to provide actionable insights through interactive dashboards.


## Architecture

### 1. Data Source
- **Description:** Data sources represent the origin of the data, which can come from multiple types of structured and unstructured formats, such as CSV files, SQL databases, NoSQL databases, or third-party APIs that provide real-time data on Olympic events, athlete statistics, and country performance.
- **Role:** These data sources act as the entry point for raw data into the data pipeline. The variety of sources ensures that the pipeline can handle different types of data, including text, numbers, and other data formats such as JSON or XML.

### 2. Data Ingestion with Azure Data Factory
- **Azure Data Factory:** A cloud-based data integration service, Azure Data Factory enables the creation of automated workflows (pipelines) to orchestrate data movement and processing tasks. The ingestion process pulls data from different sources and brings it into the cloud environment.
- **Ingestion Process:**
    - **Copy Activity:** This allows the pipeline to copy data from on-premises or cloud sources to Azure Data Lake Storage Gen 2. It can work with different connectors for SQL, Oracle, Blob Storage, and more.
    - **Triggering:** The ingestion process can be scheduled to run at regular intervals (daily, weekly, or in real-time for streaming data) depending on the freshness requirements of the dataset.
- **Raw Data Store:** Once ingested, data is stored in its raw, unprocessed format within Azure Data Lake Storage Gen 2. This is the foundational storage layer where the original data remains untouched, allowing future reprocessing if needed.

### 3. Raw Data Store (Data Lake Gen 2)
- **Description:** Azure Data Lake Storage Gen 2 provides an enterprise-level, scalable, and secure storage solution optimized for large-scale analytics workloads. The service integrates with Azure Active Directory and offers fine-grained access controls for better data governance.
- **Role:** The raw data storage acts as a staging area where ingested data is stored temporarily before transformation. The unstructured data from sources such as JSON, XML, or flat files (CSV) remains stored in this repository. From here, data is moved for further processing.

### 4. Data Transformation with Azure Databricks
- **Azure Databricks:** Azure Databricks is an Apache Spark-based platform that provides an interactive workspace for data transformation, cleaning, and advanced analytics, optimized for large-scale data processing. It supports multiple languages, including Python, R, Scala, and SQL, allowing flexibility in how data is handled.
- **Transformation Process:**
    - **Cleaning:** Remove invalid or duplicate data records, and standardize formatting (e.g., consistent date formats, case standardization).
    - **Aggregation:** Data is aggregated to derive meaningful statistics, such as medal counts per country, event performance analysis, or athlete-wise metrics.
    - **Enrichment:** Additional external data (e.g., weather conditions, socio-economic factors) can be integrated into the existing dataset for more enriched analysis.
- **Role:** Databricks performs the heavy lifting of data transformation. It processes raw data and transforms it into a structured format ready for analytics. These transformations can be tracked and monitored in Databricks notebooks.

### 5. Transformed Data Store (Data Lake Gen 2)
- **Description:** Once data has undergone transformation and cleaning in Databricks, the output is written back to Azure Data Lake Storage Gen 2. This storage area contains structured and processed datasets that can now be used for analytical purposes.
- **Role:** The transformed data stored here serves as the foundation for all further analytical operations, including querying and reporting. It is optimized and structured to allow faster access and retrieval by analytical tools.

### 6. Analytics with Azure Synapse Analytics
- **Azure Synapse Analytics:** Azure Synapse Analytics brings together big data and data warehousing. It allows seamless querying and analytics on both structured and unstructured data. With Synapse SQL pools, it provides a powerful platform to perform large-scale data queries.
- **Role in the Pipeline:**
    - **Querying:** Run complex queries to derive insights from the processed Olympic data, such as identifying trends, generating rankings, and analyzing performance across different dimensions (e.g., country, sport, or athlete).
    - **Integration:** Synapse easily connects to Data Lake Gen 2, allowing direct querying of data stored there without needing to move it into separate data stores.
    - **Analytics Workspace:** Azure Synapse allows for the execution of SQL-based queries and integrates with Spark for distributed computing, enabling advanced analytics at scale.
- **Bridge between Big Data and Data Warehousing:** The data stored in Azure Synapse serves as the intermediary between raw big data and the structured, query-ready datasets that visualization tools will use for insights.

### 7. Dashboards and Reporting
- **Visualization Tools:** Power BI, Looker Studio, and Tableau are connected to the data through Azure Synapse Analytics. These tools offer powerful capabilities to visualize the processed data and provide dashboards for real-time monitoring and business intelligence.
- **Role:** These tools are used to create interactive dashboards and reports for data visualization and business insights.