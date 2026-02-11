# Financial Data Engineering – Client Lead Generation & Geospatial Analytics

## Overview
ETL + analytics pipeline to identify high-potential clients using transactions and geospatial location.

## Architecture
RAW → Staging → Fact/Dimension → Analytics → Geospatial Insights

## Data Sources
- Kaggle Financial Datasets: https://www.kaggle.com/datasets
- Mockaroo Synthetic CSVs: https://www.mockaroo.com

## Environment Setup (Free Tier)
1. AWS S3 buckets: finance-raw, finance-staging, finance-curated
2. Snowflake: XSMALL warehouse, AUTO_SUSPEND = 60s, Database FINANCE_DB, schema PUBLIC

## Steps
1. Create file format and stage in Snowflake pointing to S3
2. Create RAW table and load CSV with COPY INTO
3. Create staging table (STG_CLIENTS) with proper types
4. Create dimension and fact tables: DIM_CLIENT, FACT_TRANSACTIONS
5. Apply business rules: remove invalid/missing transactions
6. Create STREAM and TASK for incremental loads
7. Geospatial: CLIENT_LOCATION → GEOGRAPHY, distance queries
8. Dashboard: heatmap of transactions and leads

## Cost Control
- XSMALL warehouse
- AUTO_SUSPEND = 60s
- TASK scheduled hourly

## Scripts
01_create_file_format_and_stage.sql
02_create_raw_table.sql
03_load_raw.sql
04_create_staging_table.sql
05_create_fact_dim_tables.sql
06_apply_business_rules.sql
07_create_stream_and_task.sql
08_geospatial_analysis.sql