# Exercise 1 — Multi-Source Ingestion & Power Query ETL

**Main report:** `PowerBI_Engineering_Lab_Exercise1.pbix`  
**Goal:** Build repeatable Power Query ingestion and cleaning for CSV, Excel, and SQL sources.

## Required source matrix

| Source | Lab-guide requirement | Repository artifact |
|---|---|---|
| Sales orders | CSV ingestion; promote headers; parse order date; remove corrupt rows | `Sales_Orders.csv` |
| Customer CRM | Excel ingestion; combine first/last name; clean email; trim text | `Retail_CRM_and_Products.xlsx` |
| Product catalog | SQL Server source; filter active SKUs; enforce currency types; audit query folding | SQL connection is environment-specific; confirm it is configured in the PBIX |
| Monthly forecast | CSV ingestion; unpivot month columns into date/amount rows | `MonthlyForecast.csv` |

## Work recorded in the PBIX

- Monthly forecast preparation in Power Query.
- Relationships between sales, reference tables, forecast, and date data.
- Total Sales and Total Orders cards.
- Visuals for quantity, forecast, sales over time, forecast by month, and sales by product.
- Date slicer for interactive filtering.

## Implementation workflow

1. **Parameterize sources.** Create `FilePath` for file locations and `ServerName` for SQL Server. Avoid committing machine-specific paths.
2. **Ingest the CSVs and workbook.** Keep source queries separate so each transformation can be audited.
3. **Clean sales orders.** Promote headers, parse `OrderDate` as a date, remove invalid/corrupt rows, and set numeric fields explicitly.
4. **Clean CRM fields.** Trim text, clean email strings, and create a full-name field from first and last name if required by the workbook.
5. **Prepare product data.** Filter active SKUs and set currency/whole-number types. Verify SQL steps using **View Native Query** where supported.
6. **Normalize forecast.** Use `Table.UnpivotOtherColumns` to produce a row-based month/date and forecast amount structure. Convert the month label to a proper date.
7. **Isolate staging.** Disable load for intermediate staging queries; load only tables needed by the model.
8. **Validate.** Compare row counts and totals, check nulls/duplicates in keys, refresh from a clean session, and inspect report totals.

## Acceptance checklist

Tick an item only after checking it in Power BI Desktop.

- [ ] `FilePath` and `ServerName` parameters exist and are used by the relevant queries.
- [ ] CSV and workbook source queries refresh successfully.
- [ ] Sales headers are promoted, order dates typed, and corrupt rows handled.
- [ ] CRM first/last name and email cleanup is complete.
- [ ] Monthly forecast is unpivoted into identifier/date/amount rows.
- [ ] Product SQL query filters active SKUs and applies required types.
- [ ] **View Native Query** confirms folding for the intended SQL transformations where supported.
- [ ] Intermediate staging queries have load disabled.
- [ ] Row counts, key quality, forecast totals, and sales totals have been checked.
- [ ] PBIX reopens after download without missing-source errors.

**Important:** The PBIX and sample files are present in the repository, but file presence alone does not prove that source parameterization, query folding, or every acceptance criterion passed. Record evidence before marking them complete.

## Files

- `PowerBI_Engineering_Lab_Exercise1.pbix` — report/model.
- `Sales_Orders.csv` — order data.
- `MonthlyForecast.csv` — forecast data.
- `Retail_CRM_and_Products.xlsx` — CRM/product reference workbook.
- `PowerQuery-M-Reference.md` — adaptable M patterns and validation notes.
