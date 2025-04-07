This project focuses on transforming raw Azure billing and pricing data into analytics-ready datasets, powering dashboards that support financial insights, usage trends, reservation effectiveness, and infrastructure optimization.

---

## 🔧 Technologies Used

- **Databricks**  
  Used for ingestion, transformation, data validation, and automation using PySpark.

- **SingleStore**  
  Serves as the final analytics database for fast querying and integration with BI tools.

- **Apache Superset**  
  Used to build interactive, multi-tab dashboards based on the processed data.

---

## 📁 Project Structure & Assets

### 🐍 Databricks Python Code
All core transformation logic (bronze → silver layers, validation, cost normalization, unit mapping, etc.) is implemented in:

- `cr.ipynb` — Databricks Notebook
- `cr.dbc` — Databricks Archive (importable)

> 💡 In the config section below, replace placeholders with your actual SingleStore credentials and **target database** for writing the final tables:

```python
spark.conf.set("spark.datasource.singlestore.ddlEndpoint", "{SINGLESTORE-HOST}")
spark.conf.set("spark.datasource.singlestore.user", "{SINGLESTORE-ADMIN}")
spark.conf.set("spark.datasource.singlestore.password", "{SINGLESTORE-PASSWORD}")
spark.conf.set("spark.datasource.singlestore.database", "test_cr")  # Customize if needed
```

- 📄 **ETL Rules & Mapping Source**:  
  ETL logic and transformation mappings were guided by the `azure.md` file, located in the `Task Text Files` folder.  
  This file was sourced from the **Focus FinOps Crayon** website as part of the original task description.

- 📊 **Dashboard**:
  Apart from the zip that containts the code for the Apache Superset Dashboard with 4 different tabs.
  Screenshots of the final dashboards are stored in the `Dashboard Screenshot` folder for quick reference and documentation.

- 🗄️ **SQL Table Definitions**:  
  `INFO - show create tables.sql` contains all `SHOW CREATE TABLE` outputs for the final SingleStore tables.  
  These tables were generated **automatically via PySpark scripts** during the transformation process.

## 📊 Features

- Clean transformation logic for Azure cost and pricing data
- Data quality validation (date parsing, null checks, numeric value constraints)
- Modular silver-layer structure that supports multiple use cases
- Superset dashboards split into tabs for cloud spend, usage trends, reservation analysis, and pricing visibility
- Scalable and maintainable design ready for future Crayon feature requests
