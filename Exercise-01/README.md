# Exercise 1 — Multi-Source Ingestion & Power Query ETL

**Main report:** PowerBI_Engineering_Lab_Exercise1.pbix

## Objective

Load different source formats, clean and standardize data in Power Query, reshape forecast data, and create sales-focused report visuals.

## Source files

| Source | Use | Artifact |
|---|---|---|
| Sales orders | Transaction-level sales/order analysis | Sales_Orders.csv |
| CRM and product reference | Customer attributes and product details | Retail_CRM_and_Products.xlsx |
| Monthly forecast | Forecast values by month | MonthlyForecast.csv |
| Product catalog | SQL-source practice for product data | Local SQL Server connection |

## Transformation work

1. Load CSV and Excel sources as separate queries so each source can be inspected and transformed independently.
2. Prepare sales orders by promoting headers, setting order dates to Date, assigning numeric/text types, and handling invalid rows.
3. Clean customer fields by trimming and cleaning text, standardizing email values, and combining first/last names where appropriate.
4. Prepare product data by filtering the intended active products and assigning appropriate types to price-related columns.
5. Unpivot monthly forecast columns so each forecast period becomes a row with a month attribute and forecast amount.
6. Keep staging queries separate from final tables used by the model.
7. Compare row counts and totals, inspect keys for nulls or duplicates, and refresh the report after transformations.

The Power Query M reference contains examples for parameters, SQL-source patterns, CRM cleanup, forecast unpivoting, and query-folding inspection. These are reusable patterns, not proof that every example is configured in the PBIX. Verify parameters and View Native Query directly in Power Query before reporting them as completed.

## Report visuals

The report work includes Total Sales/Revenue and Total Orders KPI cards, sales and quantity analysis, sales trends over time, monthly forecast analysis, sales by product, and a date slicer for interactive filtering.

## Concepts practiced

- CSV and Excel connectors.
- Header promotion and explicit data types.
- Text trimming and cleaning.
- Handling invalid or missing data.
- Unpivoting wide monthly data into a normalized structure.
- Separating staging queries from model tables.
- Source parameters and SQL query-folding concepts.

## Files

- PowerBI_Engineering_Lab_Exercise1.pbix — report and model.
- Sales_Orders.csv — sales-order source.
- MonthlyForecast.csv — forecast source.
- Retail_CRM_and_Products.xlsx — CRM/product workbook.
- PowerQuery-M-Reference.md — M patterns and transformation notes.

## Outcome

Exercise 1 establishes the ETL foundation for later exercises by bringing together sales, customer/product, and forecast data and preparing them for report analysis.
