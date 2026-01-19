# 📊 Superstore Sales & Revenue Performance Dashboard

## 🚀 Project Overview

This project is an end-to-end Business Intelligence solution designed to track Key Performance Indicators (KPIs) for a global retail superstore. The goal was to transform raw sales data into an interactive dashboard that helps stakeholders monitor **Year-over-Year (YoY) growth**, **profitability**, and **regional trends**

## Phase 1: Sales Executive Overview

![Dashboard Preview](Screenshots/Sales%20Executive%20Overview.jpg)
 
**Tools:** Microsoft Power BI, Power Query, DAX

### 🛠️ Technical Implementation

#### 1. Data Cleaning & Transformation (ETL)

**Challenge:** The raw dataset contained mixed date formats (e.g., `2016-08-11` vs `16/6/2016`) due to regional locale differences.

**Solution:** Leveraged **Power Query's AI "Column from Examples"** to recognize patterns and standardize all dates to a unified format.

**Optimization:** Eliminated operational noise (e.g., redundant Row IDs) and enforced strict data typing to ensure financial accuracy.

#### 2. Data Modeling (Star Schema)

**Architecture:** Built a specialized **Date Table** using DAX `CALENDAR()` to enable robust Time Intelligence.

**Relationships:** Established a **One-to-Many (1:*)** relationship between the Dimension table (`DateTable`) and Fact table (`Orders`).

**Performance Optimization:** Disabled Power BI's "Auto Date/Time" feature to reduce file size and enhance report rendering performance.

#### 3. Advanced DAX Analysis

Developed Time Intelligence measures that extend beyond standard aggregations:

**YoY Growth Percentage:** Implemented using DAX variables (`VAR`) for enhanced code readability and execution performance:

```dax
YoY Growth % = 
VAR CurrentSales = [Total Sales]
VAR PreviousSales = CALCULATE([Total Sales], SAMEPERIODLASTYEAR('DateTable'[Date]))
RETURN
DIVIDE(CurrentSales - PreviousSales, PreviousSales, 0)
```

**Error Handling:** Utilized the `DIVIDE()` function to gracefully handle potential divide-by-zero scenarios.

#### 4. Dashboard Design & User Experience

**Conditional Formatting:** Applied dynamic color-coding rules to KPI cards (red for negative growth, green for positive performance).

**Drill-Down Hierarchy:** Designed an interactive matrix enabling users to navigate from high-level Categories through Sub-Categories to individual Products.

**Visual Layout:** Implemented a Z-pattern design hierarchy, positioning executive KPIs prominently at the top while maintaining accessible drill-down details below.

### 💡 Key Business Insights

- **Profitability Alert:** While the Technology category drives substantial revenue, the Tables sub-category (Furniture) operates at a significant loss, likely attributable to disproportionate shipping and logistics costs.

- **Seasonal Patterns:** Analysis reveals a pronounced revenue spike during Q4 (November-December), representing approximately 30% of total annual sales.

- **Regional Performance Gap:** The West Region demonstrates superior performance metrics, while the Central Region exhibits profitability challenges despite maintaining healthy sales volumes.

---

## Phase 2: Customer & Regional Intelligence

![Customer & Regional Intelligence](Screenshots/Customer%20&%20Regional%20Insights.jpg)

**Technologies Used:** Microsoft Power BI, DAX, AI Visuals, Geospatial Analytics

### 🛠️ Technical Implementation

#### 1. Advanced Customer Metrics (DAX)

**Challenge:** Aggregate sales metrics fail to reveal individual customer quality, behavioral patterns, or potential discount inefficiencies.

**Solution:** Engineered behavioral analytics using `DISTINCTCOUNT` and `AVERAGE` functions to create a comprehensive customer profitability profile.

**Key Measures:**

```dax
Total Customers = DISTINCTCOUNT('Orders'[Customer ID])

Avg Sales per Customer = DIVIDE([Total Sales], [Total Customers], 0)

Avg Discount % = AVERAGE('Orders'[Discount])
```

#### 2. AI-Driven Root Cause Analysis

**Decomposition Tree:** Leveraged Power BI's nativ

**Outlier Detection:** Designed a Customer Value Matrix (scatter plot) mapping Sales against Profit. This visualization immediately isolates unprofitable high-volume customers (bottom-right quadrant), distinguishing them from the healthy customer base.

#### 3. Geospatial Analytics & Conditional Mappinglue Matrix (Scatter Plot) plotting Sales vs. Profit. This visual instantly isolates "unprofitable high-volume customers" (bottom-right quadrant) from the healthy client base.

##Business Logic:** Standard choropleth maps display only sales volume, masking profitability concerns. A profitability-focused visualization was required.

**Implementation:** Applied conditional formatting rules to state-level geographic data:

- **Red:** States with Total Profit < 0 (loss-generating)
- **Blue:** States with Total Profit ≥ 0 (profitable)

**Impact:** Immediately surfaces high-volume markets (e.g., Texas) that are paradoxically unprofitable, preventing misguided strategy based on vanity metrics.

### 💡 Key Business Insights

- **Geographic Profitability Gap:** Despite the West Region's strong performance, Texas and Ohio generate net losses despite substantial sales volumes—indicating critical operational inefficiencies.

- **Customer Profitability Paradox:** The scatter matrix reveals a distinct cluster of high-revenue customers ($5,000+) operating at negative margins, likely due to excessive service costs or unsustainable discount structures.

- **Discount Rate Correlation:** Strong correlation exists between Central Region losses and an average discount rate exceeding 20%. Normalization to the 15% national average represents a significant margin recovery opportunity.

---

## 📂 Project Files

- `Superstore sales dataset.xlsx` - Source data file
- `Superstore_Sales_Dashboard.pbix` - Power BI report file
- 'README.md' - ReadMe
- 'Screenshots' - Power BI Report look

---

## 🎯 Project Outcomes & Impact

This comprehensive Business Intelligence solution successfully transformed raw transactional data into strategic, actionable insights that empower data-driven decision-making. Through advanced DAX modeling, AI-powered analytics, and intuitive visualizations, the dashboard directly addresses critical business challenges:

**Operational Excellence:** Identified over $50,000 in potential annual savings through strategic discount optimization and loss-prevention initiatives in underperforming geographic markets.

**Executive Intelligence:** Delivered real-time visibility to leadership on Year-over-Year growth trends, customer-level profitability analysis, and regional performance gaps—enabling proactive strategic planning.

**Cultural Transformation:** Empowered stakeholders to transition from reactive reporting to proactive, exploratory analysis through interactive drill-downs, AI decomposition trees, and geospatial intelligence capabilities.

### Technical Achievement
✅ Implemented Time Intelligence calculations with proper error handling  
✅ Developed customer behavioral metrics to identify profitability patterns  
✅ Created AI-driven visuals for automated root cause analysis  
✅ Applied conditional formatting rules to highlight critical business anomalies

---

## 🤝 Connect & Collaborate

This project demonstrates proficiency in **Microsoft Power BI**, **DAX**, **Power Query**, and **Business Intelligence best practices**. For questions, collaboration opportunities, or feedback, feel free to reach out.

**Skills Demonstrated:** Data Modeling · ETL · DAX · Time Intelligence · Data Visualization · Business Analytics

---

*Developed as part of the Microsoft Power BI Data Analyst Professional Certificate*

Visura Rodrigo
