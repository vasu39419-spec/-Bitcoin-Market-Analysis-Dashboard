
## Bitcoin Market Analysis Dashboard

---

## 1. Business Problem

Investment professionals and analysts need structured, 
validated market intelligence to make informed decisions 
about Bitcoin as an asset class.

**Current challenges:**
- Historical price data exists but is unstructured
- No easy way to compare year-over-year performance
- Risk periods not clearly identified
- Executive reporting requires manual data work

---

## 2. Business Objective

Deliver a structured financial analytics dashboard that:

1. Tracks Bitcoin price performance from 2014–2026
2. Identifies strongest growth years (peak periods)
3. Identifies highest risk years (decline periods)
4. Enables executive-level reporting and decision support

---

## 3. Stakeholders

| Stakeholder | Need |
|-------------|------|
| Investment Managers | Growth period identification |
| Risk Analysts | Risk period identification |
| Portfolio Managers | Historical benchmarking |
| Executive Team | High-level market summary |

---

## 4. Key Business Questions Answered

- Which year showed the strongest Bitcoin growth?
  → **2017: +605% YoY**

- Which year showed the highest decline/risk?
  → **2022: -41% YoY**

- What is the historical price range?
  → **$0 to $73,000+ (2014–2026)**

- Are there identifiable market cycles?
  → **Yes: Consistent ~4-year cycles observed**

---

## 5. Solution Delivered

- PostgreSQL database with 4,175 days of OHLC data
- SQL analysis with YoY calculations
- 4-page Power BI dashboard
- Executive summary with key findings

---

## 6. Business Value

| Before | After |
|--------|-------|
| Manual data review | Dashboard-driven analysis |
| No YoY comparison | Automated YoY calculations |
| Scattered insights | Centralized executive view |
| No risk identification | Clear risk/growth period flags |

---

## 7. Assumptions

- OHLC data is sourced from reliable public sources
- Daily closing price used for YoY calculations
- Outliers retained (extreme prices are real market events)
- Analysis is retrospective (not predictive)

---

## 8. Constraints

- Historical data only (no real-time feeds)
- USD denomination only
- No ML/predictive modeling (out of scope)

---

## 9. Analytical Methodology

1. Data collected from public Bitcoin price history
2. Stored in PostgreSQL with proper schema
3. SQL queries written for:
   - YoY price change calculations
   - Peak/low price identification
   - Volatility analysis
4. Power BI connected to PostgreSQL
5. DAX measures for KPI calculations
6. Executive dashboard delivered

---

## 10. Key Finding for Stakeholders

Bitcoin shows consistent 4-year market cycles with 
identifiable peak and risk periods. This pattern can 
inform risk management frameworks and investment 
timing strategies.

> ⚠️ This is a portfolio analysis project.
> Not financial investment advice.
