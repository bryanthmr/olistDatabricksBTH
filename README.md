# 📊 Azure Databricks ETL Pipeline – Bronze / Silver / Gold

## 📌 Project Overview
This personal project aims to design and implement a **complete ETL pipeline** on **Microsoft Azure** using **Azure Databricks** and **Delta Lake**, following **data engineering best practices**.  
The objective is to ingest raw datasets, clean and transform them efficiently, and expose curated analytical tables ready for Business Intelligence use cases.

The project follows a **Bronze / Silver / Gold architecture**, ensuring data quality, scalability, and performance.

---

## 🏗️ Architecture Overview

CSV (Kaggle)

↓

Azure Data Lake Storage Gen2

── Bronze → Raw data (Delta Parquet)

── Silver → Cleaned & structured data

── Gold → Fact & Dimension tables

↓

Databricks SQL Tables

---

## 🧰 Tech Stack
- **Azure Databricks**
- **Apache Spark (PySpark & SQL)**
- **Delta Lake**
- **Azure Data Lake Storage Gen2**
- **Git / GitHub (version control)**

---

## 📂 Notebooks Description

### 1️⃣ `CSV_to_DELTA.ipynb` – Ingestion (Bronze)
- Ingest CSV datasets from Kaggle  
- Store raw data in **Azure Data Lake Gen2**  
- Convert CSV files to **Delta Parquet format**  
- Secure access using **Databricks Secrets**

**Purpose:**  
Create a reliable and scalable raw data layer while benefiting from Delta Lake features (compression, schema enforcement).

---

### 2️⃣ `Data profile.ipynb` – Data Profiling
- Explore datasets structure  
- Analyze null values and distributions  
- Perform a preliminary data quality diagnosis  

**Purpose:**  
Understand the data before transformation and avoid blind processing.

---

### 3️⃣ `BRONZE_TO_SILVER.ipynb` – Cleaning & Transformation (Silver)
- Filter irrelevant records  
- Select useful columns  
- Apply data type corrections  
- Standardize and clean datasets  
- Store cleaned data in **Delta Parquet (Silver layer)**  

**Purpose:**  
Provide clean, reliable, and performant datasets for analytical modeling.

---

### 4️⃣ `SILVER_TO_GOLD.ipynb` – Analytical Modeling (Gold)
- Perform joins between datasets  
- Build **fact tables** and **dimension tables**  
- Create calculated columns optimized for large volumes  
- Store curated analytical datasets in the **Gold layer**  

**Purpose:**  
Prepare data for BI consumption using a **Galaxy schema approach** and offload heavy transformations from BI tools.

---

### 5️⃣ `DELTA_TO_TABLES.ipynb` – Data Exposure
- Create a Databricks database  
- Register Delta files as SQL tables using:

```sql
CREATE TABLE IF NOT EXISTS
USING DELTA
LOCATION '...'
