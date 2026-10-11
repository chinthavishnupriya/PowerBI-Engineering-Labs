# Exercise 4 — Executive Visual Analytics

**Project:** AdventureWorks Executive Report  
**Power BI file:** [AdventureWorks_Exercise4.pbix](./AdventureWorks_Exercise4.pbix)  
**Theme reference:** [PowerBI-Theme.json](./PowerBI-Theme.json)  
**Layout reference:** [Executive-Report-Blueprint.md](./Executive-Report-Blueprint.md)

## Objective

Build an executive-facing Power BI report that summarizes revenue and profitability, supports exploration of revenue drivers, provides customer-level drill-through, and displays additional context through a report-page tooltip.

## Report pages

| Page | Purpose | Main visuals and features |
|---|---|---|
| Sales Analysis | Explore sales and customers | Sales trend, KPI cards, customer ranking, CustomerKey table |
| Executive Overview | Summarize performance | Revenue, orders, gross margin and growth KPIs, trend visuals, date slicer |
| Decomposition Tree | Explore revenue drivers | Total Revenue analysis with product-category and territory-related fields |
| Customer 360 | Inspect customer-level detail | CustomerKey drill-through filter, customer details, KPI and table visuals |
| 12M Trend Tooltip | Provide context on hover | Tooltip page selected in a visual's tooltip settings |

Screenshots from the build show these pages and their main visual elements. The Customer 360 page includes CustomerKey in the drill-through filter area with Keep all filters enabled. The Decomposition Tree analyzes Total Revenue. The tooltip page was selected in a visual's tooltip page setting.

## Design principles

- Use a consistent 16:9 canvas for standard report pages.
- Place key KPIs before trend and detail visuals.
- Keep alignment, spacing, titles, units, and number formats consistent.
- Use readable contrast and purposeful slicers.
- Use drill-through and tooltips to support focused exploration without overcrowding the overview.

## Files

- AdventureWorks_Exercise4.pbix — Power BI report.
- Executive-Report-Blueprint.md — report layout and design reference.
- PowerBI-Theme.json — starter theme.
