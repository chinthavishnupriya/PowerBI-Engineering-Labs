# Exercise 4 — Executive Visual Analytics

**Project:** AdventureWorks Executive Report  
**Power BI file:** [AdventureWorks_Exercise4.pbix](./AdventureWorks_Exercise4.pbix)  
**Theme reference:** [PowerBI-Theme.json](./PowerBI-Theme.json)  
**Layout and acceptance checklist:** [Executive-Report-Blueprint.md](./Executive-Report-Blueprint.md)

## Objective

Build an executive-facing Power BI report using the AdventureWorks data model. The report should summarize revenue and profitability, let users explore revenue drivers, support customer-level drill-through, and provide extra context through a report-page tooltip.

## Current implementation status

The PBIX file is present in this repository, and screenshots shared during the build show these report elements:

- Sales Analysis page with sales trend visuals, KPI cards, customer ranking, and a CustomerKey table.
- Executive Overview page with revenue, orders, gross margin, growth/previous-period measures, trend visuals, and a date slicer.
- Decomposition Tree page analyzing **Total Revenue**.
- Customer 360 page with a CustomerKey drill-through filter, customer details, and customer-level KPI/table visuals.
- 12M Trend Tooltip page selected as a report-page tooltip for a visual.

This confirms that the report has been built beyond the original blueprint. However, a screenshot review is not the same as opening and testing every interaction in the PBIX. Treat the remaining checks below as required validation before calling the exercise fully complete.

## Report pages

| Page | Purpose | Visible implementation | Remaining validation |
|---|---|---|---|
| Sales Analysis | Explore sales and customers | Trend visual, KPI cards, customer ranking, CustomerKey table | Check readable layout, filters, and cross-filtering |
| Executive Overview | Summarize performance | Revenue, orders, gross margin/growth KPIs, trend visuals, date slicer | Improve alignment and whitespace; verify KPI formats and slicer behavior |
| Decomposition Tree | Explore drivers of revenue | Total Revenue analysis with product-category and territory fields | Confirm available Explain by fields and validate branch totals |
| Customer 360 | Customer-level detail | CustomerKey drill-through filter, customer table/details and KPI cards | Test drill-through from a source visual and add/verify a back-navigation button |
| 12M Trend Tooltip | Show additional trend context on hover | Tooltip page is selected in a visual's tooltip settings | Confirm the page itself is configured as a tooltip, uses an appropriate tooltip canvas, and displays correctly on hover |

The PBIX may also contain working or draft pages such as **Page 1**. Rename, complete, or remove unused draft pages only after confirming they are not needed.

## Remaining completion checklist

### 1. Executive Overview layout
- [ ] Align visuals to a consistent grid and make the main KPIs easy to scan.
- [ ] Reduce unused whitespace and ensure visuals are sized consistently.
- [ ] Use meaningful titles, readable labels, and appropriate currency/percentage formats.
- [ ] Test the date slicer and cross-filtering.

### 2. Decomposition Tree
- [x] Set **Analyze** to **Total Revenue**.
- [x] Add product-category and territory-related fields to **Explain by**.
- [ ] Test several branches and confirm their totals agree with the base measure.
- [ ] Use a sales-channel field only if the model actually contains one. If it does not, document the available field used as a substitute instead of inventing a column.

### 3. Customer 360 drill-through
- [x] Add **CustomerKey** to the drill-through filter well.
- [x] Enable **Keep all filters**.
- [ ] From a source visual, right-click a customer data point and choose **Drill through → Customer 360**.
- [ ] Confirm the destination page filters to the selected customer.
- [ ] Add or verify a Back button and test it.

### 4. 12M Trend Tooltip
- [x] Select **12M Trend Tooltip** in a visual's tooltip page setting.
- [ ] On the tooltip page, enable the page's Tooltip setting and use the appropriate tooltip canvas size.
- [ ] Hover over the intended source visual and confirm the tooltip appears and is readable.
- [ ] Check that the displayed trend and YTD/variance values respond to the hovered data point.

### 5. Final quality check
- [ ] Save the PBIX, close it, reopen it, and confirm there are no missing-data or visual errors.
- [ ] Test the report at normal viewing size, not only at a highly reduced zoom.
- [ ] Capture screenshots of each finished page and add them to this folder.
- [ ] Confirm the final PBIX and documentation are committed to GitHub.

## Design notes

- Use a consistent 16:9 report canvas for standard pages.
- Keep the most important KPIs near the top, followed by trends and detailed analysis.
- Use consistent spacing, titles, units, and number formats.
- Keep colors and contrast readable.
- Prefer a small number of purposeful slicers and interactions over clutter.
- Do not commit credentials, access tokens, private customer data, or gateway secrets.

## Files

- **AdventureWorks_Exercise4.pbix** — Power BI report.
- **Executive-Report-Blueprint.md** — layout guidance and acceptance checklist.
- **PowerBI-Theme.json** — starter theme reference.
