# Organize a Fabric lakehouse using medallion architecture design

## Introduction

- The **Fabric lakehouse** combines data lakes and data warehouses to manage and analyze diverse data sources.
- The **medallion architecture** is an industry standard for structuring lakehouse-based analytics.
- It uses a layered approach:
  - **Bronze layer:** Raw data ingestion.
  - **Silver layer:** Data refinement and cleansing.
  - **Gold layer:** Curated data for analytics and reporting.
- This module covers:
  - Building a medallion architecture in Fabric lakehouses.
  - Querying and reporting on data.
  - Best practices for **security** and **governance**.
- **Prerequisites:** Familiarity with Fabric lakehouse, basic SQL, and Power BI.

## Describe medallion architecture

- **Medallion architecture** is a data design pattern used in Fabric lakehouses built on **Delta Lake**, supporting ACID transactions.
- It organizes data into three layers to improve data quality and streamline analytics, often referred to as a **"multi-hop" architecture**.

### Layers of Medallion Architecture:
- **Bronze (Raw) Layer:**  
  - Landing zone for raw data in its original format (structured, semi-structured, or unstructured).  
  - No transformations applied.

- **Silver (Validated) Layer:**  
  - Data is refined and validated.  
  - Activities include cleaning (e.g., removing nulls, deduplication), merging, and ensuring consistency.  
  - Acts as a central repository for the organization.

- **Gold (Enriched) Layer:**  
  - Data is further refined and enriched for specific business or analytics needs.  
  - Includes aggregations (e.g., daily/hourly summaries) and enrichment with external data.  
  - Ready for use by analytics, data science, or MLOps teams.

### Customizing the Architecture:
- **Flexibility:** Additional layers (e.g., "raw" or "platinum") can be added based on organizational needs.  
- **Adaptable:** Compatible with existing data models, allowing for customized solutions.

### Moving Data Across Layers:
- **Data Transformation:**  
  - Modifying data structure or content.  
  - Tools: **Dataflows (Gen2)** (for simple models) and **Notebooks** (for complex transformations).

- **Data Orchestration:**  
  - Managing and automating data movement between layers.  
  - Tool: **Pipelines** (schedule-based or event-triggered workflows).

- Considerations when moving data:  
  - Data volume.  
  - Complexity of transformations.  
  - Frequency of data movement.  
  - Preferred tools and team expertise.

## Implement a medallion architecture in Fabric

### 1. Set Up the Foundation
- **Create a Fabric lakehouse** as the base for the medallion architecture.
- You can use:
  - A single lakehouse for multiple medallion architectures.
  - Separate lakehouses (even in different workspaces) based on use cases.

### 2. Design Your Architecture
- Define the layout with **Bronze**, **Silver**, and **Gold** layers:
  - **Bronze (Raw Layer):** Ingest raw data.
  - **Silver (Curated Layer):** Cleanse and validate data.
  - **Gold (Presentation Layer):** Apply transformations, model data in a **star schema**, and optimize for reporting.

| Question                          | Bronze                    | Silver                         | Gold                                           |
|-----------------------------------|---------------------------|---------------------------------|------------------------------------------------|
| **What happens in that layer?**   | Ingest raw data           | Cleanse and validate data      | Additional transformations and modeling        |
| **What tool is used?**            | Pipelines, dataflows, notebooks | Dataflows or notebooks  | SQL analytics endpoint or semantic model       |

### 3. Ingest Data into Bronze
- Use **Pipelines**, **Dataflows**, or **Notebooks** to ingest raw data.
- Store data in its original format without transformation.

### 4. Transform Data and Load to Silver
- Use **Dataflows** or **Notebooks** for data transformations.
- Focus on improving **data quality** and **consistency** (e.g., deduplication, validation).
- Avoid complex modeling at this stage.

### 5. Generate a Gold Layer
- Refine data for reporting and analytics:
  - Apply **dimensional modeling** (e.g., star schema).
  - Define **relationships**, **measures**, and key **metrics**.
- Gold layer options:
  - **Multiple gold layers** for different audiences (e.g., finance, sales, data science).
  - **Data Warehouse** as the gold layer if needed.
- Use **Dataflows** or **Notebooks** to load data into **Gold Delta tables**.
- Connect to the **SQL analytics endpoint** for querying and reporting.

### 6. Enable Downstream Consumption
- Share data using **workspace** or **item permissions**.
- Enable connections to the **SQL analytics endpoint** for reporting tools like **Power BI**.
- Optimize gold layer data for easy access by **analytics** and **data science teams**.

## Query and report on data in your Fabric lakehouse

### Querying Data
- **SQL analytics endpoint** allows teams to query data in the **gold layer** using **T-SQL**.
  - Supports querying **Delta tables** at any medallion layer.
  - Enables creating **functions**, **views**, and applying **SQL security**.
  - Operates in **read-only** mode—data modifications require **dataflows**, **notebooks**, or **pipelines**.
  - Can be connected to **third-party tools** for data exploration and reporting.

### Reporting with Power BI
- **Power BI semantic model** integrates directly with the Fabric lakehouse.
  - Uses **Direct Lake mode** to query data without import delays.
  - Caches frequently used data, ensuring **real-time updates** with high performance.
  - Automatically generates a **default semantic model** upon lakehouse creation, enabling immediate reporting.
  
### Tailoring Medallion Layers
- Customize **Gold layers** for specific audiences or domains:
  - Example: Separate Gold layers for **Finance**, **Sales**, or **Data Science** teams.
  - Tailored layers optimize **data processing** and **access** based on use cases.
  - Supports generating cleansed and properly formatted data for **third-party tools** or specific applications.

## Considerations for managing your lakehouse

### Secure Your Lakehouse
- **Permissions Management:**
  - **Workspace-level permissions:** Control access to all items within a workspace.
  - **Item-level permissions:** Grant access to specific items, useful for selective collaboration.

- **Layer-Specific Access Control:**
  - **Gold Layer:** Restrict to **read-only** access for most users to protect refined data.
  - **Silver Layer:** Define if users can build on validated data, balancing flexibility and security.
  - **Bronze Layer:** Restrict to **read-only** to prevent modifications to raw data.

- **Security Best Practices:**
  - Store medallion layers in **separate workspaces** for enhanced security and efficient capacity management.
  - Align sharing policies with organizational **security guidelines**.

### Continuous Integration and Continuous Delivery (CI/CD)
- **Key CI/CD Considerations:**
  - Implement **data quality checks**, **version control**, **automated deployments**, and **monitoring**.
  - Plan for **scalability**, **disaster recovery**, and **compliance**.
  - Ensure continuous **collaboration** and **improvement** in pipeline management.

- **Git Integration:**
  - Microsoft Fabric supports **native Git integration** for version control.
  - Enables data teams to:
    - **Back up** and **version** work.
    - Revert to previous stages.
    - Collaborate using **Git branches**.
    - Manage Fabric items with familiar source control tools.

- **CI/CD at the Gold Layer:**
  - Ensures **high-quality**, **validated**, and **reliable** data for consumption.
  - Automates data integration, transformations, and updates.
  - Improves **data accuracy**, speeds up **decision-making**, and supports **data-driven initiatives**.