This repository contains a robust Snowflake ETL (Extract, Transform, Load) pipeline designed to ingest menu data from an S3 staging area, apply Slowly Changing Dimension (SCD) Type 2 logic to dimension tables, and load the processed information into a fact table. The entire process is orchestrated using Snowflake's powerful Tasks and Stored Procedures, ensuring automated and scheduled data ingestion and transformation.
Automated Data Ingestion: Uses Snowflake Stages and Tasks to automatically load data from an S3 bucket into a transient staging table.
SCD Type 2 Implementation: Applies SCD Type 2 logic to dim_menu_details and dim_menu_price tables, preserving historical changes for menu_name, menu_type, category, and price.
Fact Table Loading: Merges processed dimension data into a fact_Menu table, keeping it updated with the latest active menu information.
Task Orchestration: Leverages Snowflake Tasks to create a dependency-driven workflow, ensuring steps execute in the correct order (Staging -> Dimension Loads -> Fact Load -> Staging Cleanup).
Auditing: Includes UPDATE_DT and User columns in dimension tables for basic auditing of changes.
Idempotent Operations: Procedures are designed to be re-runnable without causing duplicate data or errors.
