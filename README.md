# Vegetation Change & Forest Dynamics in Western Canada

This project investigates vegetation disturbance and forest cover change across two study areas in western Canada using freely available satellite imagery and open-source R tools. It demonstrates a full remote sensing workflow — from raw data ingestion and preprocessing through time series analysis, change detection, and interpretation.

---

##  Study Areas

| Area | Province | Analysis Focus |
|---|---|---|
| Yellowhead Country | Alberta | MODIS NDVI time series & BFAST disturbance detection |
| Williams Lake | British Columbia | Landsat land cover change & forest area dynamics |

---

##  Data Sources

- **MODIS MOD13Q1** — 16-day NDVI composite, 250 m resolution, 2001–2020
  - Source: [NASA LP DAAC](https://lpdaac.usgs.gov/products/mod13q1v006/)
- **Virtual Land Cover Engine (VLCE)** — Annual Landsat-derived land cover, 30 m resolution, 1984–2016
  - Source: Hermosilla et al. (2018), *Canadian Journal of Remote Sensing*

---

##  Methods

### Part 1: MODIS NDVI Time Series (Alberta)
- Loaded and parsed a 460-layer MODIS NDVI time series
- Computed pixel-wise median NDVI composite for baseline visualization
- Extracted average NDVI for two regions of interest (ROIs)
- Analyzed growing season (May–September) NDVI patterns
- Applied **BFAST Monitor** to detect structural breaks in vegetation greenness and distinguish between permanent loss and recovering disturbances

### Part 2: Land Cover Change (BC)
- Loaded a 33-year Landsat land cover time series (12 classes)
- Reclassified land cover into a binary forested / non-forested scheme
- Computed year-on-year lagged differences to identify annual forest gain and loss pixels
- Calculated annual forest gain, loss, and net change in hectares
- Visualized temporal trends in forest area dynamics with ggplot2

---

##  Key Results

- **ROI A (Alberta):** BFAST detected an abrupt NDVI decline around 2011 with no subsequent recovery, consistent with a stand-replacing disturbance such as wildfire or clear-cut harvesting
- **ROI B (Alberta):** A disturbance detected around 2008 was followed by a gradual NDVI increase, indicating natural vegetation recovery
- **Williams Lake (BC):** Clear cyclical patterns of forest loss (harvesting) and gain (regeneration) are visible across the 33-year record, with net forest change varying considerably year to year

---

---

##  R Packages Used

| Package | Purpose |
|---|---|
| `terra` | Raster data loading, processing, and analysis |
| `sf` | Vector spatial data |
| `bfast` | Break detection in time series (BFAST Monitor) |
| `dplyr` / `tidyr` | Data manipulation |
| `lubridate` | Date parsing |
| `stringr` | String manipulation for filename parsing |
| `ggplot2` | Data visualization |

---


---

## 📚 References

- Didan, K. (2015). *MOD13Q1 MODIS/Terra Vegetation Indices 16-Day L3 Global 250m SIN Grid V006*. NASA EOSDIS LP DAAC.
- Hermosilla, T., et al. (2018). Disturbance-informed annual land cover classification maps of Canada's forested ecosystems. *Canadian Journal of Remote Sensing*, 44(1), 67–87.
- Verbesselt, J., Zeileis, A., & Herold, M. (2012). Near real-time disturbance detection using satellite image time series. *Remote Sensing of Environment*, 123, 98–108.

---
