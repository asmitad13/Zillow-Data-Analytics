# Zillow Data Engineering ETL Pipeline

## Project Description
This project demonstrates how to build and automate a Python-based ETL (Extract, Transform, Load) pipeline for real estate data sourced from Zillow's Rapid API. The pipeline leverages AWS services and Apache Airflow for orchestration, resulting in efficient data transformation and visualization.

---

## Workflow Overview

1. **Data Extraction**:
   - Real estate property data is extracted from the Zillow Rapid API using Python.
   - The extracted data is stored in the landing zone (an S3 bucket on AWS).

2. **Lambda Function (Copy Data)**:
   - An S3 event triggers a Lambda function.
   - This function copies the raw data from the landing zone to an intermediate zone (another S3 bucket).

3. **Lambda Function (Transform Data)**:
   - A second Lambda function is triggered to transform the data.
   - The transformation process includes cleaning, formatting, and converting the data into CSV format.
   - The transformed data is stored in the transformed data zone (another S3 bucket).

4. **Data Loading into Redshift**:
   - Apache Airflow orchestrates the ETL process.
   - Uses an `S3KeySensor` to detect when transformed data is available in the S3 bucket.
   - Once detected, the data is loaded into an Amazon Redshift cluster for further analysis.

5. **Data Visualization**:
   - Amazon QuickSight connects to the Redshift cluster.
   - Interactive dashboards are created to visualize the processed Zillow data.

---

## Workflow Diagram

<img width="708" alt="Screenshot 2024-12-23 at 6 36 02 PM" src="https://github.com/user-attachments/assets/cdda8715-996f-4cee-83df-67a500a6c9e1" />



# S3 Buckets Used
The following S3 buckets are used in the pipeline:

1. zillow-etl: Stores raw data extracted from the API.
2. zillow-copy-of-raw-json-bucket: Holds intermediate processed data.
3. zillow-transform-from-json-to-csv: Contains transformed CSV data.

# DAG View (Apache Airflow)
The ETL pipeline is orchestrated through Apache Airflow. Below is a visual representation of the DAG workflow:

<img width="951" alt="Screenshot 2024-12-23 at 7 47 31 PM" src="https://github.com/user-attachments/assets/ef0657ba-fbcc-4f6e-a172-5183bdef946c" />

# Setting Up Amazon Redshift
Configure an Amazon Redshift cluster with appropriate security and permissions.
Load data into Redshift from the transformed S3 bucket.
Enable Amazon QuickSight to connect to Redshift for visualization.

<img width="880" alt="Screenshot 2024-12-23 at 7 03 25 PM" src="https://github.com/user-attachments/assets/c134264a-04a0-4166-9ac6-197e713b774f" />



# Technologies Used
This project utilizes the following technologies:

1. Apache Airflow: Open-source platform for orchestrating workflows and data pipelines.
2. Amazon S3: For data storage in raw, intermediate, and transformed formats.
3. AWS Lambda: For executing data copying and transformation logic.
4. Amazon Redshift: Cloud data warehouse for storing and analyzing the transformed data.
5. Amazon QuickSight: For data visualization and creating interactive dashboards.
6. Python: For extracting data from the Zillow Rapid API and integrating the pipeline.
