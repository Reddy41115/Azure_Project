# Azure_Project
## Azure Data Factory Pipeline: SQL to ADLS Gen2

This is an **end-to-end ADF pipeline** that extracts data from an **Azure SQL Database**, applies incremental loading using **CDC (Change Data Capture)**, and loads it into **ADLS Gen2** as Parquet files.  

Key features:
- Parameterized pipelines for multiple tables
- Incremental loading using CDC columns
- Dynamic folder and file naming
- Integration with **Logic Apps** for alerting
<img width="1138" height="362" alt="image" src="https://github.com/user-attachments/assets/5e583909-621c-4bf8-90b6-d20b5b84b492" />

## 🔄 Pipeline Activities

The pipeline includes the following activities:

- **ForEach (ForEach1)**  
  Loops through multiple tables using parameters.

- **Lookup (last_cdc)**  
  Retrieves the last processed CDC value from ADLS Gen2.

- **Set Variable (current)**  
  Stores current timestamp for dynamic file naming.

- **Copy (AzureSql_to_Adlsgen2)**  
  Loads incremental data from Azure SQL Database to ADLS Gen2 in Parquet format.

- **If Condition (if_incremental_data)**  
  Checks if data is available after copy operation.

- **Delete (Delete_Empty_file)**  
  Deletes file if no data is loaded.

- **Script (max_cdc)**  
  Gets the latest CDC value from source table.

- **Copy (update_last_cdc)**  
  Updates the latest CDC value into JSON file.

- **Web Activity (Web1)**  
  Sends pipeline status to Logic Apps for notification.

---

## 🔁 Flow Summary

1. Iterate tables using **ForEach**
2. Get last CDC value using **Lookup**
3. Capture current time
4. Load incremental data using **Copy**
5. Check data using **If Condition**
6.  
   - No data → Delete file  
   - Data present → Update CDC  
7. Trigger notification using **Web Activity**
