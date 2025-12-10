# databricks-dbt-pipeline

# Modern Data Pipeline using Databricks and DBT
End-to-end data engineering pipeline that ingests airline booking data in real time using Databricks Autoloader, processes it with Delta Live Tables (DLT), and models Gold-layer dimensions & facts with dbt for real-time analytics on bookings, high-value customers, profitability, and market share.

## Overview
This project builds a modern, scalable, cloud-agnostic airline analytics platform using Databricks Lakehouse architecture. It ingests raw CSV files using Autoloader, applies cleansing & transformation logic with Delta Live Tables (DLT), and generates curated Gold-layer fact and dimension models using dbt.
The platform enables the airline to: Track flight bookings in real time, Identify high-value customers, Analyze flight profitability across routes, Measure market share by airport and route

## Problem Statement

Airline companies ingest large daily booking files from multiple sources. 
Traditional ingestion pipelines suffer from: Duplicate processing when old files reappear, Manual daily updates causing operational failures, Slow processing of large historical files, No awareness of what actually changed in the data, Schema drift issues breaking pipelines, Lack of CDC (Change Data Capture) for customer and booking updates
To solve these issues, we implement a reliable, incremental, exactly-once ingestion and transformation pipeline using Databricks Autoloader and DLT.

## Dataset

- passengers.csv – passenger_id, name, email, loyalty status
- flights.csv – flight_id, origin, destination, departure_time
- bookings.csv – booking_id, passenger_id, flight_id, booking_date, fare, channel
- airports.csv – metadata for origin/destination airports

## Tools & Technologies
- Databricks Core - Autoloader (incremental ingestion, schema evolution, deduplication), Delta Lake (ACID tables: Bronze, Silver, Gold), Delta Live Tables (DLT) / Lakeflow Declarative Pipelines, SQL Warehouse (serverless BI engine)
- Development & Transformation - Python (PySpark), Delta Live Tables (Python API), dbt (data modeling: dimensions, facts)
- Orchestration & Architecture - Databricks Jobs, Cloud Storage, DBFS Checkpoints

## Methods
- Incremental Ingestion with Autoloader (Bronze Layer) - A dynamic bronze notebook loads any new CSV file without manual intervention:
- Delta Live Tables Pipeline (Silver Layer) - Using Lakeflow Declarative Pipelines (DLT): Cleansing, standardization, and enrichment; Auto-CDC (Change Data Capture); SCD-type updates; SQL and Python DLT pipelines
- Gold Modeling with dbt - Two reusable, dynamic builders: Dynamic Dimension Builder (dbt), Dynamic Fact Builder (dbt)
- SQL Warehouse for BI / Analytics - Highly optimized for BI workloads


## Output

This project delivers a production-ready airline analytics platform with:
- Fully automated ingestion (no manual file processing)
- Exactly-once, incremental processing with Autoloader
- Auto-CDC for passenger & flight changes
- DLT pipeline for clean Silver schema
- dbt Gold models powering consistent semantic layers
- Real-time analytics for bookings, profitability, market share, and customer segmentation



Add automated QA tests using dbt tests & Great Expectations
