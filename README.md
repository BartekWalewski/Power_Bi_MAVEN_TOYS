# 📊 Power BI Project – Maven Toys Dashboard




👉 [Live Dashboard](https://app.powerbi.com/reportEmbed?reportId=52c6e140-25af-4e40-89e4-b1faab0b2c10&autoAuth=true&ctid=53bc24c5-73ad-421a-9408-3ea555be4a07)
## 🎯 Project Goal
The goal of this project was to build an **interactive Power BI dashboard** for a fictional toy retail chain in Mexico – **Maven Toys 🧸🪀**.  
The dashboard enables analysis of sales, profit margins, profitability, and inventory levels, supporting decision-making at the product, store, and corporate level.

---

## 📂 Data
The dataset comes from **Maven Analytics** (public domain) and includes:
- **829,263 records**
- **19 fields** across several tables: `Products`, `Sales`, `Stores`, `Inventory`, `Calendar`.

Examples:
- `Products`: product name, category, cost, retail price.  
- `Sales`: transactions with date, store, product, and units sold.  
- `Stores`: store details (ID, name, city, opening date).  
- `Inventory`: stock levels in each store.  
- `Calendar`: date table for time-based analysis.  

---

## ⚙️ Data Modeling
- Created a **relational data model** in Power BI using `Product_ID`, `Store_ID`, `Date`.  
- Designed a **star schema**: fact tables (`Sales`, `Inventory`) + dimension tables (`Products`, `Stores`, `Calendar`).  
- Built a **date table** with hierarchy (year, quarter, month, day) to enable seasonality and trend analysis.  

---

## 🧮 DAX Measures & Their Meaning

To support analysis, I created several **calculated measures in DAX**. Each of them provides a specific business insight:

- **Total Revenue**  
  `SUMX(Sales, Sales[Units] * Products[Product_Price])`  
  → Shows the **total income** generated from all sales. This is the main performance indicator reflecting the company’s ability to generate money from selling toys.  

- **Total Orders**  
  `COUNTROWS(Sales)`  
  → Counts the **number of transactions** (orders). This measure highlights the sales volume and customer activity.  

- **Profit**  
  `SUMX(Sales, Sales[Units] * (Products[Product_Price] - Products[Product_Cost]))`  
  → Displays the **actual earnings** after subtracting product costs from sales revenue. It reveals which products or categories are truly profitable.  

- **% Margin**  
  `DIVIDE([Profit], [Total Revenue])`  
  → Shows the **profitability ratio** for each product, store, or category. A high margin means strong profitability, while a low margin indicates cost pressure.  

- **Stock Value**  
  `SUMX(Inventory, Inventory[Stock_On_Hand] * Products[Product_Cost])`  
  → Calculates the **total capital locked in inventory**. This helps evaluate the financial value of products sitting in warehouses or stores.  

- **AVG Daily Sales**  
  `AVERAGEX(VALUES(Calendar[Date]), [Total Revenue])`  
  → Shows the **average revenue per day**, which is useful for comparing sales performance across periods and for planning inventory needs.  

- **Days of Inventory**  
  `DIVIDE([Stock Value], [AVG Daily Sales])`  
  → Estimates how long the current stock will last given the current sales pace. This is a key metric for supply chain management and stock efficiency.  

- **Year-over-Year KPIs**  
  (e.g. **Revenue LY**, **Profit LY**, **Orders LY**)  
  → Compare the current year’s performance with the previous year to show **growth trends** and identify improvements or declines in performance.  

---

## 🔧 Data Preparation (Power Query)
In Power Query I performed:
- Data cleaning (duplicates removed, consistent column names).  
- Added calculated columns (e.g. store opening date transformations).  
- Filled missing values and built a calendar table.  
- Optimized model size (data types, aggregations).  

---

## 📊 Visualizations
The dashboard contains:
- **KPI cards** – Revenue, Profit, Orders, Stock Value, Days of Inventory.  
- **Treemap** – Profit by Product Category.  
- **Map** – Profit by Store City (geolocation).  
- **Ranking table** – Top 5 products by revenue, margin, and profit.  
- **Line chart** – Revenue & Profit trends over time.  
- **Inventory table** – Stock Value, Avg Daily Sales, “Daily Sales vs Inventory %”.  

Additional features:
- **Slicers** for dates and locations (city/store).  
- **Custom buttons** (e.g. reset all filters by clicking on the logo).  
- Consistent **layout and branding** (colors, fonts, visuals).  

---

## ❓ Example Business Questions
The dashboard helps answer questions such as:
- Which **product categories** drive the highest profits?  
- Are categories equally profitable across **different store locations**?  
- What **seasonal trends** can be identified in sales?  
- How much capital is tied up in inventory, and how many **days of sales** can it cover?  
- Is **stock shortage** impacting sales performance in specific stores?  

---

## 💡 Summary
This project demonstrates my skills in:
- **Data modeling** (star schema, relationships, calendar table).  
- **DAX measure creation** (KPIs, year-over-year comparisons, efficiency metrics).  
- **Power Query** (data cleaning, transformations, optimization).  
- **Dashboard design** (UX, layout, interactivity).  

The dashboard supports both **strategic analysis (across the full retail chain)** and **operational insights (store-level inventory management)**.  


Źródło: Maven Analytics (Licencja: Domena Publiczna) via Maven Analytics
