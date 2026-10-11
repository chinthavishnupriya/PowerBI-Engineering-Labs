# Exercise 1 — Power Query M Reference

These are adaptable patterns for the lab guide's multi-source ETL requirements. Replace server, database, table, column, and file names to match the actual environment. These examples are templates—not proof that the corresponding steps are already configured in the PBIX.

## 1. Source parameters

Create Power Query parameters from **Home → Manage Parameters**:

- `FilePath` (Text): the folder path containing the CSV/XLSX inputs.
- `ServerName` (Text): SQL Server/instance name used on the current machine.

Use parameters instead of hardcoding a personal file path or server name. Keep credentials out of source code and GitHub.

Example CSV source using a folder parameter:

```powerquery
let
    Source = Csv.Document(
        File.Contents(FilePath & "\Sales_Orders.csv"),
        [Delimiter = ",", Encoding = 65001, QuoteStyle = QuoteStyle.Csv]
    ),
    PromotedHeaders = Table.PromoteHeaders(
        Source,
        [PromoteAllScalars = true]
    )
in
    PromotedHeaders
```

If `FilePath` already includes the filename, remove the appended filename from the example. Check the slash at the end of the folder path.

## 2. SQL product/sales source and folding audit

The lab guide's sample uses AdventureWorksDW2020. Use the database installed in your own environment; do not assume the sample database name matches your SQL Server instance.

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

This is an illustrative SQL transformation pattern; adjust the database/table and filter for the actual product catalog query and schema. The lab guide specifically requires filtering active product SKUs and coercing currency on the SQL product source.

**Query-folding audit:** in Power Query, right-click the relevant SQL query step and check **View Native Query**. Check the steps where folding is expected. If the menu is disabled, investigate the connector/step sequence; do not claim 100% folding from this sample alone.

## 3. Customer CRM cleaning

For the workbook's customer table, use the actual sheet/table name and column names. The following shows the common trim/clean pattern:

```powerquery
let
    Source = Excel.Workbook(File.Contents(FilePath & "\Retail_CRM_and_Products.xlsx"), null, true),
    CustomerSource = Source{[Item = "Customers", Kind = "Table"]}[Data],
    PromotedHeaders = Table.PromoteHeaders(CustomerSource, [PromoteAllScalars = true]),
    TrimmedText = Table.TransformColumns(
        PromotedHeaders,
        {
            {"FirstName", each if _ = null then null else Text.Trim(Text.Clean(_)), type text},
            {"LastName", each if _ = null then null else Text.Trim(Text.Clean(_)), type text},
            {"EmailAddress", each if _ = null then null else Text.Lower(Text.Trim(Text.Clean(_))), type text}
        }
    ),
    AddedFullName = Table.AddColumn(
        TrimmedText,
        "FullName",
        each Text.Combine(List.RemoveNulls({[FirstName], [LastName]}), " "),
        type text
    )
in
    AddedFullName
```

This is a template only. Confirm the workbook table is actually named `Customers` and that its columns are `FirstName`, `LastName`, and `EmailAddress`; otherwise substitute the real names.

## 4. Unpivot monthly forecast columns

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

Replace `Product` and `Region` with the actual identifier columns. Convert the Month attribute to a real date using the source's month format, then verify that each identifier/date combination has the intended grain.

## 5. Staging and data-quality checks

- Promote headers and remove unusable/corrupt sales rows.
- Explicitly assign date, whole-number, text, and currency types; do not rely on automatic detection.
- Trim/clean text and normalize email casing if appropriate.
- Check duplicates and nulls in keys.
- Compare row counts and totals before and after transformation.
- Confirm the forecast has one row per required identifier/date.
- Disable **Enable Load** for intermediate staging queries that are not final model tables.
- Refresh from a clean session and verify the report totals.

## Lab-guide acceptance checklist

- [ ] `FilePath` and `ServerName` parameters exist and are used.
- [ ] CSV and workbook queries refresh successfully.
- [ ] Sales order dates/types and corrupt rows are handled.
- [ ] CRM name/email cleanup is complete.
- [ ] Monthly forecast is unpivoted into date/amount rows.
- [ ] SQL product query filters active SKUs and assigns required types.
- [ ] Query folding has been checked in Power Query for supported SQL steps.
- [ ] Staging queries are isolated from final model tables.
- [ ] Row counts, key quality, and business totals have been checked.

Query folding depends on the connector and transformation sequence. A reference query is not evidence that folding is enabled in the user's actual PBIX.
