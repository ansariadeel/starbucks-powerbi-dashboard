 # Starbucks Sales Dashboard — Power BI
 
A 2-page interactive Power BI dashboard analyzing sales performance across 3 stores from **Oct 2025 to Apr 2026**.
 
---

 ## Data Sources
 
| File | Description |
|---|---|
| `sales.csv` | 10,000 transactions with amount, quantity, date, store, and payment mode |
| `items.csv` | Product catalog with category, calories, and pricing |
| `customers.csv` | 500 customer profiles with age and gender |
 
## Data Model
 
```
sales ──── items      (sales[item_id] → items[ID])
sales ──── customers  (sales[customer_id] → customers[customer_id])
```
 
---

## Dashboard Pages
 
### Page 1 — Sales Overview
- KPI cards: Total revenue, transactions, AOV, units sold
- Monthly revenue trend (Oct 2025 – Apr 2026)
- Revenue by store (101, 102, 103)
- Payment mode split (Card / Cash / UPI)
- Walk-in vs mobile app channel comparison
### Page 2 — Product Performance
- Top 10 items by revenue
- Revenue by category (7 categories)
- Category revenue bar chart
- Revenue vs units sold bubble chart
--- 
 
## Key Insights
 
- **$78,401** total revenue across 10,000 transactions
- **Bakery** dominates with 55% of all revenue ($43,439)
- All 3 stores perform almost equally (~$26K each)
- Payment modes are evenly split — Card, Cash, and UPI each ~33%
- Mobile app and walk-in channels are nearly 50/50
---

## Key DAX Measures
 
```dax
Total Revenue       = SUM(sales[total_amount])
Total Transactions  = COUNTROWS(sales)
Avg Order Value     = DIVIDE([Total Revenue], [Total Transactions])
Top Category        = CALCULATE(FIRSTNONBLANK(items[type], 1), TOPN(1, VALUES(items[type]), [Total Revenue]))
Best Seller         = CALCULATE(FIRSTNONBLANK(items[item], 1), TOPN(1, VALUES(items[item]), [Total Revenue]))
```
---

## File

`starbucks_1.pbix` — open with Power BI Desktop (June 2024 or later recommended)
