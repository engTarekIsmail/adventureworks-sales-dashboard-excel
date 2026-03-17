# 📊 Adventure Works Sales Dashboard

An interactive Excel dashboard analyzing product sales performance using the **Adventure Works** dataset — built with a Star Schema data model in Power Query.

---

## 🖼️ Dashboard Preview

![alt text](Dashborad-1.png)
---

## 📌 Overview

This project was built as part of an **Excel Data Modeling** course. The dashboard provides a comprehensive view of sales performance across products, categories, subcategories, and cities using the Adventure Works dataset — covering the period **2011 to 2014**.

---

## 📈 Key KPIs

| Metric | Value |
|---|---|
| 👥 No. of Customers | 19,119 |
| 🛒 No. of Orders | 31,465 |
| 💰 Total Sales | $2,926,970,124 |
| 📦 No. of Products | 504 |

---

## ✨ Dashboard Features

**Charts & Visuals:**
- **Total Sales by Category** (Clustered Bar) — Yearly breakdown across Accessories, Bikes, Clothing, and Components (2011–2014)
- **Top Products by Total Sales** (Horizontal Bar) — Top 10 products ranked by revenue
- **Sales Trend** (Line Chart) — Monthly Total Sales vs. Running Total over time
- **No. of Orders by Category** (Pie Chart) — Bikes lead at 39%, followed by Components 36%
- **Total Sales by Category** (Pie Chart) — Bikes dominate at 41%
- **Ship Methods** (Donut Chart) — XRQ Truck Ground 98% vs. Cargo Transport 5 2%

**Interactive Slicers:**
- 📅 **OrderDate** — Timeline slicer (2011–2014, by Year)
- 🎨 **Color** — Filter by product color (Black, Blue, Grey, Red, Silver, White, Yellow...)
- 🏷️ **Product Category** — Accessories, Bikes, Clothing, Components
- 🌍 **City / Territory** — Australia, Canada, France, Germany, UK, Northeast, Northwest, Southwest, Southeast

---

## 🧱 Data Model — Star Schema

```
                        Dim_Date
                           │
          Dim_ShipMethod ──┤
                           │
Dim_Territory ─────── Fact_Table ───── Dim_Product
                                            │
                                   Production_Product
                                            │
                                   Production_ProductCategory
                                            │
                                   Production_ProductSubcategory
```

| Table | Type | Description |
|---|---|---|
| `Fact_Table` | Fact | Core sales transactions (SalesOrderDetail + SalesOrderHeader merged) |
| `Dim_Product` | Dimension | Product details with full category hierarchy |
| `Dim_Date` | Dimension | Date table with `Date_Key` (yyyyMMdd) for time intelligence |
| `Dim_Territory` | Dimension | Sales territory and geographic data |
| `Dim_ShipMethod` | Dimension | Shipping method details |
| `Production_Product` | Source | Raw product data |
| `Production_ProductCategory` | Source | Category lookup |
| `Production_ProductSubcategory` | Source | Subcategory lookup |

**Key Power Query transformation:**
```m
Table.AddColumn(#"Changed Type", "Date_Key", each Date.ToText([OrderDate],"yyyyMMdd"))
```

---

## 🗂️ Project Structure

```
adventure-works-dashboard/
│
├── AdventureWorks_Dashboard.xlsx   # Main Excel dashboard file
├── screenshots/
│   └── dashboard.png               # Dashboard preview image
└── README.md
```

---

## 🛠️ Tools & Skills Used

| Tool / Skill | Details |
|---|---|
| Microsoft Excel | Dashboard creation & visualization |
| Power Query (M Language) | Data import, transformation, and merging |
| Star Schema Design | Fact + Dimension table modeling |
| Pivot Tables & Charts | Bar, Line, Pie, Donut charts |
| Timeline & Slicers | Interactive filtering by date, color, category, city |
| KPI Cards | Revenue, Orders, Customers, Products |

---

## 📦 Dataset

**Source:** [Adventure Works — Microsoft](https://learn.microsoft.com/en-us/sql/samples/adventureworks-install-configure)

Tables used: `Sales.SalesOrderHeader`, `Sales.SalesOrderDetail`, `Production.Product`, `Production.ProductCategory`, `Production.ProductSubcategory`, `Sales.SalesTerritory`

---

## 🚀 How to Use

1. Clone or download this repository
2. Open `AdventureWorks_Dashboard.xlsx` in Microsoft Excel (2016 or later)
3. Enable content if prompted
4. Use the slicers (Date, Color, Category, City) to filter and explore the data interactively

---

## 👤 Author

**[Tarek Ismail]**
- GitHub: [@Tarek Ismail](https://github.com/engTarekIsmail)
- LinkedIn: [Tarek Shabana](https://www.linkedin.com/in/tarek-shabana-76318732b/)

---

## 📄 License

This project is for educational purposes. The Adventure Works dataset is provided by Microsoft.
