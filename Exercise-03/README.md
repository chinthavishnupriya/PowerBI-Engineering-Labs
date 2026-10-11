# Exercise 3 — Calculated Fields & Advanced DAX Measures

**Project:** AdventureWorks Data Analysis  
**Main report:** AdventureWorks_Exercise3.pbix  
**Reference:** DAX-Measure-Library.md

## Objective

Create centralized DAX measures for sales, cost, margin, customer ranking, and time intelligence. The exercise uses a dedicated _Measures table and context-aware calculations rather than adding calculated columns for these measures to the fact table.

## Model and measure inventory

The report uses FactInternetSales, customer attributes from DimCustomer, and date fields from DimDate / DimDate_Calendar. A dedicated _Measures table is present in the model.

The Fields pane showed these 11 measure names:

| Measure | Purpose |
|---|---|
| Total Revenue | Sales amount aggregation |
| Total Cost | Product cost aggregation |
| Gross Margin | Revenue less cost |
| Gross Margin % | Margin divided by revenue |
| Total Orders | Order-count KPI |
| Customer Rank | Rank customers by revenue |
| Revenue YTD | Year-to-date revenue |
| Revenue Previous Year | Comparable prior-year revenue |
| Revenue YoY Growth % | Year-over-year growth percentage |
| Rolling 12M Sales | Moving 12-month revenue |
| Sales by Ship Date | Revenue using the ship-date relationship |

The supplied screenshots show DimDate_Calendar with a Date column selected in the **Mark as a date table** dialog. The Rolling 12M Sales formula was changed from a reference to DimDate[Date] to DimDate_Calendar[Date]; a later screenshot showed a displayed value. Formula correctness should be judged from the saved PBIX and actual results, not measure names alone.

## DAX techniques

- SUM for base sales and cost aggregation.
- DIVIDE for safe ratios.
- CALCULATE to modify filter context.
- TOTALYTD for year-to-date revenue.
- SAMEPERIODLASTYEAR for prior-year comparisons.
- DATESINPERIOD for rolling 12-month analysis.
- USERELATIONSHIP to use an inactive ship-date relationship.
- RANKX for customer ranking.

See [DAX-Measure-Library.md](./DAX-Measure-Library.md) for representative formulas. Adapt table and column names to the exact model.

## Report elements

The report screenshots show KPI cards for Total Revenue, Total Cost, Total Orders, Gross Margin, Gross Margin %, and Revenue YoY Growth %, plus a sales-by-ship-date trend, customer-rank horizontal bar chart, and Rolling 12M Sales visual/card.

## Number formatting

| Measure type | Suggested format |
|---|---|
| Revenue, cost, margin, YTD, prior-year sales, rolling sales, ship-date sales | Currency |
| Gross Margin %, Revenue YoY Growth % | Percentage |
| Total Orders, Customer Rank | Whole number |

Keep units and decimal places consistent across KPI cards.

## Files

- AdventureWorks_Exercise3.pbix — report and model.
- DAX-Measure-Library.md — DAX patterns, explanations, and format guidance.
