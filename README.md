# Bootcamp Project 2 - Transactions and Loan Data for a Customer

## Project Overview

This project focuses on building a robust and scalable data pipeline to process customer account data, specifically transaction and loan records. The goal is to extract raw data from the Bronze layer (stored in Azure Data Lake Storage Gen2), transform it in the Silver layer using Azure Databricks, and finally load it into a Gold Delta Table using Slowly Changing Dimensions (SCD) Type 1 methodology. The cleaned and consolidated data supports downstream analytics and reporting using Power BI and Microsoft Fabric.

## Tools & Technologies

- Azure Data Lake Storage Gen2
- Azure Databricks
- Power BI Desktop
- Microsoft Fabric
- Draw.io (for architecture diagram)
- PySpark

## Setup Instructions

### 1. Create Service Principal and Key Vault

- Go to Microsoft Entra ID → Manage → App registrations → New registration.
- Copy **Application ID** and **Tenant ID**.
- Go to **Certificates & Secrets** and create a **new client secret**.
- Store **Application ID**, **Tenant ID**, and **Secret Value** securely.
- Save these secrets in **Azure Key Vault**.

### 2. Create Secret Scope in Databricks

- Link your Azure Key Vault to your Databricks workspace.
- Create a scope, e.g., `askvconnection`.

### 3. Mount ADLS Gen2 in Databricks
4. Data Transformation (Bronze → Silver Layer)
Use PySpark in Databricks to read data from Bronze.

Remove nulls and duplicates.

Write cleaned data in Parquet format to Silver layer.

5. Data Consolidation
Join all cleaned files into a single DataFrame.

Write the consolidated data back to the Silver layer in Parquet format.

6. Apply SCD Type 1 in Gold Layer
Apply SCD Type 1 logic to all datasets using Delta Lake.

Store final versioned records in Gold layer.

7. Schedule Pipeline
Create and schedule a Databricks job to run your notebook on a daily or scheduled basis.

8. Reporting and Visualization
Load final Delta table into Power BI Desktop.

Create visual reports and publish them to Microsoft Fabric workspace.


Contributors
Deepthi
