# Interactive Global Earthquake Explorer

An interactive geospatial dashboard analysing 998 major earthquake events (1995–2023), built with GeoPandas, Shapely and Plotly, and published as a static single-page site.

**Course:** Geospatial Big Data Analysis, M.Sc. Geoinformatics, BVIEER, Pune
**Course Coordinator:** Dr. Aravinth R
**Student:** [Your Name] · PRN: [Your PRN]

---

## Live links

| Deliverable | Link |
|---|---|
| **Live dashboard (GitHub Pages)** | https://smiley1go.github.io/Global/Earthquake_Explorer.html |
| **Reproducible notebook (Google Colab)** | https://colab.research.google.com/drive/1nUzVKm69g2dd0N1ESPMoLamSx-hmfHcc?usp=sharing |
| **This repository** | https://github.com/Smiley1Go/Global |

> Make sure the Colab notebook link above is set to **view-only / anyone with the link can view**, and that all cell outputs are visible without needing to re-run anything.

---

## What this dashboard shows

- A rotatable, zoomable 3D orthographic globe of all cleaned earthquake events, colour- and size-coded by magnitude, with hover detail (location, magnitude, depth, time)
- A toggleable hotspot layer marking the 30 most earthquake-dense 10° grid cells
- Summary indicator cards (event count, magnitude range, depth, spatial concentration)
- A magnitude-by-continent box plot and an annual event-count line chart
- A written methods, interpretation, and limitations section

---

## Dataset

- **Title:** Earthquake Dataset (1995–2023)
- **Source:** Kaggle — https://www.kaggle.com/datasets/farazrahman/earthquake
- **Publisher / author, download date, licence:** [Fill in from the dataset's Kaggle page before submission]
- **Scope:** Global earthquakes of magnitude 6.5 and above, 1995–2023 (998 events after cleaning)

---

## Methodology summary

1. Source spreadsheet read in Google Colab; column names standardised and mapped to a common schema (latitude, longitude, magnitude, depth, time, place).
2. Coordinates, magnitude, and depth coerced to numeric; invalid and duplicate rows removed (2 of 1000 original rows).
3. Cleaned table converted to a GeoPandas GeoDataFrame with Shapely Point geometries in EPSG:4326, validated for geometry type, validity, and world-extent membership.
4. Spatial concentration measured using a reproducible 10° latitude × 10° longitude grid, with a 5°/20° comparison to check scale sensitivity (the modifiable areal unit problem).
5. Interactive globe and supporting charts built with Plotly, exported as static HTML components, and assembled into a single responsive `index.html` — no server-side processing required.

## Key results

- **998** cleaned events, magnitude range **6.5–9.1** (mean 6.94), median depth **29.0 km**
- Most active 10° cell: **20°S–10°S, 160°E–170°E** (Solomon Islands–Vanuatu arc) — **80 events, 8.0%** of the dataset
- Top 5 cells together account for **26.9%** of all events
- Concentration share at other grid sizes: **5° → 3.81%**, **10° → 8.02%**, **20° → 11.02%** (top cell), illustrating scale sensitivity

## Limitations

- Dataset contains only major earthquakes (M6.5+); it is not a complete seismicity record, and the concentration map reflects major-earthquake reporting patterns rather than overall tectonic hazard or risk.
- Annual event counts may partly reflect changes in global detection and cataloguing standards over the 1995–2023 period, not only true changes in earthquake frequency.
- Roughly a third of records lack continent/country attribution, so the magnitude-by-continent chart uses a smaller subset than the full dataset.
- The 10° grid concentration index is a descriptive spatial measure, not a seismic-hazard or risk assessment.

---

## Reproducing this analysis

1. Open the Colab notebook linked above.
2. Run all cells top to bottom (Runtime → Run all). The notebook reads the Kaggle CSV, cleans it, builds the GeoDataFrame, runs the concentration analysis, and generates the globe and charts.
3. Exported Plotly HTML components and printed KPI values are used to assemble `index.html`.

## Tools used

Python · pandas · GeoPandas · Shapely · Plotly · Google Colab · GitHub Pages
