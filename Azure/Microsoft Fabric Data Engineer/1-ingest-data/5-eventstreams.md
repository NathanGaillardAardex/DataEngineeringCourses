# Use real-time evenstreams in Microsoft Fabric

## Introduction 
- Eventstreams enable capturing and processing real-time events without coding.
- Set up event sources, destinations, and transformations using a no-code drag-and-drop interface.
- Supports multiple source connectors like Azure Event Hubs, Azure IoT Hub, Azure Storage, and Apache Kafka.
- Route data to multiple destinations for further analysis or processing.
- Scalable infrastructure automatically manages resources for efficient streaming ETL operations.
- This module teaches how to create eventstreams, ingest and transform real-time data, and route it to destinations.

## Components of eventstreams

- Microsoft Fabric eventstreams create pipelines to move events from multiple sources to various destinations.
- The visual editor allows drag-and-drop design of pipelines with sources, transformations, and destinations.
- Real-time monitoring of event data flow is available within the editor.
- Eventstreams automatically handle scaling, reliability, and security without requiring code or infrastructure management.

**Main components:**
- **Sources:** Origin of event data, such as Azure Event Hubs, sample data, or custom apps. Users can define data formats and consumer groups.
- **Transformations:** Enable filtering, joining, aggregating, grouping, and temporal windowing for data analysis within specific time frames.
- **Destinations:** Store transformed data in eventhouses, lakehouses, or redirect to other eventstreams or activators for further processing.

- The eventstream editing canvas provides tools to manage sources, destinations, view data flow, insights, and logs.

## Eventstream sources and destinations

- **Eventstreams** capture real-time data from sources and load it into destinations for processing and analysis.

### Eventstream sources
- **Azure Event Hub:** Streams events from Azure Event Hubs with configurable data formats and consumer groups.
- **Azure IoT Hub:** Connects and manages IoT devices for real-time data streaming.
- **Azure SQL Database CDC:** Tracks changes in SQL databases for near real-time data movement.
- **PostgreSQL Database CDC:** Captures snapshots and changes from PostgreSQL databases.
- **MySQL Database CDC:** Tracks changes and captures data from MySQL databases.
- **Azure Cosmos DB CDC:** Streams real-time data changes from Cosmos DB.
- **Google Cloud Pub/Sub:** Publishes and subscribes to event data streams.
- **Amazon Kinesis Data Streams:** Processes real-time streaming data.
- **Confluent Cloud Kafka:** Managed Kafka service for stream processing.
- **Fabric workspace events:** Captures events from Fabric workspace changes.
- **Azure Blob Storage events:** Streams blob creation, updates, and deletions.
- **Custom endpoint:** Sends data from custom apps via REST API or SDK.
- **Sample data:** Uses pre-built sample datasets like IoT, Retail, or Finance.

### Eventstream destinations
- **Eventhouse:** Streams data into KQL databases for querying with Kusto Query Language.
- **Lakehouse:** Stores events in Delta Lake format for data warehousing.
- **Custom endpoint:** Routes data to custom applications outside of Fabric.
- **Derived Stream:** Processed streams after transformations, ready for further routing.
- **Fabric Activator:** Triggers automated actions based on streaming data.

- **Multiple destinations** can be attached simultaneously without conflicts.

## Eventstream transformations

- **Eventstream editor** offers a drag-and-drop interface for building complex data processing workflows.

### Transformation types
- **Filter:** Filters events based on field values (e.g., is null, is not null).
- **Manage fields:** Adds, removes, renames, or changes data types of fields.
- **Aggregate:** Calculates sums, minimums, maximums, or averages over time; allows renaming and filtering of results.
- **Group by:** Aggregates events within time windows, supporting multiple fields and complex windowing.
- **Union:** Merges events from multiple streams with matching fields into one table.
- **Expand:** Converts array elements into individual rows.
- **Join:** Combines two streams based on matching conditions.

### Windowing functions
- Perform operations over time-based windows for analyzing streaming data.
  
**Window types:**
- **Tumbling windows:** Fixed, non-overlapping intervals (e.g., count events every 10 seconds).
- **Sliding windows:** Overlapping windows based on time (e.g., alert if an event occurs 3+ times in 10 seconds).
- **Session windows:** Variable intervals based on activity gaps (e.g., group events with less than 5-minute gaps).
- **Hopping windows:** Overlapping windows that refresh at set intervals (e.g., 10s window refreshing every 5s).
- **Snapshot windows:** Groups events with the same timestamp.

**Window parameters:**
- **Duration:** Defines the length of each window (e.g., 10 minutes).
- **Offset:** Shifts window intervals (e.g., start 2 minutes later).
- **Grouping key:** Columns to group by (e.g., sensor ID).
- **Aggregation functions:** Functions like count, sum, average, min/max, or custom logic.

# [Next](./6-eventhouse.md)