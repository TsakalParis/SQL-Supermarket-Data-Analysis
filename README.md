# Supermarket Data Analysis using SQL and PySpark

A comprehensive data analysis project exploring supermarket order patterns and product performance using SQL queries and PySpark.

## 📊 Overview

This project analyzes supermarket transaction data to uncover insights about customer behavior, product popularity, and reordering patterns. Using PySpark for data processing and SQL for analytics, the project demonstrates how to effectively query and manipulate large datasets in a Databricks environment.

Key analyses include:
- Identifying top products with the most reorders
- Analyzing ordering patterns across departments and aisles
- Data transformation and storage optimization

## 📈 Data Sources

The project utilizes multiple related datasets:

1. `order_products.csv` - Links orders with products and indicates if items were reordered
2. `products.csv` - Product details including names and department information
3. `orders_small_version.csv` - Order information including timestamps and customer data
4. `departments.csv` - Department classifications
5. `aisles.csv` - Aisle classifications

## 🔧 Technical Implementation

### Technologies Used
- **PySpark**: Data processing and transformation
- **SQL**: Data querying and analysis
- **Databricks**: Notebook environment for execution
- **Pandas**: Additional data manipulation

### Key Components
- Data loading from CSV files into Spark DataFrames
- Schema inference and validation
- Creation of temporary views for SQL querying
- Custom functions for file format conversion (CSV, Parquet, etc.)

## 🚀 Key Features

1. **Efficient Data Loading**
   - Automatic schema inference
   - Support for multiple file formats
   - Streamlined data import process

2. **Flexible SQL Analytics**
   - Complex join operations
   - Aggregation and grouping
   - Sorting and filtering

3. **File Format Optimization**
   - Conversion between different file formats (CSV, Parquet, etc.)
   - Support for 10+ file formats including Pickle, JSON, Excel

## 📋 Usage

### Setting Up
1. Upload the CSV files to your Databricks File System (DBFS)
2. Update file locations in the notebook if necessary

### Running Analyses
The notebook includes examples of:
```sql
-- Example: Top 10 products with the most reorders
SELECT order_products.product_id, products.product_name, SUM(order_products.reordered) AS reordered_sum
FROM order_products
INNER JOIN products ON order_products.product_id = products.product_id
GROUP BY order_products.product_id, products.product_name
ORDER BY sum(order_products.reordered) DESC
LIMIT 10;
```

### File Conversion Utility
The project includes custom functions for reading and writing data in multiple formats:

```python
# Reading files
name, file = read_file(filename, read_path)

# Converting to different format
save_file(name, "parquet", save_path, new_filename)
```

## 📝 Project Structure

```
Supermarket-Data-Analysis-using-SQL/
├── data/
│   ├── aisles.csv
│   ├── departments.csv
│   ├── order_products.csv
│   ├── orders_small_version.csv
│   ├── products.csv
│   └── parquet/
│       ├── p_aisles
│       ├── p_departments
│       └── ...
├── notebooks/
│   └── supermarket_analysis.ipynb
└── README.md
```

## 🔍 Sample Insights

The analysis reveals:
- Most frequently reordered products
- Popular product categories
- Customer ordering patterns

## 📚 Future Enhancements

Potential areas for expansion:
- Time series analysis of ordering patterns
- Customer segmentation based on product preferences
- Recommendation system for frequently paired products
- Prediction of reorder probabilities

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

---

*Note: This analysis was performed in a Databricks notebook environment. The code can be adapted for use in standard PySpark environments with minimal modifications.*
