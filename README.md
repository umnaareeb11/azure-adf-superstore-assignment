# Azure Data Factory - Superstore Data Pipeline

## Overview
I built a data pipeline using Azure Data Factory (ADF) to copy and process the Superstore dataset from a source blob container to a destination blob container.

## Tools & Services Used
- Microsoft Azure Portal
- Azure Resource Group
- Azure Storage Account (Blob Storage)
- Azure Data Factory V2
- Azure Blob Storage Containers

## What I Did

### 1. Created Azure Resources
I created a Resource Group named `rg-adf-superstore-project` and inside it deployed two resources — an Azure Storage Account (`storesuperstore2024`) and an Azure Data Factory (`adf-superstoreproject-01`), both in the East US region.

### 2. Set Up Blob Storage
I created two containers inside the storage account:
- `source-data` — where I uploaded the source file `Sample - Superstore.csv`
- `destination-data` — where the pipeline writes the processed output file

### 3. Configured Azure Data Factory
Inside ADF Studio, I set up the following:
- **Linked Service** (`ls_AzureBlobStorage_Superstore`) — connected ADF to the storage account using an account key
- **Source Dataset** (`ds_Source_Superstore_CSV`) — points to the CSV file in the source-data container
- **Destination Dataset** (`ds_Destination_Superstore_CSV`) — points to the output file in the destination-data container

### 4. Built the Pipeline
I created a pipeline named `pl_Superstore_DataPipeline` with two activities:
- **Get Metadata** — retrieves file properties (Item name, Item type, Size, Column count, Exists)
- **Copy Data** — copies data from the source container to the destination container

### 5. Ran the Pipeline
I first ran a Debug run to test the pipeline, then triggered an official pipeline run using "Trigger Now". Both runs completed successfully. The output file `Superstore_Processed.csv` (2.18 MiB) was written to the destination-data container.

## Results
- Source file: `Sample - Superstore.csv` (2.18 MiB, 9,994 rows, 21 columns)
- Output file: `Superstore_Processed.csv` (2.18 MiB)
- Pipeline status: Succeeded
- Duration: 42 seconds

## Screenshots
All screenshots are included in the `ADF-Superstore-Project` folder.
