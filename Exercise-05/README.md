# Exercise 5 — Capstone: End-to-End Pipeline & Deployment

**Status:** Planning/reference materials only. Publishing, gateway refresh, ML integration, and RLS must be implemented and tested in the appropriate environment before marking this exercise complete.

## Objective

Integrate batch ML scoring outputs with the Power BI model, publish a governed report to Power BI Service, configure refresh, and apply regional Row-Level Security (RLS).

## Target pipeline

1. Prepare an ML scoring file/table with `CustomerKey`, `ChurnProbability`, and `SpendingCluster`.
2. Ingest it through Power Query and validate keys, data types, missing rows, and score ranges.
3. Relate the scoring output to customer data using the appropriate customer key and cardinality.
4. Add a churn-risk tier and visuals for high-risk accounts and revenue at risk.
5. Publish the report/dataset to the intended Power BI Service workspace.
6. Configure credentials and a gateway where the source requires one; set a refresh schedule supported by the environment.
7. Define and test RLS roles using test identities/roles; verify users only see permitted regional data.
8. Record refresh history and security-test outcomes.

## Required lab-guide outcomes

- ML prediction fields are available in report visuals.
- A high-risk churn view highlights customers above the lab's 65% threshold.
- Dataset and report are deployed to the intended workspace/app.
- Scheduled refresh runs successfully with a clean history.
- RLS is tested across multiple regional personas.

## Supporting files

- `Capstone-Implementation-Checklist.md` — ordered implementation and evidence checklist.
- `RLS-Examples.dax` — illustrative filter pattern to adapt to the actual security table and relationship design.
- `AdventureWorks_Exercise5.pbix` — expected final report filename when the capstone is implemented.

## Important

Power BI Service, gateway, workspace permissions, credentials, and RLS cannot be proven by repository documentation alone. Never place passwords, OAuth tokens, gateway keys, or personal customer data in GitHub.
