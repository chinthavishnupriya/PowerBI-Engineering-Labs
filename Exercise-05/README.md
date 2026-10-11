# Exercise 5 — Capstone: End-to-End Pipeline & Deployment

**Current repository content:** Planning and reference materials for the capstone. The Power BI Service deployment, gateway refresh, ML integration, and Row-Level Security configuration are environment-dependent implementation activities.

## Objective

Integrate batch machine-learning scoring outputs with the Power BI model, publish a governed report to Power BI Service, configure refresh, and apply regional Row-Level Security (RLS).

## Target pipeline

1. Prepare an ML scoring file or table with CustomerKey, ChurnProbability, and SpendingCluster.
2. Ingest the scoring data through Power Query and validate keys, data types, missing rows, and score ranges.
3. Relate scoring outputs to customer data using the appropriate customer key and cardinality.
4. Add a churn-risk tier and visuals for high-risk accounts and revenue at risk.
5. Publish the report and semantic model to the intended Power BI Service workspace.
6. Configure source credentials and a gateway where required, then set a supported refresh schedule.
7. Define and test RLS roles for regional users and verify that each role sees only permitted data.
8. Review refresh history and record security-test outcomes.

## Intended outcomes

- ML prediction fields are available in report visuals.
- A high-risk churn view highlights customers above the lab's 65% threshold.
- The report and semantic model are deployed to the intended workspace or app.
- Scheduled refresh runs successfully.
- RLS behavior is verified across regional personas.

## Supporting files

- RLS-Examples.dax — illustrative filter pattern to adapt to the actual security table and relationships.

## Security note

Workspace access, gateway configuration, credentials, refresh history, and RLS behavior must be verified in Power BI Service. Do not store passwords, OAuth tokens, gateway keys, or private customer data in GitHub.
