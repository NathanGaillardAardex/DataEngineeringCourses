# Introduction to end-to-end analytics using Microsoft Fabric

## Explore End-to-End Analytics with Microsoft Fabric

### Overview
Microsoft Fabric simplifies scalable analytics by unifying multiple services into a single, easy-to-manage product. Instead of integrating different vendor solutions, Fabric provides persona-optimized tools within a shared user interface. 

Key benefits:
- Unified **Software-as-a-Service (SaaS)** solution.
- All data is stored in **OneLake**, a centralized, open-format repository.
- **Scalability, cost-effectiveness, and cloud accessibility** with automatic updates.

### Explore OneLake

#### OneLake: A Lake-Centric Architecture
OneLake acts as a **single, integrated data environment** for collaboration, eliminating the need to move or copy data between different systems. It enables:
- **OneCopy:** Read data without duplication.
- **Shortcuts:** References within OneLake to external storage locations, allowing seamless access to cloud data.

#### Key Features
- Built on **Azure Data Lake Storage (ADLS)**.
- Supports **Delta, Parquet, CSV, JSON, and more**.
- **Fabric Compute Engines** natively interact with OneLake.
- **Delta-Parquet Format**: Ensures interoperability across Fabric's analytical engines.

### Explore Fabric's Experiences

Fabric offers various **analytics experiences**, each designed for specific tasks while working together:

| Experience                   | Description |
|------------------------------|-------------|
| **Synapse Data Engineering** | Spark-based transformation and processing of large-scale data. |
| **Synapse Data Warehouse**   | High-performance SQL-based data warehousing. |
| **Synapse Data Science**     | Machine learning and model training using Azure ML and Spark. |
| **Synapse Real-Time Intelligence** | Real-time querying and analytics on large data streams. |
| **Data Factory**             | Integration of Power Query with Azure Data Factory for data movement and transformation. |
| **Power BI**                 | Business intelligence for reporting and decision-making. |

Fabric unifies these experiences within a **single platform** for seamless data processing and analysis.

### Explore Workspaces

#### What Are Workspaces?
- Logical containers that **organize and manage data assets**.
- Facilitate **collaboration, access control, and security**.
- Support **separation of development and production** environments.

#### Key Capabilities:
- **Access control**: Permissions ensure users access only what they need.
- **Compute management**: Optimize performance and cost.
- **Git integration**: Version control for tracking changes.
- **Data lineage & impact analysis**: Provides transparency into data flow and dependencies.

### Explore Security and Governance

Fabric ensures **centralized security and governance** via **OneLake**:
- **Centralized administration**: Manage permissions, data sources, and usage tracking.
- **Microsoft Purview Integration**: Uses **sensitivity labels** to classify and protect sensitive data.
- **Automation & APIs**: Fabric admin APIs and SDKs enable automation and system integration.

#### Admin Center Features:
- **User & group management**
- **Data access control**
- **Performance monitoring**
- **Integration with Microsoft Purview Information Protection**

### Conclusion

Microsoft Fabric streamlines end-to-end analytics by offering:
1. **A unified data ecosystem** (OneLake).
2. **Integrated analytics experiences** (Synapse, Data Factory, Power BI).
3. **Collaborative and secure workspaces**.
4. **Robust governance and compliance** through Microsoft Purview.

By consolidating analytics capabilities into a single platform, Fabric enhances productivity, scalability, and data-driven decision-making.

## Data Teams and Microsoft Fabric

### Overview
Microsoft Fabric provides a **unified data analytics platform**, enhancing collaboration between data professionals by eliminating **data silos** and reducing the need for multiple system integrations. This approach streamlines workflows and enables more efficient data management.

### Traditional Roles and Challenges

In traditional analytics workflows, **data engineers, analysts, and scientists** work in separate environments, leading to inefficiencies:

#### Challenges:
- **Data Engineers**: Process and curate large datasets but require extensive communication with analysts.
- **Data Analysts**: Spend significant time on downstream transformations to prepare data for Power BI, often lacking **direct data context**.
- **Data Scientists**: Struggle with integrating data science techniques due to **complex, fragmented systems**.
- **Collaboration Issues**: Misinterpretations and delays due to the separation of responsibilities.

### Evolution of Collaborative Workflows

Microsoft Fabric improves data workflows by integrating **data engineering, analysis, and science** within a single **SaaS platform**, reducing redundancies and streamlining processes.

#### Key Improvements:
- **Data Engineers**:
  - Ingest, transform, and load data into **OneLake**.
  - Use **pipelines** and **medallion architectures** to simplify data processing.
  
- **Data Analysts**:
  - Gain better context and streamline transformations **upstream**.
  - Leverage **Data Factory** and **DirectLake mode** for direct data access.
  
- **Data Scientists**:
  - Integrate **native data science techniques** more seamlessly.
  - Use **Power BI interactive reporting** for data insights.
  
- **Analytics Engineers**:
  - Bridge the gap between **data engineering and data analysis**.
  - Ensure **data quality** and enable **self-service analytics**.

- **Low-to-No-Code Users & Citizen Developers**:
  - Discover curated data through **OneLake Hub**.
  - Process and analyze data independently without **duplicating efforts**.

### Conclusion

Microsoft Fabric **redefines collaboration** in data teams by:
1. **Unifying tools** to eliminate redundant workflows.
2. **Enhancing direct access** to data for analysts and scientists.
3. **Simplifying data pipelines** with OneLake and Data Factory.
4. **Empowering non-technical users** to work with data independently.

By centralizing data processes, Fabric accelerates analytics development and improves data-informed decision-making across roles.

## Enable and Use Microsoft Fabric

### Enable Microsoft Fabric
To use Fabric, an admin must enable it in **Power BI Admin Center** under **Tenant Settings**. Required roles:
- **Fabric admin**
- **Power Platform admin**
- **Microsoft 365 admin**

Admins can enable Fabric for **all users** or **specific groups**. A **free trial** is available for exploration.

### Create Workspaces
Workspaces are collaborative environments for managing **lakehouses, warehouses, and reports** stored in **OneLake**.

#### Key Settings:
- **License Type** (Trial, Fabric Capacity)
- **OneDrive & Azure Data Lake Storage Integration**
- **Git for Version Control**
- **Spark Workload Configuration**

Access control is managed via **workspace roles**.

### Discover Data with OneLake Data Hub
OneLake Hub helps users **find and connect** to shared data sources. Key features:
- **Filter by domains, workspaces, and item types**
- **Explore My Data, Endorsed Data, and Favorites**
- **Keyword-based search for faster discovery**

### Create Items in Fabric
Users can create **lakehouses, dataflows, pipelines, and reports** from the **Create menu** in Power BI.

### Fabric Workloads
Fabric integrates multiple workloads in a **unified SaaS platform**:
- **Data Engineering** (ETL, transformations)
- **Data Factory** (Pipelines, integrations)
- **Data Science** (ML & AI analytics)
- **Data Warehousing** (SQL analytics)
- **Real-Time Intelligence** (Streaming data)
- **Power BI** (BI & visualization)

### Why Fabric?
Fabric **combines Power BI, Azure Synapse, and Data Factory** into a **single platform**, enabling **seamless collaboration and analytics** without requiring **Azure access**.

# [Next](2-lakehouse.md)
