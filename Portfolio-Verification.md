# Portfolio Verification — Exercises 1–5

This inventory checks whether the expected report and supporting files are present in the repository. A file being present does **not** prove that its PBIX opens, refreshes, or that every visual and interaction works; those checks require Power BI Desktop/Service.

## Repository inventory

| Exercise | Main PBIX | Supporting artifacts found | Repository-level result |
|---|---|---|---|
| 1 — Power Query ETL | `Exercise-01/PowerBI_Engineering_Lab_Exercise1.pbix` | README, Sales_Orders.csv, MonthlyForecast.csv, Retail_CRM_and_Products.xlsx, PowerQuery-M-Reference.md | Expected report and source/reference files are present. |
| 2 — Dimensional modeling | `Exercise-02/AdventureWorks_Exercise2.pbix` | README, DAX-Reference.md, Model-Validation-Checklist.md | Report and documentation are present. AdventureWorksDW2022 backup is an external/local setup dependency and is not stored in this folder. |
| 3 — DAX measures | `Exercise-03/AdventureWorks_Exercise3.pbix` | README, DAX-Measure-Library.md | Report and measure reference are present. |
| 4 — Executive analytics | `Exercise-04/AdventureWorks_Exercise4.pbix` | README, Executive-Report-Blueprint.md, PowerBI-Theme.json | Report, layout reference, and theme are present. |
| 5 — Churn-risk capstone | `Exercise-05/AdventureWorks_Exercise5.pbix` | README, implementation checklist, architecture PDF, DAX Studio CSV, RLS example, screenshot | Core submission artifacts are present. See Exercise 5 README for known implementation gaps. |

## Cross-exercise checks

- Each exercise folder has a README describing its purpose and artifacts.
- The root README links to all five exercise folders.
- The PBIX files are present in GitHub; open each file in Power BI Desktop to verify that it loads without errors.
- The source CSV/XLSX files for Exercise 1 are present.
- Exercise 5 includes the PBIX, architecture PDF, and DAX Studio log required by the current submission bundle.

## Checks still requiring local Power BI validation

1. Open each PBIX in Power BI Desktop and confirm visuals, measures, relationships, and interactions.
2. Refresh Exercises 1–4 against the intended local/source environment and confirm credentials/paths.
3. For Exercise 5, complete regional RLS validation and scheduled refresh. The local SQL Server gateway setup was not confirmed working.
4. Capture successful refresh-history evidence and a regional RLS test matrix when those checks pass.
5. Review any performance requirements against the lab rubric; the Exercise 5 DAX Studio CSV is trace output and is not, by itself, proof of improved performance.

## Safe repository practices

Do not commit database backups unless the lab explicitly requires them and redistribution is permitted. Do not commit credentials, gateway keys, tokens, or private customer data.
