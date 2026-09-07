# Olist E-Commerce Analytics — Microsoft Fabric

An end-to-end e-commerce analytics project built using Microsoft Fabric.

## Project Overview

This project takes raw Olist e-commerce data through a complete data pipeline, from ingestion and transformation to data modeling and Power BI reporting.

The solution follows a Medallion Architecture:

**Bronze → Silver → Gold → Semantic Model → Power BI**

## Architecture

![Project Architecture](architecture/01_Architecture_Flowchart.png)

## Technologies

- Microsoft Fabric
- Lakehouse
- PySpark
- Delta Tables
- Star Schema
- ## Data Pipeline

### Bronze Layer

Raw Olist CSV files were ingested into a Microsoft Fabric Lakehouse.

The Bronze layer contains the original datasets for:

- Orders
- Customers
- Order Items
- Payments
- Reviews
- Products
- Sellers
- Product Category Translation

### Silver Layer

The raw data was cleaned and transformed using PySpark.

Key transformations included:

- Removing duplicate records
- Standardizing IDs and categorical values
- Converting columns to appropriate data types
- Converting timestamp fields
- Validating keys and record relationships
- Cleaning product, customer, seller, payment and review data

The cleaned data was stored as Delta tables in the Silver Lakehouse.

### Gold Layer

The Gold layer was designed as a star schema for analytics.

**Dimensions**

- `dim_customer`
- `dim_product`
- `dim_seller`
- `dim_category`
- `dim_date`
- `dim_order`

**Facts**

- `fact_order_items`
- `fact_payments`
- `fact_reviews`
- Power BI Semantic Model
- DAX
