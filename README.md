# FMCG Commercial & Supply Chain Analytics

## Rebalancing Promotional Profitability & Demand Volatility Across European Markets

![Microsoft Excel](https://img.shields.io/badge/Microsoft%20Excel-Data%20Analytics-217346?logo=microsoftexcel&logoColor=white)
![Power Query](https://img.shields.io/badge/Power%20Query-ETL-217346)
![Power Pivot](https://img.shields.io/badge/Power%20Pivot-Data%20Modeling-217346)
![DAX](https://img.shields.io/badge/DAX-Analytics-4472C4)
![FMCG](https://img.shields.io/badge/Domain-FMCG-orange)

---

## 1. Project Overview

This project presents an end-to-end commercial and supply chain analysis of an enterprise FMCG dataset covering **65.11 million units sold** and **$472.95M in net sales** across seven European markets: **Italy, Spain, Germany, Austria, France, Poland, and the Netherlands**.

Using **Microsoft Excel, Power Query, and Power Pivot**, the project transforms more than **1.1 million raw transaction rows** into a structured analytical model. The analysis investigates two major business challenges:

- **Promotional margin compression** — promotions generate substantial volume uplift but materially reduce gross margins.
- **Supply chain disruption and stockouts** — volatile demand contributes to recurring stockouts and lost fulfillment opportunities.

The resulting interactive Excel dashboard provides an executive view of commercial performance, promotional effectiveness, demand volatility, inventory risk, and safety-stock requirements.

> **Portfolio focus:** This project demonstrates the ability to move from raw transactional data through ETL, data modeling, analytical calculations, visualization, insight generation, and business recommendations.

---

## 2. Business Problem

Despite strong top-line performance, executive leadership identified two operational bottlenecks affecting profitability and customer service.

### 2.1 Promotional Margin Compression

Trade promotions create significant volume uplift, but deep discounting reduces gross-margin performance.

The analysis therefore evaluates whether promotional volume growth is sufficient to compensate for the associated margin deterioration.

### 2.2 Supply Chain Disruption & Stockouts

Demand volatility contributes to recurring stockouts across the product portfolio.

The dataset records a **3.01% average stockout rate**, representing **33,114 total stockout days** across SKUs.

Without a centralized analytical model, regional managers lacked visibility into:

- Promotional responsiveness
- Category-level demand volatility
- Margin impact of promotions
- Regional performance
- Appropriate safety-stock requirements

---

## 3. Project Objectives

The analysis was designed around five objectives:

1. **Data Harmonization**  
   Clean, transform, and structure more than 1.1 million raw transaction rows into an optimized star-schema data model.

2. **Trade Promotion Audit**  
   Quantify promotional effectiveness by comparing volume uplift with promotional margin spread.

3. **Demand Volatility Classification**  
   Apply XYZ inventory classification using the Coefficient of Variation (CV).

4. **Supply Chain Optimization**  
   Model SKU-level safety-stock requirements to address stockout risk.

5. **Executive Decision Support**  
   Build an interactive dashboard containing dynamic KPIs, slicers, timelines, performance matrices, and analytical visualizations.

---

## 4. Key Business Questions

The project answers the following business questions:

1. What is the net financial return of promotional campaigns across each product category?
2. Which product categories drive volume versus those that sacrifice margin for revenue?
3. How volatile is demand across the product portfolio?
4. How should products be categorized using XYZ demand classification?
5. What safety-stock levels are required to reduce stockout risk?
6. How do promotional responsiveness and gross margins vary across European markets?
7. Which categories and markets require management attention?

---

## 5. Dataset Overview

| Metric | Value |
|---|---:|
| Total Net Sales | **€472,946,452.83** |
| Total Gross Revenue | **€484,748,674.02** |
| Total Net Profit | **€182,208,955.50** |
| Total Units Sold | **65,115,982** |
| Total Stockout Days | **33,114** |
| Overall Gross Margin | **38.53%** |
| Average Discount | **1.50%** |
| Promotional Sales Share | **10.44%** |
| Promotional Volume Uplift | **88.67%** |
| Promotional Margin Spread | **-14.39%** |
| Stockout Rate | **3.01%** |
| Portfolio Demand CV | **0.7603** |
| Recommended Safety Stock | **~189 units/SKU** |
| Countries | **7** |
| Product Categories | **5** |
| Raw Transaction Rows | **1.1M+** |

### Geographic Coverage

- Italy
- Spain
- Germany
- Austria
- France
- Poland
- Netherlands

### Product Categories

- Snacks
- Beverages
- Personal Care
- Dairy
- Home Care

---

## 6. Data Source

**Primary source:** [Dataset](https://www.kaggle.com/datasets/robertocarlost/fmcg-multi-country-sales-dataset/data)

**Core workbook:** `FMCG Commercial & Supply Chain Performance Analysis.xlsx`

---

## 7. Data Dictionary

| Field / Metric | Type | Description / Formula |
|---|---|---|
| `Transaction_ID` | String | Unique identifier for each sales transaction line item. |
| `Order_Date` | Date | Date when the customer order was processed. |
| `Country` | String | Target European market. |
| `Category` | String | FMCG product category. |
| `Gross_Revenue` | Currency | Gross sales before discounts: `Units × Base Price`. |
| `Net_Sales` | Currency | Revenue after trade discounts: `Gross Revenue − Discounts`. |
| `Total_Cost` | Currency | Cost of Goods Sold (COGS) for fulfilled units. |
| `Net_Profit` | Currency | Profit generated: `Net Sales − Total Cost`. |
| `Promo_Flag` | Boolean | Indicates whether an item was on promotion (`1 = Yes`, `0 = No`). |
| `Promo_Uplift_%` | Percentage | Relative increase in promotional units versus non-promotional baseline. |
| `Promo_Margin_Spread` | Percentage | Promotional gross margin minus non-promotional gross margin. |
| `Demand_CV` | Decimal | Coefficient of Variation: `σ / μ`. |
| `XYZ_Class` | String | Demand-volatility classification based on CV thresholds. |
| `Stockout_Days` | Integer | Number of days inventory was unavailable at distribution centers. |

---

## 8. Data Quality Assessment

Before modeling, the dataset underwent a data-quality audit.

### Issues Identified

#### Inconsistent Attribute Naming

Country and regional fields contained trailing spaces and inconsistent capitalization, such as:

- `Germany `
- `germany`

#### Missing Promotional Metadata

Approximately **2.1% of transactions** lacked promotional flags despite containing discounted prices.

#### Duplicate Transaction Records

Redundant transaction records were identified, attributed to multi-system synchronization errors.

#### Temporal Discrepancies

Order dates were represented using mixed formats, including:

- `DD/MM/YYYY`
- `YYYY-MM-DD`

These inconsistencies were addressed during the Power Query transformation process.

---

## 9. Data Cleaning & Preparation

Data transformation was performed in **Power Query**.

### Transformation Workflow

1. **Text Standardization**
   - Applied `Text.Trim`
   - Applied `Text.Clean`
   - Standardized `Category` and `Country` values

2. **Promotional Flag Reconstruction**

Missing promotional flags were recalculated using conditional logic:

```powerquery
if [Gross_Revenue] > [Net_Sales] then 1 else 0
```

3. **Deduplication**

Duplicate records were removed using `Transaction_ID` as the primary identifier.

4. **Data Type Standardization**

Numerical fields were converted to appropriate Currency/Decimal types and date fields were standardized to ISO format:

```text
YYYY-MM-DD
```

5. **Data Modeling**

The cleaned data was transformed into a relational star schema.

---

## 10. Data Model

The Power Pivot model uses a **star-schema architecture**.

```text
                         ┌──────────────────┐
                         │    Dim_Date      │
                         └────────┬─────────┘
                                  │
                                  │
┌──────────────────┐     ┌────────▼─────────┐     ┌──────────────────┐
│   Dim_Product    │────▶│    Fact_Sales    │◀────│  Dim_Geography   │
└──────────────────┘     └──────────────────┘     └──────────────────┘
```

### Fact Table

`Fact_Sales`

Contains transactional sales and performance measures.

### Dimension Tables

- `Dim_Product`
- `Dim_Geography`
- `Dim_Date`

The dimensions are connected to the central fact table through **1-to-Many, single-direction relationships**.

---

## 11. Tools & Technologies

### Data Preparation / ETL

- Microsoft Excel
- Power Query
- Text transformation
- Conditional columns
- Deduplication
- Data-type conversion

### Data Modeling

- Power Pivot
- Star-schema modeling
- Relational table relationships
- DAX measures

### Analysis

- PivotTables
- PivotCharts
- Excel formulas
- Statistical calculations
- XYZ inventory classification
- Safety-stock modeling

### Visualization

- Interactive dashboard
- KPI cards
- Slicers
- Timelines
- Conditional formatting
- Data bars
- Heatmaps

### Excel Functions Used

```text
XLOOKUP
INDEX/MATCH
SUMIFS
STDEV.S
AVERAGE
CEILING.MATH
```

---

## 12. Analytical Methodology

### 12.1 Promotional Sensitivity & Margin Analysis

Promotional effectiveness was evaluated by measuring both volume uplift and margin degradation.

#### Promotional Volume Uplift

```text
Promo Uplift % =
(Promotional Sales Volume − Baseline Sales Volume)
÷ Baseline Sales Volume
```

#### Promotional Margin Spread

```text
Promo Margin Spread =
Promotional Gross Margin %
− Non-Promotional Gross Margin %
```

This approach allows promotional performance to be evaluated from both a **volume** and **profitability** perspective.

---

### 12.2 XYZ Demand Volatility Analysis

Demand volatility was evaluated using the **Coefficient of Variation (CV)**.

```text
CV = Standard Deviation of Demand ÷ Mean Demand
```

The portfolio was classified using the following thresholds:

| Classification | CV Range | Interpretation |
|---|---:|---|
| **X** | `CV ≤ 0.20` | Steady demand |
| **Y** | `0.20 < CV ≤ 0.70` | Moderate volatility |
| **Z** | `CV > 0.70` | High volatility |

A higher CV indicates greater variability relative to average demand.

---

### 12.3 Safety Stock Calculation

Safety stock was modeled using:

```text
Safety Stock =
Z × σ(demand) × √Lead Time
```

Where:

- `Z = 1.65`
- Service level assumption = **95%**
- `σ(demand)` = demand standard deviation
- `Lead Time` = supplier lead time

The resulting portfolio-level recommendation was approximately:

> **189 units per SKU**

---

## 13. Exploratory Data Analysis

### 13.1 Portfolio-Level KPIs

| KPI | Result |
|---|---:|
| Net Sales | **$472,946,452.83** |
| Gross Revenue | **$484,748,674.02** |
| Net Profit | **$182,208,955.50** |
| Gross Margin | **38.53%** |
| Average Discount | **1.50%** |
| Promotional Sales Share | **10.44%** |
| Promotional Volume Uplift | **88.67%** |
| Promotional Margin Spread | **-14.39%** |
| Stockout Rate | **3.01%** |
| Stockout Days | **33,114** |
| Portfolio Demand CV | **0.7603** |
| XYZ Classification | **Z — High Volatility** |
| Recommended Safety Stock | **~189 units/SKU** |

---

## 14. Category Performance

| Category | Net Sales (€) | Gross Margin % | Promo Uplift % | Margin Spread | Stockout Rate % | Demand CV | XYZ |
|---|---:|---:|---:|---:|---:|---:|---|
| Snacks | $130,143,246.54 | 38.01% | 67.03% | -14.33% | 3.04% | 0.7176 | Z |
| Beverages | $104,103,731.68 | 38.17% | 104.88% | -14.29% | 3.03% | 0.7905 | Z |
| Personal Care | $89,550,289.64 | 38.94% | 67.17% | -14.72% | 3.00% | 0.7719 | Z |
| Dairy | $83,820,530.98 | 39.50% | 63.49% | -13.88% | 2.97% | 0.7115 | Z |
| Home Care | $65,328,653.99 | 38.32% | 131.33% | -14.57% | 3.00% | 0.7044 | Z |
| **Total** | **$472,946,452.83** | **38.53%** | **88.67%** | **-14.39%** | **3.01%** | **0.7603** | **Z** |

---

## 15. Regional Performance

| Country | Net Sales (€) | Gross Margin % | Promo Uplift % | Stockout Rate % |
|---|---:|---:|---:|---:|
| Italy | $137,193,076.12 | 38.53% | 88.33% | 3.00% |
| Spain | $106,704,767.04 | 38.60% | 90.72% | 2.99% |
| Germany | $88,525,559.01 | 38.48% | 88.48% | 3.01% |
| Austria | $43,020,025.97 | 38.64% | 85.33% | 3.09% |
| France | $42,601,612.57 | 38.55% | 89.74% | 3.07% |
| Poland | $42,385,262.52 | 38.36% | 81.51% | 2.96% |
| Netherlands | $12,516,149.60 | 38.20% | 114.60% | 3.04% |
| **Total** | **$472,946,452.83** | **38.53%** | **88.67%** | **3.01%** |

---

## 16. KPI Definitions

### Net Sales

Net realized revenue after trade allowances and discounts.

### Gross Margin %

The ratio of gross profit to net sales, representing baseline product profitability.

### Promotional Volume Uplift %

The percentage increase in physical units sold during promotional periods relative to the non-promotional baseline.

### Promotional Margin Spread %

The percentage-point difference between promotional gross margin and non-promotional baseline margin.

### Demand Volatility — CV

The ratio of demand standard deviation to mean demand:

```text
CV = σ / μ
```

### Stockout Rate %

The percentage of active sales days during which product demand could not be fulfilled because inventory was unavailable.

---

## 17. Dashboard

The Excel dashboard is designed as an executive decision-support interface.

### Dashboard Components

- Executive KPI overview
- Category revenue and profitability analysis
- Promotional uplift analysis
- Promotional margin compression analysis
- Country performance comparison
- Demand volatility matrix
- Stockout-rate analysis
- Safety-stock recommendations
- Interactive slicers
- Timeline controls
- Conditional-formatting heatmaps

### Dashboard Screenshots

#### Executive Overview

<img width="1846" height="812" alt="image" src="https://github.com/user-attachments/assets/db01887f-2c86-4f82-bffb-a044f5364528" />

*Interactive KPI cards, category revenue mix, and country slicer controls.*

#### Promotional Efficiency & Margin Analysis

<img width="1463" height="700" alt="image" src="https://github.com/user-attachments/assets/d645e493-78d3-4226-97c6-29f1c13b338b" />

*Visualization of promotional volume uplift against promotional margin compression.*

---

## 18. Key Findings & Insights

### 1. Promotions Generate Significant Volume but Compress Margin

Promotional activity produced an **88.67% volume uplift** across the portfolio while promotional gross margin was **14.39 percentage points lower** than the non-promotional baseline.

This indicates a material trade-off between volume growth and profitability.

### 2. Home Care Shows the Highest Promotional Uplift

Home Care recorded the highest category-level promotional uplift at **131.33%**, while its promotional margin spread was **-14.57%**.

This highlights the importance of evaluating promotional campaigns using both volume and margin metrics.

### 3. Beverages Also Shows High Promotional Responsiveness

Beverages recorded **104.88% promotional uplift** alongside a **-14.29% margin spread**.

### 4. The Portfolio Exhibits High Demand Volatility

The portfolio CV was **0.7603**, placing the overall portfolio in **Class Z — High Volatility**.

All five product categories were classified as Z under the defined CV thresholds.

### 5. Stockouts Represent a Material Supply Chain Issue

The portfolio recorded a **3.01% stockout rate**, equivalent to **33,114 stockout days**.

The risk is particularly important during promotional periods, when demand can increase substantially.

### 6. The Netherlands Shows High Promotional Sensitivity

The Netherlands recorded the highest promotional uplift at **114.60%**, despite having the smallest sales contribution among the seven markets at approximately **$12.52M**.

This suggests that market-level promotional responsiveness should be considered when planning promotional inventory and campaign execution.

---

## 19. Business Recommendations

The following recommendations are derived from the observed commercial and supply-chain patterns.

### 1. Restructure High-Uplift Promotional Mechanics

For categories such as **Home Care and Beverages**, consider moving from broad price reductions toward mechanisms such as:

- Multi-buy offers
- Threshold-volume bundles
- Targeted promotions
- Customer-segment-specific offers

The objective is to retain demand responsiveness while reducing unnecessary margin dilution.

### 2. Deploy Dynamic Safety-Stock Targets

Use the modeled **~189 units/SKU** recommendation as a starting point for inventory planning, subject to SKU-level validation and operational constraints.

The stated analytical target is to reduce the **3.01% stockout rate toward below 1%**.

### 3. Protect High-Margin Categories

Dairy recorded the highest baseline gross margin at **39.50%** and the lowest promotional uplift among the categories at **63.49%**.

Management could evaluate whether value-based positioning and brand-building activities can support profitability without relying heavily on discounting.

### 4. Align Inventory with Promotional Elasticity

Markets with stronger promotional responsiveness, particularly the Netherlands, should receive additional attention during campaign planning so that promotional demand does not create avoidable stockouts.

---

## 20. Limitations & Assumptions

Several limitations should be considered when interpreting the results.

### Pricing Elasticity

The analysis assumes that historical promotional volume elasticity remains reasonably representative under future pricing structures.

### Lead-Time Variability

Safety-stock calculations assume a constant supplier lead time across European regions because detailed shipping-transit logs were not available.

### Marketing Spend

The profitability analysis focuses on gross margin and trade allowances. Indirect promotional costs such as advertising-agency fees and slotting fees were not available.

### Interpretation

The analysis is based on historical transactional patterns. Observed relationships should therefore not automatically be interpreted as causal effects without further experimentation or statistical validation.

---

## 21. Conclusion

This project demonstrates an end-to-end approach to **commercial and supply chain analytics using Microsoft Excel**.

By combining Power Query ETL, Power Pivot data modeling, DAX measures, statistical calculations, PivotTables, interactive dashboard design, and business interpretation, the analysis connects **sales performance, promotional strategy, profitability, demand volatility, and inventory execution**.

The analysis identifies a clear portfolio-level trade-off:

> **Promotional activity generates substantial volume growth, but the associated margin compression and demand volatility create commercial and supply-chain risks that require coordinated decision-making.**

The modeled safety-stock requirement of approximately **189 units per SKU** provides a quantitative starting point for addressing inventory risk, while category- and market-level promotional analysis provides a framework for more disciplined promotion planning.

---

## 22. Project Structure

```text
FMCG-Commercial-SupplyChain-Analytics/
│
├── data/
│   ├── raw_fmcg_transactions.xlsx
│   └── cleaned_fmcg_model.xlsx
│
├── dashboard/
│   ├── Portfolio Project.xlsx
│   └── screenshots/
│       ├── executive_overview.png
│       ├── promo_margin_analysis.png
│       └── supply_chain_heatmap.png
│
├── docs/
│   ├── data_dictionary.md
│   └── analytical_methodology.pdf
│
├── README.md
└── LICENSE
```

---

## 23. How to Reproduce the Analysis

### Step 1 — Clone the Repository

```bash
git clone https://github.com/StefanJnr/FMCG-Commercial-SupplyChain-Analytics.git
cd FMCG-Commercial-SupplyChain-Analytics
```

### Step 2 — Open the Core Workbook

Open:

```text
FMCG Commercial & Supply Chain Performance Analysis.xlsx
```

Use a version of Microsoft Excel that supports the Power Query and Power Pivot functionality required by the workbook.

### Step 3 — Inspect the Data Model

Open:

```text
Power Pivot → Manage
```

Review the relationships between:

- `Fact_Sales`
- `Dim_Product`
- `Dim_Geography`
- `Dim_Date`

### Step 4 — Refresh the Model

In Excel:

```text
Data → Refresh All
```

This updates the Power Query outputs, PivotTables, PivotCharts, and connected dashboard elements.

### Step 5 — Explore the Dashboard

Navigate to the `Main_Dashboard` worksheet.

Use the available:

- Slicers
- Timelines
- Category filters
- Country filters
- Promotional filters

to explore the analytical results.

---

## 24. Skills Demonstrated

### Commercial & Financial Analytics

- Margin analysis
- Promotional effectiveness analysis
- Volume elasticity analysis
- Profitability analysis
- Commercial decision support

### Supply Chain Analytics

- Demand volatility analysis
- XYZ inventory classification
- Stockout analysis
- Safety-stock modeling
- Inventory risk assessment

### Data Engineering / ETL

- Data ingestion
- Data cleaning
- Data standardization
- Deduplication
- Conditional transformations
- Power Query development

### Data Modeling

- Star-schema architecture
- Fact and dimension tables
- Relational modeling
- Power Pivot
- DAX measures

### Data Visualization & Storytelling

- Executive KPI scorecards
- Interactive dashboards
- PivotCharts
- Slicers
- Timelines
- Conditional-formatting heatmaps
- Business insight communication

---

## 25. Future Improvements

### 1. Automate ETL with Python & SQL

Migrate the transactional pipeline to a relational database such as PostgreSQL and use Python for automated ingestion and transformation.

### 2. Predictive Demand Forecasting

Introduce time-series forecasting approaches such as:

- ARIMA
- Prophet
- Other appropriate forecasting models

The objective would be to predict promotional demand spikes and improve inventory planning.

### 3. Incorporate Freight & Holding Costs

Expand the financial model to include:

- Warehouse storage costs
- Freight costs
- Carrier charges
- Other logistics expenses

This would allow analysis of **Net Contribution Margin** rather than gross margin alone.

### 4. Move to Power BI

The Excel model could be extended into Power BI for:

- Scalable data modeling
- More advanced DAX
- Automated refresh
- Richer interactive reporting
- Enterprise dashboard deployment

---

## 26. Author

**Author:** Stefan Frimpong

**Role:** Emerging Data Scientist, Data Analyst & Business Analyst

**LinkedIn:** www.linkedin.com/in/stefan-frimpong-370a9b2b1

**GitHub:** https://github.com/StefanJnr

**Email:** stefanfrimpongjnr


---

## 27. Portfolio Disclaimer

This project is presented for **professional portfolio and analytical demonstration purposes**.

Where the underlying dataset is confidential or derived from internal enterprise systems, proprietary records and unauthorized sensitive information should not be published. Any public repository should contain only data and materials that are legally permitted for portfolio use.

---

## 28. Project Takeaway

This project demonstrates the complete analytical workflow:

```text
Raw Enterprise Data
        ↓
Data Quality Assessment
        ↓
Power Query ETL
        ↓
Data Cleaning & Transformation
        ↓
Star-Schema Data Model
        ↓
Power Pivot & DAX
        ↓
Exploratory Data Analysis
        ↓
Commercial & Supply Chain KPIs
        ↓
Interactive Excel Dashboard
        ↓
Business Insights
        ↓
Actionable Recommendations
```

**The core objective is not simply to build an Excel dashboard, but to demonstrate how structured data analysis can translate commercial and operational data into decision-support insights.**
