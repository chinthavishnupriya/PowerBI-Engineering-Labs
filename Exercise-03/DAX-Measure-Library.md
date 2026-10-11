# Exercise 3 — DAX Measure Library

This reference covers the 11 measure names visible in the Exercise 3 Fields pane and the patterns described by the lab guide. Check the actual table and column names in `AdventureWorks_Exercise3.pbix` before replacing formulas. The formulas below are reference implementations, not an independent validation of the saved PBIX.

## Measure inventory

| Measure | Purpose |
|---|---|
| `Total Revenue` | Sum of sales amount |
| `Total Cost` | Sum of product cost |
| `Gross Margin` | Revenue minus cost |
| `Gross Margin %` | Margin divided by revenue |
| `Total Orders` | Distinct sales order count, if that is the intended definition |
| `Customer Rank` | Rank customers by revenue |
| `Revenue YTD` | Year-to-date revenue |
| `Revenue Previous Year` | Comparable prior-year revenue |
| `Revenue YoY Growth %` | Year-over-year revenue change |
| `Rolling 12M Sales` | Revenue over a rolling 12-month window |
| `Sales by Ship Date` | Revenue using the inactive ship-date relationship |

## Base measures

### Total Revenue

```dax
Total Revenue =
SUM ( FactInternetSales[SalesAmount] )
```

### Total Cost

```dax
Total Cost =
SUM ( FactInternetSales[TotalProductCost] )
```

### Gross Margin

```dax
Gross Margin =
[Total Revenue] - [Total Cost]
```

### Gross Margin %

```dax
Gross Margin % =
DIVIDE ( [Gross Margin], [Total Revenue], 0 )
```

### Total Orders

If the intended metric is the number of distinct sales orders, use the sales order identifier present in the model:

```dax
Total Orders =
DISTINCTCOUNT ( FactInternetSales[SalesOrderNumber] )
```

Check the intended business definition: order count and fact-row count are not necessarily the same.

## Time intelligence

The user's screenshots show a separate `DimDate_Calendar` table with a `Date` column. Use that table only if it is the marked date table and the relationships in the PBIX support these measures.

### Revenue YTD

```dax
Revenue YTD =
TOTALYTD (
    [Total Revenue],
    DimDate_Calendar[Date]
)
```

### Revenue Previous Year

```dax
Revenue Previous Year =
CALCULATE (
    [Total Revenue],
    SAMEPERIODLASTYEAR ( DimDate_Calendar[Date] )
)
```

### Revenue YoY Growth %

```dax
Revenue YoY Growth % =
DIVIDE (
    [Total Revenue] - [Revenue Previous Year],
    [Revenue Previous Year],
    0
)
```

### Rolling 12M Sales

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

## Ship-date relationship

The lab guide calls for `USERELATIONSHIP` so ship-date analysis can use an inactive relationship rather than the active order-date path. The user's screenshot showed a measure using `FactInternetSales[ShipDateKey]` and the `DimDate_Calendar` table. Confirm the exact relationship endpoints in Model view; if the inactive relationship uses another date-key column, use that exact column.

```dax
Sales by Ship Date =
CALCULATE (
    [Total Revenue],
    USERELATIONSHIP (
        FactInternetSales[ShipDateKey],
        DimDate_Calendar[DateKey]
    )
)
```

This formula assumes an inactive relationship exists between those columns. It must be adapted if the actual model uses a different key or date table.

## Customer rank

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

The ranking scope depends on the expression used in `ALL`. If ranking should respond to selected customer groups or other filters, review the intended filter behavior.

## Formatting

| Measure type | Suggested format |
|---|---|
| Total Revenue, Total Cost, Gross Margin, Revenue Previous Year, Rolling 12M Sales, Sales by Ship Date, Revenue YTD | Currency |
| Gross Margin %, Revenue YoY Growth % | Percentage |
| Total Orders, Customer Rank | Whole number |

The lab guide recommends explicit currency, percentage, and integer formats on the measures themselves.

## Validation checklist

- [ ] Verify that all referenced columns exist in the PBIX.
- [ ] Confirm the calendar table is marked as a Date table and covers the relevant dates.
- [ ] Check YTD and prior-year values across more than one year.
- [ ] Test Rolling 12M Sales with date slicers and check its rolling window.
- [ ] Test Sales by Ship Date with a date slicer and verify the inactive relationship endpoints.
- [ ] Check customer ranking under slicers.
- [ ] Confirm formats and divide-by-zero behavior.
- [ ] Confirm no calculated columns were added to `FactInternetSales` for these metrics.

A measure listed in the Fields pane confirms its presence, not that its result is correct in every filter context.
