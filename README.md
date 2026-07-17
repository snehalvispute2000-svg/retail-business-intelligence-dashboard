# Retail Business Intelligence Dashboard

## Project Overview

This project presents an interactive Power BI dashboard designed to analyze retail business performance across customers, products, stores, locations, and time periods.

The dashboard provides executive-level insights into revenue, profit, profitability, customer demographics, product performance, and store efficiency.

The project is divided into three report pages:

1. Executive Summary
2. Customer Demographics
3. Product & Store Performance

---

## Business Objectives

The main objectives of this project are:

- Track total revenue, profit, cost, and transactions
- Compare current revenue with previous-year revenue
- Monitor year-over-year growth
- Analyze profitability and profit margin
- Identify top-performing products and brands
- Evaluate store and city-level performance
- Understand customer demographic patterns
- Identify high-value customers
- Support business decisions using interactive visual analysis

---

## Dataset

The project uses multiple related retail datasets:

- Calendar
- Customers
- Products
- Regions
- Stores
- Transactions 1997
- Transactions 1998

The transaction files were combined and connected with the dimension tables using a star-schema-style data model.

---

## Data Model

The main relationships include:

- Calendar to Transactions
- Customers to Transactions
- Products to Transactions
- Stores to Transactions
- Regions to Stores

The model uses one-to-many relationships between dimension tables and the transaction fact table.

---

## Dashboard Pages

### 1. Executive Summary

The Executive Summary page provides a high-level overview of business performance.

#### KPI Cards

- Total Revenue
- Total Profit
- Profit Margin %
- YoY Growth %
- Revenue YTD
- Revenue PY
- Total Transactions
- Return Rate %

#### Visuals

- Total Revenue and Revenue PY by Month
- Total Revenue by Store City
- Top 10 Products by Total Revenue
- Year, Country, and Product Brand slicers

#### Key Insights

- Revenue and cost move closely across product and store activity.
- A limited number of products and locations contribute significantly to total revenue.
- Year-over-year comparison helps identify business growth and performance changes.

---

### 2. Customer Demographics

This page analyzes customer segments and customer-level business contribution.

#### KPI Cards

- Total Customers
- Average Revenue per Customer
- Average Transactions per Customer
- Profit per Customer

#### Visuals

- Revenue by Gender
- Revenue by Marital Status
- Revenue by Education
- Top 50 Customers by Total Revenue

#### Matrix Columns

- Customer Name
- Total Revenue
- Total Transactions
- Total Profit

#### Key Insights

- Revenue contribution differs across customer demographic segments.
- A relatively small number of customers generate a large share of total revenue.
- Customer segmentation can support targeted marketing and retention strategies.

---

### 3. Product & Store Performance

This page evaluates product brands, store types, and store-level profitability.

#### KPI Cards

- Total Stores
- Total Brands
- Revenue per Store
- Profit per Store

#### Visuals

- Store Performance Matrix
- Revenue vs Total Cost by Product Brand Scatter Plot

#### Store Matrix Fields

Rows:

- Store Type
- Store Name

Values:

- Total Revenue
- Total Profit
- Profit Margin %

#### Scatter Plot Fields

- X-Axis: Total Cost
- Y-Axis: Total Revenue
- Legend: Product Brand
- Size: Total Profit
- Tooltips: Revenue, Profit, Profit Margin %, Total Transactions

#### Key Insights

- Revenue generally increases with total cost across product brands.
- Top-performing brands contribute significantly to overall revenue and profit.
- Profit-margin analysis helps identify brands with better operational efficiency.

---
## DAX Measures

**Total Revenue** =
SUMX(
    Transactions,
    Transactions[quantity] *
    RELATED(Products[product_retail_price])
)

**Total Cost** =
SUMX(
    Transactions,
    Transactions[quantity] *
    RELATED(Products[product_cost]))

**Total Profit** =
[Total Revenue] - [Total Cost]


**Profit Margin %** =
DIVIDE(
    [Total Profit],
    [Total Revenue],
    0)

**Total Transactions** =
COUNTROWS(Transactions)

**Revenue PY** =
CALCULATE(
    [Total Revenue],
    SAMEPERIODLASTYEAR(Calendar[Date]))

**Revenue YTD** =
TOTALYTD(
    [Total Revenue],
    Calendar[Date])


**YoY Growth %** =
DIVIDE(
    [Total Revenue] - [Revenue PY],
    [Revenue PY],
    0)

**Return Rate %** =
DIVIDE(
    [Returned Transactions],
    [Total Transactions],
    0)

**Total Customers** =
DISTINCTCOUNT(Customers[customer_id])


**Average Transactions per Customer** =
DIVIDE(
    [Total Transactions],
    [Total Customers],
    0)

**Profit per Customer** =
DIVIDE(
    [Total Profit],
    [Total Customers],
    0)

**Total Stores** =
DISTINCTCOUNT(Stores[store_id])

**Total Brands** =
DISTINCTCOUNT(Products[product_brand])

**Revenue per Store** =
DIVIDE(
    [Total Revenue],
    [Total Stores],
    0)

**Profit per Store** =
DIVIDE(
    [Total Profit],
    [Total Stores],
    0)

**Dashboard Features**
- Interactive slicers
- Page-navigation buttons
- Previous-year comparison
- Year-to-date analysis
- Conditional formatting
- Revenue data bars
- Positive and negative profit indicators
- Dynamic filtering
- Map-based store-city analysis
- Product-brand profitability analysis
- Custom Canva background
- Consistent corporate color theme

**Tools Used**
- Power BI Desktop
- Power Query
- DAX
- Canva
- Microsoft Excel / CSV

**Skills Demonstrated**
- Data modeling
- DAX measure creation
- Time-intelligence calculations
- Dashboard design
- Data visualization
- KPI development
- Customer segmentation
- Product analysis
- Store analysis
- Profitability analysis
- Business storytelling
- Conditional formatting
- Interactive report navigation

**Business Value**

This dashboard enables business stakeholders to:

- Monitor overall financial performance
- Compare current and previous-year revenue
- Identify profitable stores and brands
- Detect high-value customer segments
- Understand geographic sales performance
- Improve product, inventory, pricing, and marketing decisions

