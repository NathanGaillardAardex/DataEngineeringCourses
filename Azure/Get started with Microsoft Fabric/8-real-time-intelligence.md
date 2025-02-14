# Get started with Real-Time Intelligence in Microsoft Fabric
## Introduction 

### Two Common Data Analytics Patterns
1. **Batch Data Analytics** – Periodic data ingestion for **historical analysis** using **data warehouses or lakehouses**.
2. **Real-Time Data Analytics** – Continuous **stream processing** for **immediate insights and automated actions**.

### Lambda Architecture for Analytics
- **Combines batch and real-time processing**.
- **Batch layer** stores historical data.
- **Speed layer** processes real-time event streams.

### Microsoft Fabric's Real-Time Intelligence Capabilities
- Supports **both batch and real-time analytics** at scale.
- **Minimal coding required**, enabling **large-scale real-time solutions**.

### Core Topics Covered
- **Understanding real-time data analytics concepts**.
- **Exploring Microsoft Fabric's Real-Time Intelligence components**.
- **Ingesting real-time data using eventstreams**.
- **Analyzing data with eventhouse and KQL databases**.
- **Building real-time dashboards** for visualization.
- **Defining alerts and triggers using Activator**.

### Key Takeaways
- **Fabric enables real-time data ingestion, analysis, and automation**.
- **Eventstreaming and KQL databases** facilitate scalable real-time insights.
- **Dashboards and alerting systems** allow for **immediate decision-making**.

## What is Real-Time Data Analytics?

### Definition
- **Real-time data analytics** processes continuous **data streams** of events.
- Data sources include **social media feeds, IoT sensors, financial transactions, and environmental monitoring**.
- Enables **instant insights, automation, and historical trend analysis**.

### Use Cases
- **Live monitoring** of events for anomaly detection and operational efficiency.
- **Automated actions** based on sensor or event data (e.g., adjusting HVAC systems dynamically).
- **Historical insights** from streaming data for future planning (e.g., sentiment analysis in marketing).

### Key Characteristics of Real-Time Data Analytics
1. **Unbounded data streams** – Continuous flow of event data.
2. **Time-based records** – Events are timestamped for tracking and analysis.
3. **Temporal aggregation** – Data is grouped into time windows (e.g., per minute, per hour).
4. **Hybrid analytics** – Supports **real-time visualization and automation**, while also persisting data for historical analysis.

### Microsoft Fabric's Real-Time Intelligence
- **Minimal to no coding** required for implementing **real-time analytics**.
- **Integrated with Microsoft Fabric** for **seamless data ingestion, processing, and visualization**.
- Supports **real-time monitoring, automation, and long-term analytics** in a single ecosystem.

### Key Takeaways
- **Real-time analytics enables immediate insights and automated decision-making**.
- **Combines real-time processing with historical storage for comprehensive analysis**.
- **Microsoft Fabric provides an efficient, scalable platform for real-time intelligence**.

## Real-Time Intelligence in Microsoft Fabric

### Overview
- **Fabric's Real-Time Intelligence** is an **end-to-end streaming solution** for **real-time data analytics**.
- **Scalable from gigabytes to petabytes**, supporting diverse **data sources and formats**.
- **Ideal for IoT, log analytics, and event-driven processing** across industries like **manufacturing, oil & gas, and automotive**.

### Key Capabilities
1. **Eventstream** – Captures, transforms, and ingests real-time data.
2. **Eventhouse** – Stores real-time data in **KQL databases**.
3. **KQL Queryset** – Enables querying and analysis using **Kusto Query Language (KQL)**.
4. **Real-Time Dashboards** – Visualizes streaming data instantly.
5. **Activator Alerts** – Triggers automated actions based on real-time events.

### Microsoft Fabric Real-Time Hub
- **Centralized interface** for managing **real-time data sources**.
- Accessible via the **Real-Time icon** in the Fabric menu.
- Features include:
  - **Connecting to real-time data sources**.
  - **Creating and managing eventstreams**.
  - **Subscribing to Fabric and Azure event triggers**.
  - **Previewing and managing real-time data connections**.
  - **Creating real-time dashboards** from event streams.
  - **Sharing and endorsing real-time data across the organization**.

### Key Takeaways
- **Fabric's Real-Time Intelligence unifies real-time ingestion, storage, analysis, and visualization**.
- **Eventhouse and KQL provide scalable querying and analytics**.
- **Real-Time Hub simplifies data source management and automation**.

## Ingest and Transform Real-Time Data in Microsoft Fabric

### Eventstreams in Microsoft Fabric
- **Eventstreams** capture, transform, and load **real-time data** from various streaming sources.
- **Runs continuously**, processing data as it arrives.
- Defines **data ingestion sources, transformations, and destinations**.

### Supported Data Sources
- **External Services**: 
  - **Azure Event Hubs, Azure IoT Hubs, Apache Kafka, Change Data Capture (CDC)**, and more.
- **Fabric Events**:
  - Changes in **Fabric workspaces, OneLake data stores, Fabric jobs**.
- **Sample Data**:
  - Predefined datasets for **testing and exploring real-time scenarios**.

### Data Transformations in Eventstreams
1. **Filter** – Keeps or removes events based on conditions (e.g., **is null, is not null**).
2. **Manage Fields** – Add, remove, rename, or change **data types**.
3. **Aggregate** – Computes **Sum, Min, Max, Average** over a time period.
4. **Group By** – Aggregates events based on **field values and time windows**.
5. **Union** – Combines multiple streams into a single dataset.
6. **Expand** – Converts array values into **separate rows**.
7. **Join** – Merges **two event streams** based on a matching condition.

### Data Destinations
1. **Eventhouse** – Stores event data for **KQL-based queries and analysis**.
2. **Lakehouse** – Converts real-time data to **Delta Lake format** for storage.
3. **Derived Stream** – Redirects transformed data **to another eventstream**.
4. **Fabric Activator** – Automates actions **based on stream values**.
5. **Custom Endpoint** – Routes data to **external systems or applications**.

### Key Takeaways
- **Eventstreams enable real-time ingestion, transformation, and routing of event data**.
- **Transformations enhance streaming data by filtering, aggregating, and joining streams**.
- **Microsoft Fabric supports multiple destinations, including Eventhouse, Lakehouse, and external applications**.

## Store and Query Real-Time Data in Microsoft Fabric

### Eventhouses in Microsoft Fabric
- **Eventhouses** store **real-time data** ingested from eventstreams.
- Data is organized into **KQL databases** and queried using **Kusto Query Language (KQL)**.

### Key Components of an Eventhouse
1. **KQL Databases** – Optimized **real-time data stores** supporting:
   - **Tables**
   - **Stored functions**
   - **Materialized views**
   - **Shortcuts**
2. **KQL Querysets** – Collections of **KQL queries** to process data efficiently.

### Querying Data with KQL
- **KQL (Kusto Query Language)** is designed for **real-time analytics** and **time-based queries**.
- Example: Retrieve **10 rows** from a table:
  ```kql
  stock
  | take 10
  ```
- Example: Compute **average stock price per symbol** in the last 5 minutes:
  ```kql
  stock
  | where ["time"] > ago(5m)
  | summarize avgPrice = avg(todecimal(bidPrice)) by symbol
  | project symbol, avgPrice
  ```

### Querying Data with SQL
- Eventhouses **support SQL syntax** for users familiar with traditional databases.
- Example: Retrieve **10 rows** using SQL:
  ```sql
  SELECT TOP 10 * FROM stock;
  ```

### Using Copilot for Query Assistance
- **Copilot for Real-Time Intelligence** helps generate **KQL and SQL queries** using AI.
- Enhances **query efficiency and accessibility** for **real-time insights**.

### Key Takeaways
- **Eventhouses store and process real-time data** using **KQL databases**.
- **KQL enables efficient querying of large, time-based datasets**.
- **SQL compatibility and Copilot AI assist users in extracting insights quickly**.

## Visualize Real-Time Data in Microsoft Fabric

### Real-Time Dashboards
- **Dashboards display real-time insights** from eventhouse data.
- Each **tile** in a dashboard is powered by a **KQL query** that extracts live data.
- Provides an **interactive visual interface** for monitoring and exploration.

### Creating a Real-Time Dashboard
- Can be created:
  1. **In a workspace** with a configurable data source.
  2. **Directly from a KQL queryset** in an eventhouse.
- **Administrator must enable the feature** at the tenant level.

### Dashboard Features
- **Composed of tiles**, each based on a **KQL query expression**.
- **Customizable visualizations** (default is a table).
- Users can:
  - **Drill into data** for deeper insights.
  - **Filter and aggregate data interactively**.
  - **Modify visualization types**.

### Visualizing Real-Time Data with Power BI
- **Power BI seamlessly integrates** with Fabric for real-time reporting.
- Data from a **KQL database** can be used to build **Power BI reports**.
- Enables **advanced analytics, filtering, and dashboards**.

### Key Takeaways
- **Real-time dashboards** provide **instant insights** from streaming data.
- **KQL query-driven tiles** allow for **custom visualization and interaction**.
- **Power BI enhances real-time analytics** with **advanced reporting and visualization tools**.

## Automate Actions with Activator in Microsoft Fabric

### What is Activator?
- **Activator automates event-driven actions** based on real-time data.
- Enables **alerts, notifications, and automated processes** when specific conditions occur.
- Can trigger **emails, Spark-based data processing, or workflow execution**.

### Key Concepts of Activator
1. **Events** – Each **data record represents an event** occurring at a specific time.
2. **Objects** – Data within an event maps to **business entities** (e.g., sales order, sensor data).
3. **Properties** – Fields in the event **represent state attributes** (e.g., temperature, sales total).
4. **Rules** – Define **conditions** under which an **action is triggered** (e.g., alert if temperature > threshold).

### Use Cases for Activator
- **Marketing Automation** – Launch campaigns when **product sales drop**.
- **Inventory & Logistics** – Notify managers if **shipments are delayed**.
- **Customer Engagement** – Trigger offers when **account balances change**.
- **Operational Efficiency** – Flag **anomalies in website or app performance**.
- **Disaster Prevention** – Alert grocery stores when **freezer malfunctions**.
- **Data Processing Automation** – React to **failures in data workflows**.

### Key Takeaways
- **Activator enables real-time, rule-based automation** for data-driven actions.
- **Uses event properties to trigger alerts and workflows** based on defined conditions.
- **Applicable across industries for inventory, marketing, security, and system monitoring**.

# [Next](./9-data-science.md)