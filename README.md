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

## How to Access the Report
- **Power BI File:** The latest version of the Power BI `.pbix` file can be found in this repository under the `/Reports` directory.
- **Instructions:** Open the `.pbix` file in Power BI Desktop to explore the report and review the data transformations applied.

---

### Commit Summary:
- Updated README with detailed documentation of the data import and transformation process for Milestone 1.
- Added the latest version of the Power BI report (`.pbix` file) to the repository.
