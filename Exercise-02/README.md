# Exercise 2 — Dimensional Data Modeling: Star Schema & Relationships

**Main report:** `AdventureWorks_Exercise2.pbix`  
**Dataset:** AdventureWorks Data Warehouse  
**Tools:** SQL Server, SSMS, Power BI Desktop

## Objective

Build and validate a dimensional model for AdventureWorks sales. Separate transaction-level metrics from descriptive attributes and use clear relationship paths for analysis.

## Work recorded

- Loaded the relevant AdventureWorks tables into Power BI.
- Inspected the model and relationship settings.
- Reviewed fact/dimension roles, one-to-many cardinality, and single-direction filtering.
- Reviewed active and inactive date relationships for order, due, and ship dates.
- Created a column chart for sales amount by month-year.

## Model inventory

| Table | Role | Typical use |
|---|---|---|
| `FactInternetSales` | Fact | Transaction amounts and foreign keys |
| `DimCustomer` | Dimension | Customer attributes |
| `DimProduct` | Dimension | Product attributes |
| `DimProductSubcategory` | Dimension | Product subcategory hierarchy |
| `DimProductCategory` | Dimension | Product category hierarchy |
| `DimDate` | Date dimension | Warehouse date attributes |
| `DimDate_Calendar` | Reporting calendar | Date, year, quarter, month and month-year labels |

The actual loaded table/column names depend on the selected backup and model. Check the Fields pane before copying any example DAX.

## Relationship design

- Use a star-schema pattern wherever possible: dimensions filter the fact table.
- Prefer one-to-many dimension-to-fact relationships with **Single** cross-filter direction.
- Use the order-date path as the active reporting relationship when appropriate.
- Keep alternate date roles (such as ship date) inactive if activating them would create competing filter paths.
- Use `USERELATIONSHIP` inside a measure when a calculation needs an inactive date path.
- Sort text month-year labels by a chronological numeric/date key.

## Report visual recorded

- **X-axis:** `DimDate_Calendar[MonthYear]`
- **Y-axis:** Sum of `FactInternetSales[SalesAmount]`

Verify the sort-by column and ensure the date table covers the fact table's date range.

## Validation checklist

- [x] PBIX file is present in the repository.
- [x] Fact and dimension tables were inspected.
- [x] Relationships were reviewed in Manage relationships.
- [x] One-to-many cardinality and single-direction filtering were reviewed.
- [x] Active/inactive date relationship concepts were reviewed.
- [x] Sales by month-year visual was created.
- [ ] Reopen the committed PBIX from a fresh download.
- [ ] Add screenshots of Model view, Manage relationships, and report visual.
- [ ] Confirm all relationship endpoints and date sorting against the actual model.

## Supporting files

- `DAX-Reference.md` — calendar table and inactive-date examples.
- `Model-Validation-Checklist.md` — practical review checklist.
- `AdventureWorks_Exercise2.pbix` — report/model file.
