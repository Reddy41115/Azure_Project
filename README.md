# Azure_Project
## Azure Data Factory Pipeline: SQL to ADLS Gen2

This is an **end-to-end ADF pipeline** that extracts data from an **Azure SQL Database**, applies incremental loading using **CDC (Change Data Capture)**, and loads it into **ADLS Gen2** as Parquet files.  

Key features:
- Parameterized pipelines for multiple tables
- Incremental loading using CDC columns
- Dynamic folder and file naming
- Integration with **Logic Apps** for alerting
<img width="1146" height="362" alt="image" src="https://github.com/user-attachments/assets/d7db584d-d485-4059-80c1-ccca9d3ba52c" />
