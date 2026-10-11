# Exercise 4 — Executive Report Visualization & UI/UX Design

**Status:** Documentation and design references prepared; the completed four-view report experience described in the lab guide is not yet evidenced as finished in this repository.

## Objective

Design an executive reporting experience that surfaces important KPIs first, then supports deeper investigation through decomposition, customer detail, and hover tooltips.

## Lab-guide report architecture

| View | Purpose | Required design |
|---|---|---|
| Executive Overview | KPI and trend summary | 16:9 canvas, KPI cards, combo trend, category breakdown |
| Decomposition Tree | Explore drivers of revenue | Analyze Total Revenue; explain by category, region, and sales channel |
| Customer 360 | Inspect a selected customer | Drill-through page with customer key and order-history detail |
| 12M Trend Tooltip | Show context on hover | Tooltip page with sparkline and YTD variance |

The guide describes three main report pages plus a dedicated tooltip page.

## Design principles

- Establish a top-down visual hierarchy and consistent alignment grid.
- Use a restrained, accessible palette and maintain readable contrast.
- Put key KPI cards near the top of the overview.
- Add purposeful slicers and cross-filtering instead of excessive controls.
- Enable drill-through with **Keep all filters** where appropriate.
- Create a dedicated tooltip page and bind it to relevant visuals.
- Use clear titles, useful units, and consistent number formats.

## Files

- `Executive-Report-Blueprint.md` — page layout and implementation checklist.
- `PowerBI-Theme.json` — starter theme that can be imported and customized.
- `AdventureWorks_Exercise4.pbix` — expected report filename when implementation is ready.

## Completion checklist

- [ ] Build the Executive Overview page.
- [ ] Add revenue, gross margin, and YoY growth KPI cards.
- [ ] Build the Decomposition Tree and validate the Explain By fields.
- [ ] Build the Customer 360 drill-through page.
- [ ] Build and bind the 12M Trend Tooltip page.
- [ ] Check keyboard navigation, contrast, labels, and cross-filtering.
- [ ] Save and reopen the PBIX; add screenshots to this folder.
