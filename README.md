# Chocolate Profit Analysis: Regional Performance Dashboard

## Executive Summary
This project analyzes a global chocolate retail operation spanning **6 countries** and **100 stores**. By integrating disparate datasets, this dashboard identifies key seasonal trends and channel efficiencies to optimize a **$25.24M revenue** stream.

| Metric | Value |
| :--- | :--- |
| **Total Revenue** | $25.24M |
| **Total Profit** | $10.10M |
| **Total Customers** | 990.24K |
| **Global Footprint** | 7 Cities across 6 Countries |

---

## 📈 Core Business Findings

### 1. Seasonal Periodicity (The "Q3 Spike")

![chocolate sales performance](./media/chocolateDashboard.png)

* **Trend:** Profitability consistently reaches its annual peak in **July (Q3)**, hitting **$1,278K** in Q3 2023 and **$1,276K** in Q3 2024.
* **Uniformity:** This pattern is statistically consistent across both 2023 and 2024.
* **Insight:** The business experiences a universal demand surge in Q3 that precedes traditional Q4 holiday cycles, regardless of brand or region.

### 2. Product & Market Hierarchy
* **Top Categories:** **Praline** is the primary profit driver globally at **$2.7M**, followed by **White Chocolate ($2.4M)** and **Dark Chocolate ($2.1M)**.
* **Market Leaders:** The **UK** and **USA** are the strongest markets, contributing **19.96% ($5.04M)** and **18.93% ($4.78M)** of total revenue, respectively.
* **Regional Consistency:** The preference for Praline remains the dominant trend across all analyzed countries.

### 3. Operational Channel Efficiency

![chocolate profits by store type](./media/salesByStoreType.png)

* **Channel Ranking:** **Airport locations** are the most profitable channel at **$3.0M**, followed by Malls ($2.6M), Online ($2.5M), and Retail ($1.9M).
* **Brand Distribution:** Profit is evenly spread across brands, with **Ferrero (18.58%)** leading, followed by **Mars (18.48%)**, **Lindt (17.53%)**, **Godiva (16.45%)**, **Hershey (15.01%)**, and **Cadbury (13.95%)**.
* **City Performance:** **Toronto ($1.82M)** and **London ($1.61M)** are the top-performing cities, with all 7 cities generating over **$1M** in profit — indicating consistent performance across the global footprint.
* **Channel Insight:** The narrow gap between Airport, Mall, and Online (~$0.5M spread) suggests a well-diversified channel strategy with no single format dominating.

---

## 🚀 Strategic Recommendations

### 1. Optimize Marketing Spend for Q3
Since profits spike in **July**, the marketing budget should be front-loaded. Shift **40% of the annual promotional budget** to May and June to capture the maximum audience before the peak Q3 window begins.

### 2. Expand the "Airport-First" Retail Model
Airport stores generate the highest profit density at **$3.0M**. Future physical expansion should prioritize international transit hubs in high-revenue regions like the **UK** and **USA** rather than traditional street-level retail.

### 3. Premium Inventory Pivot
With **Praline** and **White Chocolate** driving the bulk of profits, the supply chain should prioritize these categories. Consider reducing inventory of lower-performing categories like **Milk Chocolate ($1.3M)** to free up capital for premium, high-margin product development.

---

## 🛠️ Technical Architecture

### Data Modeling & ETL
The analysis utilizes a **Star Schema** to maintain high performance and filter integrity:

* **Fact Table:** Sales (metrics, keys, dates).
* **Dimension Tables:** Products, Customers, and Stores.
* **Power Query:** The following transformations were applied to standardize data across all EXCEL sources:
  * **Header Normalization:** Resolved structural alignment issues in the `Store` table to ensure consistent column mapping.
  * **Data Type Validation:** Enforced correct data types across all tables to prevent implicit conversion errors in DAX.
  

### DAX Measures
The following time intelligence measure was implemented to track cumulative Year-to-Date profit, enabling within-year performance monitoring against the seasonal Q3 peak:

```dax
Sum of profit YTD =
IF(
    ISFILTERED('sales'[order_date]),
    ERROR("Time intelligence quick measures can only be grouped or filtered by the Power BI-provided date hierarchy or primary date column."),
    TOTALYTD(SUM('sales'[profit]), 'sales'[order_date].[Date])
)
```

This measure uses `TOTALYTD()` to accumulate profit from January 1 of each year through the current date context, making it directly comparable across 2023 and 2024 within the same visual. The `ISFILTERED()` guard ensures the measure only activates under valid date hierarchy filtering, preventing incorrect aggregation when the report is filtered by non-date dimensions.

### Version Control
* **Format:** Saved as a **Power BI Project (.pbip)** for transparent, folder-based metadata tracking.
* **Deployment:** Managed via local **Git** and pushed to **GitHub** to facilitate collaborative development and version history.

---

## How to View
1. **Clone:** `git clone https://github.com/NadaHossam97/data-modeling-and-visualization-powerbi`
2. **Open:** Launch the `.pbip` file in **Power BI Desktop**.
3. **Data Refresh:** Ensure all EXCEL source files remain in the project directory to maintain connection strings.