# AWS Data Pipeline Architecture

## Overview

This architecture shows the end-to-end data flow of the project.

Transactional data is stored in Amazon RDS PostgreSQL. AWS Database Migration Service (DMS) performs full load and Change Data Capture (CDC) to replicate data into Amazon S3. The data is then queried and processed through AWS analytics services, including AWS Glue, Amazon Athena, and Amazon Redshift.

## Data Flow

```mermaid
flowchart LR
    A[Amazon RDS PostgreSQL<br/>OLTP - Transactional Data]
    B[AWS DMS<br/>Full Load + CDC]
    C[Amazon S3<br/>Raw Data Lake]
    D[AWS Glue<br/>Data Catalog]
    E[Amazon Athena<br/>SQL Analytics]
    F[Amazon Redshift<br/>Data Warehouse]
    G[Staging + MERGE<br/>Incremental Processing]

    A --> B
    B --> C
    C --> D
    D --> E
    C --> F
    F --> G
