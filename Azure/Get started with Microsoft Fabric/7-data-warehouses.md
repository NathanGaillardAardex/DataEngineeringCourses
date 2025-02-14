# Get started with data warehouses in Microsoft Fabric
## Understand Data Warehouse Fundamentals

### Key Processes in Building a Data Warehouse
1. **Data Ingestion** – Moving data from source systems to the warehouse.
2. **Data Storage** – Storing data in a format optimized for analytics.
3. **Data Processing** – Transforming data into a consumable format.
4. **Data Analysis & Delivery** – Extracting insights and making data accessible.

### Microsoft Fabric's Data Warehouse Experience
- **Relational, fully managed, and scalable** warehouse supporting **T-SQL**.
- Stores and queries data in the **Lakehouse**.
- Supports **SQL-based queries and Spark-based processing**.
- Facilitates collaboration between **data engineers and analysts**.

### Data Warehouse Table Design

#### Fact Tables
- Contain **numerical data** for analysis (e.g., sales amounts, revenue).
- Typically have a **large number of rows**.
- Used for **aggregations and calculations**.

#### Dimension Tables
- Contain **descriptive data** providing context for fact tables.
- Typically have **fewer rows** but **detailed attributes**.
- Include:
  - **Surrogate Key** – System-generated unique ID.
  - **Alternate Key** – Business identifier (e.g., customer ID, product code).

### Special Types of Dimensions
- **Time Dimensions** – Enable analysis by **year, quarter, month, day**.
- **Slowly Changing Dimensions** – Track **historical changes** (e.g., price updates, address changes).

### Data Warehouse Schema Designs

#### **Star Schema**
- **Single fact table** connected to **multiple dimension tables**.
- Optimized for **fast queries** with minimal joins.
- Example: **Sales fact table linked to dimensions like Customer, Product, and Time**.

#### **Snowflake Schema**
- **Normalized dimensions** to reduce data redundancy.
- Requires **more joins** but **saves storage**.
- Example: **Product dimension split into separate Category and Supplier tables**.

### Key Takeaways
- **Data warehouses store structured data** optimized for analytics using **fact and dimension tables**.
- **Star schemas** prioritize query speed, while **snowflake schemas** enhance data integrity.
- **Microsoft Fabric provides a fully managed, SQL-compatible data warehouse** for efficient data processing and reporting.

## Understand Data Warehouses in Fabric

### Fabric Lakehouse vs. Data Warehouse
- **Lakehouse**: Stores raw data in files, supports **big data processing** with **Spark and SQL**.
- **Data Warehouse**: **Relational layer** on top of Lakehouse data, enabling **T-SQL queries, transformations, and analytics**.

### Data Ingestion Methods
- **Pipelines** and **Dataflows** for ETL processes.
- **Cross-database queries** to access data from multiple sources.
- **COPY INTO command** for loading data from external storage (e.g., Azure Blob).

### Table Management
- **Create tables** using **T-SQL** in Fabric UI or external SQL clients.
- **Clone tables** for **development, testing, recovery, and historical reporting** without data duplication.
- **Use staging tables** for **data cleansing, transformation, and validation** before inserting into fact/dimension tables.

### Data Warehouse Load Process
1. **Ingest new data** into the **Lakehouse** with cleansing if needed.
2. **Load data into staging tables** for preprocessing.
3. **Update dimension tables** with new or modified records.
4. **Insert fact table data** while referencing dimension surrogate keys.
5. **Optimize performance** by updating indexes and distribution statistics.

### Querying Lakehouse Data from the Warehouse
- **Cross-database querying** allows **direct access to Lakehouse data** without duplication.
- Facilitates seamless **SQL-based analytics** across **Lakehouse and Data Warehouse**.

### Key Takeaways
- **Fabric's Data Warehouse provides a structured relational layer** on top of **Lakehouse data** for T-SQL querying and transformations.
- **Efficient data ingestion, staging, and querying techniques** optimize performance.
- **Cross-database querying eliminates redundant data copies**, simplifying analysis.

## Query and Transform Data in Microsoft Fabric

### Querying Data in Fabric
- **Two ways to query data**:
  1. **SQL Query Editor** – Write **T-SQL queries** for precise data manipulation.
  2. **Visual Query Editor** – Drag-and-drop **no-code** experience for easy data transformation.
- Both editors allow you to create **tables, views, and stored procedures**.

### SQL Query Editor
- Provides **IntelliSense, code completion, syntax highlighting, and validation**.
- Similar to **SSMS and Azure Data Studio** for experienced T-SQL users.
- Example: **Creating a view** for Power BI reports.
  ```sql
  CREATE VIEW SalesSummary AS
  SELECT CustomerID, SUM(TotalAmount) AS TotalSales
  FROM Sales
  GROUP BY CustomerID;
  ```
- Supports **ad-hoc queries** and **complex transformations**.

### Visual Query Editor
- Similar to **Power Query Online**, offering **graphical transformations**.
- Steps:
  1. **Drag a table** onto the **canvas**.
  2. Use the **Transform menu** to add columns, filters, or aggregations.
  3. Use the **(+) button** to apply quick transformations.
- Ideal for **non-SQL users** who need to manipulate data visually.

### SQL Analytics Endpoint
- Allows connecting Fabric’s **data warehouse and Lakehouse** to **external tools**.
- Enables querying from **Power BI, Excel, and third-party BI tools**.

### Key Takeaways
- **SQL Query Editor** is best for **T-SQL users** needing precise data control.
- **Visual Query Editor** provides **no-code transformations** for easy data preparation.
- **SQL Analytics Endpoint** enables seamless **external tool connectivity** for reporting and analysis.

## Prepare Data for Analysis and Reporting in Microsoft Fabric

### Understanding Semantic Models
- A **semantic model** defines **relationships, aggregation rules, and calculations** for reports.
- Used in **Power BI** to generate insights from structured data.
- **Automatically synced** with the **Fabric data warehouse**.

### Building Relationships
- **Connect tables** in the semantic model using the **Model view**.
- Uses a **click-and-drag** interface to define relationships between **fact and dimension tables**.

### Creating Measures
- **Measures** are **calculated metrics** using **Data Analysis Expressions (DAX)**.
- Created in **Model view** using the **New measure** button.
- Example: **Month-over-month sales growth calculation**.

### Hiding Fields for Simplicity
- **Right-click on tables/columns** and select **Hide** to clean up the model.
- Hidden fields remain available but are not visible in reports.

### Default vs. Custom Semantic Models
- **Default Semantic Model**:
  - Created automatically when a **data warehouse is set up**.
  - Includes **all new tables from the Lakehouse**.
  - Maintained and optimized by **Fabric**.
- **Custom Semantic Models**:
  - Allows selecting **specific tables or views** for **more control**.
  - Useful for **tailored business reporting needs**.

### Visualizing Data
- Use **New Report** in Fabric to create **Power BI reports** directly from the data warehouse.
- Enables **real-time exploration** of data while refining transformations.

### Key Takeaways
- **Semantic models enable structured reporting**, ensuring **consistent business logic**.
- **Relationships and measures** refine data for **meaningful analysis**.
- **Fabric seamlessly integrates with Power BI**, streamlining **data visualization and insights generation**.

## Secure and Monitor Your Data Warehouse in Microsoft Fabric

### Security Features
- **Role-Based Access Control (RBAC)** – Restricts access based on user roles.
- **SSL Encryption** – Secures communication between the warehouse and clients.
- **Azure Storage Service Encryption** – Protects data in transit and at rest.
- **Azure Monitor & Log Analytics** – Tracks activity and audits data access.
- **Multifactor Authentication (MFA)** – Adds an extra layer of security.
- **Microsoft Entra ID Integration** – Manages user identities and access.

### Workspace Permissions
- **Workspaces** control access at a broad level.
- **Item Permissions** allow granular access control for specific warehouses.
- Key SQL permissions:
  - **Read** – Required for SQL connection.
  - **ReadData** – Allows reading from tables and views.
  - **ReadAll** – Grants access to raw Parquet files in OneLake.

### Monitoring Data Warehouse Activity
- **Dynamic Management Views (DMVs)** provide live query insights:
  - `sys.dm_exec_connections` – Shows active connections.
  - `sys.dm_exec_sessions` – Lists authenticated sessions.
  - `sys.dm_exec_requests` – Tracks active queries.

### Query Monitoring & Optimization
- Identify long-running queries:
  ```sql
  SELECT request_id, session_id, start_time, total_elapsed_time
  FROM sys.dm_exec_requests
  WHERE status = 'running'
  ORDER BY total_elapsed_time DESC;
  ```
- Find the user responsible for a long-running session:
  ```sql
  SELECT login_name
  FROM sys.dm_exec_sessions
  WHERE session_id = 'SESSION_ID';
  ```
- Terminate an inefficient query (Admin role required):
  ```sql
  KILL 'SESSION_ID';
  ```

### Key Takeaways
- **RBAC, encryption, and monitoring tools** ensure data security.
- **Workspace and item permissions** allow fine-grained access control.
- **DMVs help track active queries**, identify performance issues, and optimize execution.

# [Next](./8-real-time-intelligence.md)