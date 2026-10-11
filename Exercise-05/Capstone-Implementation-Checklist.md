# Exercise 5 — Capstone Implementation Checklist

Use this as a staged implementation log. Mark an item complete only after testing it in the intended environment.

## A. ML output ingestion

- [ ] Prepare a scoring output with `CustomerKey`, `ChurnProbability`, and `SpendingCluster`.
- [ ] Validate probability values are within the expected 0–1 range.
- [ ] Check duplicate/missing customer keys and unmatched customers.
- [ ] Import through Power Query and apply explicit types.
- [ ] Define the intended relationship to the customer dimension.

## B. Risk analysis

- [ ] Create High / Medium / Low risk tiers using the guide thresholds: High > 65%, Medium 35–65%, Low < 35%.
- [ ] Build a visual for high-risk customers.
- [ ] Define the business logic for revenue at risk and validate its total.
- [ ] Test slicers and drill interactions.

## C. Power BI Service deployment

- [ ] Save and reopen the final PBIX.
- [ ] Publish to the intended workspace, subject to available permissions/licensing.
- [ ] Confirm the semantic model and report are available.
- [ ] Configure credentials without storing secrets in the repository.
- [ ] Configure an appropriate gateway only when required by the data source/environment.
- [ ] Set the agreed refresh schedule and inspect refresh history.
- [ ] Document the refresh result and any failures.

## D. Row-Level Security

- [ ] Create a security mapping table with user identity and permitted region.
- [ ] Implement RLS on an appropriate dimension/security path.
- [ ] Test with multiple test identities or **View as** roles.
- [ ] Verify restricted users cannot see other regions.
- [ ] Record test cases and outcomes without exposing personal information.

## E. Submission bundle

- [ ] Final PBIX.
- [ ] Performance Analyzer export or other performance evidence, if required.
- [ ] Architecture overview.
- [ ] Refresh-history evidence.
- [ ] RLS test matrix.
- [ ] Final README with actual status and known limitations.

**Security:** do not commit passwords, tokens, gateway credentials, or real private customer records.
