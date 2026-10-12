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

## Suggested workflow

1. Restore the AdventureWorksDW2022 backup in SQL Server and confirm the database name and local instance.
2. Connect Power BI Desktop to the restored database using the credentials available in your environment.
3. Load the required fact and dimension tables; avoid importing unrelated tables without a report requirement.
4. In Model view, inspect the key columns and create dimension-to-fact relationships with appropriate cardinality and filter direction.
5. Create or review DimDate_Calendar, ensure its Date column is unique and covers the reporting period, and mark it as the date table.
6. Build the monthly sales visual using the calendar's MonthYear field and FactInternetSales[SalesAmount].
7. Compare the visual total to a known total from the fact table and test filtering across multiple years/months.

## Model review checklist

- FactInternetSales contains transaction-level sales and foreign keys.
- Dimension keys used on the one-side of relationships are unique.
- Relationship directions avoid unnecessary ambiguous filter paths.
- The date table has no duplicate or blank dates and is marked as a date table.
- MonthYear labels sort chronologically using a numeric/date sort column rather than alphabetically.
- Order, due, and ship dates are treated as separate date roles; an alternate date relationship should be used intentionally and documented.

## Troubleshooting

- **Database not visible:** verify the SQL Server instance, restored database name, and connection permissions.
- **Backup not listed in SSMS:** use the Restore Database workflow and browse to the actual .bak location; confirm the file is accessible to the SQL Server service.
- **Relationship warning:** check duplicate dimension keys, mismatched data types, and whether a many-to-many relationship is genuinely required.
- **Month names sort alphabetically:** sort the display label by a chronological sort column.

## Validation record

The repository includes the PBIX, DAX reference, and model-validation checklist. Reopen the saved model to confirm the actual relationship endpoints, active/inactive states, calendar coverage, and visual totals; reference documentation alone does not prove those settings.
