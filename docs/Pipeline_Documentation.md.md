# Pipeline Documentation

## Project Overview
This project uses Azure Data Factory to ingest, process, and prepare COVID-19 data for reporting through Azure SQL Database and Power BI.

## Data Sources
- ECDC COVID-19 data.

## Pipeline Orchestration
### `ingestion_pipeline`
Coordinates the ingestion workflow.

### `pl_ingest_ecdc_data`
Handles ingestion of ECDC source data.

### `pl_process_cases_and_deaths_data`
Processes COVID-19 cases and deaths data.

### `pl_process_hospital_admissions_data`
Processes hospital admissions data.

### `pl_process_population_data_bricks`
Handles population data processing using the Databricks-related workflow.

### SQL Loading Pipelines
- `pl_sql_cases_and_deaths_data`
- `pl_sql_hospital_admissions`
- `pl_sql_testing_data`

These pipelines support loading the relevant datasets into SQL reporting tables. Confirm the exact activities and destinations against your exported pipeline definitions.

### `pl_execute_population`
Orchestrates the population ingestion and processing steps.

## Data Transformation
The project includes Mapping Data Flows:
- `df_transform_death_cases`
- `df_transform_hospital_admission`

## Data Storage and Reporting
Processed data is stored in Azure storage and Azure SQL Database for downstream reporting. Power BI is used to visualize and analyze the resulting data.

## Technologies
- Azure Data Factory
- Azure Data Lake Storage
- Azure Blob Storage
- Azure Databricks
- Azure SQL Database
- Power BI
