# Tokyo Olympic Analysis 2021 - Microsoft Azure Data Pipeline Project

## Overview

This project demonstrates the development of an end-to-end data pipeline leveraging the Microsoft Azure platform for data ingestion, transformation, storage, and analytics. The pipeline processes Tokyo Olympic 2021 data, enabling analysis and visualization through a cloud-native approach. By utilizing Azure services such as Azure Data Factory, Data Lake Storage Gen 2, Databricks, Synapse Analytics, and visualization tools, this project outlines a scalable data processing workflow. The goal is to provide actionable insights through interactive dashboards.

<img width="600" alt="Azure Data Pipeline Flow" src="Images/Azure Data Pipeline Flow.png">

## Table of Contents

1. [Architecture](#architecture)
2. [How It Works](#how-it-works)
3. [Prerequisites](#prerequisites)
4. [Setup and Deployment](#setup-and-deployment)
5. [Data Sources](#data-sources)
6. [Data Transformation](#data-transformation)
7. [Analytics and Visualization](#analytics-and-visualization)
8. [Conclusion](#conclusion)
9. [Contributing](#contributing)

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

## How It Works

1. **Data Ingestion:**
    - Data from various sources (CSV files, APIs) is ingested using Azure Data Factory.
    - The raw data is stored in Azure Data Lake Gen 2 in its native format for processing.


    <img width="600" alt="Data Ingestion using APIs" src="Images/Data Ingestion.png">


2. **Data Transformation:**
    - Azure Databricks is used to transform the raw data through cleansing, filtering, and aggregation.
    - Additional enrichment of the dataset occurs here, preparing the data for advanced analytics.


    <img width="600" alt="Azure Databricks - Data Transformation" src="Images/Azure Databricks - Data Transformation.png">


3. **Data Storage:**
    - The transformed data is saved back into Data Lake Gen 2, creating a structured dataset ready for analysis.


    <img width="600" alt="Data Storage" src="Images/Data Storage.png">


4. **Data Analytics:**
    - Azure Synapse Analytics is used to query and analyze the transformed data. Complex SQL queries are run to gain insights into Olympic performances, trends, and statistics.

5. **Data Visualization:**
    - Visualization tools like Power BI, Looker Studio, or Tableau connect to Azure Synapse Analytics, enabling interactive reports and dashboards that provide rich insights from the data.


## Prerequisites

- **Azure Subscription:** Required to deploy Azure services such as Data Factory, Databricks, and Synapse Analytics.
- **Data Sources:** Set up the necessary data sources, such as CSV files, databases, or APIs.
- **Visualization Tools:** Install and configure Power BI, Looker Studio, or Tableau to connect to your Azure environment.

## Setup and Deployment

1. **Provision Azure Services:**
   - Set up Azure Data Factory, Data Lake Gen 2, Azure Databricks, and Synapse Analytics in your Azure account.

2. **Data Ingestion:**
   - Use Azure Data Factory to create pipelines that ingest data from source systems into Data Lake Gen 2.

3. **Develope Databricks Notebooks:**
   - Create and execute Databricks notebooks to perform data transformations and connect to the raw data in Data Lake Gen 2.

4. **Configure Synapse Analytics:**
   - Set up Azure Synapse Analytics to query the transformed data and perform analytical tasks.

5. **Create Dashboards:**
   - Use Power BI, Looker Studio, or Tableau to create interactive visualizations based on the analysis performed in Synapse Analytics.

## Data Sources

This project utilizes various data sources related to the Tokyo 2021 Olympics, including:

- Athlete information
- Event results
- Medal counts
- Country participation data

The data is primarily stored in CSV format and ingested into the Azure ecosystem for processing.

## Data Transformation

Data transformation is a crucial step in our pipeline. Here's a sample of how we connect to our data lake using Azure Databricks:

```python:Tokyo Olympic Transformation.ipynb
configs = {
    "fs.azure.account.auth.type": "OAuth",
    "fs.azure.account.oauth.provider.type": "org.apache.hadoop.fs.azurebfs.oauth2.ClientCredsTokenProvider",
    "fs.azure.account.oauth2.client.id": "<your-client-id>",
    "fs.azure.account.oauth2.client.secret": '<your-client-secret>',
    "fs.azure.account.oauth2.client.endpoint": "https://login.microsoftonline.com/<your-tenant-id>/oauth2/token"
}

dbutils.fs.mount(
    source = "abfss://tokyo-olympic-data@tokyoolympicdatarohida.dfs.core.windows.net",
    mount_point = "/mnt/tokyoolympic",
    extra_configs = configs
)
```

After mounting the data, we perform various transformations including:
- Data cleaning and normalization
- Aggregating medal counts by country
- Calculating performance metrics for athletes and teams

## Analytics and Visualization

The transformed data is analyzed using Azure Synapse Analytics, allowing for complex queries and insights generation. Visualizations are created using tools like Power BI, Looker Studio, or Tableau, providing interactive dashboards for stakeholders to explore the Olympic data.

## Conclusion

This project showcases a robust and scalable data pipeline leveraging Azure's cloud ecosystem to handle the ingestion, transformation, and visualization of Tokyo Olympic 2021 data. Through the implementation of this pipeline, we have demonstrated:

1. Efficient data ingestion from various sources using Azure Data Factory.
2. Scalable data storage solutions with Azure Data Lake Storage Gen 2.
3. Powerful data transformation capabilities using Azure Databricks.
4. Advanced analytics and querying with Azure Synapse Analytics.
5. Insightful visualizations and dashboards using tools like Power BI, Looker Studio, or Tableau.

The architecture we've developed enables efficient handling of big data while offering valuable insights through analytics and reporting tools. This pipeline is not only suitable for Olympic data analysis but is also adaptable to various scenarios, supporting data-driven decision-making across different domains.

By leveraging cloud-native services, we've created a solution that is both scalable and maintainable, capable of handling large volumes of data and complex analytical requirements. This project serves as a template for building similar data pipelines, showcasing the power and flexibility of the Microsoft Azure ecosystem in solving real-world data challenges.

As data continues to grow in volume and importance, solutions like this will become increasingly vital for organizations looking to derive actionable insights from their data assets. This project stands as a testament to the possibilities that emerge when combining cloud computing, big data, and analytics in a cohesive and well-architected solution.

## Contributing

Contributions to this project are welcome. Please fork the repository and submit a pull request with your proposed changes.
