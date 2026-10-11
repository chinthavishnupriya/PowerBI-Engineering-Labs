# Exercise 3 — Advanced DAX Engine

**Status:** PBIX present; report visuals and measures were built in Power BI Desktop.  
**Main report:** `AdventureWorks_Exercise3.pbix`

## Objective

Create a centralized measures table and use DAX for sales aggregation, profitability, customer ranking, and time-intelligence calculations. The lab guide emphasizes `CALCULATE`, `DIVIDE`, `TOTALYTD`, `SAMEPERIODLASTYEAR`, `DATESINPERIOD`, and `USERELATIONSHIP`.

## Measures visible in the model

The current model's `_Measures` table contains measures with these names:

- Total Revenue
- Total Cost
- Gross Margin
- Gross Margin %
- Total Orders
- Customer Rank
- Revenue YTD
- Revenue Previous Year
- Revenue YoY Growth %
- Rolling 12M Sales
- Sales by Ship Date

Use `DAX-Measure-Library.md` for readable reference formulas. Column names may need adjustment to match the actual PBIX.

## Report elements recorded

- KPI cards for revenue, cost, gross margin, orders, and margin percentage.
- Sales by ship date line chart.
- Customer ranking bar chart.
- Rolling 12-month sales visual.
- Revenue YoY growth measure/card.

## Engineering notes

- Keep measures in the dedicated `_Measures` table rather than adding unnecessary calculated columns to the fact table.
- Prefer `DIVIDE` for safe ratio calculations.
- Mark the intended calendar table as a Date table and verify its relationship to the fact table before relying on time-intelligence measures.
- Validate measure results at multiple filter levels; a formula compiling successfully does not guarantee the business logic is correct.
- Confirm the active/inactive date relationships used by the Ship Date measure.

## Validation checklist

- [x] PBIX file is present in the repository.
- [x] Central `_Measures` table is visible.
- [x] Core measure names listed above are present in the model.
- [x] KPI and analytical visuals are present in the report.
- [ ] Reopen the PBIX from the repository and check for missing sources.
- [ ] Validate each formula against the exact model columns.
- [ ] Capture screenshots of the DAX measure list and completed report page.

## Files

- `AdventureWorks_Exercise3.pbix` — Power BI report/model.
- `DAX-Measure-Library.md` — reference formulas and explanations.
