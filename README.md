# AWS End-to-End Data Engineering Pipeline

## Project Overview

This project demonstrates an end-to-end data engineering pipeline on AWS, designed to replicate transactional data from PostgreSQL into analytical data systems.

### Business Problem

In a typical e-commerce application, PostgreSQL handles operational transactions such as customer orders and payments. Running complex analytical queries on the same database can compete with transactional workloads and affect application performance.

### Solution

The pipeline uses AWS Database Migration Service (DMS) for initial data loading and Change Data Capture (CDC). Transactional data is replicated to Amazon S3 and Amazon Redshift, while AWS Glue and Amazon Athena support data cataloging and SQL analytics.

The project also includes SQL performance benchmarking to examine the differences between transactional and analytical workloads.

## Architecture

```mermaid
flowchart LR
    A[Amazon RDS PostgreSQL] -->|Full Load + CDC| B[AWS DMS]
    B --> C[Amazon S3]
    C --> D[AWS Glue Data Catalog]
    D -.-> E[Amazon Athena]
    C --> F[Amazon Redshift]
    F --> G[Staging + MERGE]
```

For details, see [Architecture Documentation](architecture/README.md).

## Technology Stack

| Technology | Role in the Project |
|---|---|
| Amazon RDS (PostgreSQL) | OLTP source database for transactional data |
| AWS DMS | Full-load migration and Change Data Capture (CDC) |
| Amazon S3 | Raw data storage and data lake |
| AWS Glue | Data Catalog and metadata management |
| Amazon Athena | Serverless SQL analytics on S3 data |
| Amazon Redshift | OLAP data warehouse for analytical queries |
| SQL | Data transformation, incremental MERGE, and performance benchmarking |
