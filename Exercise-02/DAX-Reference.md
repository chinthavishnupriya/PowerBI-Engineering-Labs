# Exercise 2 — DAX and Date Modeling Reference

This file records the date-modeling concepts relevant to Exercise 2 and prepares for Exercise 3. Adapt names to the tables and columns in your own Power BI model.

## Calendar table example from the lab guide

The lab guide proposes a dedicated calendar table covering 2023–2026:

```dax
DimDate =
CALENDAR(
    DATE(2023, 1, 1),
    DATE(2026, 12, 31)
)
```

Add date attributes such as fiscal year, quarter, month, and month-year as required by the lab. Check that the chosen date range covers the fact table's dates.

## Relationship principles

- Connect a date dimension to the fact table through matching date keys or date columns.
- Use one-to-many cardinality and single-direction filtering for the usual dimension-to-fact path.
- Use the order date as the active date relationship for the main sales report.
- Keep alternate date roles, such as ship date, inactive if activating them would create competing filter paths.

## Using an inactive relationship later

In Exercise 3, a measure can activate an inactive relationship for a specific calculation by using `USERELATIONSHIP`. Example pattern (replace names if your model differs):

```dax
Sales by Ship Date =
CALCULATE(
    SUM(FactInternetSales[SalesAmount]),
    USERELATIONSHIP(
        FactInternetSales[ShipDateKey],
        DimDate_Calendar[DateKey]
    )
)
```

This is a reference pattern, not a claim that the measure has already been created or validated in the PBIX.

## Sorting month labels

If `MonthYear` is text, set **Sort by column** to a chronological column such as a numeric year-month key. This prevents alphabetical sorting and keeps visuals in calendar order.
