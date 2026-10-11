# Exercise 3 — DAX Measure Library

This reference matches the measure names visible in the Exercise 3 model and the patterns in the lab guide. Check the actual table and column names in `AdventureWorks_Exercise3.pbix` before replacing formulas. The formulas below are reference implementations, not an independent validation of the saved PBIX.

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

If the intended metric is distinct sales orders, use the sales order identifier present in the model:

```dax
Total Orders =
DISTINCTCOUNT ( FactInternetSales[SalesOrderNumber] )
```

Check the intended business definition before using this measure; order counts and row counts are not necessarily the same.

## Time intelligence

These examples use `DimDate_Calendar[Date]`. Replace it with the actual marked date table/column if your model differs.

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

### Sales by Ship Date

Use the actual ship-date key/date column and the matching date dimension key. The lab guide uses `USERELATIONSHIP` to activate an inactive relationship for this calculation.

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

This formula assumes that the relationship between those columns exists and is inactive. If your model uses date columns instead of date keys, adapt both arguments to the actual relationship endpoints.

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

## Formatting and checks

| Measure | Suggested format |
|---|---|
| Total Revenue, Total Cost, Gross Margin, Revenue Previous Year, Rolling 12M Sales, Sales by Ship Date | Currency |
| Gross Margin %, Revenue YoY Growth % | Percentage |
| Total Orders, Customer Rank | Whole number |
| Revenue YTD | Currency |

- [ ] Verify the actual columns exist.
- [ ] Confirm the calendar is marked as a Date table.
- [ ] Check YTD and prior-year values across multiple years.
- [ ] Test Sales by Ship Date with a date slicer.
- [ ] Confirm percentage formats and divide-by-zero behavior.
