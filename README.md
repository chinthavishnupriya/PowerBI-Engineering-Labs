# Power BI Engineering Labs

A hands-on portfolio for the **Power BI Engineering Lab Series**: Power Query ETL, dimensional modeling, advanced DAX, executive report UX, and governed deployment.

## Exercise index

| Exercise | Focus | Repository status | Main folder |
|---|---|---|---|
| 1 | Multi-source ingestion and Power Query ETL | PBIX and sample source files present | [Exercise-01](./Exercise-01/) |
| 2 | AdventureWorks dimensional modeling and relationships | PBIX and documentation present | [Exercise-02](./Exercise-02/) |
| 3 | Advanced DAX measures and time intelligence | PBIX present; DAX reference documented | [Exercise-03](./Exercise-03/) |
| 4 | Executive visual analytics and report UX | PBIX and documentation present; interaction and visual QA checklist remains | [Exercise-04](./Exercise-04/) |
| 5 | Capstone pipeline, deployment, refresh, and security | Planning and implementation checklist; deployment remains | [Exercise-05](./Exercise-05/) |

**Status convention:** “Present” means a file is in the repository. It does not independently verify every visual, formula, refresh, or service configuration inside the PBIX. Exercise 4 has been built in Power BI Desktop; use its README checklist to validate the interactions and finish visual polish.

## Repository layout

    PowerBI-Engineering-Labs/
    ├── README.md
    ├── Exercise-01/
    │   ├── README.md
    │   ├── PowerBI_Engineering_Lab_Exercise1.pbix
    │   ├── Sales_Orders.csv
    │   ├── MonthlyForecast.csv
    │   ├── Retail_CRM_and_Products.xlsx
    │   └── PowerQuery-M-Reference.md
    ├── Exercise-02/
    │   ├── README.md
    │   ├── AdventureWorks_Exercise2.pbix
    │   ├── DAX-Reference.md
    │   └── Model-Validation-Checklist.md
    ├── Exercise-03/
    │   ├── README.md
    │   ├── AdventureWorks_Exercise3.pbix
    │   └── DAX-Measure-Library.md
    ├── Exercise-04/
    │   ├── README.md
    │   ├── AdventureWorks_Exercise4.pbix
    │   ├── Executive-Report-Blueprint.md
    │   └── PowerBI-Theme.json
    └── Exercise-05/
        ├── README.md
        ├── Capstone-Implementation-Checklist.md
        └── RLS-Examples.dax

## How to use this repository

1. Open the relevant PBIX file with Power BI Desktop.
2. Read that exercise's README before changing the model or report.
3. Treat Markdown, DAX, and JSON files as references/templates; adapt names and paths to the actual model.
4. Keep screenshots or evidence in the matching exercise folder when available.
5. Do not commit credentials, access tokens, private customer data, or gateway secrets.

## Technology

- Power BI Desktop and Power Query M
- SQL Server / SSMS and AdventureWorks DW
- Dimensional modeling and relationship design
- DAX measures and time intelligence
- Interactive report design, drill-through, and tooltips
- Power BI Service concepts: refresh, gateway, app deployment, and row-level security
