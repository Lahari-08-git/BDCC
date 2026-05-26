# Branded Food Analytics using Azure Databricks & PySpark

## 📌 Project Overview

This project focuses on analyzing a large-scale **USDA Branded Food dataset containing approximately 9.9 million records (4.16 GB)** using a cloud-based big data architecture. The objective is to demonstrate scalable data ingestion, distributed processing, exploratory data analysis, and a simple machine learning workflow using modern cloud technologies.

The entire pipeline is implemented using **Apache Spark within Databricks**, with data stored in **Azure Blob Storage**, enabling efficient processing of large-scale structured data.

The project demonstrates how cloud computing can be used to transform raw enterprise-grade datasets into meaningful business insights such as brand dominance, category trends, geographic distribution, and predictive modeling.

---
## 🗂️ Dataset Information

The dataset used in this project is based on the **USDA FoodData Central Branded Food Products files**, which were originally provided in multiple quarterly CSV archives.

### 📥 Data Source & Construction Process

Instead of using a single pre-built dataset, the data was constructed through a merging pipeline:

1. Multiple quarterly datasets were downloaded separately:
   - 2024 Q1
   - 2024 Q2
   - 2025 Q1
   - 2025 Q2
   - 2026 Q1 (partial data)

2. Each archive contained a `branded_food.csv` file.

3. All quarterly files were merged into a single consolidated dataset:

   ```
   branded_food_all_years.csv
   ```

4. The final merged dataset was then uploaded to Azure Blob Storage for processing in Databricks.

---



### 📊 Dataset Summary
- **Source:** USDA FoodData Central
- **Format:** CSV (merged dataset)
- **Size:** ~4.16 GB
- **Total Records:** 9,911,885 rows
- **Total Features:** 24 columns

### 📌 Key Attributes
The dataset includes the following important fields:

- `fdc_id` → Unique product identifier  
- `brand_owner` → Manufacturer or brand company  
- `branded_food_category` → Product category classification  
- `ingredients` → Ingredient composition of the product  
- `serving_size` → Standard serving quantity  
- `market_country` → Country of product availability  
- `data_year` → Year of record entry  
- `data_quarter` → Time period of dataset  

These attributes enable both **market analysis and machine learning applications**.

---

## ☁️ Cloud Architecture Overview

The project follows a simple but scalable cloud-based data pipeline architecture.

```
Azure Blob Storage → Databricks (Apache Spark) → Data Cleaning → Exploratory Analysis → Machine Learning Model → Insights Generation
```

### 🔧 Technology Stack
- **Cloud Platform:** Microsoft Azure  
- **Storage Layer:** Azure Blob Storage  
- **Processing Engine:** Apache Spark (Databricks)  
- **Programming Language:** Python (PySpark)  
- **Visualization:** Built-in Databricks display functions  

This architecture ensures scalability, fault tolerance, and high-performance distributed processing for millions of records.

---

## 🧹 Data Preprocessing and Cleaning

Before performing analysis, the dataset was cleaned and optimized to ensure accuracy and consistency.

### 🧼 Cleaning Steps Performed

1. **Duplicate Removal**
   - Removed approximately **9,739 duplicate records**
   - Ensured each product entry is unique and consistent

2. **Missing Value Handling**
   - Identified missing values in critical column `brand_owner`
   - Removed **88,681 rows with null brand_owner values**

3. **Data Optimization**
   - Cached cleaned dataset in memory using Spark caching
   - Improved query performance for repeated analysis

### 📊 Final Cleaned Dataset
- **Final Rows:** 9,813,465  
- **Final Columns:** 24  
- **Data Quality:** High (less than 1% data removed)

---

## 📊 Exploratory Data Analysis (EDA)

Exploratory Data Analysis was performed using distributed Spark operations to identify trends, patterns, and anomalies in the dataset.

### 🏷️ Brand Analysis

The dataset was grouped by `brand_owner` to identify market leaders.

#### 🔝 Top Brands by Product Count
- Walmart Stores, Inc.
- Target Stores
- Meijer, Inc.
- Safeway, Inc.
- General Mills Sales Inc.

#### 📌 Key Insight
The market is highly fragmented, where even the leading brand holds only a small percentage (~2–3%) of total product listings.

---

### 🍿 Category Analysis

Product categories were analyzed using `branded_food_category`.

#### 🔝 Top Categories
- Popcorn, Peanuts, Seeds & Related Snacks  
- Candy  
- Cheese  
- Ice Cream & Frozen Yogurt  
- Cookies & Biscuits  

#### 📌 Key Insight
Snack-related categories dominate the dataset, indicating strong consumer demand in processed and packaged snack foods.

---

### 🌍 Geographic Distribution

The `market_country` field was analyzed to understand global distribution.

#### 🔝 Key Result
- United States accounts for approximately **99.7% of all products**

#### 📌 Key Insight
The dataset is heavily concentrated in the U.S. market, making it primarily a domestic food industry dataset rather than global.

---

## 📈 Time Series Analysis

The dataset was analyzed across multiple years (2024–2026).

### 📊 Yearly Distribution
- **2024:** 3.94 million products  
- **2025:** 3.97 million products  
- **2026 (Q1 only):** 1.99 million products  

### 📌 Observations
- Slight growth between 2024 and 2025  
- 2026 appears lower due to incomplete quarterly data  
- When annualized, 2026 indicates continued expansion

---

## 🤖 Machine Learning Model

A simple machine learning model was built using **Spark MLlib** to demonstrate predictive analytics.

### 🎯 Objective
Predict whether a product belongs to the dominant category:
> *Popcorn, Peanuts, Seeds & Related Snacks*

---

### ⚙️ Model Configuration
- **Algorithm:** Logistic Regression  
- **Framework:** PySpark MLlib  
- **Train/Test Split:** 70/30  
- **Features Used:**
  - brand_owner (encoded)
  - market_country (encoded)

---

### 📊 Model Performance
- **Accuracy:** 95.33%

### 📌 Interpretation
Although the model achieves high accuracy, this is influenced by class imbalance in the dataset. However, it demonstrates the ability of Spark ML to handle large-scale classification tasks efficiently.

---

## 💡 Key Business Insights

The analysis produced several meaningful insights:

### 📌 Market Structure
- Highly fragmented brand ecosystem
- No single dominant player (>3% share)

### 📌 Category Trends
- Snack foods dominate the packaged food industry
- High concentration in processed food categories

### 📌 Geographic Insight
- Strong U.S. dominance (99.7%)
- Limited international representation

### 📌 Predictive Capability
- Machine learning model successfully classifies food categories
- Demonstrates potential for automated product tagging

---

## 🚀 Conclusion

This project demonstrates how cloud computing and distributed systems can be used to process and analyze millions of records efficiently. Using Azure and Spark, the dataset was transformed into actionable insights related to brand distribution, product categories, and market trends.

The implementation also shows how machine learning can be integrated into big data pipelines to provide predictive capabilities alongside traditional analytics.

---