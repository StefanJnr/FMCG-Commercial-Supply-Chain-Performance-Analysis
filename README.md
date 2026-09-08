# FMCG Commercial & Supply Chain Performance Analysis
Evaluating Revenue, Promotional Elasticity, and Inventory Risk
# Dashboard
<img width="1580" height="800" alt="dashboard" src="https://github.com/user-attachments/assets/9887e52b-2351-4059-b30a-6198bddf66b0" />

# Introduction
As a Data Analyst, I audited €472.95M in net sales to investigate promotional margin erosion and high inventory volatility across 5 FMCG categories (Snacks, Beverages, Personal Care, Dairy, and Home Care) spanning 7 European countries and 65.12M units sold.

The goal of this project was to move beyond simple sales reporting and build a dynamic analytical model capable of answering three core commercial questions:
* How much do promotions actually lift sales volume, and at what cost to margin?
* Which categories carry the highest inventory/demand volatility, and what safety stock is needed to reduce stockouts?
* Where should promotional and inventory investment be reallocated to protect profitability?

# Analysis Workbook
The workbook contains the following tabs:

* Main_Dashboard – the interactive, slicer-driven dashboard (front end)
* Data_Model_Backend – baseline KPI calculations and named ranges
* Category_Analysis, Country_Analysis, Channel_Analysis, Day_Analysis, Weekly_Analysis, Monthly_Analysis, Quarterly_Performance, State_Analysis – supporting PivotTable/PivotChart analysis sheets (hidden, feeding the dashboard)

# Skills Used
* Data Cleaning & ETL: Power Query (trimming text, standardizing country names, casting date strings into date hierarchies, handling missing promotional flags via conditional columns, removing duplicate orders)
* Data Modeling: Star schema design — Fact table (fact_sales) linked 1-to-many to Dimension tables (dim_product, dim_geography, dim_date) via Power Pivot / the Excel Data Model
* DAX & Advanced Formulas: Calculated measures for Total Gross Revenue, Total Net Sales, Total Cost, Gross Margin, Promo Uplift %, Average Discount %, and Promo Margin Spread
* Statistical Analysis: Standard deviation, mean, and Coefficient of Variation (CV) formulas for demand volatility (XYZ classification)
* Data Visualization: Dynamic PivotTables and PivotCharts (bar, line/combo, donut) connected to slicers
* Dashboard Design: Interactive KPI cards, cross-filtered slicers (Year, Quarter, Month, Category, Country, Promo Flag), and explicit number formatting for clean monetary display
* Tools: Microsoft Excel (Power Query, Power Pivot, PivotTables/PivotCharts, Slicers, DAX)

# Dataset
The dataset consists of raw transactional FMCG sales records covering:

* 7 countries: Austria, France, Germany, Italy, Netherlands, Poland, Spain
* 5 categories: Snacks, Beverages, Personal Care, Dairy, Home Care
* 65.12M units sold, spanning multiple channels (Supermarket, Hypermarket, E-commerce, Convenience)
[Dataset](https://www.kaggle.com/datasets/robertocarlost/fmcg-multi-country-sales-dataset/data)

# Dashboard Content
**KPI Cards**

Total Sales, Gross Margin %, Stockout Rate %, and Units Sold — driven by DAX measures referencing the Data Model and displayed with custom number formatting.

**Charts**

Revenue & Profitability Driver — Combo chart (clustered column + line) showing Total Net Sales vs. Gross Margin % by category
Promotional Responsiveness Ranking — Horizontal bar chart ranking categories by Promo Uplift %
Country Net Profit — Horizontal bar chart of net profit by country
Monthly Sales Trend — Line chart of net sales across the 12-month calendar
Channel Distribution of Units Sold — Donut chart showing the share of units sold across Supermarket, Hypermarket, E-commerce, and Convenience channels
