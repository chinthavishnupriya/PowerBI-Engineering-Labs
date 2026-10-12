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

## Suggested workflow

1. Keep the three source files in the same project folder and record their source paths.
2. In Power BI Desktop, use **Get Data** to import the sales CSV, CRM/product workbook, and forecast CSV.
3. In Power Query, check headers and data types before applying transformations. Use Date for date fields, numeric types for quantities/prices, and text for identifiers that must retain their formatting.
4. Clean customer text and email fields consistently; inspect nulls and malformed values instead of silently treating them as valid.
5. Unpivot the monthly forecast columns into a row-based structure with a period column and a forecast-value column.
6. Review query dependencies and keep staging queries distinct from the final model tables where practical.
7. Close and apply, then compare the row counts and key totals against the source data.
8. Build the report visuals and test the date slicer against multiple selections.

## Data model and checks

The project notes describe a product dimension derived from forecast/product data, retaining ProductID and ProductName and removing duplicates. If that table is used in the current PBIX, verify that ProductID is unique and that relationships to sales and forecast tables use the intended keys and cardinality.

- Confirm each query loads the expected number of rows.
- Check for blank or duplicate business keys before creating relationships.
- Verify that forecast unpivoting creates one row per product/period combination where expected.
- Check that sales and forecast totals remain sensible after transformations.
- Refresh the report after changing source paths or transformations.

## Troubleshooting

- **File not found:** update the source path in Power Query to the local project folder.
- **Dates appear as text:** set the correct locale and Date data type.
- **Forecast values are in separate month columns:** select the month columns and use Unpivot Columns.
- **Totals change unexpectedly:** check duplicate keys, join expansion, filters, and data types.

## Validation record

This README describes the intended workflow and work documented for the exercise. Confirm actual query settings, parameters, query folding, and final totals inside the saved PBIX before claiming those items are fully validated.
