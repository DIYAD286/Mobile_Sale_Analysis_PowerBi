# 📱 Mobile Sales Analysis Dashboard using Power BI

An end-to-end data analytics project built in Power BI analyzing mobile phone sales across Indian cities. The raw dataset was cleaned using **Power Query** and enriched with custom **DAX measures** to build an interactive dashboard for business insights.

---

## 📊 Dashboard Preview

<img width="1242" height="701" alt="Dashboard" src="https://github.com/user-attachments/assets/41c333d5-fdd8-4a3b-a18b-31edee932a01" />


---

## 📁 Project Structure

```
mobile-sales-analysis/
│
├── dashboard.png                    # Dashboard screenshot
├── Mobile_Sales_Data_Raw.xlsx       # Original raw dataset
├── MobileSalesAnalysis.pbix         # Power BI project file
└── README.md                        # Project documentation
```

---

## 📂 Dataset Overview

The raw dataset contains **mobile sales transactions** across Indian cities from 2021–2022.

| Column | Description |
|---|---|
| `Transaction ID` | Unique ID for each sale |
| `Day / Month / Year` | Date broken into separate columns |
| `Day Name` | Name of the weekday (had inconsistencies — cleaned) |
| `Brand` | Mobile brand (Apple, Samsung, OnePlus, Vivo, Xiaomi) |
| `Mobile Model` | Specific model sold |
| `Units Sold` | Number of units per transaction |
| `Price Per Unit` | Price of one unit (₹) |
| `Customer Name` | Buyer's name |
| `Customer Age` | Buyer's age |
| `City` | City of purchase (15+ Indian cities) |
| `Payment Method` | UPI / Cash / Credit Card / Debit Card |
| `Customer Ratings` | Rating given (1–5) |

---

## 🧹 Data Cleaning (Power Query)

The following cleaning steps were applied in Power Query inside Power BI:

- **Standardized `Day Name` column** — values had inconsistencies like `"Sat"` vs `"Saturday"`, `"Mon"` vs `"Monday"`. Replaced all abbreviations with full day names.
- **Fixed data types** — ensured `Price Per Unit`, `Units Sold` were numeric; `Date` fields were set correctly.
- **Created a full `Date` column** — merged `Day`, `Month`, `Year` columns into a single proper date using a custom column.
- **Removed nulls and duplicates** — checked all columns for missing or duplicate transaction entries.
- **Trimmed text fields** — removed extra spaces from `Brand`, `City`, and `Payment Method` columns.

---

## 📐 DAX Measures

Custom DAX measures created for the dashboard:

```dax
-- Total Sales Revenue
total_sales = SUMX(Mobile_salesdata,Mobile_salesdata[Units Sold]*Mobile_salesdata[Price Per Unit])

-- Total Transactions
Transactions = COUNTROWS(Mobile_salesdata)

-- Total Units Sold
total Quanity = SUM(Mobile_salesdata[Units Sold])

-- Average Transaction Value
Average = AVERAGE(Mobile_salesdata[Price Per Unit])

-- Previous Month Sales
Previous Month Sales = 
CALCULATE(
    [total_sales],
    DATEADD(Calendar[Date], -1, MONTH)
)
-- Month-over-Month Growth %
Monthly Growth(MOM)% = 
DIVIDE(
    [total_sales] - [Previous Month Sales],
    [Previous Month Sales]
)
-- Top Brand by Sales
Top Brand = 
TOPN(
    1,
    VALUES(Mobile_salesdata[Brand]),
    [total_sales],
    DESC
)
```

---

## 📈 Key Insights from the Dashboard

- 💰 **Total Revenue: ₹769M** across 4,000+ transactions
- 📦 **19K units sold** with an average transaction value of **₹40K**
- 🏆 **Apple** is the top brand with **₹161.6M** in sales, closely followed by Samsung (₹160M)
- 💳 **UPI** is the most used payment method (26.25%), with fairly even distribution across all 4 methods
- ⭐ **311 customers** gave a 5/5 rating — the highest count across all rating levels
- 📉 Monthly Growth (MOM%) shows fluctuating trends, highlighting seasonal demand patterns

---

## 🛠️ Tools Used

| Tool | Purpose |
|---|---|
| Power BI Desktop | Dashboard building & visualization |
| Power Query | Data cleaning & transformation |
| DAX | Custom measures & KPIs |
| Excel (.xlsx) | Raw data source |

---

## 🚀 How to Use

1. Download or clone this repository
2. Open `MobileSalesAnalysis.pbix` in **Power BI Desktop**
3. If prompted, update the data source path to point to `Mobile_Sales_Data_Raw.xlsx`
4. Click **Refresh** to reload the data
5. Explore the dashboard using the filters (Month, Brand, Payment Method, Day)

---

## 👩‍💻 Author

**Diya**
--- B.E. Electronics and Computer Engineering — Thapar Institute of Engineering and Technology
- 📧 ddiyadawra28@gmail.com
- 🔗 [LinkedIn](https://linkedin.com)
- 🐙 [GitHub](https://github.com)

