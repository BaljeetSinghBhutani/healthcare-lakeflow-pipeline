# 🏥 Healthcare Data Pipeline using Databricks Lakeflow Declarative Pipelines

A production-style Healthcare Data Engineering project built using **Databricks Lakeflow Declarative Pipelines (formerly Delta Live Tables)**, **Delta Lake**, and **Medallion Architecture**.

The pipeline ingests raw healthcare datasets, applies incremental processing and data quality validations, and produces analytical Gold-layer datasets for reporting.

---

# 🚀 Project Overview

Healthcare organizations generate patient records every day. Processing these records efficiently while maintaining data quality is essential for reporting and analytics.

This project demonstrates how to build an incremental ETL pipeline using Databricks Lakeflow Declarative Pipelines.

The solution follows the Medallion Architecture:

- Bronze Layer
- Silver Layer
- Gold Layer

using Streaming Tables and Materialized Views.

---

# 🏗 Solution Architecture

```

Healthcare CSV Files

↓

Databricks Volumes

↓

Raw Delta Tables

↓

Bronze Layer

↓

Silver Layer

↓

Gold Layer

↓

Analytics

```

---

# 🛠 Technologies Used

- Databricks
- Databricks Lakeflow Declarative Pipelines
- Delta Lake
- Databricks SQL
- Apache Spark
- PySpark
- Unity Catalog
- Databricks Volumes
- Streaming Tables
- Materialized Views
- GitHub

---

# 📂 Dataset

The project uses two healthcare datasets:

### Patient Daily Records

Contains:

- Patient ID
- Name
- Age
- Gender
- Address
- Contact Number
- Admission Date
- Diagnosis Code

### Diagnosis Mapping

Maps diagnosis codes to diagnosis descriptions.

---

# 🔄 Pipeline Workflow

## Step 1

Read CSV files from Databricks Volumes.

↓

Store them as Delta Tables.

↓

Raw Tables

```

raw_patients_daily

raw_diagnosis_map

```

---

## Step 2

Bronze Layer

Creates:

- daily_patients (Streaming Table)
- diagnostic_mapping_v1 (Materialized View)

---

## Step 3

Silver Layer

Joins

daily_patients

+

diagnostic_mapping_v1

↓

Creates

processed_patient_data

Data Quality Rules:

- Patient ID cannot be NULL
- Name cannot be NULL
- Age cannot be NULL
- Gender cannot be NULL
- Address cannot be NULL
- Contact Number cannot be NULL
- Admission Date cannot be NULL

Invalid records are automatically dropped using Lakeflow Expectations.

---

## Step 4

Gold Layer

Creates analytical datasets:

### patient_statistics_by_gender

Contains

- Patient Count
- Average Age
- Minimum Age
- Maximum Age
- Unique Diagnosis Count

### patient_statistics_by_diagnosis

Contains

- Patient Count
- Average Age
- Minimum Age
- Maximum Age
- Unique Gender Count

---

# ⚡ Incremental Processing

The pipeline processes only newly appended records.

Example:

Initial Load

100 Records

↓

15 New Records Arrive

↓

Pipeline Processes Only

15 New Records

instead of reprocessing all 115 records.

This significantly improves pipeline efficiency.

---

# ✅ Data Quality

Lakeflow Expectations are used to ensure data quality.

Records violating mandatory field constraints are automatically dropped before reaching downstream tables.

---

# 📊 Pipeline Graph

The pipeline execution graph is shown below.

(Add your screenshot here)

---

# 📁 Project Structure

```

healthcare-lakeflow-pipeline

│

├── notebooks

│ ├── 01_ingest_raw_data.py

│ └── 02_healthcare_lakeflow_pipeline.sql

│

├── screenshots

│ └── pipeline_graph.png

│

├── README.md

├── LICENSE

└── .gitignore

```

---

# 💡 Key Features

- Incremental Data Processing
- Medallion Architecture
- Streaming Tables
- Materialized Views
- Delta Lake
- Lakeflow Declarative Pipelines
- Data Quality Expectations
- Healthcare Analytics

---

# 📈 Skills Demonstrated

- Data Engineering
- ETL Pipeline Design
- Databricks
- Delta Lake
- Apache Spark
- SQL
- Data Quality Validation
- Incremental Processing
- Git & GitHub

---

# 🔮 Future Improvements

- Implement Databricks Auto Loader for automatic file ingestion.
- Add workflow scheduling.
- Integrate Power BI dashboards.
- Add unit testing for pipeline validation.
- Parameterize source and target paths.

---

# 👨‍💻 Author

Developed as a portfolio project to demonstrate modern Data Engineering concepts using Databricks Lakeflow Declarative Pipelines.
