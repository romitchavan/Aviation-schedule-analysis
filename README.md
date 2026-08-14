# Indian Aviation Analysis

An end-to-end data analysis project exploring Indian domestic aviation schedules (2019–2024) — covering market share, route network structure, monopoly vs. competitive routes, and time-based flight patterns. Built using **Excel** for data preprocessing and **Power BI** for data modeling, DAX measures, and dashboard design.

---

## Overview

This project analyzes a dataset of **33,734 Indian domestic flight schedule records** to answer key questions about airline market dominance, route competitiveness, and operational timing patterns.

The workflow is split across two tools by design:
- **Excel** — data cleaning, derived columns, and creation of an exploded day-level table (since schedules can span multiple days of the week)
- **Power BI** — data modeling (table relationships), all DAX measures, and the final 2-page interactive dashboard

The result is a dashboard that lets a user drill from a macro view (which airline dominates overall) down to a micro view (which airline dominates a *specific* route), while also surfacing time-of-day and day-of-week demand patterns.

📊 Jump to: [Dashboard Screenshots](#dashboard-screenshots) · [KPI Summary](#kpi-summary) · [Business Questions Solved](#business-questions-solved) · [Key Insights](#key-insights)

---

## Dataset

- **Source**: Kaggle (Indian domestic aviation schedules)
- **Size**: 33,734 rows
- **Columns**: airline, flightNumber, origin, destination, daysOfWeek, scheduledDepartureTime, scheduledArrivalTime, validFrom, validTo, and derived columns added during preprocessing
- **Time range**: 2019–2024 (2025 data excluded from trend analysis as it is a partial-year pull)

---

## Data Model

Two tables, linked via a synthetic ID column:

| Table | Description |
|---|---|
| `Schedule_Main` | Schedule-level data — one row per unique flight schedule |
| `Schedule_DayLevel` | Exploded table — one row per operating day, derived from the comma-separated `daysOfWeek` values in `Schedule_Main` |

The day-level table exists because a single schedule can legitimately operate on multiple different days of the week — this is genuine schedule variation, not dirty data.

---

## Project Workflow

1. **Data collection** — Sourced the raw domestic aviation schedule dataset (33,734 rows) from Kaggle.
2. **Data preprocessing (Excel)** — Cleaned the raw data, added derived columns (e.g., flight duration, overnight flag, time-of-day bucket), and built an exploded day-level table to correctly represent multi-day schedules.
3. **Data modeling (Power BI)** — Imported the cleaned data, built the `Schedule_Main` and `Schedule_DayLevel` tables, and established a single-direction relationship between them.
4. **DAX measure development** — Wrote measures for market share, top airline identification, monopoly route detection, and year-over-year growth.
5. **Dashboard design** — Designed a 2-page report: Page 1 focused on market share and route dominance, Page 2 focused on network depth and time-based patterns, with synced slicers across both pages.
6. **Documentation & publishing** — Documented the preprocessing steps, DAX measures, and findings, and published the project to GitHub as a portfolio piece.

---

## Dashboard Screenshots

- [Page 1 — Market Share & Routes](https://github.com/romitchavan/Aviation-schedule-analysis/blob/main/Screenshots/Dashboard_Page_1.png)
- [Page 2 — Network Depth & Time Patterns](https://github.com/romitchavan/Aviation-schedule-analysis/blob/main/screenshots/Dashboard_Page_2.png)


---

## KPI Summary

| KPI | Value |
|---|---|
| Total Flights | 34K |
| Total Airlines | 14 |
| Total Routes | 1,423 |
| Monopoly Routes % | 44.1% |
| Market Share Leader | IndiGo — 56.5% |
| Overnight Flight % | 2.1% |

---

## Business Questions Solved

1. Which airline operates the highest number of flights?
2. What is each airline's share of total flights?
3. Which airline dominates a specific route?
4. What are the top 20 busiest routes?
5. How many routes are monopolies vs. competitive?
6. How are flights distributed across time of day?
7. Which airlines operate overnight flights?
8. How do flight volumes vary by day of week?
9. What is the average flight duration by route and airline?

---

## Key Insights

**Market share by airline (top 10):**

| Rank | Airline | Share |
|---|---|---|
| 1 | IndiGo | 56.5% |
| 2 | SpiceJet | 10.0% |
| 3 | Air India | 9.24% |
| 4 | GoAir | 5.50% |
| 5 | Air India Express | 5.34% |
| 6 | Vistara | 4.49% |
| 7 | Alliance Air (India) | 4.43% |
| 8 | Jet Airways | 1.37% |
| 9 | Akasa Air | 1.22% |
| 10 | TruJet | 0.89% |

- **Route competitiveness**: 627 routes (18.65%) are monopoly routes — served by a single airline — while 2,735 routes (81.35%) are competitive, served by two or more airlines.
- **Route network reach**: IndiGo, SpiceJet, and Alliance Air (India) are also the top 3 airlines by number of routes covered, closely mirroring their flight-volume dominance.
- **Day-of-week demand**: Flight volume is fairly consistent across the week, with only minor variation. Busiest to slowest order: Saturday → Tuesday → Thursday → Friday → Sunday → Monday.
- **Time-of-day demand**: Morning, afternoon, and evening account for the large majority of flight volume, while night and early-morning slots see comparatively little activity.
- **Overnight operations**: Only 2.1% of flights are overnight, indicating the Indian domestic market is overwhelmingly daytime-driven.
- **Multi-year trend**: From 2019 to 2024, IndiGo has consistently held the dominant position in India's domestic aviation market, with its lead widening over the period.

---

## Project Outcome

- Delivered a fully interactive, 2-page Power BI dashboard answering 9 distinct business questions about India's domestic aviation market.
- Identified that nearly half of all routes (44.1%) are effectively monopolies, and pinpointed IndiGo as the dominant carrier both by flight volume (56.5%) and route coverage.
- Correctly modeled multi-day flight schedules using an exploded day-level table, avoiding the common pitfall of miscounting schedules with variable weekly patterns.
- Built a reusable, well-documented data model and DAX measure library that can be extended to future years of data as they become available.
- Produced a portfolio-ready project demonstrating the full analytics workflow — from raw data to a polished, decision-ready dashboard.

---

## Skills Demonstrated

- Data cleaning and preprocessing in Excel (formula-based transformations, derived columns)
- Data restructuring (exploding multi-value fields into a normalized day-level table)
- Data modeling in Power BI (table relationships, filter context management)
- DAX measure development (CALCULATE, ALL, DISTINCTCOUNT, conditional logic without time-intelligence functions)
- Dashboard design and UX (multi-page layout, synced slicers, consistent color theming)
- Analytical thinking (macro-to-micro drill-down design, monopoly vs. competitive market segmentation)
- Technical documentation and version control (Git/GitHub)

---

## Tools Used

- **Excel** — data preprocessing, derived columns, exploded day-level table creation
- **Power BI** — data modeling, DAX measures, dashboard design
- **GitHub** — version control and project hosting

---

## Author

**Romit Chavan**
GitHub: [@romitchavan](https://github.com/romitchavan)
Repository: [Aviation-schedule-analysis](https://github.com/romitchavan/Aviation-schedule-analysis)
