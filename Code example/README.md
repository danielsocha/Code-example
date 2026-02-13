# Data Engineering Notebooks (Team Version)

This folder contains three self-contained notebooks intended for technical review.

## Notebooks
1. **01_Data_Warehouse_ELT_DuckDB.ipynb**
   - Raw → Staging → Mart (Star Schema) using DuckDB
   - Demonstrates dimensional modeling and analytics-ready tables

2. **02_Incremental_Batch_Idempotency_SQLite.ipynb**
   - Daily incremental batch pattern
   - Idempotent upserts using primary keys and ON CONFLICT
   - Includes basic data-quality checks

3. **03_API_ETL_Raw_Clean_Report.ipynb**
   - API extraction with raw snapshot persistence
   - Transformation + simple reporting output
   - Includes fallback data for offline runs

## Notes
- These notebooks avoid Kubernetes/K8s by design.
- Code is function-driven with print checkpoints for transparent execution.
