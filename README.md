# Bitcoin Market Analysis — Financial Business Intelligence Case Study

> An end-to-end financial analytics project analyzing 4,175 days 
> of Bitcoin OHLC data (2014–2026) to deliver executive-level 
> market intelligence for investment decision-making and 
> risk management.

**Project Owner:** Vasu Sharma  
**Project Type:** Financial Analytics / Business Intelligence Portfolio  
**Status:** ✅ Completed  
**Date:** 2025  
**Tools:** SQL · PostgreSQL · Power BI · DAX  
**GitHub:** [View Repository](https://github.com/vasu39419-spec/-Bitcoin-Market-Analysis-Dashboard)

---

## 📁 Project Documentation

| Document | Description | Link |
|----------|-------------|------|
| 📄 Business Context | Problem statement, stakeholders, objectives | [View](./Business_Context.md) |
| 🔍 SQL Queries | All analysis queries for financial metrics | [View Queries] |
| 📊 Dashboard | 4-page Power BI dashboard | See screenshots below |

---

## 🎯 Business Context

### The Business Problem

Investment firms, portfolio managers, and individual investors 
struggle to identify Bitcoin market cycles, growth periods, 
and risk periods without structured analytical tools.

Key questions stakeholders needed answered:

- Which year showed the strongest Bitcoin growth?
- Which year represented the highest investment risk?
- How volatile is Bitcoin year-over-year?
- What are the historical price ranges for risk modeling?
- How can executives quickly understand market cycles?

### My Approach (Business Analysis Thinking)

I treated this as a **financial business intelligence problem**:

1. Defined the business problem and stakeholder questions
2. Collected 4,175 days of OHLC historical data
3. Stored in PostgreSQL for structured analysis
4. Wrote SQL queries for YoY calculations
5. Built executive Power BI dashboard
6. Delivered insights in executive summary format

### Business Impact

| Metric | Value |
|--------|-------|
| Data Analyzed | 4,175 days (2014–2026) |
| Strongest Growth Year | 2017 (+605% YoY) |
| Highest Risk Year | 2022 (-41% YoY) |
| Research Time | Reduced from weeks to minutes |
| Stakeholder Value | Executive summary for investment decisions |

---

## 👥 Stakeholders Identified

| Stakeholder | Role | Key Question |
|-------------|------|--------------|
| Investment Managers | Primary User | Which years showed strongest growth? |
| Risk Analysts | Primary User | Which periods showed highest risk? |
| Portfolio Managers | Secondary User | How to benchmark BTC performance? |
| Executive Team | Report Consumer | What is the market cycle pattern? |

---

## 📈 Key Business Findings

✅ **2017** — Strongest growth year **(+605% YoY)**  
✅ **2022** — Highest risk/decline year **(-41% YoY)**  
✅ **2020–2021** — Second major bull cycle identified  
✅ **Consistent 4-year market cycles** observed in data  
✅ **High volatility periods** mapped for risk management  
✅ **Price range:** $0 to $73,000+ across 12 years  

---

## 📊 Dashboard Pages

| Page | Business Question Answered |
|------|---------------------------|
| 📌 Market Overview | What does the overall price history look like? |
| 📈 YoY Performance | Which years showed growth vs decline? |
| ⚠️ Risk Analysis | When were the highest risk periods? |
| 📋 Executive Summary | What are the key takeaways for decision-makers? |

---

## 💼 Business Requirements (Summary)

| Requirement | Description | Status |
|-------------|-------------|--------|
| BR-01 | YoY price performance calculation | ✅ Done |
| BR-02 | Peak and risk year identification | ✅ Done |
| BR-03 | Historical price range analysis | ✅ Done |
| BR-04 | Interactive filtering by year/period | ✅ Done |
| BR-05 | Executive summary delivery | ✅ Done |

---

## 🔄 Analytical Approach
Business Problem Defined
↓
Stakeholder Questions Identified
↓
Data Collected (4,175 days OHLC)
↓
PostgreSQL Database Setup
↓
SQL Analysis (YoY calculations)
↓
Power BI Dashboard Built
↓
Executive Summary Delivered
↓
Insights for Investment Decisions


---

## 🛠️ Technical Stack

| Layer | Technology |
|-------|------------|
| Database | PostgreSQL |
| Analysis | SQL (Joins, CTEs, Aggregations, YoY) |
| Visualization | Power BI Desktop |
| Calculations | DAX Measures (YoY % change) |
| Data Format | OHLC (Open, High, Low, Close) |

---

## 📊 Dataset Profile

| Field | Details |
|-------|---------|
| Total Records | 4,175 days |
| Date Range | 2014 – 2026 |
| Data Type | OHLC Financial Data |
| Fields | Date, Open, High, Low, Close, Volume |
| Currency | USD |

---

## 🔍 Sample SQL Analysis

```sql
-- Year-over-Year Performance Calculation
SELECT
    EXTRACT(YEAR FROM date) AS year,
    ROUND(AVG(close)::numeric, 2) AS avg_price,
    ROUND(MAX(high)::numeric, 2) AS peak_price,
    ROUND(MIN(low)::numeric, 2) AS lowest_price,
    ROUND(
        ((AVG(close) - LAG(AVG(close)) 
        OVER (ORDER BY EXTRACT(YEAR FROM date))) 
        / LAG(AVG(close)) 
        OVER (ORDER BY EXTRACT(YEAR FROM date))) * 100
    , 2) AS yoy_change_pct
FROM bitcoin_data
GROUP BY EXTRACT(YEAR FROM date)
ORDER BY year;

📋 Executive Summary (Key Insight)
This analysis identified clear 4-year market cycles in
Bitcoin's price history:

Cycle 1 (2013–2017): Early adoption → First major peak
Cycle 2 (2018–2022): Correction → Second major peak → Crash
Cycle 3 (2023–2026): Recovery → Current cycle

Investment Implication:
Risk analysts can use historical cycle patterns to identify
potential entry/exit points and risk management windows.

⚠️ Note: This is an analytical portfolio project.
Not financial advice.

🚀 BA Skills Demonstrated
Skill	Evidence
Business Problem Framing	Defined investment/risk questions
Stakeholder Analysis	Investment managers, risk analysts, portfolio teams
Requirements Definition	5 business requirements documented
Financial Domain Knowledge	OHLC data, YoY analysis, market cycles
SQL Analysis	YoY calculations, aggregations, window functions
Executive Reporting	Dashboard designed for non-technical executives
Data Storytelling	Findings framed as business insights
📂 Repository Structure
text

Bitcoin-Market-Analysis-Dashboard/
│
├── 📄 Business_Context.md
├── 📊 Dashboard screenshots
├── 🔍 SQL queries
├── 📁 bitcoin_data.csv
└── 📖 README.md
🔗 Related Projects
Project	Domain	Link
India Job Market Analysis	Career Analytics / Full BA Case Study	View
YouTube Shorts Analysis	Digital Media Analytics	View
📧 Contact
Vasu Sharma
Business Analyst | SQL · Power BI · Financial Analytics · Agile

📧 vasu39419@gmail.com
💼 LinkedIn
🐱 GitHub

📜 Note
This is a self-directed portfolio project created to demonstrate
Business Analyst skills in financial domain including problem
framing, stakeholder analysis, SQL analysis, and executive
Power BI reporting.

⭐ If this project demonstrates strong financial BA thinking,
please consider starring this repository.
