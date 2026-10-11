# Exercise 1 — Multi-Source Ingestion & Power Query ETL

**Main report:** PowerBI_Engineering_Lab_Exercise1.pbix  
**Goal:** Build repeatable Power Query ingestion and cleaning for CSV, Excel, and SQL sources.

## Source data

| Source | Transformation focus | Repository artifact |
|---|---|---|
| Sales orders | Promote headers, parse order dates, handle invalid rows | Sales_Orders.csv |
| Customer CRM | Combine names, clean email values, trim text | Retail_CRM_and_Products.xlsx |
| Product catalog | Filter active SKUs, set currency types, consider query folding | SQL connection is environment-specific |
| Monthly forecast | Unpivot month columns into date/amount rows | MonthlyForecast.csv |

## Report and transformation overview

The exercise focuses on parameterized data sources, separate staging queries, consistent data types, CRM text cleanup, SQL product filtering, and a normalized monthly forecast structure. Intermediate queries can be kept out of the model when they are used only for staging.

The PBIX work includes monthly forecast preparation, relationships between sales and reference data, Total Sales and Total Orders cards, visuals for quantity and sales trends, forecast-by-month and sales-by-product analysis, and a date slicer.

## Implementation approach

1. Use FilePath and ServerName parameters for environment-specific source locations.
2. Keep source queries separate so transformations can be audited.
3. Clean sales dates and numeric fields and handle invalid rows.
4. Trim CRM text, clean email values, and create a full-name field where needed.
5. Filter active product SKUs and apply appropriate data types.
6. Unpivot forecast month columns and convert month labels to dates.
7. Load only the tables required by the data model.

## Files

- PowerBI_Engineering_Lab_Exercise1.pbix — report and data model.
- Sales_Orders.csv — sales order source data.
- MonthlyForecast.csv — forecast source data.
- Retail_CRM_and_Products.xlsx — CRM and product reference workbook.
- PowerQuery-M-Reference.md — reusable M patterns and transformation notes.
