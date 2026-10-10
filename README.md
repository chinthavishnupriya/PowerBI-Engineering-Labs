# Power BI Engineering Labs

A practical collection of Power BI lab exercises focused on preparing data, building a relational data model, and creating interactive reports for analysis.

## Exercise 1 — Sales and Monthly Forecast Dashboard

**Status:** Completed  
**Main file:** [`PowerBI_Engineering_Lab_Exercise1.pbix`](./PowerBI_Engineering_Lab_Exercise1.pbix)

### 1. Objective

The goal of this exercise is to build an interactive Power BI report that brings sales orders and monthly forecast data together. The report lets a user review key totals and explore sales and forecast patterns by date, month, and product.

### 2. Data used

The exercise uses sample retail/business data loaded into Power BI, including:

- **Sales orders** (`stg_Sales_Orders`) — order-level sales information, including order date, customer, product, quantity, and sales amount.
- **Customer data** (`stg_DimCustomer`) — customer details associated with sales orders.
- **Monthly forecast** (`stg_MonthlyForecast`) — product-level forecast amounts by month, including `ProductID`, `ProductName`, `Month`, `ForecastAmount`, and `ForecastDate`.
- **Product dimension** (`DimProduct`) — product identifiers and names used to analyze sales and forecasts by product.
- **Date dimension** (`DimDate`) — calendar dates used for date-based filtering and analysis.

### 3. What was done

#### Data preparation with Power Query

- Imported the provided sales, customer, and forecast data into Power BI.
- Reviewed the tables and prepared the forecast data for date-based reporting.
- Used `ForecastDate` as the date field for relating monthly forecast records to the calendar table.

#### Data modeling and relationships

Created relationships so report visuals can analyze sales and forecasts using shared dimensions:

- `stg_Sales_Orders[OrderDate]` → `DimDate[Date]`
- `stg_Sales_Orders[ProductID]` → `DimProduct[ProductID]`
- `stg_Sales_Orders[CustomerID]` → `stg_DimCustomer[CustomerID]`
- `stg_MonthlyForecast[ForecastDate]` → `DimDate[Date]`
- `stg_MonthlyForecast[ProductID]` → `DimProduct[ProductID]`

These relationships connect the fact data to date, product, and customer information for reporting.

#### Report and visualizations

The report includes:

- **Total Sales card** — summarizes the sales amount.
- **Total Orders card** — gives a quick view of order volume.
- **Total Quantity visual** — summarizes the quantity recorded in sales data.
- **Total Forecast visual** — summarizes forecast amounts.
- **Sales Amount by Order Date** — helps inspect sales across dates.
- **Forecast Amount by Month** — compares forecast values across months.
- **Sales Amount by Product Name** — helps identify how sales are distributed across products.
- **Date slicer** — allows the report to be filtered by a selected date or date range.

### 4. How to use the report

1. Download the `.pbix` file from this repository.
2. Open it in **Microsoft Power BI Desktop**.
3. Navigate to the report page.
4. Use the date slicer to filter the report.
5. Review the cards and charts to explore sales, order quantities, product-level results, and monthly forecasts.

### 5. Skills practiced

- Importing data into Power BI
- Basic data preparation with Power Query
- Understanding fact tables and dimension tables
- Creating and checking table relationships
- Connecting sales and forecast data through shared dimensions
- Building report cards, charts, and slicers
- Designing an interactive report for business analysis

### 6. Outcome

Exercise 1 produced a working Power BI dashboard that brings together sales and monthly forecast information in one report. It demonstrates the basic workflow from importing data and creating relationships to presenting summary metrics and interactive visual analysis.

## Repository contents

| Path | Description |
|---|---|
| `PowerBI_Engineering_Lab_Exercise1.pbix` | Completed Exercise 1 Power BI report |
| `README.md` | Exercise documentation and usage instructions |

Additional exercises will be documented here as they are completed.

## Tools

- Microsoft Power BI Desktop
- Power Query
- Data modeling and relationships
- Report visuals and slicers