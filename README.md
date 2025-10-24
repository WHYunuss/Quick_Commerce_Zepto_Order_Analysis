# 🧠 Zepto SQL Data Analysis Project

## 📘 Project Overview
This project is a **full end-to-end SQL analysis** of the **Zepto product dataset**.  
The goal was to simulate what a **retail data analyst** would actually do in a real-world scenario — setting up a clean schema, fixing messy data, running exploratory queries, and finally uncovering insights that matter to the business.

The dataset is rich, containing details about **product categories, pricing, discounts, stock levels, and quantities**, making it a great case study for **SQL-based retail and e-commerce analytics**.

Rather than running random queries, this project follows a **structured workflow** involving:
- Data quality checks  
- Exploratory analysis  
- KPI creation  
- Business insight generation  

---

## 🧾 Dataset Information

**Source:** Zepto product dataset (fields on price, stock, discount, and category)  
**Size:** 3000+ rows used for all queries and analysis  

### 🧱 Key Fields
| Field Name | Description |
|-------------|-------------|
| `sku_id` | Unique product ID |
| `category` | Product category |
| `name` | Product name |
| `mrp` | Maximum retail price |
| `discount_percent` | Discount applied |
| `available_quantity` | Stock on hand |
| `discounted_selling_price` | Selling price after discount |
| `weight_in_gms` | Product weight |
| `out_of_stock` | Stock status (TRUE/FALSE) |
| `quantity` | Historical purchase quantity |
| `discount_amount` *(derived)* | Difference between MRP and selling price |

---

## ⚙️ Steps Followed

### 1️⃣ Data Setup
- Built a `zepto` table with schema, constraints, and checks (no negative prices or quantities).  
- Imported the dataset into **PostgreSQL**.

### 2️⃣ Data Verification
- Checked **row counts**, **sample previews**, and **distinct categories**.  
- Looked for **null values** across key fields.  
- Analyzed **stock status** (in-stock vs out-of-stock).  
- Flagged **duplicate product names**.

### 3️⃣ Data Cleaning
- Dropped rows with invalid prices (`MRP = 0` or `discounted_selling_price = 0`).  
- Fixed inflated values (converted **paise → rupees**).  
- Removed duplicates using `sku_id`.  
- Standardized category names (**lowercase**, **trimmed spaces**).  
- Detected and handled **outliers** (negative or extreme values).

### 4️⃣ Data Analysis & Business Questions
Designed queries to answer **real-world retail questions**, including:

- Top 10 best-value products by **discount %**  
- **High-MRP** products that are **out of stock**  
- **Revenue contribution** per category  
- **Premium products** with **low discounts (<10%)**  
- Top 5 categories by **average discount %**  
- **Price per gram** for products over 100g  
- Grouping products into **weight ranges** (Low, Medium, Bulk)  
- **Total inventory weight** per category  
- **Revenue share** by category  
- Top 3 discounted products **per category**  
- Correlation between **discount range** and **stock levels**  
- **Revenue lost** due to out-of-stock items  
- **Price gap** between MRP and discounted price  
- **Low-stock, high-value** products likely to sell out soon  
- **Weighted average discount** per category (stock-adjusted)

### 5️⃣ Data Transformation
- Added a **derived column**: `discount_amount`  
- Created a **summary table** `zepto_summary` with stock value and revenue share per category  

---

## 💡 Key Insights

| Area | Insight |
|-------|----------|
| **Discount Trends** | Some categories consistently offer bigger discounts, attracting value-seeking customers. |
| **Stock Risks** | Premium, high-MRP products often go out of stock, putting revenue at risk. |
| **Revenue Concentration** | A handful of categories generate most of the revenue (classic Pareto effect). |
| **Unit Economics** | Price per gram shows strong differentiation between bulk and smaller SKUs. |
| **Discount vs Stock** | Higher discounts often correlate with higher stock levels — tied to promotions. |
| **High-Value Risk Items** | Low-stock but high-value products are potential sellout risks that need close monitoring. |

---

## 🧮 SQL Concepts Used

### 🔢 Aggregation Functions
- `COUNT()` → Product counts, duplicate detection  
- `SUM()` → Revenue totals, stock value  
- `AVG()` → Average discounts and prices  
- `ROUND()` → Readable output formatting  

### 🎯 Conditional Logic
- `CASE WHEN` → For creating weight and discount range categories  

### 🧹 Data Cleaning
- Null and invalid value checks  
- Duplicate removal using `DELETE USING`  
- Outlier detection via conditional filters  

### 📦 Grouping & Filtering
- `GROUP BY` → Category and brand-level insights  
- `HAVING` → For duplicate or condition-based filtering  

### 🔽 Sorting & Ranking
- `ORDER BY … LIMIT` → Top-N queries  
- `ROW_NUMBER() OVER (PARTITION BY …)` → Top products per category  

### 🔍 Window Functions
- `SUM() OVER()` → Revenue share and partitioned aggregations  

### 🧩 Derived Metrics
- `discount_amount` = `mrp - discounted_selling_price`  
- `price_per_gram` = `discounted_selling_price / weight_in_gms`  
- `weighted_avg_discount` (stock-adjusted)  

---

## 🧰 Tools & Technologies
- **PostgreSQL** – for SQL queries and analysis  
- **Excel / CSV** – for data review and exports  
- **VS Code / DBeaver** – for query execution and visualization  

---

## 📁 Project Structure
Zepto_SQL_Data_Analysis/
│

├── data/

│ └── Zepto_Inventory_Data.csv

│

├── scripts/

│ └── Zepto_SQL_Queries.sql

│

├── outputs/

│ ├── Zepto_Summary_Table.csv

│ └── Zepto_Insights_Report.md

│

└── README.md


---

## 🚀 Final Thoughts
This project goes beyond simple querying — it shows how **SQL can power real business insights** in the retail space.  
By cleaning, analyzing, and transforming data effectively, we can uncover patterns in **pricing, stock, and performance** that drive smarter business decisions.

---
## Meeee 🥺👉👈
**YY** - trying some of this & that
