# s3-glue-ETL-ANTHENA-Quicksight-Labs
---

# 📊 AWS Data Pipeline: From S3 to QuickSight

This project demonstrates how to build an end-to-end data pipeline on AWS, utilizing services like Amazon S3, AWS Glue, Amazon Athena, and Amazon QuickSight to process and visualize data efficiently.

---

## 📁 Prerequisites

- **AWS Account**: Ensure you have access to an AWS account with necessary permissions.
- **AWS CLI**: Installed and configured on your local machine.
- **IAM Role**: Create an IAM role with the following permissions:
  - Amazon S3 Full Access
  - AWS Glue Console Full Access
  - Amazon Athena Full Access
  - Amazon QuickSight Access

---

## 🛠️ Step-by-Step Guide

### 1. Create an Amazon S3 Bucket

- Navigate to the [Amazon S3 Console](https://s3.console.aws.amazon.com/s3/).
- Click on **"Create bucket"**.
- Provide a unique bucket name and select a region.
- Click **"Create bucket"**.

### 2. Upload the Dataset

- Download the `employees.csv` file from the provided source.
- In your newly created S3 bucket, create a folder named `input/`.
- Upload the `employees.csv` file into the `input/` folder.

### 3. Configure AWS Glue

#### a. Create a Glue Crawler

- Navigate to the [AWS Glue Console](https://console.aws.amazon.com/glue/).
- Click on **"Crawlers"** and then **"Add crawler"**.
- Name your crawler (e.g., `employees-crawler`).
- For the data source, select **S3** and specify the path to your `input/` folder.
- Choose the IAM role created earlier.
- Set the crawler to update the Data Catalog.
- Run the crawler to populate the Glue Data Catalog with the schema from your CSV file.

#### b. Create an ETL Job

- In the Glue Console, navigate to **"Jobs"** and click **"Add job"**.
- Name your job (e.g., `employees-etl-job`).
- Choose the same IAM role.
- For the script, you can use the provided `glue-job.py` script.
  - Ensure you modify the script to reference your specific S3 bucket and folder names.
- Define the source as the table created by the crawler.
- Define the target as a new folder in your S3 bucket (e.g., `output/`).
- Save and run the job to transform and load the data into the `output/` folder.

---

## 🔍 Query Data with Amazon Athena

- Navigate to the [Amazon Athena Console](https://console.aws.amazon.com/athena/).
- Set up a query result location in S3 (e.g., `s3://your-bucket-name/athena-results/`).
- In the query editor:
  - Select the database created by the Glue crawler.
  - Run SQL queries on the table to analyze your data.

---

## 📈 Visualize Data with Amazon QuickSight

- Navigate to the [Amazon QuickSight Console](https://quicksight.aws.amazon.com/).
- Sign in and set up QuickSight if you haven't already.
- In QuickSight:
  - Click on **"Manage data"** and then **"New data set"**.
  - Choose **Athena** as the data source.
  - Connect to the database and table you queried in Athena.
  - Create analyses and build visualizations based on your data.

---

## ✅ Summary

By following this guide, you've successfully:

1. Stored raw data in Amazon S3.
2. Cataloged and transformed data using AWS Glue.
3. Queried data with Amazon Athena.
4. Visualized insights using Amazon QuickSight.

This pipeline provides a scalable and serverless approach to data analysis on AWS.

---
