# 🎵 Spotify Top 50 World — Power BI Dashboard

<div align="center">

[![GitHub](https://img.shields.io/badge/Author-Syed%20Mohd%20Altamash-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/syedaltamash-analytics)

![Power BI](https://img.shields.io/badge/Power%20BI-Report-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![Spotify](https://img.shields.io/badge/Spotify-Top%2050%20World-1DB954?style=for-the-badge&logo=spotify&logoColor=white)
![DAX](https://img.shields.io/badge/DAX-Measures-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)

</div>

An interactive **Power BI dashboard** analyzing Spotify's **Top 50 World** chart data. The report tracks song popularity, artist performance, chart positions, album types, and listening trends across a multi-page layout with full navigation.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Report Pages](#report-pages)
- [Dataset](#dataset)
- [DAX Measures](#dax-measures)
- [Project Structure](#project-structure)
- [How to Open](#how-to-open)
- [Key Insights](#key-insights)
- [Technologies Used](#technologies-used)
- [Author](#author)

---

## Overview

This dashboard was built on Spotify's global Top 50 chart dataset and provides a 360° view of music trends — from which artists dominate the chart to how song duration and explicitness affect popularity. The report features a custom-designed **Home page** with full page navigation, and three dedicated analysis pages.

**Dashboard highlights:**
- KPI cards for total songs, distinct artists, avg popularity & avg duration
- Monthly trend analysis of chart entries and popularity scores
- Explicit vs non-explicit song breakdown
- Album type distribution by popularity
- Artist-level deep dive with average chart position ranking
- Song-level detail with release year, duration, and peak popularity

---

## Report Pages

### 🏠 Home
Landing page with a branded background and navigation buttons to all three report sections.

---

### 📊 Overview
A high-level summary of the entire dataset.

| Visual | Description |
|---|---|
| KPI Cards (×4) | Distinct Songs, Distinct Artists, Avg Popularity, Avg Song Duration |
| Clustered Bar Chart | Top artists by number of distinct songs |
| Clustered Bar Chart | Top songs by total popularity |
| Area Chart | Popularity trend over months |
| Clustered Column Chart | Songs released per month |
| Donut Chart | Explicit vs Non-Explicit song split |
| Donut Chart | Album type distribution by explicit content |
| Donut Chart | Distinct songs by year |
| Donut Chart | Average popularity by album type |
| Slicers | Song filter, dynamic slicer option |

---

### 🎤 Artists
An in-depth look at artist-level performance.

| Visual | Description |
|---|---|
| Clustered Bar Chart | Artists by distinct songs on chart |
| Clustered Bar Chart | Artists by total popularity score |
| Clustered Bar Chart | Artists by average chart position |
| Detail Table | Song-level breakdown: release year, month, album type, avg duration, avg & max popularity |
| Slicer | Filter by song name |

---

### 🎵 Songs
Song-level performance and chart tracking.

| Visual | Description |
|---|---|
| Clustered Bar Chart | Songs by number of distinct artists featured |
| Clustered Bar Chart | Songs by total popularity |
| Clustered Bar Chart | Songs by total chart position (lower = better) |
| Detail Table | Artist breakdown: album type, distinct songs, chart positions, avg tracks, no. of albums, avg popularity |
| Slicer | Filter by song name |

---

## Dataset

**Table:** `Top-50-world`

| Column | Description |
|---|---|
| `song` | Song title |
| `artist` | Artist name |
| `album_type` | Type of release (single, album, etc.) |
| `release_date` | Date of release |
| `popularity` | Spotify popularity score (0–100) |
| `position` | Chart position (1–50) |
| `duration_ms` | Song duration in milliseconds |
| `is_explicit` | Whether the song contains explicit content |
| `total_tracks` | Total tracks in the album |

---

## DAX Measures

All custom measures were written in DAX and defined in the `Top-50-world` table:

| Measure | Formula / Logic |
|---|---|
| `Total Songs` | `COUNTROWS('Top-50-world')` |
| `Distinct Songs` | `DISTINCTCOUNT([song])` |
| `Distinct Artists` | `DISTINCTCOUNT([artist])` |
| `Average Popularity` | `AVERAGE([popularity])` |
| `Max Popularity` | `MAX([popularity])` |
| `Min Popularity` | `MIN([popularity])` |
| `Average Song Duration (Minutes)` | `AVERAGE([duration_ms]) / 60000` |
| `Max Song Duration (Minutes)` | `MAX([duration_ms]) / 60000` |
| `Min Song Duration (Minutes)` | `MIN([duration_ms]) / 60000` |
| `Explicit Songs Count` | `CALCULATE(COUNTROWS(...), is_explicit = TRUE)` |
| `Non-Explicit Songs Count` | `CALCULATE(COUNTROWS(...), is_explicit = FALSE)` |
| `Explicit %` | `DIVIDE([Explicit Songs Count], [Total Songs], 0)` |
| `Average Chart Position` | `AVERAGE([position])` |
| `Average Album Tracks` | `AVERAGE([total_tracks])` |
| `Number of Albums` | `DISTINCTCOUNT([album_type])` |
| `Latest Release Year` | `MAX(YEAR([release_date]))` |
| `Oldest Release Year` | `MIN(YEAR([release_date]))` |
| `Top 10 Entries` | `CALCULATE(COUNTROWS(...), position <= 10)` |
| `Top 5 Entries` | `CALCULATE(COUNTROWS(...), position <= 5)` |

---

## Project Structure

```
├── Spotify_report.pbix         # Main Power BI report file
├── data/
│   └── Top-50-world.csv        # Source dataset (Spotify Top 50 World)
└── README.md
```

---

## How to Open

1. Install **[Power BI Desktop](https://powerbi.microsoft.com/desktop/)** (free)
2. Clone or download this repository
   ```bash
   git clone https://github.com/syedaltamash-analytics/spotify-powerbi-dashboard.git
   ```
3. Open `Spotify_report.pbix` in Power BI Desktop
4. If prompted, update the data source path to your local CSV location
5. Click **Refresh** to reload the data

---

## Key Insights

- 🎯 **KPI snapshot** — Total distinct songs, artists, average popularity and avg song duration visible at a glance on the Overview page
- 📈 **Trending artists** — The Artists page reveals which artists have the most chart entries and highest average popularity scores
- 🏆 **Chart dominance** — Average chart position metric shows which artists consistently rank in the top spots
- 🔞 **Explicit content analysis** — Donut charts break down explicit vs clean songs and how explicitness correlates with album type
- 📅 **Release trends** — Monthly and yearly breakdowns show when the most charting songs were released
- ⏱️ **Duration patterns** — Average song duration tracked across artists and songs to spot listener preferences

---

## Technologies Used

![Power BI](https://img.shields.io/badge/Power%20BI-Desktop-F2C811?style=flat&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-Custom%20Measures-0078D4?style=flat&logo=microsoft&logoColor=white)
![Spotify](https://img.shields.io/badge/Data%20Source-Spotify%20Top%2050-1DB954?style=flat&logo=spotify&logoColor=white)

---

## 👤 Author

<div align="center">

### Syed Mohd Altamash

*Data Science & Analytics Enthusiast*

[![GitHub](https://img.shields.io/badge/GitHub-syedaltamash--analytics-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/syedaltamash-analytics)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Syed%20Mohd%20Altamash-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/syedaltamash-analytics)

</div>

---
