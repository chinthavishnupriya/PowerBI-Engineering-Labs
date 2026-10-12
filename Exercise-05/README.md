# Exercise 5 — Capstone: Customer Churn Risk Analysis

**Main report:** [AdventureWorks_Exercise5.pbix](./AdventureWorks_Exercise5.pbix)  
**Architecture:** [Exercise5_Architecture_Blueprint (1).pdf](./Exercise5_Architecture_Blueprint%20(1).pdf)  
**Performance evidence:** [Exercise5_DAXStudio_Log.csv](./Exercise5_DAXStudio_Log.csv)  
**Implementation checklist:** [Capstone-Implementation-Checklist.md](./Capstone-Implementation-Checklist.md)  
**RLS reference:** [RLS-Examples.dax](./RLS-Examples.dax)

## Objective

Integrate machine-learning churn scoring with customer and sales data, analyze high-risk customers, publish the report to Power BI Service, configure refresh, and apply regional Row-Level Security (RLS).

## Implemented and documented

- Imported a matched-key scoring dataset containing `CustomerKey`, `ChurnProbability`, and `SpendingCluster`.
- Related the scoring table to `DimCustomer`; sales data is related through `FactInternetSales`.
- Created churn-risk tiers using the lab thresholds: High above 65%, Medium from 35% through 65%, and Low below 35%.
- Built churn-risk visuals, a customer table, a spending-cluster breakdown, and a revenue-at-risk measure.
- Published the report and semantic model to Power BI Service in My workspace.
- Created and tested a `HighRiskCustomers` role; the test view showed the 10 high-risk records, and the unrestricted view showed all 30 scoring records.
- Exported DAX Studio trace/performance log evidence and included an architecture blueprint.

## Current validation status

| Requirement | Status | Notes |
|---|---|---|
| PBIX report and scoring analysis | Implemented | Saved report is included; reopen it in Power BI Desktop to confirm current state. |
| DAX Studio log | Included | The CSV records a DAX Studio trace. It is trace evidence, not by itself a benchmark or proof of query performance. |
| Power BI Service publication | Published | Report and semantic model were observed in My workspace. |
| High-risk RLS role | Tested in Desktop | The `HighRiskCustomers` role restricted the test view to 10 records. |
| Regional Director RLS | Incomplete | Regional filter behavior was not validated successfully. Do not treat the illustrative DAX file as configured security. |
| Scheduled refresh | Incomplete | A usable gateway was not established for the local SQL Server source; successful scheduled refresh has not been verified. |
| Revenue at risk | Needs business validation | The current measure sums historical sales associated with high-risk customers; it is not a validated prediction of future lost revenue. |
| Final submission evidence | Partial | PBIX, architecture PDF, and DAX Studio CSV are present. Add refresh-history evidence and a regional RLS test matrix after those checks succeed. |

## Risk-tier definition

- **High:** `ChurnProbability > 0.65`
- **Medium:** `ChurnProbability >= 0.35` and `ChurnProbability <= 0.65`
- **Low:** `ChurnProbability < 0.35`

The scoring table currently contains 30 matched customer records: 10 High, 11 Medium, and 9 Low. These counts describe the current sample and may change if the scoring data is updated.

## Revenue-at-risk interpretation

The current measure totals historical sales associated with high-risk customers. Label it as an exposure indicator unless a defensible forecast methodology is added; do not interpret it as expected future churn loss.

## Remaining work

1. Fix the on-premises data gateway / source connection and configure the required refresh schedule.
2. Implement and test `Regional_Director` RLS against a real region-security mapping and relationship path.
3. Capture successful refresh-history evidence and document regional test identities/results without exposing personal data.
4. Reopen the final PBIX and verify that the report visuals, relationships, and measures are intact.

## Security

Do not commit passwords, tokens, gateway keys, or private customer records. The RLS example is reference material only and does not prove that a role is deployed or secure.
