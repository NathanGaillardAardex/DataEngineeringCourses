# Work with real-time data in a Microsoft Fabric eventhouse

## Get started with an eventhouse

- **Eventhouse** requires a workspace with Fabric capacity supporting Real-Time Intelligence.
- Contains one or more **KQL databases** for managing data with tables, stored procedures, and materialized views.
- Data can be imported from static sources (e.g., local files, OneLake, Azure Storage) or real-time sources (e.g., Azure Event Hubs, Fabric eventstreams).
- **OneLake integration** allows enabling data access at the database or table level.

### Querying with KQL
- **Kusto Query Language (KQL)** is used to query tables, offering intuitive and concise syntax.
- Supports both **KQL** and a subset of **SQL**, but KQL is preferred for simplicity, performance, and integration with Microsoft services.
  
**KQL vs. SQL examples:**
- Retrieve all data:  
  - KQL: `Automotive`  
  - SQL: `SELECT * FROM Automotive`
  
- Filter data:  
  - KQL:  
    ```
    Automotive
    | where fare_amount > 20
    | project trip_id, pickup_datetime, fare_amount
    ```
  - SQL:  
    `SELECT trip_id, pickup_datetime, fare_amount FROM Automotive WHERE fare_amount > 20`

- Group and aggregate:  
  - KQL:  
    ```
    Automotive
    | summarize trip_count = count() by vendor_id
    | project vendor_id, trip_count
    ```
  - SQL:  
    `SELECT vendor_id, COUNT(*) AS trip_count FROM Automotive GROUP BY vendor_id`

### Visualization and AI Assistance
- KQL Querysets support visualizing query results directly as charts.
- **Copilot for Real-Time Intelligence** assists with KQL queries by generating code based on user questions, enhancing query development efficiency.

## Use KQL effectively

- **KQL databases** in eventhouses are optimized for handling large real-time data streams.
- Optimize queries by filtering data and limiting returned results to improve performance and avoid exceeding data limits.

### Best practices for KQL:
- **Filter columns:** Use `project` to select only necessary columns.  
  ```kql
  Automotive
  | project trip_id, vendor_id, pickup_datetime, fare_amount
  ```

- **Filter rows:** Use `where` to filter rows based on conditions.  
  Example: Trips in the current month.  
  ```kql
  Automotive
  | where getmonth(pickup_datetime) == getmonth(now()) 
    and getyear(pickup_datetime) == getyear(now())
  | project trip_id, vendor_id, pickup_datetime, fare_amount
  ```

- **Time-based filtering:**  
  - Events from the last 30 minutes:  
    ```kql
    Automotive
    | where pickup_datetime > ago(30min)
    | project trip_id, vendor_id, pickup_datetime, fare_amount
    ```
  - Events ingested in the past hour using `ingestion_time()`:  
    ```kql
    Automotive
    | where ingestion_time() > ago(1h)
    | project trip_id, vendor_id, pickup_datetime, fare_amount
    ```

- **Summarize data:** Use `summarize` to aggregate data and analyze patterns.  
  Example: Average fare by vendor per hour over the last day.  
  ```kql
  Automotive
  | where ingestion_time() > ago(1d)
  | summarize average_fare = avg(fare_amount) by vendor_id, pickup_hour = hourofday(pickup_datetime)
  | project pickup_hour, vendor_id, average_fare
  | sort by pickup_hour
  ```

  ## Materialized views and stored functions

### Materialized Views
- A **materialized view** summarizes data from a source table or another view, encapsulating a `summarize` statement.
- Example: Create a view showing the number of trips per vendor each day:  
  ```kql
  .create materialized-view TripsByVendor on table Automotive
  {
      Automotive
      | summarize trips = count() by vendor_id, pickup_date = format_datetime(pickup_datetime, "yyyy-MM-dd")
  }
  ```
- **Backfill existing data** into the view using an asynchronous operation:  
  ```kql
  .create async materialized-view with (backfill=true) TripsByVendor on table Automotive
  {
      Automotive
      | summarize trips = count() by vendor_id, pickup_date = format_datetime(pickup_datetime, "yyyy-MM-dd")
  }
  ```
- Query the materialized view like a regular table:  
  ```kql
  TripsByVendor
  | project pickup_date, vendor_id, trips
  | sort by pickup_date desc
  ```

### Stored Functions
- **Stored functions** encapsulate reusable queries with optional parameters.
- Example: Create a function to retrieve trips with a minimum number of passengers:  
  ```kql
  .create-or-alter function trips_by_min_passenger_count(num_passengers:long)
  {
      Automotive
      | where passenger_count >= num_passengers 
      | project trip_id, pickup_datetime
  }
  ```
- Call the function with a parameter to get trips with at least three passengers:  
  ```kql
  trips_by_min_passenger_count(3)
  | take 10
  ```