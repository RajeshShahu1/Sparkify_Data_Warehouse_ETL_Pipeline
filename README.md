# Sparkify Data Warehouse ETL Pipeline

This repository contains an ETL pipeline designed to load and transform raw data from Amazon S3 into a Redshift data warehouse for Sparkify, a digital music streaming service.

## Project Purpose

The goal of this project is to create a robust and scalable data warehouse solution that allows Sparkify to analyze user activity, the songs they listen to, and the artists involved. By transforming the raw log and song datasets into an analytical format, Sparkify can extract valuable insights such as:

- Most popular songs
- Peak user activity hours
- Artist trends and user preferences

## Why Use Redshift?

Amazon Redshift is a fast, fully managed, petabyte-scale data warehouse that integrates seamlessly with various AWS services. It is ideal for running complex queries and analytical workloads on large-scale datasets. With Redshift, Sparkify can:

- Store and manage massive amounts of data
- Perform efficient and fast SQL-based analytics
- Scale seamlessly as the business grows

## Data Warehouse Schema Design

A **Star Schema** is used in this project to optimize query performance and support analytical operations.

- **Fact Table**
  - `songplays`: Stores log data for user activity related to song plays.
  
- **Dimension Tables**
  - `users`: User details
  - `songs`: Song information
  - `artists`: Artist information
  - `time`: Timestamps broken into different time units

## Data Pipeline Overview

The ETL process is implemented in Python and uses libraries like `pandas` and `psycopg2` to facilitate data processing and interaction with Redshift.

1. **Data Sources**
   - Song data and log data in JSON format, stored in Amazon S3.
2. **Staging Phase**
   - Load raw data into Redshift staging tables: `staging_songs` and `staging_events`.
3. **ETL Phase**
   - Transform data in staging tables and insert it into final star schema tables (`songplays`, `users`, `songs`, `artists`, `time`).

### Architecture Overview

