# Get started with data science in Microsoft Fabric

## Understand the Data Science Process

Machine learning helps identify patterns in complex datasets to generate insights or predictions. For example, businesses can forecast sales or detect customer churn. However, training a model is only part of a larger data science workflow.

### Common Machine Learning Models
Machine learning models fall into four main categories:
- **Classification**: Predicts categorical outcomes (e.g., will a customer churn?).
- **Regression**: Estimates numerical values (e.g., price prediction).
- **Clustering**: Groups similar data points (e.g., customer segmentation).
- **Forecasting**: Predicts future values based on time-series data (e.g., sales projections).

Choosing the right model depends on understanding the business problem and the available data.

### The Data Science Process
1. **Define the problem**: Work with business stakeholders to determine what to predict and how success is measured.
2. **Get the data**: Collect and store data, often in a **Lakehouse** for easy access.
3. **Prepare the data**: Load, clean, and transform data in notebooks to fit model requirements.
4. **Train the model**: Select an algorithm, tune hyperparameters, and track experiments using **MLflow**.
5. **Generate insights**: Use the trained model for predictions through batch scoring.

### Experimentation and Model Management
Data scientists spend most of their time on data preparation and model training. The choice of data cleaning techniques and algorithms impacts model accuracy. Open-source tools like **Pandas, NumPy, Scikit-Learn, PyTorch, and SynapseML** support this process.

To manage models effectively, tracking experiments is crucial. **MLflow in Microsoft Fabric** helps monitor, compare, and deploy models efficiently, ensuring that the best-performing models are used for decision-making.

## Explore and Process Data with Microsoft Fabric

### Data Ingestion
High-quality and large-scale data are essential for effective machine learning. **Microsoft Fabric** provides robust ingestion and processing tools, supporting both **low-code** and **code-first** approaches. Data can be ingested from **local files, cloud storage (Azure Data Lake Storage Gen2), and other sources**, and stored in a **Fabric lakehouse**. The lakehouse serves as a **centralized storage** for structured, semi-structured, and unstructured data, making it easily accessible for exploration and transformation.

### Data Exploration and Transformation
Fabric provides a **notebook-based environment powered by Apache Spark**, enabling large-scale data processing. Key features:
- **Notebooks auto-attach to Spark compute**, with sessions persisting across executions but stopping after inactivity to save costs.
- **Supports multiple languages**, including **PySpark (Python)** and **SparkR (R)**.
- **Built-in visualization options** for data exploration.
- **Data transformation capabilities**, allowing processed data to be written back to the lakehouse.

### Data Preparation with Data Wrangler
Fabric includes **Data Wrangler**, an intuitive tool for **quick data exploration and cleaning**:
- Provides **summary statistics** to detect issues like missing values.
- Supports **built-in cleaning operations** with an auto-generated preview.
- Allows exporting **transformation steps as code**, enabling execution within a notebook.

By integrating ingestion, exploration, and transformation within **Microsoft Fabric**, data scientists can efficiently prepare high-quality datasets for machine learning and analytics.

## Train and Score Models with Microsoft Fabric

### Model Training and Experiment Tracking
Once data is ingested, explored, and preprocessed, it can be used for **training machine learning models**. Model training is **iterative**, requiring tracking and comparison of multiple runs. **Microsoft Fabric integrates with MLflow**, allowing data scientists to log and track experiments to ensure **reproducibility** and optimize model performance.

### Understanding Experiments
In Fabric, an **experiment** consists of **multiple runs**, where each run represents a model training task. For example:
- **Different datasets** can be tested on the same algorithm.
- **Various hyperparameter settings** can be compared.
- **Multiple experiment runs** help determine the best-performing model.

### Tracking Metrics and Model Performance
Fabric enables **tracking parameters, metrics, and artifacts** across runs:
- **Experiment overview** provides a high-level summary.
- **Run details tab** allows individual run inspection.
- **Run list** enables direct comparison between different runs.

Tracking results ensures **better decision-making** when finalizing model configurations.

### Model Storage and Versioning
After training, **models and artifacts** are stored in **Microsoft Fabric** as **registered models**. Each model version is maintained, allowing:
- **Easy model management** over time.
- **Version tracking** to monitor performance improvements.

### Generating Predictions with the PREDICT Function
Trained models are used for **scoring new data** with the **PREDICT function**, which seamlessly integrates with **MLflow models**. For example:
- A **sales forecasting model** can predict next week's sales based on historical data.
- New predictions are stored in **a lakehouse** and visualized in **Power BI** for business insights.

With **MLflow integration, experiment tracking, and scalable batch scoring**, Microsoft Fabric streamlines the end-to-end machine learning workflow.

# [Next](./10-administration.md)