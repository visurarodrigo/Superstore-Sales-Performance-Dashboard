# 📊 Superstore Sales & Revenue Performance Dashboard

![Dashboard Preview](Sales%20Executive%20Overview.png)

## 🚀 Project Overview

**Status:** Phase 1 Complete (Executive Overview)  
**Tools:** Microsoft Power BI, Power Query, DAX

This project is an end-to-end Business Intelligence solution designed to track Key Performance Indicators (KPIs) for a global retail superstore. The goal was to transform raw sales data into an interactive dashboard that helps stakeholders monitor **Year-over-Year (YoY) growth**, **profitability**, and **regional trends**.

---

## 🛠️ Technical Implementation

### 1. Data Cleaning & Transformation (ETL)

**Challenge:** The raw dataset contained mixed date formats (e.g., `2016-08-11` vs `16/6/2016`) due to regional locale differences.

**Solution:** Leveraged **Power Query's AI "Column from Examples"** to recognize patterns and standardize all dates to a unified format.

**Optimization:** Removed operational noise (Row IDs) and enforced strict data typing for financial accuracy.

### 2. Data Modeling (Star Schema)

**Architecture:** Built a specialized **Date Table** using DAX `CALENDAR()` to enable robust Time Intelligence.

**Relationships:** Established a **One-to-Many (1:*)** relationship between the Dimension table (`DateTable`) and Fact table (`Orders`).

**Performance:** Disabled "Auto Date/Time" to reduce file bloat and improve report rendering speed.

### 3. Advanced DAX Analysis

Moved beyond basic aggregations to create "Time Intelligence" measures:

**YoY Growth %:** Calculated using variables (`VAR`) for readability and performance:

```dax
YoY Growth % = 
VAR CurrentSales = [Total Sales]
VAR PreviousSales = CALCULATE([Total Sales], SAMEPERIODLASTYEAR('DateTable'[Date]))
RETURN
DIVIDE(CurrentSales - PreviousSales, PreviousSales, 0)
```

**Dynamic Logic:** Implemented `DIVIDE()` to handle divide-by-zero errors gracefully.

### 4. Dashboard UX/UI

**Conditional Formatting:** Applied dynamic rules to KPI cards (Red for negative growth, Green for positive).

**Drill-Down Matrix:** Created a hierarchical view allowing users to drill from Category → Sub-Category → Product.

**Visual Hierarchy:** Used a Z-pattern layout with high-level KPIs at the top and granular details at the bottom.

---

## 💡 Key Business Insights Discovered

- **Profitability Warning:** While "Technology" drives revenue, the "Tables" (Furniture) sub-category is operating at a significant loss, likely due to high shipping costs.

- **Seasonality:** A distinct revenue spike occurs in Q4 (Nov-Dec), accounting for ~30% of annual sales.

- **Regional Performance:** The West Region is the top performer, while the Central Region lags in profitability despite healthy sales volume.

---

## 📈 Roadmap

**Next Update:** Adding Customer Segmentation & Geo-Spatial Analysis (Page 2)

---

## 📂 Project Files

- `Superstore sales dataset.xlsx` - Source data file
- `Superstore_Sales_Dashboard.pbix` - Power BI report file

---

## 🤝 Contributing

Feedback and suggestions are welcome! Feel free to open an issue or submit a pull request.
