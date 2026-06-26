# 🍫 Chocolate Sales Dashboard | Power BI

![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-F2C811?logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-Measures-blue)
![Power Query](https://img.shields.io/badge/Power%20Query-ETL-green)
![Excel](https://img.shields.io/badge/Excel-Dataset-217346?logo=microsoftexcel&logoColor=white)

---

## 📌 Project Overview

This interactive Power BI dashboard analyzes chocolate sales performance across multiple countries and products.

It enables users to monitor business KPIs, identify profitable products, compare country-wise sales, and explore shipment performance using interactive visualizations.

---

## 📷 Dashboard Preview

![Dashboard](dashboard-preview.png)

---

## 🎥 Dashboard Demo

Download the demo video from this repository:

**dashboard-demo.mp4**

---

## 📊 Business KPIs

- 💰 Total Sales
- 📦 Total Boxes Sold
- 🚚 Total Shipments
- 💵 Total Profit
- 📈 Profit %
- 📉 Month-over-Month Performance

---

## 📈 Dashboard Features

- Interactive Country Filters
- Product Category Filters
- KPI Cards
- Sales Trend Analysis
- Donut Chart
- Gauge Chart
- Shipment Distribution
- Product Profitability Table
- Conditional Formatting

---

## 🛠 Tools & Technologies

- Power BI Desktop
- DAX
- Power Query
- Microsoft Excel

---

## 📂 Repository Contents

| File | Description |
|------|-------------|
| Chocolate Sales Dashboard.pbix | Power BI Project |
| dashboard-preview.png | Dashboard Preview |
| dashboard-demo.mp4 | Dashboard Walkthrough |

---

## 🗂️ Sample Asset Structure

```text
Powerbi-Chocolate-Sales-Dashboard/
├── Chocolate Sales Dashboard.pbix
├── dashboard-preview.png
├── dashboard-demo.mp4
├── images/
│   ├── overview.png
│   ├── country-analysis.png
│   └── product-performance.png
├── data/
│   └── sample-sales-data.xlsx
├── README.md
└── LICENSE
```

> `images/` and `data/` are optional but recommended for better project organization and sharing.

---

## 🧩 Data Model

The dashboard follows a star-schema style model for efficient filtering and KPI calculation.

### Core Tables

- **Fact_Sales** (transaction-level data)
  - Date
  - Product
  - Country
  - Sales Amount
  - Profit
  - Boxes/Quantity
  - Shipment ID

- **Dim_Date** (calendar table)
  - Date
  - Month
  - Quarter
  - Year
  - Month-Year (for trend visuals)

- **Dim_Product**
  - Product Name
  - Category / Segment
  - Cost (if available)

- **Dim_Country**
  - Country
  - Region / Market (if available)

### Relationships

- `Fact_Sales[Date]` → `Dim_Date[Date]` (Many-to-One)
- `Fact_Sales[Product]` → `Dim_Product[Product Name]` (Many-to-One)
- `Fact_Sales[Country]` → `Dim_Country[Country]` (Many-to-One)

This structure enables:
- Fast time-intelligence calculations
- Accurate slicer behavior
- Better maintainability and scalability

---

## 🧠 Top DAX Measures

```DAX
Total Sales = SUM(Fact_Sales[Sales Amount])
```
Returns the total revenue across current filter context.

```DAX
Total Profit = SUM(Fact_Sales[Profit])
```
Calculates total profit for selected period/products/countries.

```DAX
Total Boxes = SUM(Fact_Sales[Boxes])
```
Tracks total unit volume sold.

```DAX
Total Shipments = DISTINCTCOUNT(Fact_Sales[Shipment ID])
```
Counts unique shipments to measure logistics activity.

```DAX
Profit % = DIVIDE([Total Profit], [Total Sales], 0)
```
Shows profit margin safely (avoids divide-by-zero errors).

```DAX
Sales MoM % =
VAR PrevMonthSales =
    CALCULATE([Total Sales], DATEADD(Dim_Date[Date], -1, MONTH))
RETURN
    DIVIDE([Total Sales] - PrevMonthSales, PrevMonthSales, 0)
```
Measures month-over-month sales growth rate.

```DAX
Sales YTD = TOTALYTD([Total Sales], Dim_Date[Date])
```
Computes cumulative year-to-date sales.

---

## 💡 Skills Demonstrated

- Data Cleaning
- Data Transformation
- Data Modeling
- DAX Calculations
- Business Intelligence
- Dashboard Design
- Data Visualization

---

## 📈 Business Insights

- A small group of products contributes a large share of overall revenue.
- Some countries consistently outperform others in both sales and profitability.
- Sales show noticeable periodic peaks, indicating seasonal demand patterns.
- High shipment volume does not always align with high profit %, highlighting margin optimization opportunities.

---

## 🚀 How to Use

1. Download the `.pbix` file.
2. Open it using Power BI Desktop.
3. Refresh the dataset if required.
4. Explore the dashboard using the slicers and filters.

---

## 👨‍💻 Author

### Kafeel Haji

Aspiring Data Analyst

- SQL
- Power BI
- Excel
- Python

⭐ If you found this project useful, consider giving it a Star.

---

## 📄 License

This project is licensed under the **MIT License**.  
See the [LICENSE](LICENSE) file for details.
