# [Get started with Microsoft Fabric](https://learn.microsoft.com/en-us/training/paths/get-started-fabric/)
## Summary
Microsoft Fabric is a unified SaaS platform that integrates data engineering, data science, and business intelligence, eliminating silos through **OneLake**. It enables seamless collaboration, scalable data processing with **Apache Spark**, and structured analytics via **lakehouses** and **data warehouses**. **Delta Lake** ensures ACID compliance, while **Pipelines** and **Dataflows Gen2** automate data movement. **Real-time intelligence** processes streaming data with **eventstreams** and **KQL databases**. Machine learning is streamlined with **MLflow** and **PREDICT functions**. **Governance and security** are managed via **RBAC** and automated monitoring. Fabric simplifies analytics with low-code tools, AI-driven insights, and deep **Power BI** integration.
## **1. [Introduction to end-to-end analytics using Microsoft Fabric](1-end-to-end-analytics.md)**
- **Microsoft Fabric unifies data analytics** by integrating data engineering, data science, and business intelligence into a **single SaaS platform**, eliminating data silos and streamlining workflows with **OneLake** as a centralized data repository.
- **Fabric enhances collaboration** by allowing data engineers, analysts, and scientists to work together seamlessly, providing **direct access to shared data**, simplifying **ETL processes**, and enabling **self-service analytics** for business users.
- **Fabric is easy to enable and manage** through the **Power BI Admin Center**, with configurable **workspaces, security settings, and workload management**, supporting **version control, real-time insights, and governance via Microsoft Purview**.

## **2. [Get started with lakehouses in Microsoft Fabric](2-data-science.md)**
- **Microsoft Fabric lakehouses unify data lakes and warehouses**, offering **scalable storage, SQL-based querying, and Spark-powered transformations**. They support **structured and unstructured data** with **ACID-compliant Delta tables** for consistency.
- **Data ingestion and transformation are flexible**, allowing **direct uploads, Power Query (Dataflows Gen2), Apache Spark notebooks, and Data Factory pipelines**. Shortcuts enable seamless **external data access** without duplication.
- **Lakehouses integrate deeply with Power BI and analytics tools**, enabling **machine learning, SQL-based querying, real-time analytics, and dashboard reporting**, making them a **versatile choice for enterprise data solutions**.

## **3. [Use Apache Spark in Microsoft Fabric](3-apache-spark.md)**
- **Distributed Processing with Spark in Fabric:** Apache Spark in Microsoft Fabric uses Spark pools (head and worker nodes) and supports multiple languages (e.g., PySpark, Spark SQL, Scala) along with customizable runtimes and environments, enabling scalable and efficient big data analytics.
- **Flexible Code Execution:** Users can run Spark code interactively in notebooks for real-time data exploration and visualization or automate ETL processes using Spark job definitions, integrating seamlessly with Fabric lakehouses.
- **Robust Data Manipulation and Visualization:** Spark DataFrames allow for efficient data loading, transformation (selection, filtering, grouping, partitioning), and saving (e.g., in Parquet), while built-in charting or external libraries like Matplotlib enable comprehensive inline data visualization.

## **4. [Work with Delta Lake tables in Microsoft Fabric](4-delta-lake.md)**
- **Delta Lake in Microsoft Fabric**: Delta Lake enhances Spark-based data lakes with ACID transactions, full CRUD support, time travel, and seamless batch and streaming data processing using the Parquet format.
- **Optimizing Delta Tables**: Use **OptimizeWrite** to prevent small file issues, **OPTIMIZE** for file consolidation, **V-Order** for faster reads, **VACUUM** to remove old data files, and **partitioning** for efficient query performance.
- **Delta Tables with Spark and Streaming**: Work with **Spark SQL** or the **Delta API** for CRUD operations, enable **time travel** for historical queries, and use **Structured Streaming** to continuously process real-time data, transforming and storing it in Delta tables.

## **5. [Orchestrate processes and data movement with Microsoft Fabric](5-process-and-data-movement.md)**
- **Microsoft Fabric Pipelines** enable **data movement, transformation, and orchestration** through a graphical interface with activities for control flow and data processing.
- **Copy Data Activity & Templates** streamline **data ingestion** from various sources, supporting **predefined templates** for rapid development and customization.
- **Monitoring & Execution** allow for **interactive or scheduled runs**, with **detailed run history and execution tracking** to optimize and troubleshoot pipeline processes.

## **6. [Ingest Data with Dataflows Gen2 in Microsoft Fabric](6-dataflows-gen2.md)**
- **Dataflows Gen2 streamline ETL/ELT processes** by providing a **visual, low-code interface** for data ingestion, transformation, and integration with Power Query Online.
- **Pipelines and Dataflows Gen2 work together** to automate workflows, schedule data processing, and orchestrate additional activities like script execution and metadata extraction.
- **Key benefits include improved data consistency, self-service analytics, and reduced data refresh time**, though Dataflows Gen2 require Fabric capacity and do not replace data warehouses.

## **7. [Get started with data warehouses in Microsoft Fabric](7-data-warehouses.md)**
- **Microsoft Fabric's Data Warehouse** combines relational and big data capabilities, enabling **structured analytics, T-SQL querying, and semantic modeling** for efficient reporting.
- **Data preparation involves relationships, measures, and transformations**, using **SQL Query Editor, Visual Query Editor, and Power BI integration** for interactive analysis.
- **Security and monitoring features include RBAC, encryption, and dynamic management views (DMVs)** to ensure **data protection, access control, and performance optimization**.

## **8. [Get started with Real-Time Intelligence in Microsoft Fabric](8-real-time-intelligence.md)**
- **Microsoft Fabric Real-Time Intelligence** enables seamless ingestion, transformation, and querying of streaming data using **eventstreams**, **eventhouses**, and **KQL databases** for large-scale analytics.  
- **Real-time dashboards** and **Power BI integration** provide interactive visualizations, while **Activator automates actions** based on real-time conditions, improving decision-making and operational efficiency.  
- **Low-code, scalable architecture** supports IoT, financial transactions, and log analytics, with **Copilot AI assisting in writing KQL and SQL queries** for faster data exploration.

## **9. [Get started with data science in Microsoft Fabric](9-data-science.md)**
- **Microsoft Fabric streamlines data science workflows** by integrating data ingestion, exploration, transformation, and machine learning within a **unified SaaS platform**. It supports **low-code and code-first approaches** for scalable data processing.
- **MLflow integration enables experiment tracking**, allowing data scientists to log, compare, and refine model training runs efficiently. **Fabric lakehouses** provide centralized storage for structured and unstructured data, ensuring accessibility and reproducibility.
- **Model scoring and predictions** are seamlessly integrated with the **PREDICT function**, allowing real-time and batch inference. Predictions can be stored in **lakehouses** and visualized in **Power BI** for actionable business insights.

## **10. [Administer a Microsoft Fabric environment](10-administration.md)**
- Fabric administration involves managing security, governance, monitoring, and optimization using tools like the Fabric Admin Portal, Microsoft 365 Admin Center, PowerShell, and REST APIs.
- Admins ensure secure access control through Role-Based Access Control (RBAC), enforce governance with endorsement, scanner APIs, and data lineage tracking, and optimize performance with monitoring tools.
- Automation via PowerShell and APIs helps streamline management, while proper license allocation and workspace permissions enhance security and cost efficiency.