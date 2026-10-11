# Exercise 2 — Dimensional Data Modeling: Star Schema & Relationships

**Main report:** AdventureWorks_Exercise2.pbix  
**Dataset:** AdventureWorks Data Warehouse  
**Tools:** SQL Server Express, SSMS, Power BI Desktop

## Objective

Load AdventureWorks data and organize it for sales analysis with fact/dimension tables, appropriate relationships, and a dedicated reporting calendar.

## Environment setup

Installed SQL Server Express and SSMS, connected to the local SQLEXPRESS instance using Windows Authentication, and downloaded the AdventureWorksDW2022 backup for use as the source database. The database name selected in Power BI should match the database restored in SSMS.

## Tables reviewed

| Table | Role | Purpose |
|---|---|---|
| FactInternetSales | Fact | Sales amount, product cost, customer/product/date keys |
| DimCustomer | Dimension | Customer attributes |
| DimProduct | Dimension | Product attributes |
| DimProductSubcategory | Dimension | Product subcategory hierarchy |
| DimProductCategory | Dimension | Product category hierarchy |
| DimDate | Date dimension | Existing AdventureWorks date attributes and keys |
| DimDate_Calendar | Reporting calendar | Calendar dates and reporting labels |

## Modeling work

- Inspected fact and dimension tables in Power BI.
- Reviewed relationship cardinality and cross-filter direction.
- Considered date roles for order date, due date, and ship date.
- Created a separate DimDate_Calendar table.
- Selected the calendar's Date column in the Mark as date table dialog.
- Created a monthly sales chart with DimDate_Calendar[MonthYear] on the X-axis and Sum of FactInternetSales[SalesAmount] on the Y-axis.

## Relationship concepts

Dimension tables provide descriptive context; the fact table stores transaction measures and keys. Standard dimension-to-fact relationships commonly use one-to-many cardinality and single-direction filtering. The order-date relationship can be the active path for the main sales report, while an alternate ship-date path can be inactive and used by a measure with USERELATIONSHIP.

The calendar should have a unique Date column, cover the required fact dates, and use a chronological sort key for MonthYear labels. Confirm exact relationship endpoints, active/inactive states, key quality, and date coverage in Model view; reference examples do not independently verify these settings.

## Report result

The monthly sales visual provides a time-based view of AdventureWorks sales and establishes the date-model concepts used by the DAX time-intelligence measures in Exercise 3.

## Supporting files

- AdventureWorks_Exercise2.pbix — report and model.
- DAX-Reference.md — calendar and inactive-date examples.
- Model-Validation-Checklist.md — detailed model review reference.
