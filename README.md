# Power BI Quarterly Report

## Project Overview
This project involves creating a comprehensive Power BI report for a medium-sized international retailer. The goal is to transform data from various sources into actionable insights to facilitate better decision-making across different regions.

## Milestone 1: Data Loading and Transformation

### 1. Orders Table
- **Data Source:** Azure SQL Database
- **Import Method:** Connected using the Database credentials option in Power BI.
- **Transformations Performed:**
  - Removed the `[Card Number]` column to ensure data privacy.
  - Split `[Order Date]` and `[Shipping Date]` into separate Date and Time columns.
  - Filtered out rows with missing `[Order Date]` values to maintain data integrity.
  - Renamed columns to follow Power BI naming conventions for consistency.

### 2. Products Table
- **Data Source:** CSV File (`Products.csv`)
- **Import Method:** Imported using the `Get Data > Text/CSV` option in Power BI.
- **Transformations Performed:**
  - Removed duplicates from the `[Product Code]` column to ensure each product code is unique.
  - Renamed columns to align with Power BI naming conventions, ensuring clarity in reporting.

### 3. Stores Table
- **Data Source:** Azure Blob Storage
- **Import Method:** Connected using the Azure Blob Storage connector in Power BI.
- **Transformations Performed:**
  - Renamed columns to follow Power BI naming conventions, ensuring consistency across the report.

### 4. Customers Table
- **Data Source:** Folder containing multiple CSV files (`Customers` folder)
- **Import Method:** Used the `Get Data > Folder` option to combine and transform data from the CSV files.
- **Transformations Performed:**
  - Combined `[First Name]` and `[Last Name]` into a single `Full Name` column.
  - Removed unused columns (e.g., index columns) to streamline the dataset.
  - Renamed the remaining columns to align with Power BI naming conventions for consistency and clarity.

## Milestone 2: Data Modeling and Measures

### 1. Date Table
- **Data Source:** Generated in Power BI using DAX.
- **Steps Taken:**
  - Created a continuous date table covering the time period from the earliest `[Order Date]` to the latest `[Shipping Date]`.
  - Added columns for Day of Week, Month Number, Month Name, Quarter, Year, Start of Year, Start of Quarter, Start of Month, and Start of Week using DAX formulas.

### 2. Star Schema Data Model
- **Relationships Created:**
  - `Products[product_code]` to `orders_powerbi[product_code]`
  - `data-analytics (2)[store code]` to `orders_powerbi[Store Code]`
  - `Customers[User UUID]` to `orders_powerbi[User ID]`
  - `DateTable[date]` to `orders_powerbi[Order Date]`
  - Ensured that the relationship between `orders_powerbi[Order Date]` and `DateTable[date]` is the active relationship.

### 3. Key Measures
- **Measures Created:**
  - `Total Orders`: Counts the number of orders in the `orders_powerbi` table.
  - `Total Revenue`: Multiplies `orders_powerbi[Product Quantity]` by `Products[Sale Price]` and sums the result.
  - `Total Profit`: Calculates the difference between `Products[Sale Price]` and `Products[Cost Price]`, multiplies by `orders_powerbi[Product Quantity]`, and sums the result.
  - `Total Customers`: Counts the number of unique customers in the `orders_powerbi` table.
  - `Total Quantity`: Counts the number of items sold in the `orders_powerbi` table.
  - `Profit YTD`: Calculates the total profit for the current year.
  - `Revenue YTD`: Calculates the total revenue for the current year.

### 4. Hierarchies
- **Date Hierarchy:** Created a hierarchy with levels for Start of Year, Start of Quarter, Start of Month, Start of Week, and Date.
- **Geography Hierarchy:** Created a hierarchy with levels for World Region, Country, and Country Region, including calculated columns for `Country` and `Geography` in the `data-analytics (2)` table.

## How to Access the Report
- **Power BI File:** The latest version of the Power BI `.pbix` file can be found in this repository under the `/Reports` directory.
- **Instructions:** Open the `.pbix` file in Power BI Desktop to explore the report and review the data transformations applied.

---

### Commit Summary:
- Updated README with detailed documentation of the data import and transformation process for Milestone 1 and Milestone 2.
- Added the latest version of the Power BI report (`.pbix` file) to the repository.
