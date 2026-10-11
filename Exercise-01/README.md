# Exercise 1 — Multi-Source Ingestion & Power Query ETL

**Status:** PBIX and source files are present in this repository. Validate transformations against the lab guide before claiming query-folding acceptance.

## Objective

Build a Power BI sales and monthly forecast report by combining flat files and workbook data, cleaning each source in Power Query, applying reliable data types, and creating a report that supports date-based analysis.

## Files

| File | Purpose |
|---|---|
| `PowerBI_Engineering_Lab_Exercise1.pbix` | Power BI Desktop report/model |
| `Sales_Orders.csv` | Sales-order sample data |
| `MonthlyForecast.csv` | Forecast data in monthly format |
| `Retail_CRM_and_Products.xlsx` | Customer and product reference data |
| `PowerQuery-M-Reference.md` | M-code patterns and ETL validation notes |

## Workflow

1. **Ingest sources:** import the sales CSV, forecast CSV, and Excel workbook.
2. **Clean columns:** promote headers, trim text, remove unusable rows, and standardize column names.
3. **Enforce types:** assign date, whole-number, text, and currency types explicitly.
4. **Normalize forecast:** unpivot month columns into a row-based date/forecast structure where applicable.
5. **Model:** create appropriate relationships between sales, customer/product dimensions, forecast, and date fields.
6. **Report:** use KPI cards, time trends, product analysis, and a date slicer.
7. **Audit:** check row counts, nulls, totals, date coverage, and source refresh behavior.

## Work recorded

- Monthly forecast preparation in Power Query.
- Relationships between sales, reference tables, forecast, and date data.
- Total Sales and Total Orders cards.
- Visuals for quantity, forecast, sales over time, forecast by month, and sales by product.
- Date slicer for interactive filtering.

## Lab-guide engineering checks

- [ ] Parameterize source paths/server values instead of hardcoding environment-specific values.
- [ ] Confirm query folding is available for supported SQL transformations using **View Native Query** where applicable.
- [ ] Disable load for intermediate staging queries that should not appear in the model.
- [ ] Confirm the forecast table has a useful date column and numeric forecast amount.
- [ ] Refresh the report from a clean session and verify totals.

> Query folding is source- and transformation-dependent. Do not mark it as verified unless you checked it in Power Query.

## Open the project

Open `PowerBI_Engineering_Lab_Exercise1.pbix` in Power BI Desktop. If a source path cannot be resolved, update the source parameter/path and refresh.
