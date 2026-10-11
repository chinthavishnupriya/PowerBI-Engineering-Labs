# Exercise 2 — Dimensional Data Modeling: Star Schema & Relationships

## Objective

Build and validate a dimensional model for Adventure Works sales data in Power BI. The goal is to separate transaction-level measures from descriptive dimension attributes and configure reliable relationships for reporting.

## Dataset and tools

- **Dataset:** Adventure Works Data Warehouse. The lab guide refers to `AdventureWorksDW2020`; this project used the available Adventure Works DW backup.
- **Fact table:** `FactInternetSales`
- **Tools:** SQL Server, SQL Server Management Studio (SSMS), and Power BI Desktop.

## Work completed

- Connected Power BI Desktop to the Adventure Works data source and loaded the required tables.
- Inspected the model in Model view.
- Reviewed fact and dimension tables and their key columns.
- Reviewed one-to-many relationships and single-direction filtering.
- Identified active and inactive relationships for role-playing dates.
- Built a column chart showing sales amount by month-year.

## Model tables

| Table | Role | Purpose |
|---|---|---|
| `FactInternetSales` | Fact | Sales transactions and numeric measures such as `SalesAmount`; contains customer, product, and date keys. |
| `DimCustomer` | Dimension | Descriptive customer attributes. |
| `DimProduct` | Dimension | Product attributes linked to sales and product subcategories. |
| `DimProductSubcategory` | Dimension | Subcategory attributes linking products to categories. |
| `DimProductCategory` | Dimension | Product category attributes. |
| `DimDate` | Date dimension | Date attributes from the warehouse. |
| `DimDate_Calendar` | Reporting calendar | Calendar attributes such as year, quarter, month, and month-year used for reporting. |

The exact set of loaded tables depends on the source backup and the tables selected in Power BI.

## Relationship design

The intended pattern is a **star schema**: the sales fact table connects to descriptive dimensions using keys. Product subcategory and category form a hierarchy.

- Use **many-to-one (*:1)** from sales rows to the matching dimension key (equivalent to one-to-many from dimension to fact).
- Keep cross-filter direction **Single** unless the lab requirement explicitly needs otherwise.
- Keep the order-date relationship used for the main report active.
- Keep alternate role-playing date relationships, such as ship date, inactive when activating them would create ambiguous filtering paths.
- Use a date/calendar table for consistent time-based analysis.

### Role-playing dates

The model contains date-key relationships for order, due, and ship dates. Only one suitable relationship should be active when multiple date roles could create ambiguous filtering. An inactive relationship can be activated inside a DAX measure with `USERELATIONSHIP` when needed; this is relevant to Exercise 3.

## Report visual

A column chart was created with:

- **X-axis:** `DimDate_Calendar[MonthYear]`
- **Y-axis:** Sum of `FactInternetSales[SalesAmount]`

This visual shows sales amount by month-year. Verify the sort order of `MonthYear` before interpreting the trend; text month labels should be sorted by a chronological key when needed.

## Validation checklist

- [x] Fact and dimension tables are visible in the model.
- [x] Relationships were reviewed in **Manage relationships**.
- [x] One-to-many cardinality and single-direction filtering are used for the shown relationships.
- [x] Active and inactive date relationships are visible in the model.
- [x] Sales amount by month-year visual has been created.
- [ ] Upload the final `.pbix` file to this folder.
- [ ] Add screenshots of Model view, Manage relationships, and the report visual.
- [ ] Download and reopen the uploaded `.pbix` to confirm it works.

## Files for this exercise

- `README.md` — objective, model design, work completed, and validation.
- `AdventureWorks_Exercise2.pbix` — final Power BI Desktop project; upload it from your computer.
- `screenshots/` — optional evidence images of the model and report.
- `DAX-Reference.md` — date-table and role-playing date notes.

> **Important:** This documentation update does not upload the PBIX file or screenshots. Those files must be uploaded separately from your computer.
