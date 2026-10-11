# Exercise 2 — Dimensional Data Modeling: Star Schema & Relationships

**Main report:** AdventureWorks_Exercise2.pbix  
**Dataset:** AdventureWorks Data Warehouse  
**Tools:** SQL Server, SSMS, Power BI Desktop

## Objective

Build a dimensional model for AdventureWorks sales. Separate transaction-level measures from descriptive attributes, create a reporting calendar, and use clear relationship paths, including an inactive ship-date relationship for role-playing date analysis.

## Work overview

The exercise includes loading and inspecting AdventureWorks tables, reviewing fact/dimension roles, one-to-many cardinality, single-direction filtering, and active/inactive date relationships for order, due, and ship dates. A sales amount by month-year column chart was created. A separate DimDate_Calendar table was created, and its Date column was selected in the **Mark as date table** dialog.

## Model inventory

| Table | Role | Main purpose |
|---|---|---|
| FactInternetSales | Fact | Sales amounts, product cost, customer/product/date keys |
| DimCustomer | Dimension | Customer attributes and customer key |
| DimProduct | Dimension | Product attributes and product key |
| DimProductSubcategory | Dimension | Product subcategory hierarchy |
| DimProductCategory | Dimension | Product category hierarchy |
| DimDate | Warehouse date dimension | AdventureWorks date attributes and keys |
| DimDate_Calendar | Reporting calendar | Date, year, quarter, month, and month-year labels |

Exact relationship endpoints and field names should be read from the saved model in Model view.

## Relationship design concepts

- Dimensions filter the fact table through clear relationship paths.
- Dimension-to-fact relationships commonly use one-to-many cardinality and single-direction filtering.
- The order-date relationship can serve as the active date path for primary sales analysis.
- An inactive ship-date relationship can be used in a measure with USERELATIONSHIP.
- A reporting calendar should have a unique Date column, cover the required date range, and be marked as a Date table.
- Month-year labels should sort by a chronological key rather than alphabetically.

## Report visual

The recorded monthly sales visual uses DimDate_Calendar[MonthYear] on the X-axis and Sum of FactInternetSales[SalesAmount] on the Y-axis.

## Supporting files

- DAX-Reference.md — calendar and inactive-date examples.
- Model-Validation-Checklist.md — detailed model review reference.
- AdventureWorks_Exercise2.pbix — Power BI report and model.
