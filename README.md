# Flight-Booking-Analytics-Data-Engineering-Project-using-Databricks and DBT (Data Build Tool)

This project demonstrates an end-to-end data pipeline built using **Databricks**, **Delta Live Tables**, and **DBT (Data Build Tool)** to process, transform, and model flight booking data for advanced analytics and business intelligence.

---

## 🧭 Project Overview

The project simulates a real-world data engineering workflow for ingesting flight-related datasets (passengers, bookings, flights, airports), applying transformations and data quality rules, and modeling a **star schema** for downstream analytics using **DBT**.

It covers:

- Autoloading CSVs from managed volume into **Bronze** layer
- Using **Delta Live Tables** to build the **Silver** layer with DLT expectations
- Creating a **dynamic star schema** in the **Gold** layer
- Consuming gold data using **DBT** for curated business views

---

## 🗺️ Architecture Overview

The architecture follows the modern **lakehouse paradigm** with an integrated warehouse and transformation layer.

![Project Architecture](./assets/project_architecture.png)

---

## 🥉 Bronze Ingestion Pipeline

This pipeline ingests raw CSV files using **Autoloader** and moves data into the Bronze layer using dynamic iteration logic.

- Uses a **lookup notebook** for incremental load tracking
- Autoloads multiple files using schema evolution

![Bronze Ingestion Pipeline](./assets/bronze_ingestion_pipeline.png)

---

## 🥈 Silver Layer Transformation (DLT)

The Silver layer is built using **Delta Live Tables (DLT)** with the following features:

- Streaming ingestion of data
- Transformations like joins, filtering, and normalization
- DLT **expectations** to enforce data quality

![Silver DLT Pipeline](./assets/silver_dlt_pipeline.png)

---

## 🥇 Gold Layer: Dynamic Star Schema

The Gold layer includes:

- `Gold_Dimension` notebook: dynamically creates dimension tables
- `Gold_Fact` notebook: builds the central `factbookings` table

This schema is dynamically generated to enable extensibility and modularity.

---

## 🧰 DBT for Business View Modeling

DBT is used to build curated business views on top of the gold layer. An example model aggregates booking amounts by country.

- Materialized as tables
- Maintains version control
- Enables SQL-based transformation on curated data

![DBT Model](./assets/dbt_model.png)

---

## 🗂️ Notebooks in This Project

```
flight DB & DBT/
├── Lookup Notebook.python          # Used for last load tracking
├── Bronze Layer.python             # Ingests data using Autoloader
├── DLT_DIMENSION/                  # Contains DLT streaming logic for silver layer
├── Gold_Dimension.python           # Dynamically builds star schema dimensions
├── Gold_Fact.python                # Builds the fact table
├── Script Notebook.python          # Auxiliary scripts
```




