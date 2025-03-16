# Employee Data ETL Pipeline with Data Fusion and Airflow

This project demonstrates an ETL (Extract, Transform, Load) pipeline for processing employee data using Google Cloud Data Fusion and Apache Airflow. The pipeline extracts employee information from a source, transforms the data as needed, and loads it into a destination for further analysis or reporting.

## Project Structure

- **/dags**: Contains Apache Airflow DAGs (Directed Acyclic Graphs) that orchestrate the ETL workflow.
- **/datafusion_pipelines**: Includes Data Fusion pipeline configurations defining the data processing steps.
- **/scripts**: Holds custom scripts used within the pipeline for data transformation or other tasks.
- **/resources**: Contains auxiliary files such as sample data, configuration files, or schemas.
- **/images**: Contains project-related images for documentation purposes.

## Prerequisites

Before setting up this project, ensure you have the following:

- **Google Cloud Platform (GCP) Account**: Access to GCP services, including Data Fusion.
- **Apache Airflow**: Installed and running to manage and schedule the ETL workflows.
- **Python 3.x**: Required for running scripts and Airflow.
- **Service Account Key**: A GCP service account key with necessary permissions for Data Fusion operations.

## Setup Instructions

### 1. Clone the Repository

```bash
   git clone https://github.com/abhira15/etl-pipeline-datafusion-airflow.git
   cd etl-pipeline-datafusion-airflow/Employeedata
```

### 2. Set Up Virtual Environment

Create and activate a Python virtual environment to manage dependencies.

```bash
   python3 -m venv venv
   source venv/bin/activate
```

### 3. Install Dependencies

Install the required Python packages.

```bash
   pip install -r requirements.txt
```

### 4. Configure Airflow

- Initialize the Airflow database:

  ```bash
  airflow db init
  ```

- Start the Airflow web server and scheduler:

  ```bash
  airflow webserver --port 8080
  airflow scheduler
  ```

- Access the Airflow UI at `http://localhost:8080` and ensure the DAGs are loaded correctly.

![Airflow UI](images/airflow_ui.png)

### 5. Set Up Google Cloud Data Fusion

- Create a Data Fusion instance in your GCP project.
- Upload the pipeline configurations from the `/datafusion_pipelines` directory to Data Fusion.
- Ensure that the service account used by Airflow has the necessary permissions to trigger Data Fusion pipelines.

![Google Cloud Data Fusion](images/datafusion_pipeline.png)

### 6. Configure Connections in Airflow

- In the Airflow UI, navigate to **Admin > Connections**.
- Set up a connection for Google Cloud with the service account key.
- Configure any other connections required by your pipelines (e.g., databases, APIs).

### 7. Trigger the ETL Pipeline

- In the Airflow UI, enable and trigger the DAG responsible for the ETL process.
- Monitor the DAG's progress and logs to ensure successful execution.

![Airflow DAG Execution](images/airflow_dag_execution.png)

## Data Flow Overview

### 1. Extraction

- The pipeline extracts employee data from the source system, which could be a database, CSV file, or API.

### 2. Transformation

- Data Fusion processes the extracted data, performing transformations such as data cleaning, normalization, and enrichment.

### 3. Loading

- The transformed data is loaded into the destination system, such as a data warehouse or analytics platform, for further use.

## Customization

To adapt this project to your specific needs:

- Modify the Data Fusion pipeline configurations to match your data sources, transformations, and destinations.
- Update the Airflow DAGs to reflect your scheduling requirements and any additional tasks.
- Adjust the scripts in the `/scripts` directory for custom transformations or data handling.

## Troubleshooting

- **Airflow Issues**: Check the Airflow logs for errors and ensure all connections and variables are set correctly.
- **Data Fusion Errors**: Review the Data Fusion pipeline logs to identify and resolve issues in data processing.
- **Permissions**: Verify that all service accounts have the necessary permissions for the operations they perform.

## Resources

- [Google Cloud Data Fusion Documentation](https://cloud.google.com/data-fusion/docs)
- [Apache Airflow Documentation](https://airflow.apache.org/docs/)

---

*Note: This README provides a general framework for setting up an ETL pipeline using Google Cloud Data Fusion and Apache Airflow. Specific details may vary based on your environment and requirements.*

