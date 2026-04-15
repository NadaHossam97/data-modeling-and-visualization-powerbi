# Chocolate Profit Analysis: Regional Performance Dashboard

## Project Overview

This project provides a comprehensive analysis of chocolate sales and profit margins across different global regions. By integrating data from customers, products, and stores, the dashboard identifies high-performing regions and product categories to drive data-informed business strategies.

## Data Architecture

The analysis is built on a **Star Schema** model, utilizing four primary datasets provided in CSV format:

- **Sales (`sales.csv`)**: The fact table containing transaction IDs, dates, product keys, store keys, and profit metrics.
- **Products (`products.csv`)**: Dimension table containing product names, categories, and cost structures.
- **Customers (`customers.csv`)**: Dimension table with customer demographics and regional segments.
- **Store (`store.csv`)**: Dimension table containing store locations and types.

## ETL Process (Power Query)

Data was cleaned and transformed using Power Query to ensure reporting accuracy:

1.  **CSV Integration**: Imported multiple flat files into the Power BI engine.
2.  **Store Table Header Fix**: Addressed a structural issue in the `store` table where the first row was not automatically recognized as a header. Used the **"Use First Row as Headers"** transformation to align the schema.
3.  **Data Typing**: Validated currency, date, and text formats across all tables to prevent calculation errors.

## Data Modeling

Relationships were established to enable cross-filtering and drill-down capabilities:

- **Sales ↔ Products**: One-to-many relationship via `ProductKey`.
- **Sales ↔ Customers**: One-to-many relationship via `CustomerKey`.
- **Sales ↔ Store**: One-to-many relationship via `StoreKey`.

## Version Control & Deployment

To follow modern DevOps and BI best practices, this project is handled via:

- **Format**: Saved as a **Power BI Project (.pbip)** to allow for folder-based tracking of report metadata and datasets.
- **Git**: Local repository initialized to track changes in report definitions.
- **GitHub**: Pushed to a remote repository for documentation and portfolio sharing.

## How to View the Project

1. Clone the repository: `git clone <your-repo-url>`
2. Open the `.pbip` file in **Power BI Desktop**.
3. Ensure the CSV source files are in the same relative directory to maintain data connection strings.
