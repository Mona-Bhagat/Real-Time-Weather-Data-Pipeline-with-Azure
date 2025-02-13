# Real-Time-Weather-Data-Pipeline-with-Azure
This pipeline fetches weather data from an API, processes it through Azure Event Hub and Stream Analytics, and visualizes it in Power BI. 


![Weather Stream_PBI Dashboard](https://github.com/user-attachments/assets/90653bba-393d-4f07-b49d-44b25891ed3c)



# Architecture & Tech Stack
- Weather API  (Source)
- Azure Key Vault  (Secure Credential Management)
- Azure Databricks  (Executes the data ingestion Python script)
- Azure Event Hub  (Real-time data streaming service)
- Azure Stream Analytics (Processes and transforms the streamed data)
- Azure Storage Account (ADLS Gen2) (Stores processed data in Container)
- Power BI  (Connects to storage and visualizes the data)


![Waeather Stream_Data Architecture](https://github.com/user-attachments/assets/89cb3ca5-7022-4562-98e5-d295b174d88f)


# Project Workflow

## 1. API Key Management

To access the weather API, an API key was retrieved and securely stored in Azure Key Vault to protect sensitive information.

## 2. Databricks Setup
An Azure Databricks workspace and compute cluster were set up. The azure-eventhub library was installed in the cluster to enable integration with Azure Event Hub.

## 3. Event Hub Configuration

A new Event Hub instance was created to handle real-time data ingestion. A shared access policy was established, and the connection string was stored as a secret in Key Vault.

## 4. Key Vault Integration

A Key Vault secret scope was configured in Databricks. A Key Vault secret user role was assigned to Databricks

## 5. Data Ingestion Pipeline

A Python script was written to: Connect to the Weather API, Fetch weather data at regular intervals, Ingest the data into Event Hub for streaming.

## 6. Stream Analytics Job Configuration

A Stream Analytics job was created, selecting Event Hub as the input source. Managed Identity authentication was used to enhance security. 

## 7. Data Storage Setup

A new Azure Storage Account and Container were created to store processed data. The storage container was added as an output in Stream Analytics using Managed Identity authentication. The Storage Blob Data Contributor role was assigned to the Stream Analytics job.

## 8. Stream Analytics Query

A query was written in Stream Analytics to: Retrieve data from Event Hub, Process and store the transformed data in the Azure Storage Container.

## 9. Power BI Integration

The Azure Storage Container was connected to Power BI using an access key. The ingested weather data was then visualized using interactive Power BI dashboards.


# Conclusion

This project showcases a scalable and secure data pipeline for real-time data ingestion, processing, and visualization using Azure services











