# Exercise 4 — Executive Report Blueprint

This blueprint follows the supplied Power BI Engineering Hands-on Lab Guide. It describes the target design; it is not proof that the report has been implemented.

## Canvas and visual hierarchy

- Standard report pages: 16:9 canvas.
- Use a consistent grid, aligned edges, and spacing.
- Put headline KPIs first, trends second, and detail/drill paths after the summary.
- Use a limited palette and check text/background contrast.
- Use clear titles, units, and number formatting.

## Page 1 — Executive Overview

**Purpose:** summarize revenue, profitability, growth, and trend.

Suggested layout:
1. Header: report title and selected period.
2. KPI row: Total Revenue, Gross Margin, Revenue YoY Growth %.
3. Main trend: sales over time.
4. Supporting breakdown: product category or region.
5. Slicers: date and relevant business dimensions.

Checklist:
- [ ] New Card visuals use clear reference labels where applicable.
- [ ] KPI formats and comparison periods are correct.
- [ ] Cross-filtering and slicers behave as expected.

## Page 2 — Decomposition Tree

**Purpose:** investigate factors associated with revenue.

- Analyze: `[Total Revenue]`
- Explain by: Category, Region, Sales Channel (use fields available in the actual model)
- [ ] Confirm the hierarchy fields are populated.
- [ ] Test multiple branches and verify totals against the base measure.

## Page 3 — Customer 360 drill-through

**Purpose:** view customer-level details from a selected customer context.

- Add a customer key to the drill-through filter well.
- Enable **Keep all filters** when appropriate.
- Include customer attributes, lifetime metrics, and an order-history table.
- [ ] Verify right-click drill-through from the overview.
- [ ] Provide a clear back-navigation path.

## Tooltip page — 12M Trend Tooltip

- Page type: Tooltip.
- Guide canvas target: 320 × 240.
- Include a compact sparkline and YTD/variance label.
- Bind the tooltip page to the intended visual.
- [ ] Test hover behavior and ensure the tooltip is readable.

## Acceptance review

- [ ] All report pages and tooltip page are implemented.
- [ ] Measures return expected values at different filter levels.
- [ ] Labels and number formats are consistent.
- [ ] Keyboard navigation and contrast have been checked.
- [ ] Save, close, reopen, and inspect the PBIX.
