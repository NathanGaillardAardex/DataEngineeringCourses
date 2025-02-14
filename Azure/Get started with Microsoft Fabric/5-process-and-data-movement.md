# Orchestrate processes and data movement with Microsoft Fabric
## Understand Pipelines in Microsoft Fabric

### Overview
- **Pipelines** in Microsoft Fabric manage data movement and processing.
- Enable **data transfer, transformation, and orchestration** with control flow logic.
- **Graphical interface** allows building complex pipelines with minimal coding.

### Core Pipeline Concepts

#### Activities
- **Executable tasks** in a pipeline that dictate workflow sequencing.
- **Two main categories**:
  - **Data transformation activities**: Include **Copy Data**, **Data Flows (Gen2)**, **Spark Notebooks**, **Stored Procedures**, and **Delete Data**.
  - **Control flow activities**: Enable **looping, branching, variable management**, and **conditional execution**.

#### Parameters
- **Allow dynamic input values**, enhancing pipeline reusability.
- Example: Save ingested data to different folders by specifying folder names at runtime.

#### Pipeline Runs
- **Each execution instance** of a pipeline is a **run**.
- Runs can be **on-demand** or **scheduled**.
- **Unique run IDs** help track execution details and troubleshoot failures.

## Use the Copy Data Activity in Microsoft Fabric

### Overview
- **Copy Data activity** is a fundamental component of data pipelines.
- Primarily used to **ingest data** from external sources into **lakehouse files or tables**.
- Can be **standalone** or **combined** with other activities (e.g., **Delete Data, Notebooks**) for complex ingestion workflows.

### The Copy Data Tool
- **Graphical interface** simplifies configuration of data sources and destinations.
- Supports a **wide range of source connections**, including:
  - **Lakehouse**
  - **Warehouse**
  - **SQL Database**
  - **Other OneLake-compatible destinations**

### When to Use the Copy Data Activity
- **Best for direct copying** between supported sources and destinations **without transformations**.
- Use when importing **raw data** to apply transformations **later** in the pipeline.
- If **real-time transformations** or **merging multiple sources** is required, consider using a **Data Flow (Gen2) activity** instead.

### Configuring Copy Data in a Pipeline
- Add **Copy Data activity** in the **pipeline canvas**.
- Configure **source and destination** in the **settings pane**.
- Optionally, **combine with other activities** (e.g., **Delete Data, Notebooks**) for preprocessing or post-processing tasks.
## Use Pipeline Templates in Microsoft Fabric

### Overview
- **Pipeline templates** provide predefined workflows for **common data ingestion and transformation tasks**.
- Enable rapid development by **reducing manual configuration** and **offering best-practice designs**.

### Creating a Pipeline from a Template
1. **Start a new pipeline** and select **"Choose a task to start"**.
2. **Browse available templates** suited for various data scenarios.
3. **Select a template** that matches your requirements.
4. **Customize** the pipeline in the **pipeline canvas** by modifying activities and settings.

### Benefits of Using Templates
- **Faster development** with ready-made configurations.
- **Customizable** to fit **specific ingestion and transformation needs**.
- **Standardized best practices** for consistency and efficiency in data workflows.

## Run and Monitor Pipelines in Microsoft Fabric

### Running a Pipeline
- **Validate the pipeline** using the **Validate** option to check for configuration errors.
- Execute the pipeline **interactively** or **schedule it** for automatic execution.

### Viewing Run History
- Access **pipeline run history** from:
  - **Pipeline canvas**
  - **Workspace pipeline list**
- Each run includes:
  - **Start time**
  - **Execution details**
  - **Activity durations**
- **Detailed execution timeline** is available via a **Gantt chart**.

### Monitoring Individual Runs
- Select a **specific run** from the history to view **execution details**.
- Helps in **debugging failures**, optimizing performance, and **ensuring smooth operation**.

# [Next](./6-dataflows-gen2.md)