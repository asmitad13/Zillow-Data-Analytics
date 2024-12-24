
# Zillow Data Analytics (RapidAPI) | End-To-End Python ETL Pipeline

The project demonstrates how to build and automate a Python-based ETL (Extract, Transform, Load) pipeline for real estate data sourced from Zillow's Rapid API. The pipeline is designed to utilize various AWS services and Apache Airflow for orchestration and scheduling, resulting in efficient data transformation and visualization. The key steps involve data extraction, processing, loading into Amazon Redshift, and visualization using Amazon QuickSight.

# Workflow Overview

1. Data Extraction: Real estate property data is extracted from the Zillow Rapid API using Python.
The extracted data is stored in the landing zone, which is an S3 bucket on AWS.

2. Lambda Function (Copy Data):
An S3 event trigger activates a Lambda function.
This function copies the raw data from the landing zone to an intermediate zone (another S3 bucket).

3. Lambda Function (Transform Data):
A second Lambda function is triggered to transform the data.
The transformation process includes cleaning, formatting, and converting the data into CSV format.
The transformed data is stored in the transformed data zone (another S3 bucket).

4. Data Loading into Redshift:
Apache Airflow orchestrates the process using an S3KeySensor to detect when the transformed data is available in the S3 bucket.
Once detected, the data is loaded into an Amazon Redshift cluster for further analysis.

5. Data Visualization:
Amazon QuickSight is connected to the Redshift cluster.
Interactive dashboards are created to visualize the processed Zillow data.

<img width="708" alt="Screenshot 2024-12-23 at 6 36 02 PM" src="https://github.com/user-attachments/assets/eb629070-c13c-4eeb-a6b4-db4c007d43f2" />

# Creation of S3 Bucket
1. Bucket Name: zillow-etl
2. Bucket Name: zillow-copy-of-raw-json-bucket
3. Bucket Name: zillow-trasnform-from-json-to-csv

# Setting up Amazon Redshift

<img width="880" alt="Screenshot 2024-12-23 at 7 03 25 PM" src="https://github.com/user-attachments/assets/6c835a55-bc0d-405b-838c-83280f8e48a4" />

# DAG View

<img width="951" alt="Screenshot 2024-12-23 at 7 47 31 PM" src="https://github.com/user-attachments/assets/a59a597e-0abf-455d-ab11-40a2dd80133b" />


# Technologies Used

1. Apache Airflow: Open-source platform for orchestrating workflows and data pipelines.
2. AWS Cloud Platform: The entire project is implemented on the AWS cloud.


