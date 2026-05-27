# Bitcoin Market Analysis Dashboard (2014-2026)

An interactive, 4-page Power BI dashboard designed to analyze historical Bitcoin market cycles, trading volumes, and volatility metrics to uncover seasonal price behaviors and historical performance patterns.

---

## 📊 Dashboard Pages & Insights

### 1. Bitcoin Market Analysis (Overview)
* Focuses on macro-level historical trends across a 4,175-day timeline.
* Key features include **All-Time High ($126.20K)** and **All-Time Low ($171.51)** metric cards.
* Includes a **Bull vs Bear Days** distribution donut chart and a waterfall visualization tracking **Yearly Price Change YoY**.

### 2. Bitcoin Price Analysis
* Features an advanced **Bitcoin Price Trend** dual-axis area chart scaling historical valuations.
* Highlights yearly peak performance via a **Yearly All-Time High** column chart.
* Embeds a granular breakdown tracking daily price ranges and historical volatility variations.

### 3. Volume & Volatility Analysis
* Details trading liquidity by mapping a **Trading Volume Trend** over time.
* Implements a **Volume vs Volatility Scatter Plot** to prove the direct correlation: *High Volume = High Volatility Pattern*.
* Employs a custom 3-color conditional gradient chart illustrating **Yearly Avg Volatility %** (Red for high risk, Green for low risk).

### 4. Year & Month Deep Dive
* Isolates granular performance cycles using a sequential **Monthly Historical Price Trend** layout.
* Hosts a comprehensive **Year Wise Summary Matrix Table** displaying average prices, maximum highs, minimum lows, and aggregate bull/bear counts.
* Utilizes localized color-scale formatting to instantly call out top-performing financial intervals.

---

## 🛠️ DAX Measures Implemented

The project leverages customized Data Analysis Expressions (DAX) to build dynamic calculations:

* **Year-over-Year Growth:** Evaluates annual closing average shifts cleanly.
  ```dax
  YoY Growth = 
  VAR CurrentYear = MAX(Bitcoin_history_data[year])
  VAR CurrentAvg = CALCULATE(AVERAGE(Bitcoin_history_data[Close]), Bitcoin_history_data[year] = CurrentYear)
  VAR PrevAvg = CALCULATE(AVERAGE(Bitcoin_history_data[Close]), Bitcoin_history_data[year] = CurrentYear - 1)
  RETURN
  DIVIDE(CurrentAvg - PrevAvg, PrevAvg) * 100
  ```
* **Average YoY Growth:** Aggregates individual year-over-year variances over dynamic evaluation scales.
  ```dax
  Avg YoY Growth = 
  AVERAGEX(
      VALUES(Bitcoin_history_data[year]), 
      [YoY Growth]
  )
  ```

---

## 🚀 How to Interact with the Report
1. Use the **YEAR** and **Market Day** slicers positioned at the top of the dashboard pages to dynamically slice the data.
2. Cross-filter the visualizations by clicking directly on data columns, scatter points, or matrix rows.
