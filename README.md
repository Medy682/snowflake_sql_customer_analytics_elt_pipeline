
# Snowflake Data Pipeline CI/CD [![Snowflake Data Pipeline CI/CD](https://github.com/Medy682/snowflake_sql_customer_analytics_elt_pipeline/actions/workflows/snowflake_pipeline.yml/badge.svg)](https://github.com/Medy682/snowflake_sql_customer_analytics_elt_pipeline/actions/workflows/snowflake_pipeline.yml)


Author: Kidima Medy Masuka 

Date: 2026

# 🚀 Snowflake Sql Customer Analytics Elt Pipeline

The Snowflake Sql Customer Analytics Elt Pipeline is an end-to-end ELT data engineering solution designed to ingest, process, transform, and analyze customer sales data using a modern cloud data stack.

In this project, I designed and deployed a complete Snowflake-based ELT pipeline integrated with Azure Data Factory, Azure Key Vault, and GitHub Actions CI/CD automation. The solution was built using enterprise-style cloud data engineering practices with a strong focus on orchestration, security, automation, reliability, and production-ready deployment workflows.

---

# 📌 Project Overview

This pipeline was designed using a layered ELT architecture with a strong focus on:

- Cloud data warehousing
- Workflow orchestration
- CI/CD automation
- Incremental loading
- Data quality validation
- Secure credential management
- Analytics-ready dimensional modeling

The solution uses Snowflake for data warehousing, Azure Data Factory for orchestration, Azure Key Vault for secret management, and GitHub Actions for automated deployment workflows.

---

# ⚡ Key Features

✅ Snowflake cloud data warehouse

✅ Azure Data Factory orchestration

✅ GitHub Actions CI/CD pipeline

✅ Azure Key Vault integration

✅ RSA key-pair authentication

✅ Incremental loading using watermarking and CDC

✅ Data quality validation checks

✅ Layered ELT architecture

✅ Star schema dimensional modeling

✅ Automated deployment workflows

---

# 📊 Architecture Diagram

![Architecture](docs/Architecture.png)

---

# 🔄 ELT Workflow

![ELT_Workflow](docs/ELT_workflow.png)

---

# ⚙️ ADF Pipeline Orchestration

![adf_pipeline_orchestration_diagram](docs/adf_pipeline_orchestration_diagram.png)

---

# 🚀 Quick Start

## 1️⃣ Clone the Repository

```bash
git clone https://github.com/Medy682/snowflake_sql_customer_analytics_elt_pipeline.git
cd snowflake_sql_customer_analytics_elt_pipeline
```

## 2️⃣ Configure Environment Variables

Update the configuration files inside the `config/` folder:

- `.env.example`
- `snowflake_config.yml`
- `pipeline_config.yml`

Add your:

- Snowflake credentials
- Azure configuration
- Key Vault details

### Example `.env.example`

```env
SNOWFLAKE_USER=your_username
SNOWFLAKE_ACCOUNT=your_account
KEY_VAULT_NAME=your_key_vault
```
---

## 3️⃣ Upload Raw CSV Files

Place source datasets inside:

```text
data/raw/
```

---

## 4️⃣ Run Snowflake SQL Scripts

Execute SQL scripts in sequence:

```text
1_setup/
2_schemas/
3_external_stage/
4_metadata/
5_raw/
6_staging/
7_data_quality/
8_analytics/
9_incremental/
```

---

## 5️⃣ Trigger the Pipeline

Run the Azure Data Factory pipeline manually or through scheduled triggers.

---

# 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| Snowflake | Cloud data warehouse |
| SQL |  Data transformation and modeling |
| Azure Data Factory |  Pipeline orchestration |
| Azure Key Vault |  Secret management |
| GitHub Actions |  CI/CD automation |
| Git & GitHub |  Version control and repository hosting |
| YAML |  Pipeline configuration |
| CSV |  Raw source datasets |

---

# 🏗️ Data Pipeline Architecture

The pipeline follows a layered ELT architecture:

```text
Raw CSV Data
      │
      ▼
RAW Schema
      │
      ▼
STAGING Schema
(Cleaning & Standardization)
      │
      ▼
ANALYTICS Schema
(Star Schema Modeling)
      │
      ▼
Fact & Dimension Tables
      │
      ▼
Business Analytics Views
```

Supporting schemas:

### DATA_QUALITY
- Null checks
- Duplicate checks
- Schema validation
- Data consistency validation

### METADATA
- Watermark tracking
- Pipeline logging
- Audit tables

---

# 🔁 Incremental Loading & CDC

The project implements incremental loading using:

- Watermark tables
- CDC logic
- MERGE operations

This allows the pipeline to process only new or updated records while improving efficiency and scalability.

---

# 🔐 Security & Authentication

The pipeline uses:

- RSA key-pair authentication
- Azure Key Vault secret storage
- Azure Managed Identity integration

This enables secure automated authentication without exposing credentials directly in code.

---

# ⚙️ CI/CD Automation

I improved deployment reliability by implementing idempotent SQL deployment logic using IF NOT EXISTS statements and repeatable deployment patterns. This resolved Snowflake object creation conflicts and prevented repeated CI/CD deployment failures.

As a result:

deployment scripts run consistently without failure,
GitHub Actions deployments became more reliable,
and SQL compilation conflicts across environments were eliminated.

# ✅ Data Quality Validation

The project includes multiple validation layers to improve data reliability.

Validation checks include:

- Null value checks
- Duplicate detection
- Table validation
- Row count validation
- Schema consistency checks

Validation scripts are stored in:

```text
tests/data_quality/
```

---

# 📈 Analytics Layer

The analytics layer implements a dimensional star schema.

### Fact Table
- `fact_sales`

### Dimension Tables
- `dim_customer`
- `dim_products`
- `dim_date`

---

# 📊 Analytical Views

The project includes analytical views such as:


✅ Sales by country

✅ Sales by category

✅ Sales by date

✅ Top customers by revenue

✅ Number of orders per customer

✅ Average order value per customer

✅ Top 5 best-selling products

✅ Quantity sold per product

✅ Yearly sales trends

✅ Year-over-year sales change


A global KPI summary view was also created to provide high-level business metrics.

These views support reporting and business analysis.

---

## 📂 Repository Structure

```text
Snowflake_Sql_Customer_Analytics_Elt_Pipeline
├── .github/
│   └── workflows/
│       └── snowflake_pipeline.yml
├── adf/
│   ├── linked_services/
│   ├── pipelines/
│   └── screenshots/
│        ├── adf_pipeline_runs.png
│        ├── adf_trigger_runs.png
│        ├── key_vault_linked_service.png 
│        ├── orchestration_monitoring.png
│        ├── snowflake_linked_service.png
│        └── successful_pipeline_execution.png
│
├── config/
│   ├── snowflake_config.yml
│   ├── pipeline_config.yml
│   └── .env.example
├── data/
│   └── raw/
│       ├── country_raw.csv
│       ├── customer_raw.csv
│       ├── product_raw.csv
│       └── sales_raw.csv
├── docs/
│   ├── architecture.png
│   ├── elt_workflow.png
│   └── adf_pipeline_orchestration_diagram.png
├── screenshots/
│   └── (25+ project screenshots)
├── snowflake/
│   ├── Query_run/
│   │   └── Alter_warehouse.sql
│   ├── 1_setup/
│   │   └── 01_create_database.sql
│   ├── 2_schemas/
│   │   └── 02_create_schemas.sql
│   ├── 3_external_stage/
│   │   ├── 03_create_stage.sql
│   │   └── 04_create_file_format.sql
│   ├── 4_metadata/
│   │   ├── 05_create_logging_tables.sql
│   │   ├── 06_create_metadata_tables.sql
│   │   └── 07_create_dq_results_tables.sql
│   ├── 5_raw/
│   │   ├── 08_create_raw_tables.sql
│   │   └── 09_load_data_into_raw_tables.sql
│   ├── 6_staging/
│   │   └── 10_staging_transformations.sql
│   ├── 7_data_quality/
│   │   └── 11_data_quality_checks.sql
│   ├── 8_analytics/
│   │   └── 12_analytics.sql
│   └── 9_incremental/
│       ├── 13_get_watermark.sql
│       ├── 14_incremental_extract.sql
│       ├── 15_merge_sales.sql
│       └── 16_update_watermark.sql
├── tests/
│   └── data_quality/
│       ├── test_null_values.sql
│       ├── test_duplicates.sql
│       ├── test_row_counts.sql
│       └── test_table_exists.sql
└── README.md
```

---

# 📸 Project Screenshots

##  ⚒ Orchestration

###  ✅ adf_pipeline_runs

![adf_pipeline_runs](adf/screenshots/adf_pipeline_runs.png)

###  ✅ adf_trigger_runs

![adf_trigger_runs](adf/screenshots/adf_trigger_runs.png)

###  ✅ Snowflake linked service success

![Snowflake linked service success](adf/screenshots/snowflake_linked_service.png)

###  ✅ Key Vault integration

![Key Vault integration](adf/screenshots/key_vault_linked_service.png)

---

# 🧠 Engineering Challenges Solved

During this project, I worked through several real-world engineering challenges, including:

- Snowflake authentication troubleshooting
- RSA key rotation
- CI/CD deployment validation
- Incremental loading implementation
- Azure Key Vault access configuration
- SQL deployment conflict resolution
- Pipeline orchestration debugging

These experiences helped strengthen my practical cloud data engineering and troubleshooting skills.

---

# 🎯 Skills Demonstrated

- Data Engineering
- ELT Pipeline Development
- Cloud Data Warehousing
- CI/CD Automation
- Azure Data Factory
- Snowflake SQL Development
- Incremental Loading
- Data Quality Engineering
- Dimensional Modeling
- GitHub Actions

---

# 👤 Author

**Kidima Medy Masuka**

Junior Data Engineer

Focused on:
- Data Engineering
- Data Analytics
- Machine Learning
- Data-Driven Decision Making

---

# 📌 Portfolio Note

This project was built for educational and portfolio purposes to demonstrate practical cloud data engineering skills using modern data platform technologies.

If reused or adapted, appropriate credit must be given to the author.

📰This project is part of my personal data science and analytics portfolio ✅