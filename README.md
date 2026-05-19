# 🛒 E-Commerce Sales & Customer Behavior Analysis

<p align="center">
  <img src="https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black" />
  <img src="https://img.shields.io/badge/DAX-0078D4?style=for-the-badge&logo=microsoft&logoColor=white" />
  <img src="https://img.shields.io/badge/Power%20Query-217346?style=for-the-badge&logo=microsoft&logoColor=white" />
  <img src="https://img.shields.io/badge/Domain-E--Commerce-FF6B35?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge" />
</p>

<p align="center">
  <b>An end-to-end Business Intelligence project analyzing e-commerce customer behavior, revenue trends, promotion effectiveness, and product performance using Power BI.</b>
</p>

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Problem Statement](#-problem-statement)
- [Dataset](#-dataset)
- [Dashboards](#-dashboards)
- [Tools & Technologies](#-tools--technologies)
- [Key Insights](#-key-insights)
- [Results & Conclusion](#-results--conclusion)
- [How to Run](#-how-to-run)
- [Project Structure](#-project-structure)
- [Author & Contact](#-author--contact)

---

## 📌 Overview

This project transforms raw e-commerce transactional data into a fully interactive **Power BI Business Intelligence solution** with 4 analytical dashboards.

The analysis covers customer purchasing behavior, revenue performance, promotion impact, channel effectiveness, and time-based traffic patterns — providing actionable insights for business decision-making.

**Skills demonstrated:**
- ⚡ Power BI Dashboard Design & Development
- 🔄 Data Cleaning & Transformation (Power Query)
- 📐 DAX Calculations & Measures
- 🗃️ Data Modeling & Relationships
- 📊 Interactive Data Visualization
- 🧠 Business Intelligence Reporting

---

## ❓ Problem Statement

> *An e-commerce company needs to understand customer activity, product performance, pricing behavior, and promotion effectiveness to make smarter business decisions.*

**This project answers 10 core business questions:**

| # | Business Question |
|---|---|
| 1 | Which brands and categories generate the highest revenue? |
| 2 | How does customer traffic vary by day of week and hour? |
| 3 | What is the conversion rate from View → Cart → Purchase? |
| 4 | Which channel performs better — App or Browser? |
| 5 | What is the impact of promotions on profit and sales? |
| 6 | How does revenue differ across U.S. states? |
| 7 | Which hours are most profitable for the business? |
| 8 | How do high-score users compare to low-score users in revenue? |
| 9 | Which promotion campaigns drive the highest return? |
| 10 | What are the overall KPIs — Revenue, Profit, and Discount? |

---

## 🗂️ Dataset

| Dataset | Description |
|---|---|
| `Sales_Data_Ecommerce` | Transactional data with user IDs, event types, product info, pricing, channel, and timestamps |
| `Promotion Dataset` | Promotion IDs, discount amounts, and campaign-level details |

**Key Fields:**

```
user_id        → Unique customer identifier
event_type     → View / Cart / Purchase
brand          → Product brand (Apple, Samsung, Xiaomi, etc.)
category       → Product category (Electronics, Computers, Appliances, etc.)
price          → Transaction price
channel        → App or Browser
event_hour     → Hour of the day (0–23)
Day_of_Week    → Day name (Monday–Sunday)
state          → U.S. state
Promotion_Id   → Linked promotion campaign
discount_amount→ Discount applied on transaction
```

---

## 🖥️ Dashboards

The Power BI report contains **4 interactive dashboard pages**, each focused on a different analytical lens.

---

### 📊 Page 1 — Total Calculations *(KPI Overview)*

> High-level KPIs with revenue breakdowns by brand, category, channel, month, and day.

![Total Calculations Dashboard](images/dashboard_total_calculations.png)

**Highlights:**
- 💰 **Revenue:** 155.6M &nbsp;|&nbsp; **Profit:** 94.58M &nbsp;|&nbsp; **Discount:** 1.31M
- 🏆 **Top Brand:** Apple (leads all brands by a wide margin)
- 📦 **Top Category:** Electronics (~40M+ in revenue)
- 📱 **Channel Split:** App 50.1% vs Browser 49.8% — nearly equal
- 📅 **Peak Days:** Friday & Saturday record the highest sales volume

---

### 📅 Page 2 — Traffic by Time, Week & Channel

> Deep-dive into when and how customers interact with the platform.

![Traffic by Time, Week and Channel Dashboard](images/dashboard_traffic_time_week_channel.png)

**Highlights:**
- 🗓️ **Friday App** leads with 13,875 users and $13.6M in revenue
- 👁️ **Event Funnel:** View → 125.93K &nbsp;→&nbsp; Cart → 19.43K &nbsp;→&nbsp; Purchase → 14.65K
- ⚠️ **Conversion Rate: 11.6%** — significant cart abandonment opportunity
- ⏰ **Peak Hour:** 3–4 PM (hour 15–16) with 10.3K users
- 🗺️ **Top States by Revenue:** Georgia (GA) and Kentucky (KY) lead

---

### 💰 Page 3 — Revenue Calculations

> Profit trends, brand & promotion performance, and customer score analysis.

![Revenue Calculations Dashboard](images/dashboard_revenue_calculations.png)

**Highlights:**
- 📈 **Peak Profit Hours:** 8 AM – 6 PM; drops sharply after hour 20
- 🗓️ **Friday = 17.31%** and **Saturday = 17.17%** of weekly profit
- 🍎 **Apple Electronics:** $59.4M revenue from 7,769 promotions — #1 brand-category combo
- ⭐ **User Score 4** customers generate ~$65M — highest-value segment by far

---

### 🎯 Page 4 — Effects of Special Promotions on Sales

> Promotion campaign effectiveness measured by count, profit, and revenue by event type.

![Effects of Special Promotions on Sales Dashboard](images/dashboard_effects_promotions.png)

**Highlights:**
- 🏅 **Top Campaign:** `APnD_x2016` drives the highest promotion count and profit
- 📊 **Gauge:** Profit = 94.58M out of 155.64M Revenue (60.8% margin) — max scale 189.16M
- 🛒 **Revenue by Event Type:** View events generate ~115M vs Cart/Purchase at ~20M each

---

## 🛠️ Tools & Technologies

| Technology | Usage |
|---|---|
| **Power BI Desktop** | Report building, visualization, publishing |
| **Power Query (M)** | Data ingestion, cleaning, shaping |
| **DAX** | KPI measures, calculated columns, time intelligence |
| **Data Modeling** | Star schema — Sales ↔ Promotions relationship |
| **Slicers & Bookmarks** | Dynamic interactivity and page navigation |

### 📐 Key DAX Measures

```dax
-- Total Revenue
Total Revenue = SUM(Sales_Data[price])

-- Total Profit
Total Profit = SUM(Sales_Data[profit])

-- Total Discount
Total Discount = SUM(Sales_Data[discount_amount])

-- Purchase Conversion Rate
Conversion Rate =
DIVIDE(
    CALCULATE(COUNTROWS(Sales_Data), Sales_Data[event_type] = "purchase"),
    CALCULATE(COUNTROWS(Sales_Data), Sales_Data[event_type] = "view"),
    0
)

-- Revenue by Channel
Revenue by Channel =
CALCULATE(
    SUM(Sales_Data[price]),
    ALLEXCEPT(Sales_Data, Sales_Data[channel])
)

-- Profit Margin %
Profit Margin % =
DIVIDE([Total Profit], [Total Revenue], 0) * 100
```

---

## 💡 Key Insights

```
1.  🍎  Apple is the top brand — $59.4M revenue, more than 2× Samsung ($28.5M)
2.  📦  Electronics dominates all categories with ~$40M+ in revenue
3.  ⚠️  Only 11.6% of viewers convert to buyers — major cart abandonment issue
4.  ⏰  Peak traffic: 2–4 PM daily — best window for ads and campaigns
5.  📅  Friday + Saturday = 34.5% of total weekly profit
6.  📱  App vs Browser nearly equal (50.1% vs 49.8%) — strong mobile presence
7.  ⭐  Score 4 users generate ~$65M — 4× more than Score 1 users
8.  🎯  Campaign APnD_x2016 is the top-performing promotion by volume & profit
9.  🗺️  Georgia & Kentucky lead all U.S. states in revenue
10. 💹  Profit margin of 60.8% ($94.58M / $155.64M) indicates strong unit economics
```

---

## 📈 Results & Conclusion

This project successfully converts raw transactional data into a **complete BI solution** with executive-ready dashboards.

| Analysis Area | Key Finding |
|---|---|
| 💰 Revenue & KPIs | $155.6M total revenue, 60.8% profit margin |
| 📅 Traffic Patterns | Peak: 2–4 PM, Friday–Saturday |
| 🏆 Top Performers | Apple + Electronics = highest-value segment |
| 🎯 Promotions | `APnD_x2016` campaign drives max ROI |
| ⭐ Customers | Score 4 users generate 4× more revenue |
| 📱 Channels | App leads slightly; both channels are essential |

**Business Recommendations:**
- 🎯 Run ad campaigns on **Fridays & Saturdays at 2–4 PM** for maximum reach
- 📦 Prioritize **Apple and Samsung Electronics** inventory investment
- 🔁 Implement **cart abandonment retargeting** to lift the 11.6% conversion rate
- 💎 Launch a **loyalty program** targeting Score 4 customers to maximize LTV
- 📣 Scale **top promotion campaigns** (`APnD_x2016`, `c1JgDc2016`) across more SKUs
- 🗺️ Focus expansion efforts on **GA, KY, AL** — top revenue-generating states

---

## 🚀 How to Run

### Prerequisites
- [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free download)

### Steps

```bash
# 1. Clone the repository
git clone https://github.com/your-username/Ecommerce-PowerBI-Analysis.git

# 2. Navigate into the folder
cd Ecommerce-PowerBI-Analysis
```

```
3. Open Power BI Desktop
4. File → Open → Select: case_study_ecommerce_power_bi.pbix
5. Home → Refresh  (update data source path if prompted)
6. Explore all 4 dashboard tabs
```

---

## 📁 Project Structure

```
Ecommerce-PowerBI-Analysis/
│
├── 📊 case_study_ecommerce_power_bi.pbix    ← Main Power BI file
├── 📄 README.md                             ← This file
│
└── 📁 images/
    ├── dashboard_total_calculations.png
    ├── dashboard_traffic_time_week_channel.png
    ├── dashboard_revenue_calculations.png
    └── dashboard_effects_promotions.png
```

---

## 👤 Author & Contact

<table>
  <tr>
    <td align="center">
      <b>Anubhav Chauhan</b><br/>
      Master's Student in Data Analytics<br/><br/>
      <a href="https://www.linkedin.com/in/1anubhavchauhan1/">
        <img src="https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white"/>
      </a>
      &nbsp;
      <a href="https://github.com/your-username">
        <img src="https://img.shields.io/badge/GitHub-Follow-181717?style=for-the-badge&logo=github&logoColor=white"/>
      </a>
    </td>
  </tr>
</table>

---

<p align="center">
  ⭐ <b>If you found this project helpful, please give it a star!</b> ⭐<br/><br/>
  Made with ❤️ using Power BI
</p>
