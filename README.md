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

<img width="1117" height="145" alt="KPIs" src="https://github.com/user-attachments/assets/320ad2d2-d13f-47ec-b0d5-8089e84609b4" />




**Charts**

Revenue & Profitability Driver — Combo chart (clustered column + line) showing Total Net Sales vs. Gross Margin % by category

<img width="547" height="276" alt="Revenue and Profitability Driver" src="https://github.com/user-attachments/assets/b429a72d-9cd8-433e-bf27-15ebd201a873" />


Promotional Responsiveness Ranking — Horizontal bar chart ranking categories by Promo Uplift %

<img width="532" height="267" alt="Promo Responsiveness Ranking" src="https://github.com/user-attachments/assets/5c4118bf-d39f-4053-9213-b37dd34bbc81" />


Country Net Profit — Horizontal bar chart of net profit by country

<img width="535" height="267" alt="Country Net Profit" src="https://github.com/user-attachments/assets/f796c5b7-0663-476e-a7fb-dde77b88774e" />


Monthly Sales Trend — Line chart of net sales across the 12-month calendar

<img width="536" height="272" alt="Monthly Sales Trend" src="https://github.com/user-attachments/assets/41030572-77f3-442b-9e80-16ae688ca949" />


Channel Distribution of Units Sold — Donut chart showing the share of units sold across Supermarket, Hypermarket, E-commerce, and Convenience channels

<img width="371" height="490" alt="Channel DIstribution" src="https://github.com/user-attachments/assets/fc5fb70b-b438-4f05-8cc6-a127c06e99e6" />

# Conclusion
This project demonstrates how an Excel-based commercial and supply chain analytics model can turn raw transactional data into decision-ready insights. Key takeaways from the analysis include:

* Restructure high-uplift promotions: Home Care (131.33% uplift) and Beverages (104.88% uplift) drive volume but erode margin the most (-14.57% and -14.29% spread). Shifting from deep discounting to bundles or volume-tiering can protect revenue without sacrificing margin.
* Buffer safety stock for volatile demand: All five categories show high demand volatility (CV > 0.70). A baseline safety stock of ~189 units per SKU is recommended to reduce the 3.01% stockout rate (~33,114 stockout days).
* Scale high-margin anchor categories: Dairy delivers the strongest gross margin (39.50%) despite lower promo sensitivity, suggesting an opportunity to reallocate spend from lower-margin categories like Snacks.
* Target regional growth markets: The Netherlands shows the strongest promotional response (114.60% uplift) despite the smallest sales footprint (€12.52M), indicating unmet demand worth capturing with targeted inventory allocation.

Overall, the model shows that promotional strategy and inventory planning cannot be optimized in isolation, margin protection and stockout reduction both depend on category-level demand behavior, and this dashboard provides a repeatable framework to monitor and act on that behavior going forward.
