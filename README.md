# Tech Layoffs vs Stock Market Impact

This project is an end-to-end data pipeline and interactive dashboard analyzing how major tech company's layoffs affect its respective stock prices over 5-day and 1-year horizons.

This project answers a simple but controversial question:

> Are layoffs actually good for shareholders?

Using Layoffs.fyi data and Yahoo Finance stock prices, the system automatically builds a clean dataset and visualizes how markets respond to workforce reductions.

---

## What This Project Does

This project:
- Ingests real-world layoff data
- Matches companies to stock tickers
- Measures stock reactions after each layoff
- Builds an interactive Streamlit analytics dashboard
- Runs regression and correlation analysis

The result is a research-grade dataset and a live analytical dashboard that explores the relationship between layoffs and stock performance.

---

## Data Sources

| Source | What It Provides |
|------|----------------|
| Layoffs.fyi | Company name, number laid off, % of workforce, event date |
| Yahoo Finance (via yfinance) | Historical stock prices for 5-day and 1-year returns |

---

## Pipeline Overview

```text
Layoffs.fyi CSV
      ↓
Clean + Filter (Post-IPO only)
      ↓
Company → Ticker mapping
      ↓
5-Day stock returns
      ↓
1-Year stock returns
      ↓
Final master CSV
      ↓
Streamlit dashboard
```

---

## Project Structure

```text
data/
  raw/
    Layoffs.fyi - Tech Layoffs Tracker.csv
    clean_layoff_data.csv
  processed/
    layoff_vs_immediate.csv
    layoff_vs_immediate_updated.csv

scripts/
  clean_layoff_data.py
  fetch_5d_stock_data.py
  fetch_1y_stock_data.py
  layoff_vs_immediate_integration.py
  1y_add.py

app.py
```

---

## Final Dataset Columns

Each row represents one layoff event:

| Column | Meaning |
|------|-------|
| Ticker | Stock symbol |
| Date Added | Layoff date |
| # Laid Off | Employees laid off |
| % Laid Off | % of workforce |
| $ Change 5D | Price change after 5 days |
| % Change 5D | Return after 5 days |
| $ Change 1Y | Price change after 1 year |
| % Change 1Y | Return after 1 year |

---

##  Streamlit Dashboard

The Streamlit app provides:
- Filters by ticker, date, and layoff size
- Scatter plots with regression lines
- Correlation heatmap
- Weighted and unweighted return statistics
- Raw data table

It lets users interactively explore how layoff size relates to stock performance.

---

## Running the Project

Install dependencies:
```bash
pip install pandas yfinance streamlit altair numpy requests
```

Run the pipeline:
```bash
python clean_layoff_data.py
python layoff_vs_immediate_integration.py
python 1y_add.py
```

Launch the dashboard:
```bash
streamlit run app.py
```

---
 
