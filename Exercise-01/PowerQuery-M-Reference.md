# Exercise 1 — Power Query M Reference

These are adaptable patterns for the ETL requirements in the lab guide. Replace server, database, table, column, and file names to match your environment.

## 1. SQL source parameterization

Create a Power Query text parameter named `ServerName`, then use the parameter rather than hardcoding the machine name.

```powerquery
let
    Source = Sql.Database(ServerName, "AdventureWorksDW2020"),
    Sales = Source{[Schema = "dbo", Item = "FactInternetSales"]}[Data],
    FilteredRows = Table.SelectRows(
        Sales,
        each [OrderDateKey] >= 20240101
    ),
    TypedColumns = Table.TransformColumnTypes(
        FilteredRows,
        {
            {"SalesOrderNumber", type text},
            {"SalesAmount", Currency.Type},
            {"OrderDateKey", Int64.Type}
        }
    )
in
    TypedColumns
```

This mirrors the guide's filtering/type-enforcement pattern. It will only work if the selected database and columns exist.

## 2. Unpivot monthly forecast columns

Keep the identifier columns and convert month columns into attribute/value rows.

```powerquery
let
    Source = /* replace with the actual forecast source */,
    Unpivoted = Table.UnpivotOtherColumns(
        Source,
        {"Product", "Region"},
        "Month",
        "ForecastAmount"
    ),
    Typed = Table.TransformColumnTypes(
        Unpivoted,
        {{"ForecastAmount", Currency.Type}}
    )
in
    Typed
```

Replace `Product` and `Region` with the actual identifier columns. Convert the Month attribute into a real date if required by the report.

## 3. ETL validation checklist

- [ ] Promote headers and remove unusable/corrupt rows.
- [ ] Trim and clean text fields.
- [ ] Explicitly assign date, whole-number, text, and currency types.
- [ ] Check duplicates and nulls in key columns.
- [ ] Compare row counts and totals before and after transformation.
- [ ] Confirm the unpivoted forecast has one row per identifier/date.
- [ ] For supported SQL steps, check **View Native Query** to audit query folding.
- [ ] Disable load for intermediate staging queries that are not model tables.

Query folding depends on the connector and transformation sequence. A reference query is not evidence that folding is enabled in the user's actual PBIX.
