# Bitcoin Investment Risk Assessment — Business Analysis Case Study

An end-to-end Business Analysis case study analyzing 4,175 days of 
Bitcoin OHLC data (2014–2026) to deliver structured investment risk 
intelligence for retail investors and portfolio decision-makers.

**Project Owner:** Vasu Sharma  
**Project Type:** Financial Risk Analytics / Business Analysis Case Study  
**Status:** ✅ Completed  
**Tools:** SQL · PostgreSQL · Power BI · DAX · Jira  
**GitHub:** [View Repository](https://github.com/vasu39419-spec/-Bitcoin-Market-Analysis-Dashboard)

---

## 📁 Project Documentation

| Document | Description | Link |
|----------|--------------|------|
| 📄 Business Requirements Document | Full BRD with stakeholders, objectives, and requirements | [View BRD](./business-analysis/Bitcoin_Investment_Risk_Assessment_BRD.pdf) |
| 📋 User Stories & Epics | 6 user stories across 3 Epics with acceptance criteria | See Section 6 below |
| 🔄 Jira Board | Completed Scrum board (2 sprints) | [View Screenshot](./business-analysis/Jira_Board_Bitcoin.png) |
| 🔍 SQL Queries | All analysis queries for financial metrics | [View Queries](./sql/bitcoin_queries.sql) |
| 📊 Dashboard | Power BI dashboard (4 pages) | See screenshots below |

---

## 🎯 1. Business Problem

Retail investors, risk analysts, and portfolio managers struggle to make 
structured Bitcoin investment decisions without a repeatable analytical 
framework — relying instead on social media hype, reactive commentary, 
and inconsistent "gut-feel" tracking.

**Key questions stakeholders needed answered:**
- Which years showed the strongest Bitcoin growth?
- Which years represented the highest investment risk?
- How volatile is Bitcoin year-over-year?
- Is there a recurring market cycle pattern to reference?
- How can non-technical stakeholders quickly understand market cycles?

---

## 👥 2. Stakeholders

| Stakeholder | Role | Key Question |
|-------------|------|---------------|
| Investment Managers | Primary User | Which years showed strongest growth? |
| Risk Analysts | Primary User | Which periods showed highest risk? |
| Portfolio Managers | Secondary User | How to benchmark BTC performance? |
| Executive Team | Report Consumer | What is the market cycle pattern? |

---

## 📋 3. Business Requirements

| BR ID | Requirement | Status |
|-------|-------------|--------|
| BR-01 | YoY price performance calculation | ✅ Done |
| BR-02 | Peak and risk year identification | ✅ Done |
| BR-03 | Historical price range analysis | ✅ Done |
| BR-04 | Interactive filtering by year/period | ✅ Done |
| BR-05 | Executive summary delivery | ✅ Done |

Full requirements, user stories, and acceptance criteria documented in the [BRD](./business-analysis/Bitcoin_Investment_Risk_Assessment_BRD.pdf).

---

## 📊 4. Process Mapping (As-Is vs To-Be)

| Step | As-Is (Before) | To-Be (After) |
|------|-----------------|----------------|
| 1 | See BTC price hype on social media | Open Power BI dashboard |
| 2 | Manually check charts, no framework | View YoY performance across full dataset |
| 3 | React emotionally to hype/fear | System auto-flags high-risk years (±30%) |
| 4 | Decide based on gut feeling | Review 4-year market cycle context |
| 5 | No record of reasoning | Documented, auditable recommendation |

---

## 🔄 5. Agile Delivery

**3 Epics · 6 User Stories · 2 Sprints · All stories completed**

![Jira Board](./business-analysis/Jira_Board_Bitcoin.png)

### Epics

- **Historical Performance Intelligence Engine** — YoY benchmarking across full dataset
- **Investment Risk Identification Framework** — Automated risk flagging (±30% YoY)
- **Market Cycle Intelligence & Strategic Context** — 4-year cycle pattern & recommendations

### User Stories

| ID | Story | Points | Epic |
|----|-------|--------|------|
| BIRA-4 | View YoY performance for all historical years | 5 | Historical Performance Intelligence Engine |
| BIRA-5 | Filter dashboard by specific year or period | 3 | Historical Performance Intelligence Engine |
| BIRA-6 | Auto-flag years exceeding ±30% YoY volatility | 5 | Investment Risk Identification Framework |
| BIRA-7 | Highlight the single highest-risk year | 3 | Investment Risk Identification Framework |
| BIRA-8 | Document and visualize the 4-year market cycle pattern | 5 | Market Cycle Intelligence & Strategic Context |
| BIRA-9 | Deliver plain-language investment recommendation | 3 | Market Cycle Intelligence & Strategic Context |

**Total Story Points:** 23

---

## 📈 6. Key Business Findings

- ✅ **2017** — Strongest growth year (+605% YoY)
- ✅ **2022** — Highest risk/decline year (−41% YoY)
- ✅ **2020–2021** — Second major bull cycle identified
- ✅ Consistent **4-year market cycles** observed in data
- ✅ High volatility periods mapped for risk management
- ✅ Price range: **$0 to $73,000+** across 12 years

---

## 📊 7. Dashboard Pages

| Page | Business Question Answered |
|------|------------------------------|
| 📌 Market Overview | What does the overall price history look like? |
| 📈 YoY Performance | Which years showed growth vs decline? |
| ⚠️ Risk Analysis | When were the highest risk periods? |
| 📋 Executive Summary | What are the key takeaways for decision-makers? |

*(Insert dashboard screenshots here)*

---

## 🛠️ 8. Technical Stack

| Layer | Technology |
|-------|------------|
| Database | PostgreSQL |
| Analysis | SQL (Joins, CTEs, Aggregations, Window Functions) |
| Visualization | Power BI Desktop |
| Calculations | DAX Measures (YoY % change) |
| Delivery Tracking | Jira (Scrum) |
| Data Format | OHLC (Open, High, Low, Close) |

---

## 📊 9. Dataset Profile

| Field | Details |
|-------|---------|
| Total Records | 4,175 days |
| Date Range | 2014 – 2026 |
| Data Type | OHLC Financial Data |
| Fields | Date, Open, High, Low, Close, Volume |
| Currency | USD |

---

## 🔍 10. Sample SQL Analysis


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

📋 11. Executive Summary (Key Insight)
This analysis identified clear 4-year market cycles in Bitcoin's
price history:

Cycle 1 (2014–2017): Early adoption → First major peak
Cycle 2 (2018–2022): Correction → Second major peak → Crash
Cycle 3 (2023–2026): Recovery → Current cycle
Investment Implication: Risk analysts can use historical cycle
patterns to identify potential entry/exit points and risk management
windows. Treat YoY growth beyond +200% as a strong historical
entry-pattern reference; treat YoY decline beyond −30% as a mandatory
risk-review trigger.

⚠️ Note: This is an analytical portfolio project. Not financial advice.

🚀 12. BA Skills Demonstrated
Skill	Evidence
Business Problem Framing	Defined investment/risk questions
Stakeholder Analysis	Investment managers, risk analysts, portfolio teams
Requirements Definition	5 business requirements + 6 user stories documented
Agile Delivery	3 Epics, 6 stories, 2 completed sprints in Jira
Financial Domain Knowledge	OHLC data, YoY analysis, market cycles
SQL Analysis	YoY calculations, aggregations, window functions
Executive Reporting	Dashboard designed for non-technical executives
Data Storytelling	Findings framed as business insights

📂 13. Repository Structure
Bitcoin-Investment-Risk-Assessment/
│
├── 📁 business-analysis/
│   ├── Bitcoin_Investment_Risk_Assessment_BRD.pdf
│   └── Jira_Board_Bitcoin.png
│
├── 📁 sql/
│   └── bitcoin_queries.sql
│
├── 📁 data/
│   └── bitcoin_data.csv
│
├── 📁 dashboard/
│   └── dashboard_screenshots/
│
└── 📖 README.md

📧 Contact
Vasu Sharma
Business Analyst | SQL · Power BI · Financial Analytics · Agile

📧 vasu39419@gmail.com
💼 LinkedIn
🐱 GitHub

📜 Note
This is a self-directed portfolio project created to demonstrate
Business Analyst skills in the financial domain including problem
framing, stakeholder analysis, Agile delivery, SQL analysis, and
executive Power BI reporting.
