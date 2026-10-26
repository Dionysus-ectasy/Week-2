# Superstore Executive Sales Dashboard

**AnalystLab Africa Experience Lab, Week 2: Business Analytics Case Study**
Prepared by Divine Okezie Nwaoha

An interactive Microsoft Power BI dashboard that helps senior management monitor sales performance, profitability, customer segments and regional results for a national US retail company.

---

## Business Problem

Management needs to see how the business is performing, where profit is being made or lost, and what to do next. The dashboard answers seven questions:

1. What is the overall sales performance of the company?
2. Which regions generate the highest sales and profit?
3. Which customer segments contribute the most revenue?
4. Which product categories perform best?
5. Which products are the most profitable?
6. What trends can be observed over time?
7. What recommendations should management implement?

## Dataset

- **Source:** Superstore Dataset (Kaggle, Option 1): https://www.kaggle.com/datasets/vivek468/superstore-dataset-final
- **File:** `Sample - Superstore.csv`
- **Size:** 9,994 order lines (9,993 after removing one duplicate), covering 2014 to 2017
- **Main fields:** Order Date, Ship Mode, Segment, Region, State, Category, Sub-Category, Sales, Quantity, Discount, Profit

## Tools

- Microsoft Power BI Desktop (Power Query and DAX)
- Kaggle (data source)
- GitHub and Google Drive (delivery)

## Data Preparation (Power Query)

- Imported the CSV using encoding 1252 (Western European) so text displays correctly.
- Checked column quality: no missing values or errors found.
- Set data types: Order Date and Ship Date as Date, Sales, Profit and Discount as Decimal, Quantity and Row ID as Whole Number, Postal Code as Text.
- Removed duplicate records across all columns except Row ID (9,994 rows down to 9,993).
- Added helper columns: Order Year, Month Number and Month Name (sorted by Month Number so months appear Jan to Dec).

## DAX Measures

```
Total Sales   = SUM(Superstore[Sales])
Total Profit  = SUM(Superstore[Profit])
Total Orders  = DISTINCTCOUNT(Superstore[Order ID])
Average Sales = DIVIDE([Total Sales], [Total Orders])
Profit Margin = DIVIDE([Total Profit], [Total Sales])
```

Average Sales is average sales per order. Total Orders counts unique orders, not order lines.

## Dashboard Pages

| Page | Purpose | Main visuals |
| --- | --- | --- |
| Sales Overview | Headline performance and filters | 5 KPI cards, 5 slicers, Sales by Category and Segment (column charts), Sales by Region (bar chart) |
| Trends and Profitability | Trends and profit drivers | Monthly Sales Trend by Year (line chart), Sales Share by Ship Mode (donut), Top 10 Sub-Categories by Profit (bar chart), Profit by State (map) |
| Executive Insights | Findings and actions | Profit Margin matrix by Region and Category, Key Insights, Risks, Opportunities, Recommendations |

**Slicers:** Year, Region, Product Category, Customer Segment, Ship Mode (Year and Region are synced across pages 1 and 2).

## Key Insights

1. Sales are $2.30M and profit is $286.41K, a 12.5% margin across about 5,000 unique orders.
2. West leads with $0.73M in sales and a 14.9% margin. South is lowest at $0.39M.
3. Technology is the best category: $0.84M in sales, a 17.4% margin and 51% of all profit. Copiers is the top sub-category at $56K.
4. Furniture sells well ($0.74M) but earns only a 2.5% margin and loses money in Central (-1.8%).
5. Sales grew 51.5% from 2014 ($484K) to 2017 ($733K).

## Risks

1. Furniture has a 2.5% margin. Tables lose $17.7K and Bookcases lose $3.5K.
2. Five states lose money (Texas, Ohio, Pennsylvania, Illinois and North Carolina), $78.3K combined, or 27% of total profit.
3. Technology produces 51% of profit, so the business depends heavily on one category.

## Opportunities

1. Sales have grown every year since 2015.
2. Central can close its margin gap with West (7.9% vs 14.9%).
3. Corporate ($0.71M) and Home Office ($0.43M) are small next to Consumer ($1.16M).

## Recommendations

1. Cap Furniture discounts (17% on average) and reprice Tables and Bookcases.
2. Review pricing, discounts and shipping in the five loss-making states before running new promotions there.
3. Keep Copiers, Phones and Accessories well stocked and bundle them with other products.
4. Copy West's pricing and product mix in Central and South.
5. Target Corporate and Home Office customers and stock up for the September to November peak.

## Repository Contents

```
.
├── README.md
├── Superstore_Dashboard.pbix               Power BI project file
├── Superstore_Dashboard.pdf                Dashboard export (3 pages)
├── data/
│   └── Sample - Superstore.csv             Original dataset
└── reports/
    ├── BI_Overview_Report.pdf              Business Intelligence Overview Report
    └── Executive_Summary_Report.pdf        Executive Summary Report
```

## How to Open the Dashboard

1. Download `Superstore_Dashboard.pbix`.
2. Open it in Power BI Desktop (free from Microsoft).
3. Use the slicers to filter by year, region, category, segment or ship mode.

If the data does not load, go to Home, then Transform data, then Data source settings, and point the source to `data/Sample - Superstore.csv` on your computer.

## Links

- Google Drive (all files): https://drive.google.com/drive/folders/1MAVxk_ai7feq5kMkkOm_qFaxNo2PY-pV?usp=sharing
- LinkedIn post: https://lnkd.in/p/dxYiXm4h
- X post: https://x.com/Deimoss003/status/2114705890628542569?s=20

## Acknowledgement

Built as part of the AnalystLab Africa Experience Lab Internship Programme. #AnalystLabAfrica
