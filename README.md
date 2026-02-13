# Data Engineering Notebooks

This repository contains three self-contained data engineering projects designed to demonstrate practical data modeling, batch processing, and ingestion patterns. The implementations are intentionally infrastructure-agnostic and runnable locally to facilitate technical review.

The goal is to showcase clear architectural thinking, reproducible pipelines, and maintainable Python-based data workflows.

---

## Repository Structure

```
.
├── 01_Data_Warehouse_ELT_DuckDB.ipynb
├── 02_Incremental_Batch_Idempotency_SQLite.ipynb
├── 03_API_ETL_Raw_Clean_Report.ipynb
├── data/
└── README.md
```

---

## Projects

### 1. Data Warehouse ELT (DuckDB)

Implements a layered ELT architecture:

- `raw` layer: landing tables with minimal transformation
- `staging` layer: type enforcement and basic cleansing
- `mart` layer: dimensional model (star schema)

The mart includes:

- `dim_customer`
- `dim_date`
- `fact_orders`

This notebook demonstrates dimensional modeling, schema separation by layer, and warehouse-oriented data transformations suitable for BI workloads.

In production, this pattern maps directly to Snowflake, Redshift, or BigQuery-based warehouses.

---

### 2. Incremental Batch Pipeline with Idempotent Upserts (SQLite)

Simulates a daily incremental batch process with:

- Deterministic transaction generation
- Primary-key-based idempotency
- `ON CONFLICT DO UPDATE` upsert strategy
- Basic data quality validation
  - Null checks
  - Duplicate detection
  - Value validation

The pipeline supports safe reprocessing of the same execution date without data duplication.

This pattern mirrors Airflow-orchestrated batch jobs backed by relational databases.

---

### 3. API Ingestion with Raw Snapshot Strategy

Implements a simple extraction workflow:

- Data extraction from a public API
- Persistence of raw JSON snapshot (raw zone)
- Transformation into analysis-ready structure
- Aggregated reporting output

A fallback dataset is included to ensure the notebook remains executable without internet access.

This reflects a common ingestion pattern where raw data is persisted for reproducibility and lineage before transformation.

---

## Engineering Approach

The notebooks emphasize:

- Functional decomposition
- Explicit execution flow
- Idempotent processing patterns
- Layered data modeling
- Basic observability through execution checkpoints
- Local reproducibility

The code favors clarity and traceability over framework abstraction.

---

## Requirements

Install dependencies:

```bash
pip install pandas duckdb requests
```

SQLite is included with Python and requires no additional installation.

---

## Running the Notebooks

```bash
jupyter notebook
```

Execute each notebook from top to bottom.

No external services are required. All notebooks run locally.

---

## Production Mapping

| Notebook | Production Equivalent |
|----------|----------------------|
| DuckDB ELT | Snowflake / Redshift / BigQuery |
| SQLite Batch | Airflow + Postgres |
| API ETL | Lambda / Batch + Object Storage |

---

## Intended Use

This repository is intended for:

- Technical interviews
- Code review discussions
- Architecture walkthroughs
- Demonstration of data engineering fundamentals

---

## Author

Daniel Socha  
Data Engineer / Data Scientist
