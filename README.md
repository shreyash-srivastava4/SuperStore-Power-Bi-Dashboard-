# SuperStore-Power-Bi-Dashboard-

Superstore Business Intelligence Dashboard

Tool: Microsoft Power BI
Dataset: Superstore (Public Dataset)

1. Objective of the Project

The objective of this project is to design a scalable, interactive business intelligence dashboard using the Superstore dataset that enables stakeholders to analyze sales performance, profitability, order volume, and discount behavior across multiple business dimensions.

The dashboard is built with a strong emphasis on:

Dynamic metric selection

Time-intelligence driven comparisons

Context-aware calculations

Reusable, variable-based DAX measures

Clean data modeling aligned with BI best practices

2. Dataset Description

The Superstore dataset is a widely used transactional retail dataset containing order-level information.

Key Characteristics

Transaction-level granularity

Multi-year historical data

Covers geography, products, customers, and logistics

Key Fields

Order Date, Ship Date

Sales, Profit, Quantity, Discount

Category, Sub-Category

Segment, Ship Mode

Region, State, City

3. Data Modeling Approach

A star schema data model was implemented to ensure optimal performance and clean filter propagation.

Model Structure

Fact Table

FactSales (Sales, Profit, Quantity, Discount)

Dimension Tables

DimDate

DimProducts

DimCustomers

DimLocation

DimOrders

Design Principles Applied

Single-direction relationships (1:* from dimensions to fact)

Dedicated Date table to enable time intelligence

Measures isolated in a separate Measure Table

No business logic embedded in calculated columns unless unavoidable

4. Measure Design and DAX Strategy
4.1 Variable-Based DAX Measures

All complex measures are written using DAX variables (VAR) to:

Improve readability

Reduce repeated calculations

Enhance performance

Make debugging easier

Typical pattern used:

Capture current context values

Compute intermediate results

Return final output based on business logic

4.2 Dynamic KPI Selection (Field Parameters)

A KPI Selector parameter table is used to dynamically switch between:

Sales

Profit

Quantity

Discount

This allows a single dashboard layout to respond to multiple metrics without duplicating visuals.

The selected KPI dynamically controls:

KPI cards

Charts

YoY calculations

Visual titles

Tooltip values

5. Time Intelligence & YoY Logic
Previous Year Calculations

For each metric, a Previous Year (PY) measure is defined using the Date table.

YoY Growth Logic

YoY growth is calculated dynamically based on the selected KPI and current filter context.

Key characteristics:

Context-aware across year, region, category, and state

Automatically adapts when the KPI selection changes

Returns percentage growth with proper handling of blank or zero PY values

6. Dynamic Titles Using DAX

All visual titles in the dashboard are fully dynamic and driven by DAX.

Purpose

Titles automatically reflect the selected KPI

Titles update based on year filters

Eliminates static text and manual maintenance

Example Behavior

“Sales by Region – 2017”

“Profit YoY Growth by State – 2016”

“Monthly Quantity Trend – Selected Year”

These titles are controlled using:

SELECTEDVALUE()

Field parameters

Variables to assemble readable strings

This ensures visual context is always aligned with the data being displayed.

7. Dashboard Components and Analysis
7.1 KPI Summary Section

Displays:

Current Year KPI value

Previous Year value

YoY Growth percentage

Each KPI card dynamically updates based on the selected metric and year.

7.2 Regional Performance Analysis

A bar chart visual compares performance across regions:

Central

East

South

West

The visual highlights:

Absolute contribution

YoY growth trend

Regional performance imbalance

7.3 Monthly Trend Analysis

A line chart shows month-wise performance for the selected KPI.

Key insights enabled:

Seasonality patterns

Growth and decline phases

Month-over-month volatility

YoY growth annotations are embedded to provide context beyond absolute values.

7.4 Geographic Analysis (State-Level Map)

A map visual displays state-level performance:

Bubble size represents KPI magnitude

Color segmentation by product category

This allows quick identification of:

High-performing states

Regional concentration of sales and profit

Category dominance by geography

7.5 Product Category and Sub-Category Analysis

A hierarchical breakdown visual shows:

Category contribution

Sub-category performance within each category

This helps identify:

Revenue drivers

Low-performing product lines

Portfolio concentration risk

7.6 Customer Segment and Ship Mode Analysis

Donut charts analyze:

Customer segments (Consumer, Corporate, Home Office)

Shipping modes (Standard, First Class, Second Class, Same Day)

This supports operational and customer strategy decisions.

7.7 Top 5 States Analysis

A ranked bar chart highlights:

Top 5 states by KPI value

YoY growth for each state

This enables focused regional performance tracking.

8. Interactivity and User Experience

The dashboard includes:

KPI selector buttons

Year selection slicers

Hover tooltips for contextual insights

Cross-filtering across all visuals

All interactions are controlled via DAX, not duplicated visuals.

9. Performance Considerations

Variables used extensively in DAX

No unnecessary calculated columns

Minimal use of iterators

Measures reused across visuals

Optimized filter context handling

These choices ensure the dashboard remains responsive even as data volume scales.

10. Key Business Questions Addressed

How is the business performing year-over-year?

Which regions and states are driving growth?

Which product categories and segments are most valuable?

How do trends vary month-wise?

What role do discounts play in performance?

11. Tools and Technologies

Microsoft Power BI Desktop

Power Query for ETL

DAX for calculations and logic

Star schema data modeling

12. Conclusion

This project demonstrates the application of advanced Power BI concepts including:

Variable-based DAX programming

Dynamic KPI selection

Time intelligence

Context-aware calculations

Dynamic visual titles

The result is a maintainable, scalable, and business-ready dashboard that can adapt to multiple analytical perspectives without structural changes.
