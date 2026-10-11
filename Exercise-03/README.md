# Exercise 3 — Calculated Fields & Advanced DAX Measures

**Project:** AdventureWorks Data Analysis  
**Main report:** `AdventureWorks_Exercise3.pbix`  
**Reference:** `DAX-Measure-Library.md`

## 1. Objective

Create a centralized DAX measure repository, avoid unnecessary calculated-column growth in the fact table, and calculate context-aware sales, cost, margin, customer ranking, and time-intelligence metrics. The lab guide's key acceptance criteria are **10+ explicit DAX measures validated**, a dedicated `_Measures` table, and no calculated columns added to the fact table for these measures.

## 2. Model and date table

The report uses `FactInternetSales`, customer attributes from `DimCustomer`, and date fields from `DimDate` / `DimDate_Calendar`. The saved model includes a dedicated `_Measures` table.

The screenshots supplied during the exercise show `DimDate_Calendar` with a `Date` column and the **Mark as a date table** dialog enabled with `Date` selected. The actual relationship endpoints must still be checked in the PBIX before formulas are treated as validated.

## 3. Measure inventory

The Fields pane showed these 11 measure names in `_Measures`:

| # | Measure | Purpose |
|---:|---|---|
| 1 | `Total Revenue` | Sales amount aggregation |
| 2 | `Total Cost` | Product cost aggregation |
| 3 | `Gross Margin` | Revenue less cost |
| 4 | `Gross Margin %` | Margin divided by revenue |
| 5 | `Total Orders` | Order-count KPI |
| 6 | `Customer Rank` | Rank customers by revenue |
| 7 | `Revenue YTD` | Year-to-date revenue |
| 8 | `Revenue Previous Year` | Comparable prior-year revenue |
| 9 | `Revenue YoY Growth %` | Year-over-year growth percentage |
| 10 | `Rolling 12M Sales` | Moving 12-month revenue |
| 11 | `Sales by Ship Date` | Revenue using the ship-date relationship |

**Inventory result:** 11 measure names are visible, meeting the guide's numeric target of 10+. This inventory check alone does not prove every formula is valid or that no calculated columns were added to `FactInternetSales`.

## 4. DAX techniques

- `SUM` for base sales and cost aggregation.
- `DIVIDE` rather than direct division for safe ratios.
- `CALCULATE` to change filter context.
- `TOTALYTD` for cumulative year-to-date revenue.
- `SAMEPERIODLASTYEAR` for prior-year comparison.
- `DATESINPERIOD` for rolling 12-month analysis.
- `USERELATIONSHIP` to activate an inactive ship-date relationship for a calculation.
- `RANKX` for customer ranking.

See [DAX-Measure-Library.md](./DAX-Measure-Library.md) for representative formulas. Adjust table/column names to the exact model.

## 5. Report elements visible in the supplied screenshots

- KPI cards for Total Revenue, Total Cost, Total Orders, Gross Margin, Gross Margin %, and Revenue YoY Growth %.
- Sales-by-ship-date trend.
- Customer rank horizontal bar chart.
- Rolling 12M Sales visual/card.

The screenshots also showed the Rolling 12M Sales measure initially had a warning while its formula referenced a missing `DimDate[Date]` column. The formula was subsequently changed to use `DimDate_Calendar[Date]`, and the visual later displayed a value. Reopen the PBIX and check the formula/refresh state before considering the warning permanently resolved.

## 6. Formatting

| Measure type | Suggested format |
|---|---|
| Revenue, cost, margin, YTD, prior-year sales, rolling sales, ship-date sales | Currency |
| Gross Margin %, Revenue YoY Growth % | Percentage |
| Total Orders, Customer Rank | Whole number |

The lab guide illustrates currency, percentage, and integer formats. Keep units and decimal places consistent across KPI cards.

## 7. Acceptance and remaining verification

### Confirmed from repository/screenshots
- [x] Exercise 3 PBIX exists in the repository.
- [x] A dedicated `_Measures` table is visible in the Fields pane.
- [x] 11 measure names are visible in the Fields pane.
- [x] KPI and analytical visuals are visible in the report screenshot.
- [x] The date-table dialog showed `DimDate_Calendar` marked as a date table with `Date` selected.
- [x] Rolling 12M Sales later displayed a value after the date column reference was changed.

### Still needs an explicit final check
- [ ] Reopen the saved PBIX and ensure no measure warning/error icon remains.
- [ ] Validate all 11 measure formulas against the exact column names and business definitions.
- [ ] Confirm YTD and prior-year calculations across multiple years.
- [ ] Confirm Rolling 12M Sales changes correctly with a date filter.
- [ ] Confirm `Sales by Ship Date` uses the actual inactive relationship endpoints.
- [ ] Verify the intended currency, percentage, and whole-number formats.
- [ ] Inspect `FactInternetSales` and confirm no calculated columns were added for these metrics.
- [ ] Capture final screenshots of the measure list, DAX formula results, and report page.

A measure name appearing in the Fields pane confirms its presence, not formula correctness. Do not mark the final validation items complete until checked in Power BI Desktop.

## 8. Files

- `AdventureWorks_Exercise3.pbix` — report/model.
- `DAX-Measure-Library.md` — DAX patterns, explanations, and format guidance.
- `README.md` — objective, measure inventory, evidence, and acceptance checklist.
