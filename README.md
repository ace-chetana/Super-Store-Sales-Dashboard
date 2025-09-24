# Super-Store-Sales-Dashboard

## 1. Project Overview  
This repository hosts a strategic, interactive dashboard built in Tableau to empower the National Sales Manager of *Super Store* to see beyond raw numbers and drive data-informed decisions. Rather than simply visualizing sales, the dashboard tells a story: **where** the business is succeeding or failing, **why**, and **what to do next**.

Over four years of transactional data are transformed into insights around profitability, product mix, discount strategy, regional performance, and customer behavior.

## 2. Key Questions & Business Goals  
This dashboard is built to help the leadership team answer:

- Which regions or states are profitable — and which are bleeding losses?  
- Which product lines generate profit vs. drive losses, even if they sell well?  
- Which customer segments offer the best growth or retention potential?  
- How far can discounts go before they destroy margins, and how to apply guardrails?  

The ultimate goal: shift the narrative from “sell more” to “sell smarter,” with tactical levers for margin protection, regional focus, and customer retention.

## 3. Dashboard Structure & Highlights  

### 🗺 Geospatial Performance  
A U.S. choropleth map colored by profit highlights strengths and blind spots. Hover tooltips reveal state-level sales, profit, margin, and discount metrics.  
**Key insight:** Several states, particularly in the Central region, show high sales but negative profitability — likely due to aggressive discounting.

### 🛒 Product Portfolio Analysis  
- A horizontal bar chart shows profit by sub-category (positive in blue, negative in red).  
- A scatter plot (Profit vs. Sales) spotlights sub-categories that generate high revenue but negative profit.  
**Key insight:** While “Technology” leads profit, “Furniture” (especially tables and bookcases) is a recurrent profit drain under high discounting.

### 👥 Customer Segmentation  
Segment performance is shown in stacked bars (sales + profit) alongside segment-level KPIs (AOV, margin).  
**Key insight:** The “Consumer” segment drives volume, but “Corporate” transactions often have higher margins and order values. Also, low repeat purchase rates suggest a retention problem.

### 📉 Discount vs. Profitability Curve  
A scatter plot tracks each line item’s discount vs. margin, with a trend line to show tipping points.  
**Key insight:** Discounts above ~20–25% often push a product from profitable to loss-making. This provides empirical support for policy guardrails.

## 4. Interactive Features & User Guide  
- **Global filters**: Year, Region, Product Category — apply across all views.  
- **Cross-filtering actions**: Click a region, product, or customer segment to drill into related visuals.  
- **Tooltips on hover**: Reveal detailed metrics without cluttering the view.

Example exploration flow: filter for the South region → spot that Tables are losing money → click “Tables” → see which states, segments, or customers are driving those losses.

## 5. Design Principles & Best Practices  
- **Clarity & actionability** above all.  
- Visualizations are chosen intentionally (bar charts over pies, line charts for trends, scatter plots for relationships, maps for geography).  
- **Color with purpose** — reds for loss, accent highlights for focus.  
- **Zero-baseline axes**, explicit labels, and context-driven titles (e.g. “Which Products Drain Profitability?”).  
- Layout uses whitespace and a logical flow (KPIs → high-level view → drill-down).

## 6. Technical Implementation  

- **Tool**: Tableau Desktop (version 2023.3)  
- **Data source**: `Superstore.csv`  
- **Data preparation steps**:  
  1. Validate data types (dates, numeric, string)  
  2. Check for duplicates  
  3. Create calculated fields:  
     - Profit Margin = `SUM(Profit)/SUM(Sales)`  
     - Average Order Value (AOV) = `SUM(Sales) / COUNTD(Order ID)`  
- **Schema (key fields)**:  
  | Field | Type | Description |
  |---|---|---|
  | Order ID | String | Unique order identifier |
  | Order Date | Date | Date of order placement |
  | Ship Mode | String | Shipping method |
  | Customer ID | String | Unique customer identifier |
  | Segment | String | Customer segment (Consumer / Corporate / Home Office) |
  | Region | String | Geographical region |
  | State | String | U.S. state |
  | Category | String | Product category (Furniture / Technology / Office Supplies) |
  | Sub-Category | String | Product sub-category (e.g. Chairs, Phones) |
  | Sales | Decimal | Transaction sales amount |
  | Quantity | Integer | Units sold |
  | Discount | Decimal | Discount applied (0 to 1) |
  | Profit | Decimal | Profit for transaction |

## 7. Strategic Recommendations  
1. **Overhaul discounting in Furniture** — especially for tables/bookcases. Impose stricter discount caps (e.g. >15% requires managerial approval).  
2. **Refocus Central U.S. strategy** — shift from volume-based discounting to profitability-based targeting of cities, segments
