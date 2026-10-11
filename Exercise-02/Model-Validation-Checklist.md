# Exercise 2 — Model Validation Checklist

Use this checklist with `AdventureWorks_Exercise2.pbix`. Tick an item only after inspecting it in Power BI Desktop.

## Table inventory

- [ ] Confirm `FactInternetSales` is loaded.
- [ ] Confirm required customer and product dimensions are loaded.
- [ ] Confirm the intended calendar table and its date range.
- [ ] Check that key columns have compatible data types.

## Relationships

- [ ] Each dimension key is unique on the one-side of its relationship.
- [ ] Fact foreign keys map to valid dimension keys where expected.
- [ ] Use one-to-many relationships for standard dimension-to-fact paths.
- [ ] Use Single cross-filter direction unless the design requires otherwise.
- [ ] Check that the order-date relationship is the intended active path.
- [ ] Check inactive due/ship-date paths and document their intended use.
- [ ] Look for ambiguous or accidental many-to-many relationships.

## Date and visual validation

- [ ] Mark the intended calendar table as a Date table.
- [ ] Confirm the date column has no unexpected gaps or duplicate dates.
- [ ] Sort MonthYear by a chronological sort key.
- [ ] Compare monthly sales visual totals against a table or known aggregation.
- [ ] Check slicer interactions and filter behavior.

## Evidence

- [ ] Screenshot of Model view.
- [ ] Screenshot of Manage relationships.
- [ ] Screenshot of sales by month-year visual.
- [ ] Reopen the committed PBIX and confirm no source errors.

## Review result

Record the review date, any issues found, and what was corrected. This checklist is a template; it does not assert that every item has already passed.
