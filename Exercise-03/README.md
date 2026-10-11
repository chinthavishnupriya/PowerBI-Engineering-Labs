# Exercise 3 — Advanced DAX Engine

**Project:** AdventureWorks Data Analysis  
**Status:** Report and DAX measures created in Power BI Desktop; PBIX and measure reference are in this folder.  
**Main file:** `AdventureWorks_Exercise3.pbix`

## 1. Objective

Build a reusable DAX measure layer for AdventureWorks Internet Sales. This exercise moves beyond basic visuals by calculating business metrics, profitability, customer ranking, and time-based sales performance. Measures are organized in a dedicated `_Measures` table so calculations can be reused across report visuals.

The exercise follows the supplied Power BI Engineering Hands-on Lab Guide, Exercise 3: **Calculated Fields & Advanced DAX Measures**.

## 2. Dataset and model

The report uses the AdventureWorks Data Warehouse sales model. The main fact table is:

- `FactInternetSales` — sales transactions, sales amount, product cost, customer/product keys, and order/ship date keys.

The model also uses dimension tables such as:

- `DimCustomer` — customer attributes used for customer analysis.
- `DimDate` or `DimDate_Calendar` — date attributes used for time-intelligence calculations.

Check the exact table and column names in the PBIX before copying formulas: names can differ depending on the imported schema and calendar table used.

## 3. DAX concepts practiced

| Concept / function | Purpose in this exercise |
|---|---|
| `SUM` | Aggregate sales and product cost |
| Measure references | Reuse base measures in other calculations |
| `DIVIDE` | Calculate ratios safely, including a fallback for a zero denominator |
| `CALCULATE` | Evaluate a measure under a modified filter context |
| `TOTALYTD` | Calculate year-to-date revenue |
| `SAMEPERIODLASTYEAR` | Compare the selected period with the equivalent prior-year period |
| `DATESINPERIOD` | Define a rolling 12-month date window |
| `USERELATIONSHIP` | Use an inactive relationship for ship-date analysis |
| `RANKX` | Rank customers by revenue |

## 4. Measure library

The `_Measures` table in the report contains the following measure names:

| Measure | Business meaning |
|---|---|
| `Total Revenue` | Sum of sales amount |
| `Total Cost` | Sum of total product cost |
| `Gross Margin` | Revenue minus product cost |
| `Gross Margin %` | Gross margin as a share of revenue |
| `Total Orders` | Order-count KPI |
| `Customer Rank` | Customer ranking by revenue |
| `Revenue YTD` | Revenue accumulated from the start of the year through the selected date |
| `Revenue Previous Year` | Revenue for the comparable prior-year period |
| `Revenue YoY Growth %` | Percentage change compared with the prior-year period |
| `Rolling 12M Sales` | Revenue over a moving 12-month window |
| `Sales by Ship Date` | Revenue analyzed using the ship-date relationship |

### Representative DAX patterns

These formulas are reference patterns from the lab concepts. Confirm the exact columns and relationship endpoints in the saved PBIX before treating each formula as independently validated.

**Total Revenue**
```dax
Total Revenue =
SUM ( FactInternetSales[SalesAmount] )
```

**Total Cost**
```dax
Total Cost =
SUM ( FactInternetSales[TotalProductCost] )
```

**Gross Margin**
```dax
Gross Margin =
[Total Revenue] - [Total Cost]
```

**Gross Margin %**
```dax
Gross Margin % =
DIVIDE ( [Gross Margin], [Total Revenue], 0 )
```

**Revenue YTD**
```dax
Revenue YTD =
TOTALYTD (
    [Total Revenue],
    DimDate_Calendar[Date]
)
```

**Revenue Previous Year**
```dax
Revenue Previous Year =
CALCULATE (
    [Total Revenue],
    SAMEPERIODLASTYEAR ( DimDate_Calendar[Date] )
)
```

**Revenue YoY Growth %**
```dax
Revenue YoY Growth % =
DIVIDE (
    [Total Revenue] - [Revenue Previous Year],
    [Revenue Previous Year],
    0
)
```

**Rolling 12M Sales**
```dax
Rolling 12M Sales =
CALCULATE (
    [Total Revenue],
    DATESINPERIOD (
        DimDate_Calendar[Date],
        MAX ( DimDate_Calendar[Date] ),
        -12,
        MONTH
    )
)
```

**Customer Rank**
```dax
Customer Rank =
RANKX (
    ALL ( DimCustomer ),
    [Total Revenue],
    ,
    DESC,
    DENSE
)
```

**Sales by Ship Date**

The guide uses `USERELATIONSHIP` to activate the inactive ship-date relationship for this calculation. Use the same two columns that form the inactive relationship in the actual model.

```dax
Sales by Ship Date =
CALCULATE (
    [Total Revenue],
    USERELATIONSHIP (
        FactInternetSales[ShipDateKey],
        DimDate[DateKey]
    )
)
```

For all formulas, adapt the calendar table and key columns to the relationship endpoints in the PBIX. See [DAX-Measure-Library.md](./DAX-Measure-Library.md) for the longer reference and validation notes.

## 5. Report visuals and KPIs

The saved report includes the following elements:

- **KPI cards:** Gross Margin %, Revenue YoY Growth %, Total Cost, Total Orders, and Gross Margin.
- **Sales by Ship Date:** a line chart showing sales over time using the ship-date measure.
- **Rolling 12M Sales:** a visual for the rolling 12-month sales measure.
- **Customer Rank and Customer Rank by FirstName:** a horizontal bar chart ranking customers.
- **Sales by Ship Date / MonthYear:** a time-based trend visual.

The layout combines headline business indicators with trend and customer-level analysis. Use the date axis and available report filters to inspect how measures respond to context.

## 6. Formatting recommendations

| Measure type | Recommended format |
|---|---|
| Revenue, cost, gross margin, YTD, previous-year sales, rolling sales | Currency |
| Gross Margin %, Revenue YoY Growth % | Percentage |
| Total Orders, Customer Rank | Whole number |

Apply formats to the measures themselves where possible, rather than relying only on visual-level formatting. Keep percentage decimal places consistent across KPI cards.

## 7. Validation checklist

### Completed / present in repository
- [x] `AdventureWorks_Exercise3.pbix` is present.
- [x] A dedicated `_Measures` table is visible in the model.
- [x] The measure names listed above are present in the model.
- [x] KPI and analytical visuals are present in the report.

### Recommended final verification
- [ ] Open the PBIX from a fresh repository download and check for missing-source errors.
- [ ] Verify each DAX expression against the actual table and column names.
- [ ] Mark the intended calendar table as a Date table and confirm its date range covers the sales data.
- [ ] Test YTD and prior-year calculations across more than one year.
- [ ] Test Rolling 12M Sales with a date filter and confirm the expected rolling window.
- [ ] Test Sales by Ship Date and verify that the intended inactive relationship is used.
- [ ] Check customer rank under slicers and confirm the intended ranking scope.
- [ ] Confirm currency, percentage, and whole-number formatting.
- [ ] Capture screenshots of the measure list, report page, and relevant relationship settings.

A measure appearing in the Fields pane confirms that it exists in the model; it does not, by itself, prove that the calculation is correct for every filter context.

## 8. Files in this folder

- `AdventureWorks_Exercise3.pbix` — Power BI report and model.
- `DAX-Measure-Library.md` — reference formulas, explanations, formatting, and validation checks.
- `README.md` — exercise overview, concepts, report contents, and verification checklist.

## 9. Skills demonstrated

- DAX measure authoring and measure reuse
- Revenue and cost aggregation
- Profitability and percentage calculations
- Time intelligence and year-over-year comparisons
- Rolling-window analysis
- Inactive relationship activation using `USERELATIONSHIP`
- Customer ranking with `RANKX`
- KPI cards and analytical Power BI visuals
