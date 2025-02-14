# Get started with lakehouses in Microsoft Fabric

## Explore the Microsoft Fabric Lakehouse

### What is a Lakehouse?
A **lakehouse** is a **hybrid data architecture** combining the SQL-based analytics of a **relational warehouse** with the **scalability and flexibility** of a **data lake**. Built on **Delta format tables**, lakehouses enable structured and unstructured data processing while supporting **multiple analytics tools and programming languages**.

### Key Benefits:
- **Supports SQL and Spark engines** for large-scale data processing and machine learning.
- **Schema-on-read** approach allows defining schema dynamically instead of requiring predefined structures.
- **ACID transactions** via Delta Lake ensure **data integrity and consistency**.
- **Single location for data engineers, scientists, and analysts**, simplifying collaboration.
- **Cloud-native scalability, high availability, and disaster recovery**.

### Loading Data into a Lakehouse
Fabric lakehouses follow an **ETL (Extract, Transform, Load) process**:
- **Data ingestion**: Supports multiple sources, including **local files, databases, APIs**, and **external storage (Azure Data Lake, OneLake)** via **shortcuts**.
- **Data transformation**: Can be done using **Apache Spark notebooks** or **Dataflows Gen2** (Power Query-based for visual transformations).
- **Orchestration**: Use **Data Factory pipelines** to manage ETL workflows and load processed data into the lakehouse.

### Use Cases for a Fabric Lakehouse:
- **SQL-based analytics** for structured queries.
- **Machine learning model training** using Spark.
- **Real-time analytics** on streaming data.
- **Power BI integration** for business intelligence reporting.

### Securing a Lakehouse
Access is managed via:
- **Workspace roles** (for full collaboration within a workspace).
- **Item-level sharing** (for read-only access, such as Power BI users).
- **Governance and security**: Sensitivity labels and **Microsoft Purview integration** ensure compliance and controlled access.

By integrating **SQL, Spark, and scalable cloud-native storage**, **Microsoft Fabric lakehouses** provide a **powerful, unified** analytics solution.

## Work with Microsoft Fabric Lakehouses

### Creating and Exploring a Lakehouse
When you create a **Microsoft Fabric lakehouse**, three core data items are automatically generated:
1. **Lakehouse** – Contains **shortcuts, folders, files, and tables**.
2. **Semantic Model** – Provides an easy **data source for Power BI** reports.
3. **SQL Analytics Endpoint** – Allows **read-only SQL queries** on lakehouse tables.

Fabric lakehouses support **two interaction modes**:
- **Lakehouse Explorer** – Manage **tables, files, and folders**.
- **SQL Analytics Endpoint** – Query data using **SQL**.

### Ingesting Data into a Lakehouse
Data ingestion is the first step in the **ETL process**. Fabric provides multiple methods:
- **Upload** – Directly upload local files.
- **Dataflows Gen2** – Use **Power Query** for import and transformation.
- **Notebooks** – Ingest and process data using **Apache Spark**.
- **Data Factory Pipelines** – Automate **data ingestion and copying**.

Data can be loaded into **files or tables**, with **staging tables** recommended for structured transformations.

Additionally, **Spark job definitions** enable **batch and streaming processing** by submitting **compiled binaries (e.g., .jar files for Java)** to Spark clusters.

### Accessing Data with Shortcuts
**Shortcuts** allow **direct access to external data** without moving or copying it. Benefits include:
- **Seamless integration** with different **storage accounts or cloud providers**.
- **Cross-access between Fabric items**, such as **data warehouses, KQL databases, and other lakehouses**.
- **OneLake manages authentication**, using the caller’s identity for access control.

Shortcuts appear as **folders in the lakehouse**, enabling **Spark, SQL, Real-Time Intelligence, and Analysis Services** to query them directly.

By using **shortcuts, Spark jobs, and ETL pipelines**, **Microsoft Fabric lakehouses** provide a scalable and flexible solution for **enterprise data management**.

## Explore and Transform Data in a Lakehouse

### Transform and Load Data
Before data is fully usable, it often needs **transformation**. In a **lakehouse**, raw data can be **ingested first and transformed later** before loading it into structured tables. Fabric supports multiple **ETL tools** for transformation:
- **Notebooks** – Use **PySpark, SQL, or Scala** for coding-based transformations.
- **Dataflows Gen2** – Ideal for **Power BI/Excel users** using **PowerQuery** for visual transformations.
- **Pipelines** – Provide a **visual interface** for designing and orchestrating ETL workflows.

Once transformed, data can be **saved as a file or a Delta table**.

### Analyze and Visualize Data in a Lakehouse
After transformation, data is ready for **analysis and reporting**. Fabric offers multiple ways to interact with it:
- **Data Scientists** – Use **notebooks or Data Wrangler** to explore data and train ML models.
- **Report Developers** – Leverage the **semantic model** to create **Power BI reports**.
- **Analysts** – Use the **SQL Analytics Endpoint** to query, aggregate, and filter data.

By combining **lakehouse storage, SQL-based querying, and Power BI visualization**, Microsoft Fabric provides a **unified end-to-end analytics platform** for organizations.

# [Next](3-apache-spark.md)