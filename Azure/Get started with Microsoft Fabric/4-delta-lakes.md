# Work with Delta Lake tables in Microsoft Fabric

## Understand Delta Lake

Delta Lake is an open-source storage layer that brings relational database semantics to Spark-based data lake processing. In Microsoft Fabric, lakehouse tables are implemented as Delta tables, marked with the Δ icon, and use Parquet files along with a _delta_log folder to record transactional changes in JSON.

**Key Benefits:**
- **Relational Capabilities:** Supports full CRUD operations (create, read, update, delete) similar to traditional databases.
- **ACID Transactions:** Ensures atomicity, consistency, isolation, and durability, enabling reliable concurrent operations.
- **Data Versioning & Time Travel:** The transaction log maintains multiple versions of data, allowing users to query historical states.
- **Batch & Streaming Support:** Integrates with Spark Structured Streaming to handle both static and real-time data.
- **Interoperability:** Uses standard Parquet format, making it compatible with various analytics tools and SQL queries through Fabric's SQL analytics endpoint.

## Summary: Optimizing Delta Tables in Microsoft Fabric

### The Small File Problem
- **Spark processes data in parallel** across multiple worker nodes.
- **Parquet files are immutable**, meaning every update or delete creates new files.
- This leads to many small files, slowing down queries (**small file problem**).

### OptimizeWrite Function
- **OptimizeWrite** reduces the number of small files when writing data.
- Writes **fewer, larger files**, improving performance.
- Enabled by default in Microsoft Fabric but can be controlled:
  ```python
  spark.conf.set("spark.microsoft.delta.optimizeWrite.enabled", False)  # Disable
  spark.conf.set("spark.microsoft.delta.optimizeWrite.enabled", True)   # Enable
Can also be set in Table Properties or individual write commands.
### Optimize Command
Consolidates small Parquet files into larger ones after data loads.
Benefits:
Fewer, larger files
Better compression
Efficient data distribution
Can be run in Lakehouse Explorer or via SQL:
sql
Copy
Edit
OPTIMIZE my_table;
### V-Order Function
V-Order optimizes Parquet files for faster reads.
Default in Microsoft Fabric, improving read speed by 10%-50%.
Works with Power BI, SQL, and Spark.
Uses:
Sorting, row group distribution, dictionary encoding, compression.
Compatible with all Parquet engines.
Best for read-heavy scenarios. Can be disabled for write-heavy workloads.
Vacuum Command
Removes old Parquet files but retains transaction logs for time travel.
Required because updates & deletes create new files, leading to data accumulation.
Retention period determines how far back time travel is possible.
Default: 7 days (168 hours)
Cannot set a lower retention period.
Run VACUUM via SQL:
sql
Copy
Edit
VACUUM lakehouse2.products RETAIN 168 HOURS;
Previous runs can be checked using:
sql
Copy
Edit
DESCRIBE HISTORY lakehouse2.products;
Partitioning Delta Tables
Partitions group data into subfolders for better query performance.
Example: Partition sales data by year to skip irrelevant data.
Benefits:
Improves query efficiency via data skipping.

## Work with Delta Tables in Spark

### Using Spark SQL
- The **most common** way to interact with delta tables in Spark is via **SQL queries**.
- SQL can be embedded in PySpark or Scala using `spark.sql()`:
  ```python
  spark.sql("INSERT INTO products VALUES (1, 'Widget', 'Accessories', 2.99)")
  ```
- Use `%sql` magic command in a notebook:
  ```sql
  %%sql
  UPDATE products
  SET Price = 2.49 WHERE ProductId = 1;
  ```

### Using the Delta API
- When working with **delta files directly**, the **Delta Lake API** is useful.
- Create a `DeltaTable` instance from a delta file location:
  ```python
  from delta.tables import *
  from pyspark.sql.functions import *

  delta_path = "Files/mytable"
  deltaTable = DeltaTable.forPath(spark, delta_path)

  # Update price of all "Accessories" by reducing it by 10%
  deltaTable.update(
      condition = "Category == 'Accessories'",
      set = { "Price": "Price * 0.9" }
  )
  ```

### Using Time Travel for Table Versioning
- Delta tables **log all transactions**, enabling **time travel** (viewing past versions).
- View table modification history:
  ```sql
  %%sql
  DESCRIBE HISTORY products;
  ```
- Example output (columns omitted for brevity):

  | version | timestamp           | operation | operationParameters                         |
  |---------|---------------------|-----------|--------------------------------------------|
  | 2       | 2023-04-04T21:46:43Z | UPDATE    | {"predicate":"(ProductId = 1)"}           |
  | 1       | 2023-04-04T21:42:48Z | WRITE     | {"mode":"Append","partitionBy":"[]"}      |
  | 0       | 2023-04-04T20:04:23Z | CREATE    | {"isManaged":"true","partitionBy":"[]"}   |

- View history for an **external table** (by specifying folder path):
  ```sql
  %%sql
  DESCRIBE HISTORY 'Files/mytable';
  ```

### Retrieving Data from Specific Table Versions
- Read a **specific version** of a delta table:
  ```python
  df = spark.read.format("delta").option("versionAsOf", 0).load(delta_path)
  ```
- Read a table at a **specific timestamp**:
  ```python
  df = spark.read.format("delta").option("timestampAsOf", '2022-01-01').load(delta_path)
  ```

## Use Delta Tables with Streaming Data

### Spark Structured Streaming
- Spark enables **real-time data processing** using **Structured Streaming**.
- A **stream processing solution** typically:
  1. Reads a stream from a source.
  2. Processes and transforms the data.
  3. Writes results to a sink.
- Supported streaming sources:
  - **Network ports**
  - **Message brokers (Kafka, Azure Event Hubs)**
  - **File system locations**

### Using a Delta Table as a Streaming Source
- Delta tables can serve as both **streaming sources and sinks**.
- Example: Creating a Delta table to store incoming orders:
  ```sql
  %%sql
  CREATE TABLE orders_in (
      OrderID INT,
      OrderDate DATE,
      Customer STRING,
      Product STRING,
      Quantity INT,
      Price DECIMAL
  ) USING DELTA;
  ```
- Insert sample streaming data:
  ```sql
  %%sql
  INSERT INTO orders_in (OrderID, OrderDate, Customer, Product, Quantity, Price)
  VALUES
      (3001, '2024-09-01', 'Yang', 'Road Bike Red', 1, 1200),
      (3002, '2024-09-01', 'Carlson', 'Mountain Bike Silver', 1, 1500);
  ```
- Read data from the input table:
  ```python
  df = spark.read.format("delta").table("orders_in")
  display(df)
  ```
- Load a **streaming DataFrame** from the Delta table:
  ```python
  stream_df = spark.readStream.format("delta") \
      .option("ignoreChanges", "true") \
      .table("orders_in")
  ```
- Verify that the DataFrame is streaming:
  ```python
  stream_df.isStreaming
  ```

### Transforming the Data Stream
- Example: Filter out null prices and add new computed columns.
  ```python
  from pyspark.sql.functions import col, expr

  transformed_df = stream_df.filter(col("Price").isNotNull()) \
      .withColumn('IsBike', expr("INSTR(Product, 'Bike') > 0").cast('int')) \
      .withColumn('Total', expr("Quantity * Price").cast('decimal'))
  ```

### Using a Delta Table as a Streaming Sink
- Write the **transformed data stream** to a Delta table:
  ```python
  output_table_path = 'Tables/orders_processed'
  checkpointpath = 'Files/delta/checkpoint'

  deltastream = transformed_df.writeStream.format("delta") \
      .option("checkpointLocation", checkpointpath) \
      .start(output_table_path)

  print("Streaming to orders_processed...")
  ```
- Query the processed data:
  ```sql
  %%sql
  SELECT * FROM orders_processed ORDER BY OrderID;
  ```
- Stop the streaming process to reduce processing costs:
  ```python
  deltastream.stop()
  ```

### Key Takeaways
- **Delta tables can serve as both streaming sources and sinks.**
- **Structured Streaming enables real-time analytics** using Spark's DataFrame API.
- **Checkpoints** ensure stream processing **resumes from failure points**.
- **Transformations** can be applied to filter, compute, and enhance streaming data.

# [Next](./5-process-and-data-movement.md)