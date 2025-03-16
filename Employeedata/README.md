# Employee Data ETL Pipeline with Data Fusion, Airflow, BigQuery, and Looker Studio

This project demonstrates an ETL (Extract, Transform, Load) pipeline for processing employee data using Google Cloud Data Fusion, Apache Airflow, Google BigQuery, and Looker Studio. The pipeline extracts employee information from a source, transforms the data as needed, and loads it into a destination for further analysis and visualization.

## Project Structure

- **/dags**: Contains Apache Airflow DAGs (Directed Acyclic Graphs) that orchestrate the ETL workflow.
- **/datafusion_pipelines**: Includes Data Fusion pipeline configurations defining the data processing steps.
- **/scripts**: Holds custom scripts used within the pipeline for data transformation or other tasks.
- **/resources**: Contains auxiliary files such as sample data, configuration files, or schemas.
- **/Iamge**: Contains project-related images for documentation purposes.

## Prerequisites

Before setting up this project, ensure you have the following:

- **Google Cloud Platform (GCP) Account**: Access to GCP services, including Data Fusion, BigQuery, and Looker Studio.
- **Apache Airflow**: Installed and running to manage and schedule the ETL workflows.
- **Python 3.x**: Required for running scripts and Airflow.
- **Service Account Key**: A GCP service account key with necessary permissions for Data Fusion and BigQuery operations.

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

![Airflow UI](https://github.com/abhira15/etl-pipeline-datafusion-airflow/blob/main/Employeedata/Image/Composer.png)

### 5. Set Up Google Cloud Data Fusion

- Create a Data Fusion instance in your GCP project.
- Upload the pipeline configurations from the `/datafusion_pipelines` directory to Data Fusion.
- Ensure that the service account used by Airflow has the necessary permissions to trigger Data Fusion pipelines.

![Google Cloud Data Fusion](https://github.com/abhira15/etl-pipeline-datafusion-airflow/blob/main/Employeedata/Image/Data_Fusion_ETL_Pipeline.png)

### 6. Configure BigQuery as the Data Warehouse

- Create a BigQuery dataset and table in your GCP project to store the processed employee data.
- Ensure the ETL pipeline is configured to load transformed data into BigQuery.
- Grant the required permissions to the service account for writing to BigQuery.

![BigQuery Table](https://github.com/abhira15/etl-pipeline-datafusion-airflow/blob/main/Employeedata/Image/BigQuery.png)

### 7. Configure Looker Studio for Data Visualization

- Open **Looker Studio** (formerly Google Data Studio) and connect it to your BigQuery dataset.
- Create dashboards and reports to visualize employee data insights.
- Customize charts, tables, and filters as needed.

![Looker Studio Dashboard](https://github.com/abhira15/etl-pipeline-datafusion-airflow/blob/main/Employeedata/Image/LookerStudio.png)

### 8. Configure Connections in Airflow

- In the Airflow UI, navigate to **Admin > Connections**.
- Set up a connection for Google Cloud with the service account key.
- Configure any other connections required by your pipelines (e.g., databases, APIs).

### 9. Trigger the ETL Pipeline

- In the Airflow UI, enable and trigger the DAG responsible for the ETL process.
- Monitor the DAG's progress and logs to ensure successful execution.

![Airflow DAG Execution](https://github.com/abhira15/etl-pipeline-datafusion-airflow/blob/main/Employeedata/Image/Pipeline.png)

## Data Flow Overview

### 1. Extraction

- The pipeline extracts employee data from the source system, which could be a database, CSV file, or API.

### 2. Transformation

- Data Fusion processes the extracted data, performing transformations such as data cleaning, normalization, and enrichment.

### 3. Loading

- The transformed data is loaded into **Google BigQuery** for storage and analysis.
- Looker Studio is used to visualize the data for business intelligence and decision-making.

## Customization

To adapt this project to your specific needs:

- Modify the Data Fusion pipeline configurations to match your data sources, transformations, and destinations.
- Update the Airflow DAGs to reflect your scheduling requirements and any additional tasks.
- Adjust the scripts in the `/scripts` directory for custom transformations or data handling.
- Customize Looker Studio dashboards to visualize the most relevant KPIs and metrics.

## Troubleshooting

- **Airflow Issues**: Check the Airflow logs for errors and ensure all connections and variables are set correctly.
- **Data Fusion Errors**: Review the Data Fusion pipeline logs to identify and resolve issues in data processing.
- **BigQuery Errors**: Check permissions and schema mismatches if data fails to load.
- **Looker Studio Issues**: Verify that the BigQuery dataset is correctly linked and refresh the data source if needed.

## Resources

- [Google Cloud Data Fusion Documentation](https://cloud.google.com/data-fusion/docs)
- [Apache Airflow Documentation](https://airflow.apache.org/docs/)
- [Google BigQuery Documentation](https://cloud.google.com/bigquery/docs)
- [Looker Studio Documentation](https://lookerstudio.google.com)

*Note: This README provides a general framework for setting up an ETL pipeline using Google Cloud Data Fusion, Apache Airflow, BigQuery, and Looker Studio. Specific details may vary based on your environment and requirements.*

