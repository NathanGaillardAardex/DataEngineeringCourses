
# Explore non-relational data in Azure
## Explore Azure Storage for non-relational data
### Explore Azure blob storage
Azure Blob Storage is a cloud service for storing unstructured data as blobs, accessible via APIs, and organized in containers.

---

#### **Blob Types**:  
1. **Block Blobs**:  
   - Optimized for large, discrete binary objects.  
   - Max size: 190.7 TiB.  
   - Best for files that change infrequently.  

2. **Page Blobs**:  
   - Organized as 512-byte pages, supporting random read/write.  
   - Max size: 8 TiB.  
   - Used for virtual machine disk storage.  

3. **Append Blobs**:  
   - Optimized for appending data only.  
   - Max size: ~195 GB.  
   - Ideal for log data.  

---

#### **Access Tiers**:  
- **Hot Tier**: High-performance, frequently accessed data.  
- **Cool Tier**: Lower performance and cost for infrequently accessed data.  
- **Archive Tier**: Lowest cost, high latency for rarely accessed historical data.  

---

#### **Lifecycle Management**:  
- Automates transitions between tiers based on usage patterns.  
- Can delete outdated blobs after a defined period.  

---

Azure Blob Storage supports efficient data storage, offering scalability, cost optimization, and flexible access options for diverse workloads.

### Explore Azure Data Lake Storage Gen2
Azure Data Lake Storage provides hierarchical data storage designed for big data analytics and integrates with analytics systems like Azure Databricks.

---

#### **Generations**:  
1. **Gen1**:  
   - Standalone service for hierarchical file storage.  
   - Handles structured, semi-structured, and unstructured data.  

2. **Gen2**:  
   - Integrated with Azure Blob Storage, combining scalability and cost-effective storage tiers with hierarchical namespace capabilities.  
   - Compatible with major analytics systems.  

---

#### **Features**:  
- **Hierarchical Namespace**:  
  - Supports organizing blobs like a file system for analytical workloads.  
  - Must be enabled when creating or upgrading a storage account (irreversible).  
- **Integration**:  
  - Systems like Azure Databricks can mount Gen2 storage for processing large datasets.  
  - Microsoft Fabric tenants use OneLake, built on Azure Data Lake Gen2.  

---

Azure Data Lake Storage Gen2 offers a robust solution for scalable, hierarchical data management, ideal for big data analytics.

### Explore Microsoft OneLake in Fabric
**OneLake** is a unified, logical data lake automatically provisioned with every Microsoft Fabric tenant, built on Azure Data Lake Storage Gen2.  

---

#### **Key Benefits**:  
1. **Organization-Wide Collaboration**:  
   - Single data lake for structured and unstructured data across the organization.  
   - Eliminates the need for multiple data lakes, fostering a centralized analytics ecosystem.  

2. **Distributed Ownership**:  
   - Workspaces allow different teams to manage their data independently while adhering to governance policies.  

3. **Compatibility**:  
   - Built on **ADLS Gen2**, supports **Delta Parquet** format, and integrates with existing APIs and SDKs.  

4. **Ease of Use**:  
   - Simplified navigation through the OneLake file explorer, similar to OneDrive for data.  

---

OneLake centralizes and simplifies data storage, enabling efficient collaboration and compatibility with analytical tools.

### Explore Azure Files
Azure Files provides cloud-based network file shares, similar to traditional on-premises file shares, but with the scalability, availability, and reduced maintenance benefits of Azure.  

---

#### **Key Features**:  
1. **Scalability and Capacity**:  
   - Up to 100 TB of data per storage account.  
   - Supports up to 2000 concurrent connections per share.  
   - Max file size: 1 TB.  

2. **File Management**:  
   - Files can be uploaded via the Azure portal, **AzCopy** tool, or synchronized with **Azure File Sync** for local caching.  

3. **Performance Tiers**:  
   - **Standard Tier**: Cost-effective, hard disk-based storage.  
   - **Premium Tier**: High-throughput, SSD-based storage at higher cost.  

4. **File Sharing Protocols**:  
   - **SMB**: Cross-platform compatibility (Windows, Linux, macOS).  
   - **NFS**: For Linux/macOS, requires a premium storage account and virtual network configuration.  

---

#### **Benefits**:  
- Eliminates on-premises hardware costs and maintenance.  
- High availability and scalability for modern file-sharing needs.  
- Ideal for distributed teams or applications requiring shared file access.  

Azure Files simplifies and modernizes file sharing with secure, scalable, and flexible cloud-based storage solutions.

### Explore Azure Tables
Azure Table Storage is a NoSQL storage solution for semi-structured data, optimized for scalability and performance.

---

#### **Key Features**:  
1. **Semi-Structured Data**:  
   - Rows contain key/value pairs, with no enforced schema.  
   - Each row has a **partition key** and **row key** for unique identification.  
   - Columns can vary across rows, with no relational database features (e.g., foreign keys, views, stored procedures).  

2. **Denormalized Design**:  
   - Stores complete entity data in a single row.  
   - Example: Customer data, including names, multiple phone numbers, and addresses, all in one row.  

3. **Partitioning**:  
   - Groups rows with the same partition key for efficient data organization and scalability.  
   - Partitions grow or shrink independently based on data changes.  

4. **Performance**:  
   - Point queries use both **partition key** and **row key** for precise access.  
   - Range queries fetch blocks of rows within a partition, ordered by row key.  

---

#### **Benefits**:  
- High scalability for large datasets.  
- Fast query performance by narrowing searches with partition keys.  
- Flexible schema to accommodate varying data fields.  

Azure Table Storage is ideal for applications requiring high-speed, scalable access to semi-structured data without the complexity of relational database features.

## Explore fundamentals of Azure Cosmos DB
### Describe Azure Cosmos DB
Azure Cosmos DB is a globally distributed, multi-model database service with support for multiple APIs, enabling developers to work with data using familiar paradigms.

---

#### **Key Features**:  
1. **Multi-API Support**:  
   - Supports various APIs (e.g., SQL, MongoDB, Cassandra, Gremlin) to adapt to different programming needs.  
   - Abstracts internal data structures for flexibility.  

2. **Scalability**:  
   - Automatically manages partitioning for containers (up to 10 GB per partition).  
   - Indexes are created and maintained automatically.  
   - Scales to handle massive data volumes and global distribution with multi-region writes.  

3. **Performance**:  
   - Designed for low-latency reads/writes (single-millisecond latencies).  
   - Handles burst activity and high throughput efficiently.  

---

#### **Use Cases**:  
1. **IoT and Telematics**:  
   - Handles large-scale data ingestion for analytics and real-time processing.  

2. **Retail and Marketing**:  
   - Used for catalog storage, event sourcing, and order pipelines.  

3. **Gaming**:  
   - Powers personalized content, leaderboards, and handles massive request spikes during game launches.  

4. **Web and Mobile Applications**:  
   - Enables rich personalization, social integrations, and third-party service interactions.  

---

Azure Cosmos DB is a highly scalable and versatile database solution ideal for applications requiring high performance, global distribution, and diverse data modeling needs.

### Identify Azure Cosmos DB APIs
Azure Cosmos DB is a fully managed, globally distributed database that supports multiple APIs to handle diverse data models and workloads, both relational and non-relational.

---

#### **Supported APIs**:

1. **Azure Cosmos DB for NoSQL**:  
   - Data stored in JSON document format.  
   - SQL-based query syntax (e.g., `SELECT * FROM customers WHERE id = "123"`).  
   - Ideal for unstructured or semi-structured data in applications requiring high scalability.

2. **Azure Cosmos DB for MongoDB**:  
   - Uses MongoDB’s BSON format and query language (MQL).  
   - Example: `db.products.find({id: 123})`.  
   - Allows seamless use of MongoDB client libraries.  

3. **Azure Cosmos DB for PostgreSQL**:  
   - Distributed PostgreSQL with automatic sharding for scalability.  
   - Relational database model supporting SQL queries (e.g., `SELECT ProductName FROM Products WHERE ProductID = 123`).  
   - Start with a single-node setup and scale as needed.

4. **Azure Cosmos DB for Table**:  
   - Key-value storage similar to Azure Table Storage but with higher scalability.  
   - Example: Retrieve data via REST API:  
     `https://endpoint/Customers(PartitionKey='1',RowKey='124')`.  

5. **Azure Cosmos DB for Apache Cassandra**:  
   - Column-family storage structure compatible with Cassandra.  
   - SQL-like syntax for queries (e.g., `SELECT * FROM Employees WHERE ID = 2`).  
   - Ideal for systems with sparse or variable column structures.  

6. **Azure Cosmos DB for Apache Gremlin**:  
   - Stores data in a graph structure (vertices and edges).  
   - Gremlin syntax for graph operations (e.g., `g.addV('employee').property('id', '3')`).  
   - Best for applications requiring relationships and network analysis.

---

#### **Use Cases**:  
- **NoSQL**: Web, mobile apps, and IoT.  
- **MongoDB**: Open-source database migrations.  
- **PostgreSQL**: Relational workloads requiring scalability.  
- **Table**: Key-value storage with high throughput.  
- **Cassandra**: Scalable column-family systems.  
- **Gremlin**: Social networks, recommendation engines, and relationship analysis.

Azure Cosmos DB’s API flexibility enables developers to leverage familiar tools and paradigms for diverse workloads, ensuring scalability, performance, and reliability.

# [Next](4-explore-data-analytics-in-azure.md)
