# Use Apache Spark in Microsoft Fabric

## Prepare to Use Apache Spark in Microsoft Fabric

### Overview of Apache Spark
Apache Spark is a **distributed data processing framework** designed for **large-scale analytics**. It divides computations across multiple nodes in a **Spark pool**, improving performance and scalability. Spark supports various languages, including **PySpark (Python), Spark SQL, Scala, Java, and Spark R**, with **PySpark and Spark SQL** being the most commonly used.

### Spark Pools in Microsoft Fabric
A **Spark pool** consists of:
- **Head Node**: Coordinates distributed processes via a **driver program**.
- **Worker Nodes**: Execute tasks in parallel for high-speed processing.

Microsoft Fabric provides a **starter Spark pool** in each workspace with minimal setup, and users can configure **custom pools** to optimize performance and cost. Administrators can **enable autoscaling, dynamic allocation, and node customization**.

### Spark Runtimes and Environments
Fabric supports multiple **Spark runtimes**, allowing users to define environments with **specific runtime versions, libraries, and configuration settings**. Custom environments can include:
- **Pre-installed and custom Python libraries** (from **PyPI** or uploaded packages).
- **Custom Spark configurations** to optimize execution.
- **Dedicated Spark pools** for processing.

### Optimizations and Advanced Settings
- **Native Execution Engine**: Enhances query performance by running Spark operations directly on **lakehouse infrastructure**.
- **High Concurrency Mode**: Allows multiple users to share **Spark sessions** efficiently without variable conflicts.
- **Automatic MLflow Logging**: Fabric integrates **MLflow** for implicit **experiment tracking** and model management.

### Administration and Security
Fabric admins can manage **Spark settings at the capacity level**, allowing control over **Spark pool configurations, security, and resource allocation**.

By leveraging **Spark pools, configurable environments, and performance optimizations**, Microsoft Fabric enables **scalable, efficient big data processing**.

## Run Spark Code in Microsoft Fabric

### Notebooks: Interactive Data Exploration
- **Notebooks** allow users to **write, execute, and visualize Spark code** interactively.
- They support **multiple languages** (PySpark, Spark SQL, Scala) and combine **text, images, and code** for collaboration.
- Each notebook consists of **cells** that execute **code or markdown-formatted content** with immediate feedback.

### Spark Job Definition: Automated Processing
- **Spark jobs** automate **data ingestion and transformation**.
- A **Spark Job Definition** specifies:
  - **The script to run** (e.g., Python, Scala).
  - **Reference files** (e.g., supporting Python functions).
  - **Lakehouse integration** for accessing and processing data.
- Jobs can be **run on-demand or scheduled** for **batch processing**.

By using **notebooks for interactive exploration** and **Spark jobs for automation**, Microsoft Fabric provides a **flexible and scalable environment** for big data analytics.

## Work with Data in a Spark DataFrame

Spark DataFrames are the primary structure for handling structured data in Spark,
built on top of resilient distributed datasets (RDDs) and optimized for distributed processing.
They provide an API similar to Pandas but are designed to work efficiently in a clustered environment.

DataFrames can be created by loading data from various sources, such as CSV files,
where Spark can either infer the schema automatically or use a user-defined schema.
For example, in a PySpark notebook you can load a CSV file like this:

%%pyspark
df = spark.read.load('Files/data/products.csv', format='csv', header=True)
display(df.limit(10))

Similarly, Scala code can load data with:

%%spark
val df = spark.read.format("csv").option("header", "true").load("Files/data/products.csv")
display(df.limit(10))

Specifying an explicit schema using a StructType improves performance and ensures
accurate data type mapping, especially when headers are missing.

Once loaded, DataFrames allow for easy data manipulation.
You can select columns, filter rows, and chain transformations.
For instance, to select specific columns you might write:

pricelist_df = df.select("ProductID", "ListPrice")

To filter data based on conditions and select a subset of rows:

bikes_df = df.select("ProductName", "Category", "ListPrice") \
            .where((df["Category"] == "Mountain Bikes") | (df["Category"] == "Road Bikes"))
display(bikes_df)

Grouping and aggregation are equally straightforward.
For example, to count the number of products in each category:

counts_df = df.groupBy("Category").count()
display(counts_df)

After transforming data, saving the DataFrame in an efficient format like Parquet is common.
Partitioning the output by a column, such as "Category", optimizes future queries:

bikes_df.write.partitionBy("Category").mode("overwrite").parquet("Files/bike_data")

This creates a folder structure with subfolders for each partition, such as:
- Category=Mountain Bikes
- Category=Road Bikes

Loading partitioned data is simple; you can read only the required partition:

road_bikes_df = spark.read.parquet('Files/bike_data/Category=Road Bikes')
display(road_bikes_df.limit(5))

In summary, Spark DataFrames enable scalable and efficient data processing
by supporting robust ingestion, transformation, and storage operations,
making them indispensable for large-scale analytics.

## Visualize Data in a Spark Notebook

### Using Built-in Notebook Charts
Microsoft Fabric **Spark notebooks** provide basic **charting capabilities** directly in the UI. By default, query results are displayed as a **table**, but users can **switch to a chart view** for quick visualization. Chart properties allow basic **customization**, making it easy to summarize and interpret data visually.

### Using Python Graphics Libraries
For **more control over formatting and customization**, Python graphics libraries like **Matplotlib** and **Seaborn** can be used to generate visualizations. These libraries allow **inline rendering** in notebooks, combining **code, data manipulation, and commentary**.

### Example: Creating a Bar Chart with Matplotlib
The following **PySpark** code aggregates product data and visualizes it using **Matplotlib**:

```python
from matplotlib import pyplot as plt

# Convert Spark DataFrame to Pandas
data = spark.sql("SELECT Category, COUNT(ProductID) AS ProductCount \
                  FROM products \
                  GROUP BY Category \
                  ORDER BY Category").toPandas()

# Clear plot area
plt.clf()
fig = plt.figure(figsize=(12,8))

# Create a bar plot
plt.bar(x=data['Category'], height=data['ProductCount'], color='orange')

# Customize chart properties
plt.title('Product Counts by Category')
plt.xlabel('Category')
plt.ylabel('Products')
plt.grid(color='#95a5a6', linestyle='--', linewidth=2, axis='y', alpha=0.7)
plt.xticks(rotation=70)

# Display the chart
plt.show()
```

# [Next](4-delta-lakes.md)