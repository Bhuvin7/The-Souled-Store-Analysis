📌 Project Overview
This project is a complete Business Intelligence Dashboard built on Power BI for The Souled Store — one of India's leading pop culture merchandise and apparel brands. The dashboard covers three core business areas: Products, Orders, and Inventory, providing actionable insights across sales performance, stock health, and product analytics.
The goal of this project is to simulate a real-world BA/analyst workflow — from raw data collection to dashboard storytelling — and demonstrate proficiency in Power BI, DAX, and data visualization.

📁 Dataset
TableRowsDescriptionProducts150Product catalog with pricing, fabric, fit, licensing infoOrders1500Transactional order data across channels and citiesInventory1000+SKU-level stock data with health status and reorder flags
Key Columns

Products: product_id, category, product_type, gender, mrp, cost_price, gross_margin_pct, is_licensed, is_active, fabric, fit
Orders: order_id, order_date, customer_id, channel, revenue_inr, gross_profit_inr, discount_pct, order_status, city, payment_method
Inventory: product_id, size, opening_stock, closing_stock, units_sold, sell_through_pct, stock_health_status, reorder_recommended


📊 Dashboard Pages
📄 Page 1 — Products

KPI Cards: Total Products, Active Products, Licensed Products, Total Categories
Avg MRP by Category (Bar Chart)
Total Products by Fabric (Bar Chart)
MRP vs Cost Price (Scatter Chart)
Initial Stock by Category (Treemap)
Stock based on Gender (Column Chart)
Product Licensed split (Donut Chart)

📄 Page 2 — Orders

KPI Cards: Total Revenue, Total Orders, Total Gross Profit, Order Units Sold, Cancellation Rate %
Revenue by Month (Line Chart)
Total Revenue by Quarter (Column Chart)
Total Orders by Channel (Bar Chart)
Avg Discount % by Category (Bar Chart)
Order Status split (Donut Chart)
Revenue split by Channel (Donut Chart)
Branches by City (Map Visual)

📄 Page 3 — Inventory

KPI Cards: Total Units Received, Total Opening Stock, Total Closing Stock, Dead Stock Units
Avg Sell Through % by Category (Bar Chart)
Closing Stock by Size (Column Chart)
Units Sold by Category (Bar Chart)
Dead Stock Units by Category (Bar Chart)
Ratio of Stocks — Overstocked vs Normal (Donut Chart)


🧮 DAX Measures Highlights
dax-- Weighted Sell Through Rate
SellThruPct = 
DIVIDE(
    SUM('Inventory'[units_sold]),
    SUM('Inventory'[opening_stock]) + SUM('Inventory'[units_received])
) * 100

-- Dead Stock Value
Dead Stock Value = 
SUMX(
    FILTER('Inventory', 'Inventory'[units_sold] = 0),
    'Inventory'[closing_stock] * 'Inventory'[mrp]
)

-- Cancellation Rate
Cancellation Rate % = 
DIVIDE(
    COUNTROWS(FILTER('Orders', 'Orders'[order_status] = "Cancelled")),
    COUNTROWS('Orders')
) * 100

-- Total Gross Profit (Delivered Only)
Total Gross Profit = 
SUMX(
    FILTER('Orders', 'Orders'[order_status] = "Delivered"),
    'Orders'[gross_profit_inr]
)

Full DAX measures list available in DAX_Measures.md


🔍 Key Business Insights

📦 D2C Website is the highest performing channel with 291 orders — more than Amazon and Flipkart combined
📈 Revenue shows a clear Q4 peak (₹0.20M) indicating strong festive season demand
🎵 Music category has the highest units sold, while DC and Marvel lead in dead stock value
🏷️ Harry Potter has the highest average discount % at 15.8%
🔴 DC and Marvel categories have the most overstocked SKUs — potential markdown opportunity
📊 Size M and L have the highest closing stock — most popular sizes among customers


🛠️ Tools & Technologies
ToolUsagePower BI DesktopDashboard building and visualizationDAXCustom measures and KPI calculationsMicrosoft ExcelData cleaning and preparationPower QueryData transformation

🚀 How to Run

Clone or download this repository
Open soul_store.pbix in Power BI Desktop
If data source prompts appear, re-link the Excel/CSV files from the /data folder
All visuals and measures will load automatically


📂 Repository Structure
souled-store-powerbi/
│
├── soul_store.pbix           # Main Power BI file
├── README.md                 # Project documentation
├── DAX_Measures.md           # All DAX measures reference
│
└── data/
    ├── products.csv          # Products dataset
    ├── orders.csv            # Orders dataset
    └── inventory.csv         # Inventory dataset

👤 Author
Bhuvesh
Final Year B.E. — Computer Science Engineering
Arasu Engineering College, Kumbakonam
linkedin : bhuvesh-r-0a8151229
