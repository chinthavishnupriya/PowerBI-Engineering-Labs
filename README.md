# Power BI Engineering Labs

A practical collection of Power BI lab exercises focused on data ingestion, Power Query transformation, dimensional modeling, DAX, and interactive reporting.

## Exercises

| Exercise | Topic | Status | Folder |
|---|---|---|---|
| Exercise 1 | Sales and Monthly Forecast Dashboard / Power Query ETL | Completed | [Exercise-01](./Exercise-01/) |
| Exercise 2 | Dimensional Data Modeling — Star Schema & Relationships | Completed in Power BI; documentation updated; final project files still need uploading | [Exercise-02](./Exercise-02/) |
| Exercise 3 | Advanced DAX Engine | Next | Not started |

## Exercise 2 summary

Exercise 2 models Adventure Works Internet Sales in Power BI using a fact table and descriptive dimensions.

**Main tasks completed**
- Loaded the relevant Adventure Works tables into Power BI Desktop.
- Inspected the model and reviewed relationships in Manage relationships.
- Reviewed one-to-many (*:1) cardinality and single-direction cross-filtering.
- Identified active and inactive date relationships for order, due, and ship dates.
- Created a column chart showing sum of sales amount by month-year.

**Main tables**
- `FactInternetSales` — transaction-level sales and numeric measures.
- `DimCustomer` — customer attributes.
- `DimProduct`, `DimProductSubcategory`, and `DimProductCategory` — product hierarchy.
- `DimDate` and `DimDate_Calendar` — date and calendar attributes used by the model/report.

See the [Exercise 2 README](./Exercise-02/README.md) for the objective, model design, validation checklist, and remaining uploads. The [DAX reference](./Exercise-02/DAX-Reference.md) documents the calendar-table pattern and inactive date relationship concept for Exercise 3.

## Repository structure

```text
PowerBI-Engineering-Labs/
├── README.md
├── Exercise-01/
│   ├── README.md
│   ├── PowerBI_Engineering_Lab_Exercise1.pbix
│   ├── Sales_Orders.csv
│   ├── MonthlyForecast.csv
│   └── Retail_CRM_and_Products.xlsx
└── Exercise-02/
    ├── README.md
    ├── DAX-Reference.md
    ├── AdventureWorks_Exercise2.pbix   (upload required)
    └── screenshots/                    (optional; upload required)
```

## Tools

- Microsoft Power BI Desktop
- Power Query
- SQL Server and SQL Server Management Studio (SSMS)
- Dimensional modeling and relationships
- DAX measures and time intelligence
- Interactive report visuals
