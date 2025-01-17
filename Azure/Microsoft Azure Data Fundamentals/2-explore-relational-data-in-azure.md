
# Explore relational data in Azure
## Explore fundamental relational data concepts
### Introduction
- **Early Challenges**: Early computing systems used unique data structures, making data access inefficient and hard to maintain.  
- **Relational Model**: Solves these issues with a standard for representing and querying data, using tables for structured, intuitive, and efficient storage.  
- **Applications**: Used across industries for tasks like inventory tracking, ecommerce, and customer data management.  
- **Module Focus**: Covers relational database characteristics and data structures.

### Understand relational data
- **Entity Representation**: Real-world entities (e.g., customers, products, orders) are modeled as tables, with rows representing instances and columns representing attributes.  
- **Structured Data**: Tables are structured with consistent columns, though some may allow NULL values for optional data (e.g., middle names).  
- **Datatypes**: Columns store specific datatypes (e.g., text for emails, decimals for prices, integers for quantities, date/time for order dates), with ANSI standards ensuring compatibility across most database systems.

### Understand normalization
- **Purpose**: Minimizes data duplication and enforces data integrity in database schema design.  
- **Core Principles**:  
  - Each entity is stored in its own table.  
  - Attributes are separated into individual columns.  
  - Rows are uniquely identified using primary keys.  
  - Foreign keys link related entities.  
- **Benefits**:  
  - Eliminates duplication (e.g., updating a customer's address in one place).  
  - Ensures appropriate data types for attributes (e.g., decimal for prices, integer for quantities).  
  - Enhances query granularity (e.g., filtering customers by city).  
- **Key Mechanisms**:  
  - **Primary Keys**: Unique identifiers for rows.  
  - **Foreign Keys**: Reference primary keys of related entities, enabling relational integrity.  
  - **Composite Keys**: Unique combinations of multiple columns, as seen in line items with OrderNo and ItemNo.  

### Explore SQL
- **Purpose**: SQL (Structured Query Language) is used to manage and query relational databases, with standardized syntax and database-specific dialects like T-SQL, pgSQL, and PL/SQL.
#### **SQL Statement Types**:  

1. **Data Definition Language (DDL)**:  
   - **CREATE**: Create database objects (e.g., tables, views).  
   - **ALTER**: Modify existing objects.  
   - **DROP**: Delete objects (irreversible without backup).  

2. **Data Control Language (DCL)**:  
   - **GRANT**: Allow permissions (e.g., SELECT, INSERT).  
   - **DENY**: Restrict permissions.  
   - **REVOKE**: Remove granted permissions.  

3. **Data Manipulation Language (DML)**:  
   - **SELECT**: Query rows from tables, optionally using filters (e.g., `WHERE`) and sorting (`ORDER BY`).  
   - **INSERT**: Add new rows to tables.  
   - **UPDATE**: Modify existing rows; must use `WHERE` to avoid unintended updates.  
   - **DELETE**: Remove rows; omitting `WHERE` deletes all rows.  

#### **Additional Features**:  
- **Joins**: Combine data across tables using relationships (e.g., primary/foreign keys).  
- **Data Types**: Common types include `INT`, `DECIMAL`, and `VARCHAR`.  
- **Warnings**: Careful usage of `DELETE` and `UPDATE` without `WHERE` to prevent accidental data loss.  

#### **Example**: Query to join tables:  
```sql
SELECT o.OrderNo, o.OrderDate, c.Address, c.City
FROM Order AS o
JOIN Customer AS c
ON o.Customer = c.ID;
```  

SQL is foundational for database operations across various management systems like SQL Server, PostgreSQL, and Oracle.

### Describe database objects
- **Views**:  
  - Virtual tables based on a `SELECT` query.  
  - Simplify access to data across multiple tables (e.g., delivery details from `Order` and `Customer`).  
  - Usable like a table for queries and filtering.  

- **Stored Procedures**:  
  - Encapsulate SQL statements for reusable programmatic actions.  
  - Can include parameters for flexibility (e.g., renaming a product by ID).  
  - Executed with commands like `EXEC ProcedureName`.  

- **Indexes**:  
  - Optimized structures for faster data lookup, like a book index.  
  - Built on specific columns (e.g., product names or prices).  
  - Improve query performance for large tables but consume storage and slow down insert/update/delete operations.  

Indexes, views, and stored procedures enhance relational databases by optimizing data organization, simplifying operations, and improving query performance.

## Explore relational database services in Azure
### Describe Azure SQL services and capabilities
Azure SQL is a family of Microsoft SQL Server-based database services offering different levels of management and scalability for diverse use cases.

---

#### **1. SQL Server on Azure Virtual Machines (IaaS)**  
- **Overview**: Full SQL Server installation on Azure VMs; suitable for "lift-and-shift" migrations.  
- **Features**:  
  - Full control over OS and SQL Server configurations.  
  - Ideal for hybrid deployments and applications needing OS-level features.  
  - Scalable by resizing VM resources.  
- **Use Cases**:  
  - Migrate on-premises SQL Server with minimal changes.  
  - Development and testing of traditional SQL Server applications.  

---

#### **2. Azure SQL Managed Instance (PaaS)**  
- **Overview**: Near 100% SQL Server compatibility with automated maintenance.  
- **Features**:  
  - Supports multiple databases with automated backups and updates.  
  - Compatible with advanced SQL Server features like linked servers and Service Broker.  
  - Integrated with Azure services (e.g., Azure Key Vault, Microsoft Entra ID).  
- **Use Cases**:  
  - Migrating on-premises systems requiring minimal adjustments.  
  - Applications leveraging SQL Server-specific features.  

---

#### **3. Azure SQL Database (PaaS)**  
- **Overview**: Fully managed cloud database, optimized for scalability and high availability.  
- **Deployment Options**:  
  - **Single Database**: Independent, scalable databases with serverless configurations available.  
  - **Elastic Pool**: Resource sharing among multiple databases to optimize cost and performance.  
- **Features**:  
  - Automatic updates, high availability (99.995%), and point-in-time restores.  
  - Advanced threat protection and auditing for enhanced security.  
- **Use Cases**:  
  - New cloud applications with modern design requirements.  
  - Systems with variable workloads needing dynamic scalability.  

---

#### **4. Azure SQL Edge (IoT-focused)**  
- **Overview**: Optimized for IoT scenarios requiring streaming and time-series data processing.  

---

#### **Business Benefits**  
- **Scalability**: Adjust resources as needed without manual upgrades.  
- **Security**: Encryption, threat detection, and auditing ensure compliance and protect data.  
- **Reliability**: High availability guarantees with disaster recovery options.  
- **Management**: Automated patching, backups, and monitoring reduce administrative overhead.  

Azure SQL services provide tailored solutions for diverse needs, ranging from legacy migrations to modern, scalable cloud applications.  

### Describe Azure services for open-source databases
### Azure Data Services for MySQL, MariaDB, and PostgreSQL Summary  
Azure provides managed PaaS implementations for popular relational database systems, enabling fast migration from on-premises to the cloud with minimal application changes.

---

#### **MySQL**  
- **Overview**: Open-source database, commonly used in LAMP stack applications. Available in Community (free), Standard, and Enterprise editions.  
- **Azure Features**:  
  - High availability, automatic backups (35-day point-in-time restore), and SSL security.  
  - Scalable, pay-as-you-go model without managing hardware or updates.  
- **Use Case**: Web applications requiring a scalable, cost-effective relational database.  

---

#### **MariaDB**  
- **Overview**: Derived from MySQL, optimized for performance and temporal data (queries on historical data).  
- **Azure Features**:  
  - Built-in high availability and scalability.  
  - Enterprise-grade security and minimal administrative overhead.  
- **Use Case**: Applications needing high performance with historical data tracking.  

---

#### **PostgreSQL**  
- **Overview**: Hybrid relational-object database supporting custom data types, extensibility, and geometric data.  
- **Azure Features**:  
  - High availability with failure detection and failover.  
  - Flexible Server option allows advanced control and cost optimization.  
  - Query performance tracking via `query_store.qs_view`.  
- **Limitations**: Some on-premises extensions and server-focused functionality not available.  
- **Use Case**: Advanced analytics, applications requiring custom data types, or scalable relational databases.  

---

#### **Shared Benefits of Azure Database Services**  
- High availability, automated maintenance, and backups.  
- Pay-as-you-go pricing with easy scalability.  
- Enterprise-grade security for data at rest and in motion.  
- Minimal administrative overhead for simplified database management.  

Azure Database for MySQL, MariaDB, and PostgreSQL provides robust, scalable, and secure cloud solutions for diverse application requirements.

# [Next](3-explore-non-relational-data-in-azure.md)