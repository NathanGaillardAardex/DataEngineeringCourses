# Create Real-Time Dashboards with Microsoft Fabric

## Get started with real-time dashboards

### Overview
- **Real-Time dashboards** in Microsoft Fabric display streaming data from sources like **Eventhouse** tables populated by an **eventstream**.
- Dashboards consist of **tiles** that visualize real-time data using charts, maps, or tables.

### Creating a Real-Time Dashboard
1. **Set up a real-time data source** (e.g., Eventhouse with a KQL database).
2. Create a dashboard and connect it to the data source.

### Configuring Authorization
- Choose how the dashboard accesses data:
  - **Pass-through identity:** Uses the viewer's identity.
  - **Dashboard editor's identity:** Uses the creator’s identity.

### Creating and Configuring Tiles
1. **Add a tile** to the dashboard.
2. **Write and test a KQL query** for the tile.
   - Example query to display bike rental data:
     ```kql
     bikes
     | where ingestion_time() between (ago(30min) .. now())
     | summarize latest_observation = arg_max(ingestion_time(), *) by Neighbourhood
     | project Neighbourhood, latest_observation, No_Bikes, No_Empty_Docks
     | order by Neighbourhood asc
     ```
   - This query shows the latest bike availability in each neighborhood over the last 30 minutes.

3. **Visualize the data:**  
   - Edit the tile to switch from a table view to charts, maps, or other visualizations.
   - Example: Display bike availability as a **bar chart**.

### Customizing the Dashboard
- **Add multiple tiles** to visualize various data points.
- **Rearrange tiles** for optimal data presentation.
- **Include text tiles** to provide context or additional information.

## Advanced features

### Base Queries
- Define **base queries** to retrieve general datasets for multiple tiles, improving dashboard maintainability.
- Use **tile-specific queries** to further filter or format data.
- Example:
  - **Base query** for bike rentals:
    ```kql
    bikes
    | where ingestion_time() between (ago(30min) .. now())
    | summarize latest_observation = arg_max(ingestion_time(), *) by Neighbourhood
    ```
  - **Tile query** using base query:
    ```kql
    base_bike_data
    | project Neighbourhood, latest_observation, No_Bikes, No_Empty_Docks
    | order by Neighbourhood asc
    ```

### Pages
- Add **multiple pages** to organize tiles logically by data source, subject area, or data granularity.
- Pages help manage large dashboards and improve user navigation.

### Parameters
- Use **parameters** to enable user-driven filtering of dashboard data.
- Parameters can be:
  - **Static values** (e.g., date ranges, categories).
  - **Dynamic queries** (e.g., list of neighborhoods).
- Example parameter for filtering by neighborhood:
  ```kql
  bikes
  | distinct Neighbourhood
  | order by Neighbourhood asc
  ```
  - Apply parameter in base query:
    ```kql
    bikes
    | where ingestion_time() between (ago(30min) .. now())
      and (isempty(['selected_neighbourhoods']) or Neighbourhood in (['selected_neighbourhoods']))
    | summarize latest_observation = arg_max(ingestion_time(), *) by Neighbourhood
    ```

### Auto Refresh
- Enable **auto-refresh** to keep real-time data updated without manual intervention.
- Editors can:
  - Set a **default refresh rate**.
  - Define a **minimum refresh rate** to prevent excessive cluster load.
- Viewers can adjust the refresh rate (within editor-defined limits) for optimal performance.

## Real-Time Dashboard best practices

### Clarity and Simplicity
- **Keep dashboards simple** and avoid clutter.
- Use **clear labels** for tiles and visuals.
- **Organize content** using multiple pages for better navigation and subject separation.

### Relevance
- Ensure data displayed is **relevant** to the dashboard’s purpose and the audience’s needs.
- Regularly review content to maintain alignment with user goals.

### Refresh Rate
- Set an **appropriate refresh rate** to balance real-time data needs without overloading the system.
- **Consult users** to ensure refresh rates meet expectations.

### Accessibility
- Design dashboards that are **accessible** to all users, including those with **viewer permissions**.
- Follow accessibility standards to ensure inclusivity.

### Interactivity
- Enable user engagement through **filters**, **parameters**, and **drill-down** capabilities.
- **Elicit feedback** regularly to refine interactivity and usefulness.
- Leverage **Copilot** to enhance productivity and introduce new features as users grow familiar.

### Performance
- **Optimize queries** and visuals to maintain smooth performance.
  - Apply **filters** at the query level using **parameters**.
  - Avoid querying more data than needed for visualizations.
- Ensure dashboards are responsive and load efficiently.

### Security
- Implement strict **security measures**:
  - Protect sensitive data.
  - Manage **authentication** (who can access) and **authorization** (what they can access).
- Adhere to best practices for **SaaS** solutions like Microsoft Fabric.

### Testing
- Conduct regular **functionality** and **performance** tests.
- Include **user-acceptance testing** (UAT) and create **feedback loops** to continuously improve the dashboard.