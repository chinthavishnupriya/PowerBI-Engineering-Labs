# Power BI Engineering Labs

A practical portfolio documenting five Power BI exercises: multi-source data preparation, AdventureWorks dimensional modeling, advanced DAX, an interactive executive report, and a churn-risk capstone.

## Exercise index

| Exercise | Focus | Main deliverable |
|---|---|---|
| 1 | Multi-source ingestion and Power Query ETL | [Exercise 1](./Exercise-01/) |
| 2 | AdventureWorks dimensional modeling and relationships | [Exercise 2](./Exercise-02/) |
| 3 | DAX measures and time intelligence | [Exercise 3](./Exercise-03/) |
| 4 | Executive analytics, drill-through, and tooltips | [Exercise 4](./Exercise-04/) |
| 5 | Churn-risk capstone: ML scoring, deployment, refresh, and RLS | [Exercise 5](./Exercise-05/) |

## Exercise 1 — Data preparation

Worked with sales-order CSV data, a customer/product Excel workbook, and monthly forecast CSV data. The Power Query workflow covers source ingestion, promoting headers, explicit data types, sales date cleanup, customer text/email cleanup, product filtering, and unpivoting monthly forecast columns into rows. Report visuals include sales/order KPI cards, sales and quantity analysis, forecast analysis, product analysis, and date filtering.

Files include the Exercise 1 PBIX, Sales_Orders.csv, MonthlyForecast.csv, Retail_CRM_and_Products.xlsx, and PowerQuery-M-Reference.md. The reference contains adaptable patterns; parameters and query folding should only be considered confirmed after inspecting the PBIX.

## Exercise 2 — Dimensional modeling

Set up SQL Server Express and SSMS, obtained the AdventureWorksDW2022 backup, and used AdventureWorks data in Power BI. Reviewed FactInternetSales and descriptive dimensions, relationship cardinality and filter direction, and the different date roles for order, due, and ship dates. Created a separate DimDate_Calendar table, selected its Date column in the Mark as date table dialog, and built a sales-by-MonthYear visual.

## Exercise 3 — DAX measures

Created a dedicated _Measures table. The Fields pane showed 11 measure names: Total Revenue, Total Cost, Gross Margin, Gross Margin %, Total Orders, Customer Rank, Revenue YTD, Revenue Previous Year, Revenue YoY Growth %, Rolling 12M Sales, and Sales by Ship Date. These cover aggregation, margin, ratios, ranking, YTD/prior-year comparison, rolling 12-month analysis, and ship-date analysis. The Rolling 12M Sales date reference was changed to DimDate_Calendar[Date], after which the visual displayed a value.

## Exercise 4 — Executive report

Built Sales Analysis, Executive Overview, Decomposition Tree, Customer 360, and 12M Trend Tooltip pages. The visible report includes KPI cards, sales trends, customer ranking, a CustomerKey table, a date slicer, a revenue decomposition tree using product-category and territory-related fields, a CustomerKey drill-through filter with Keep all filters enabled, and a tooltip page selected in a visual's tooltip settings.

## Repository layout

- Exercise-01/: PBIX, source files, and Power Query reference.
- Exercise-02/: PBIX, date/DAX reference, and model review material.
- Exercise-03/: PBIX and DAX measure library.
- Exercise-04/: PBIX, executive report blueprint, and theme JSON.
- Exercise-05/: capstone implementation notes and RLS example.

## Tools and concepts

Power BI Desktop, Power Query M, SQL Server, SSMS, dimensional modeling, DAX, date intelligence, drill-through, report-page tooltips, and Power BI Service concepts.

## Usage and accuracy

Open each PBIX in Power BI Desktop and read its exercise README. Configure local data paths and credentials for your environment. Never commit passwords, tokens, gateway secrets, or private customer data.

Descriptions are based on repository artifacts and screenshots shared during the exercises. A visible measure or visual does not independently prove that all formulas, totals, refreshes, or interactions have been fully validated.
