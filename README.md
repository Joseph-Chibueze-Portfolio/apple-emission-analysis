# apple-emission-analysis

Quick Links: 
* Live Dashboard: [View Dashboard Here](#) *(https://github.com/Joseph-Chibueze-Portfolio/apple-emission-analysis/blob/main/Apple%20emission%20dashboard.png)*


A comprehensive Power BI data analytics solution exploring Apple’s greenhouse gas emissions, product footprint trajectory, and carbon reduction milestones from 2015 to 2022 as part of their corporate journey toward net-zero emissions by 2030.

---

## 📊 Project Overview
This project tracks, cleans, and models Apple's environmental data alongside financial normalization factors. It highlights how corporate operations and product life cycles contribute to overall emissions while decoupling environmental impact from business growth (revenue and market capitalization).

---

## 🛠️ Data Preparation & Transformation (Power Query)

### 1. Carbon Footprint Table
* Operations: Trimmed and cleaned data for integrity, focusing on product release cycles from 2015 to 2023.

### 2. Greenhouse Gas Emissions Table
* Fiscal Range: Maintained across 2015 to 2022.
* Scope Clean-up: Filtered blank fields under the Scope column, verified that corresponding Type entries were classified as "Carbon removals", and mapped them cleanly.
* Emission Value Cleaning: Handled four distinct data structures:
  * Zeros (0): Left intact for negligible or zero-impact line items.
  * Nulls: Replaced with 0 where removal values weren't explicitly logged to prevent DAX calculation errors.
  * Negative Numbers: Retained as negative integers to accurately subtract offsets/removals from gross totals.

### 3. Normalizing Factors Table
* Integrated baseline financial and operational metrics without structural alterations.

### 4. Custom Dimension Table (Dim_FiscalYear)
To reconcile date ranges spanning up to 2023, a master year table was generated via Power Query:
= {2015..2023}
Converted to a table, renamed to Fiscal Year (Whole Number type), and organized under the query name Dim_FiscalYear.

---

## 📐 DAX Measures & KPIs

* Total Gross Emissions
Total Gross Emissions = CALCULATE(SUM('greenhouse_gas_emissions'[Emissions]), 'greenhouse_gas_emissions'[Type] = "Gross emissions")

* Total Net Emissions
Total Net Emissions = SUM('greenhouse_gas_emissions'[Emissions])

* Emission per Revenue
Emission per Revenue = DIVIDE([Total Gross Emissions], SUM('Normalizing factors'[Revenue]))

* Emission per Employee
Emission per Employee = DIVIDE([Total Gross Emissions], SUM('normalizing_factors'[Employees]))

* Total Carbon Removals
Total Carbon Removals = ABS(CALCULATE(SUM('greenhouse_gas_emissions'[Emissions]), 'greenhouse_gas_emissions'[Type] = "Carbon removals"))

* Carbon Removal Share
Carbon Removal Share = DIVIDE([Total Carbon Removals], [Total Gross Emissions])

* Carbon Intensity
Carbon Intensity = DIVIDE([Total Net Emissions], SUM('greenhouse_gas_emissions'[Revenue]))

---

## 📈 Dashboard Layout & Visualizations

1. Emissions Reduction Trajectory (2015–2022): Line chart tracking the drop in gross emissions over time.
2. Carbon Intensity Relative to Revenue: Line visual mapping efficiency metrics year-over-year.
3. Emissions by Category: Bar chart highlighting the scale of Product Life Cycle emissions vs. Corporate operations.
4. Emissions vs. Revenue Trends: Combo chart juxtaposing emission decreases against financial growth parameters.
5. iPhone Carbon Footprint Trend: Sequential chronological breakdown comparing baseline configurations from early models through recent generations.
6. Emission Breakdown by Scope: Granular horizontal distribution mapping Scope 1, 2, 3, and Carbon Removals.
7. Executive KPI Cards: High-level metrics tracking total footprints, per-capita/revenue efficiency, and removal shares.

## 📂 Repository Resources
* Power BI Dashboard File (.pbix): [Download Power BI File](#) *(https://github.com/Joseph-Chibueze-Portfolio/apple-emission-analysis/blob/main/APPLE%20EMISSION%20ENVIRONMENTAL%20%26%20FINANCIAL%20IMPACT%20DASHBOARD.pbix)*
* Raw Dataset (CSV/Excel Files): [https://github.com/Joseph-Chibueze-Portfolio/apple-emission-analysis/blob/main/carbon_footprint_by_product.csv], []https://github.com/Joseph-Chibueze-Portfolio/apple-emission-analysis/blob/main/greenhouse_gas_emissions.csv,[https://github.com/Joseph-Chibueze-Portfolio/apple-emission-analysis/blob/main/normalizing_factors.csv](#) *(Placeholder link)*
* Interactive Live Preview: [https://github.com/Joseph-Chibueze-Portfolio/apple-emission-analysis/blob/main/Apple%20emission%20dashboard.png](#) *()*

---

## 👤 Author & Contact
* Name: [Joseph Chibueze]
* Email: [josephchibuezechinonso@gmail.com]
* LinkedIn: [https://www.linkedin.com/in/joseph-chibueze-7965a6205]
* Youtube: [https://youtube.com/@jojotechman?si=0J62nD63GFrLrFhD]
