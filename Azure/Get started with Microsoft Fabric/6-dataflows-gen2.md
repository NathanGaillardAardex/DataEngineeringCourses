# Ingest Data with Dataflows Gen2 in Microsoft Fabric
## Understand Dataflows Gen2 in Microsoft Fabric

### What is a Dataflow?
- **Cloud-based ETL tool** for extracting, transforming, and loading data.
- **Dataflows Gen2** allows connecting to multiple sources, applying transformations, and landing data in a **lakehouse** or other destinations.
- **Uses Power Query Online**, providing a visual interface for data transformation.

### How to Use Dataflows Gen2
- **ETL Approach**: Extract and transform data before loading it into a destination.
- **ELT Approach**: Load raw data first (e.g., into a lakehouse) and then transform it using Dataflows Gen2.
- **Integrates with Pipelines**:
  - Use a **Data Pipeline** for initial extraction and loading.
  - Use **Dataflows Gen2** to clean and transform the data.
  - Provide curated **semantic models** for business users and analysts.
- **Reusable & Partitioned Dataflows**:
  - **Reusable ETL logic** prevents redundant data source connections.
  - **Horizontal partitioning** allows analysts to create specialized data models.

### Benefits and Limitations

#### Benefits:
- Standardizes data, e.g., **consistent date dimensions**.
- **Enables self-service analytics** for business users.
- Improves **performance** by extracting data once and **reducing refresh time**.
- Simplifies data **integration** with a **low-code** approach.
- Ensures **data quality** by enabling transformation before loading.

#### Limitations:
- **Not a replacement for a data warehouse**.
- **No row-level security**.
- **Requires Fabric capacity workspace**.

### Key Takeaway
Dataflows Gen2 simplify ETL/ELT processes, making **data preparation, transformation, and integration easier** while improving reusability and performance.

## Explore Dataflows Gen2 in Microsoft Fabric

### Overview
- **Dataflows Gen2** provide a **low-to-no-code ETL solution** for data ingestion, transformation, and loading.
- Available in **Data Factory, Power BI workspace, and Lakehouse**.
- Uses **Power Query Online** for a **visual transformation interface**.

### Key Components of the Power Query Interface

#### 1. Power Query Ribbon
- Supports **various data source connectors**, including:
  - **Relational databases (cloud/on-prem)**
  - **Excel, SharePoint, Salesforce**
  - **Spark and Fabric Lakehouse**
- Provides transformation operations such as:
  - **Filter, Sort, Pivot, Unpivot**
  - **Merge, Append, Split**
  - **Rank and Percentage calculations**
  - **Top N, Bottom N selections**
- Manage **data source connections, parameters, and destinations**.

#### 2. Queries Pane
- Displays **connected data sources (queries)**.
- Queries become **tables** when loaded.
- Options:
  - **Duplicate** or **Reference** queries.
  - **Disable query loading** for temporary transformations.

#### 3. Diagram View
- **Graphical representation** of transformations.
- Shows **relationships between queries**.
- Displays **applied transformations as a flowchart**.

#### 4. Data Preview Pane
- Shows a **sample subset** of data.
- Allows:
  - **Dragging and dropping columns**.
  - **Right-click filtering and modifications**.
  - **Visualizing transformations before applying them**.

#### 5. Query Settings Pane
- Displays **Applied Steps** for each transformation.
- **Modify steps** using the gear icon or remove/reorder them.
- **Advanced Editor** allows direct M code modification.

### Data Destinations
- Dataflows Gen2 can land data into:
  - **Lakehouse**
  - **Warehouse**
  - **SQL Database**
  - **Azure SQL Database, Azure Data Explorer, Synapse Analytics**

### Key Takeaway
- **Dataflows Gen2 streamline data ingestion and transformation** with a **visual, code-optional** interface, enabling **efficient data preparation for analytics**.

## Integrate Dataflows Gen2 and Pipelines in Microsoft Fabric

### Overview
- **Dataflows Gen2** handle **data ingestion and transformation**.
- **Pipelines** orchestrate **additional operations** on transformed data.
- Combining both allows for **automated, scalable data workflows**.

### Key Pipeline Activities
- **Copy Data**
- **Incorporate Dataflow**
- **Add Notebook**
- **Get Metadata**
- **Execute Scripts or Stored Procedures**

### Benefits of Integration
- **Orchestrate multiple tasks** in a **specific order**.
- **Automate dataflow execution** via **scheduling or triggers**.
- **Enhance data processing** by adding scripts, stored procedures, or notebooks after transformation.
- **Reduce manual effort** in refreshing data, making workflows more efficient.

### Key Takeaway
- **Using Dataflows Gen2 within Pipelines enables automation, orchestration, and scalability for complex data processing workflows in Microsoft Fabric.**

# [Next](./7-data-warehouses.md)