# Exercise 2 — Dimensional Data Modeling: Star Schema & Relationships

**Main report:** `AdventureWorks_Exercise2.pbix`  
**Dataset:** AdventureWorks Data Warehouse  
**Tools:** SQL Server, SSMS, Power BI Desktop

## Objective

Build a Kimball-style dimensional model for AdventureWorks sales. Separate transaction-level measures from descriptive attributes, create a dedicated calendar, and establish clear relationship paths—including an inactive ship-date relationship for role-playing date analysis.

## Work recorded

- Loaded and inspected the AdventureWorks tables in Power BI.
- Reviewed fact/dimension roles and relationship settings.
- Reviewed one-to-many cardinality and single-direction filtering.
- Reviewed active/inactive date relationships for order, due, and ship dates.
- Created a sales amount by month-year column chart.
- Created a separate `DimDate_Calendar` table in the Exercise 2 PBIX and selected its `Date` column in the **Mark as date table** dialog.

## Model inventory

| Table | Role | Review focus |
|---|---|---|
| `FactInternetSales` | Fact | Sales amounts, product cost, customer/product/date keys |
| `DimCustomer` | Dimension | Customer attributes and customer key |
| `DimProduct` | Dimension | Product attributes and product key |
| `DimProductSubcategory` | Dimension | Subcategory hierarchy |
| `DimProductCategory` | Dimension | Category hierarchy |
| `DimDate` | Warehouse date dimension | Existing AdventureWorks date attributes and keys |
| `DimDate_Calendar` | Reporting calendar | Date, year, quarter, month, and month-year labels |

Exact relationship endpoints and field names must be checked in the saved model; the inventory above is not a substitute for inspecting Model view.

## Required relationship design

- Use dimensions to filter the fact table wherever practical.
- Standard dimension-to-fact paths should normally be **1:*** and **Single** direction.
- Use the order-date relationship as the active date path for the primary sales analysis.
- Keep ship-date relationship inactive when activating it would create competing paths.
- Use `USERELATIONSHIP` in a measure when analysis must use the inactive ship-date path.
- Ensure the date table has a unique date column, covers the required fact-date range, and is marked as a Date table.
- Sort `MonthYear` by a chronological key (for example, a numeric year-month key), not alphabetically.

## Report visual recorded

- **X-axis:** `DimDate_Calendar[MonthYear]`
- **Y-axis:** Sum of `FactInternetSales[SalesAmount]`

Verify that the month-year labels sort chronologically and that slicers filter the visual as expected.

## Acceptance checklist

- [x] PBIX file is present in the repository.
- [x] Fact and dimension tables were inspected.
- [x] Relationship settings were reviewed in Power BI Desktop.
- [x] One-to-many cardinality and single-direction filtering were reviewed.
- [x] Active/inactive date relationship concepts were reviewed.
- [x] Sales by month-year visual was created.
- [x] A calendar table was created and the Date-table dialog was used.
- [ ] Verify the calendar date range covers all required fact dates.
- [ ] Verify all relationship endpoints, cardinalities, and active/inactive states in Model view.
- [ ] Verify every dimension key is unique and fact foreign keys map as expected.
- [ ] Verify MonthYear sort-by column and visual totals.
- [ ] Download/reopen the committed PBIX and confirm no source errors.
- [ ] Add screenshots of Model view, Manage relationships, and the report visual.

## Supporting files

- `DAX-Reference.md` — calendar and inactive-date examples.
- `Model-Validation-Checklist.md` — practical validation checklist.
- `AdventureWorks_Exercise2.pbix` — Power BI report/model.
