# 🚗 Uber NYC Data Analysis

Exploratory data analysis of Uber pickup activity in New York City (January–June 2015), using a 100,000-record sample to uncover temporal demand patterns, dispatching base performance, airport-specific demand, and geospatial pickup distribution.

---

## 📊 Project Overview

This project analyzes NYC Uber ride data to answer questions like:
- When are Uber pickups at their peak (by hour, day, and month)?
- Which dispatching bases handle the most trips?
- How does airport demand differ between JFK and LaGuardia?
- Where are the pickup hotspots across New York City?

---

## 📁 Project Structure

```
Uber_Data_Analysis/
│
├── Datasets/
│   ├── uber-raw-data-janjune-15_sample.csv   # Primary dataset (100k rows)
│   ├── uber-raw-data-janjune-15.csv
│   ├── uber-raw-data-apr14.csv
│   ├── uber-raw-data-aug14.csv
│   ├── uber-raw-data-jul14.csv
│   ├── uber-raw-data-jun14.csv
│   ├── uber-raw-data-may14.csv
│   ├── uber-raw-data-sep14.csv
│   ├── other-FHV-services_jan-aug-2015.csv
│   └── ... (other FHV operator datasets)
│
├── Uber_Data_Analysis.ipynb                  # Main analysis notebook
├── Uber_Data_Analysis_Report.pdf              #Analysis report
└── README.md
```

---

## 📦 Dataset

**Source:** [Uber Pickups in New York City — Kaggle](https://www.kaggle.com/datasets/fivethirtyeight/uber-pickups-in-new-york-city)

**Primary File:** `uber-raw-data-janjune-15_sample.csv`

| Column | Description |
|--------|-------------|
| `Dispatching_base_num` | TLC base company code dispatching the trip |
| `Pickup_date` | Date and time of the pickup |
| `Affiliated_base_num` | TLC base company code affiliated with the trip |
| `locationID` | TLC Taxi Zone ID of the pickup location |

**Engineered Features:**

| Feature | Description |
|---------|-------------|
| `month` | Extracted month name from `Pickup_date` |
| `day` | Day of the week extracted from `Pickup_date` |
| `hour` | Hour of the day (0–23) extracted from `Pickup_date` |

---

## 🔍 Key Analyses & Visualizations

### 1. 📅 Uber Pickups by Month & Day of Week
A grouped bar chart showing pickup counts broken down by month (Jan–Jun 2015) and day of the week.

**Highlights:**
- May has the highest overall demand, especially on Saturdays (~3,519 pickups)
- January is the slowest month across all days
- Weekends (Saturday & Sunday) consistently outperform weekdays

---

### 2. ⏰ Hourly Rush by Day of Week
A multi-line chart showing how pickup volume changes by hour of the day, split by day of week.

**Highlights:**
- All days follow a **bimodal pattern**: morning shoulder peak (~8–9 AM) + dominant evening peak (6 PM–midnight)
- Lowest demand: **3–5 AM** on all days
- Saturday night extends demand past midnight, reflecting weekend nightlife patterns

---

### 3. 🏆 Dispatching Base Pareto Analysis
A Pareto chart displaying trip volume by dispatching base with a cumulative percentage overlay.

**Highlights:**
- **B02764** accounts for ~40% of all trips
- The top 3 bases (**B02764, B02682, B02617**) collectively handle ~80% of all pickups — confirming the Pareto Principle
- Bases B02835 and B02836 contribute negligibly

---

### 4. ✈️ Airport Demand — JFK vs LGA
An area chart comparing hourly trip volume at JFK and LaGuardia airports.

**Highlights:**
- **LaGuardia (LGA)** consistently outperforms JFK throughout most hours
- LGA peaks at ~300+ trips by hour 22; JFK reaches ~165
- Both airports share a 3–4 AM trough
- LGA is more volatile; JFK shows a steadier climb through the day

---

### 5. 🗺️ Geospatial Heatmap (NYC)
An interactive time-lapse heatmap built with **Folium + HeatMapWithTime**, showing how pickup hotspots shift across NYC by hour.

- Centered on NYC (40.7128°N, 74.0060°W)
- Visualizes demand density across all 24 hours
- Highlights Midtown Manhattan and major transit hubs as peak zones

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| Python 3.11 | Core language |
| Pandas | Data manipulation & feature engineering |
| NumPy | Numerical operations |
| Plotly Express | Interactive visualizations |
| Folium | Geospatial heatmap |
| Matplotlib / Seaborn | Supplementary static plots |
| Jupyter Notebook | Development environment |

---

## ⚙️ Setup & Usage

### Prerequisites
```bash
pip install pandas numpy plotly folium matplotlib seaborn
```

### Run the Notebook
```bash
jupyter notebook Uber_Data_Analysis.ipynb
```

> **Note:** Update the file path in the data loading cell to match your local dataset location:
> ```python
> uber_15 = pd.read_csv("Datasets/uber-raw-data-janjune-15_sample.csv")
> ```

---

## 📈 Summary of Findings

| Metric | Result |
|--------|--------|
| Busiest Month | **May** |
| Busiest Day | **Saturday** |
| Peak Hours | **6 PM – 1 AM** |
| Quietest Hours | **3 AM – 5 AM** |
| Top Base | **B02764** (~40% of trips) |
| 80% Trip Share | Top 3 bases |
| Busier Airport | **LGA > JFK** for most hours |

---

## 📝 Full Report

See [`Uber_Data_Analysis_Report.pdf`](./Uber_Data_Analysis_Report.pdf) for the complete written analysis with chart interpretations, key takeaways, and business insights.

---

## 🙋 Author

**Alekhya Ayinam**  
Aspiring Data Analyst | Python · SQL · Data Visualization

---

## 📄 License

This project is for educational and portfolio purposes. Dataset sourced from [FiveThirtyEight via Kaggle](https://www.kaggle.com/datasets/fivethirtyeight/uber-pickups-in-new-york-city).
