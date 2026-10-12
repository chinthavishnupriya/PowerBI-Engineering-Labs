# Exercise 4 — Executive Visual Analytics

**Project:** AdventureWorks Executive Report  
**Power BI file:** [AdventureWorks_Exercise4.pbix](./AdventureWorks_Exercise4.pbix)  
**Theme reference:** [PowerBI-Theme.json](./PowerBI-Theme.json)  
**Layout reference:** [Executive-Report-Blueprint.md](./Executive-Report-Blueprint.md)

## Objective

Turn the AdventureWorks model and DAX measures into a multi-page report for executive summaries, sales analysis, revenue-driver exploration, customer detail, and contextual tooltips.

## 1. Sales Analysis page

The screenshots show a sales amount trend by month/year, KPI cards for Total Revenue, Total Cost, and Gross Margin, a customer-ranking horizontal bar chart using customer names, and a CustomerKey table. Customer names such as Maurice, Francisco, Brad, Brandi, and Rosa appear in the ranking visual. Customer keys appear in the table for browsing records.

## 2. Executive Overview page

The page includes KPI cards for Total Revenue, Total Orders, Gross Margin, Gross Margin %, Revenue YoY Growth %, and Revenue YTD, along with a date slicer and trend/breakdown visuals. Visible charts include Total Revenue by MonthYear, Total Revenue by LastName, and Total Revenue by EnglishProductName. The date slicer screenshot shows 01-01-2010 to 31-12-2014.

For a polished report, align the cards and charts, keep number formats consistent, use readable titles, and test the slicer and visual interactions at normal viewing size.

## 3. Decomposition Tree page

Created a Decomposition Tree with Analyze set to Total Revenue. The Explain by well contains product-category-related and sales-territory-related fields, and the screenshot shows the revenue tree expanded into numeric branches.

The field search did not show a clear Sales Channel field in the model, so available product-category and territory fields were used rather than assuming that a missing Sales Channel column exists. Test the branches and compare the displayed totals with the base measure.

## 4. Customer 360 page

The Customer 360 page is intended for customer-level drill-through. Screenshots show CustomerKey in the drill-through filter well, Keep all filters enabled, customer-key data in a table, and KPI/report visuals. The drill-through field was added from DimCustomer[CustomerKey].

Test the complete flow by right-clicking a customer data point on a source page, choosing Drill through → Customer 360, and checking that the destination is filtered to that customer. Add or verify a back-navigation button if required by the lab.

## 5. 12M Trend Tooltip page

Created a page named 12M Trend Tooltip and selected it in a visual's tooltip page setting under Format visual → General → Tooltips. The screenshot shows the page selected in the Page dropdown. Verify that the tooltip page itself is configured as a tooltip, contains the intended context visuals, and appears correctly when hovering over the source visual.

## Design and usability

- Use a consistent canvas size for standard report pages.
- Align visual edges and keep spacing consistent.
- Place key performance indicators before supporting detail.
- Use consistent currency, percentage, and whole-number formats.
- Keep chart titles and axis labels readable.
- Use drill-through and tooltips to show details without overcrowding the overview.
- Verify interactions and filter behavior in Power BI Desktop.

## Files

- AdventureWorks_Exercise4.pbix — report and model.
- Executive-Report-Blueprint.md — layout and design reference.
- PowerBI-Theme.json — starter theme.

## Outcome

Exercise 4 combines earlier measures into a report with sales analysis, an executive summary, decomposition-tree analysis, a Customer 360 drill-through destination, and a trend tooltip page. Screenshots document the visible build; final interaction and layout validation should be performed in the saved PBIX.

## Suggested build and review order

1. Confirm the required DAX measures and date fields are available from earlier exercises.
2. Build the Sales Analysis page first, with key KPIs, monthly trend, customer ranking, and customer-level detail.
3. Arrange the Executive Overview page so summary KPIs appear before supporting trends and breakdowns.
4. Configure the Decomposition Tree with Total Revenue in Analyze and appropriate explanatory fields available in the model.
5. Add Customer 360 as a drill-through destination using DimCustomer[CustomerKey] and retain the relevant filters.
6. Create the 12M Trend Tooltip page and configure the source visual to use it as a report-page tooltip.
7. Apply the provided theme if desired, align visual edges, and use consistent titles and number formats.
8. Test every page in Reading view and at a normal report size.

## Interaction test checklist

- Change the date slicer and verify that the expected visuals respond.
- Select a bar or data point and check whether cross-filtering/highlighting is intentional.
- Right-click a customer data point and test Drill through → Customer 360.
- Confirm the destination shows the selected customer's context and that navigation back to the source page is available if required.
- Hover over the intended source visual and confirm the 12M Trend Tooltip appears with relevant context.
- Expand multiple branches in the Decomposition Tree and compare the values with the base Total Revenue measure.

## Design review

- Use consistent alignment, spacing, font hierarchy, and number formatting.
- Avoid overcrowding the overview page; move detailed records to Customer 360.
- Use meaningful visual titles and axis labels.
- Ensure colors provide contrast and are consistent with the imported theme.
- Check that labels remain readable without relying on hover-only information.

## Validation record

The repository documents the five pages and includes a report blueprint and theme JSON. The saved PBIX still needs a hands-on interaction check to confirm drill-through, tooltip configuration, slicer behavior, and totals work as intended.
