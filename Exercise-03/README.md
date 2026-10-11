# Exercise 3 — Calculated Fields & Advanced DAX Measures

**Project:** AdventureWorks Data Analysis  
**Main report:** AdventureWorks_Exercise3.pbix  
**Reference:** DAX-Measure-Library.md

## Objective

Create explicit, reusable DAX measures for sales performance, profitability, customer ranking, and time-based comparisons. Measures are organized in a dedicated _Measures table.

## Measure inventory

The Fields pane showed these 11 measure names:

| Measure | Purpose |
|---|---|
| Total Revenue | Aggregate sales amount |
| Total Cost | Aggregate product cost |
| Gross Margin | Revenue minus cost |
| Gross Margin % | Margin as a proportion of revenue |
| Total Orders | Order-count KPI |
| Customer Rank | Rank customers by revenue |
| Revenue YTD | Year-to-date revenue |
| Revenue Previous Year | Comparable prior-year revenue |
| Revenue YoY Growth % | Year-over-year revenue change |
| Rolling 12M Sales | Revenue in a rolling 12-month window |
| Sales by Ship Date | Revenue using the ship-date relationship |

The report uses FactInternetSales, customer attributes from DimCustomer, and date fields from DimDate / DimDate_Calendar.

## DAX work and concepts

The measure set covers SUM for base revenue/cost, measure references for gross margin, DIVIDE for ratios, CALCULATE for filter context, TOTALYTD for year-to-date calculations, SAMEPERIODLASTYEAR for prior-year comparisons, DATESINPERIOD for rolling 12-month analysis, USERELATIONSHIP for ship-date analysis, and RANKX for customer ranking.

Representative formulas are in DAX-Measure-Library.md. Confirm exact column names and relationship endpoints in the saved model before treating a reference formula as validated.

## Date table and Rolling 12M Sales

The screenshots show DimDate_Calendar with its Date column selected in the Mark as date table dialog. During troubleshooting, the Rolling 12M Sales formula was changed from DimDate[Date] to DimDate_Calendar[Date]. A later screenshot showed a displayed value for the measure. The saved formula and its behavior under date filters should still be checked in the PBIX.

## Report visuals

The report screenshots show KPI cards for Total Revenue, Total Cost, Total Orders, Gross Margin, Gross Margin %, and Revenue YoY Growth %, plus a customer-ranking horizontal bar chart, a sales-by-ship-date trend, and a Rolling 12M Sales visual/card.

## Formatting

| Measure type | Format |
|---|---|
| Revenue, cost, margin, YTD, prior-year, rolling, and ship-date sales | Currency |
| Gross Margin %, Revenue YoY Growth % | Percentage |
| Total Orders, Customer Rank | Whole number |

Keep currency symbols, decimal places, and percentage formatting consistent.

## Files

- AdventureWorks_Exercise3.pbix — report and model.
- DAX-Measure-Library.md — measure inventory, formulas, and formatting guidance.

## Outcome

Exercise 3 extends the dimensional model with centralized measures and KPI/time-intelligence visuals. The visible measure list documents the work performed; final correctness depends on formula and filter-context testing.
