# SPECTO2 — Urban and Regional Economics
## Spatial Analysis of Philippine Cities

This repository contains the R workshop materials for **SPECTO2: Urban and Regional Economics**, an undergraduate economics course. The workshops introduce spatial data analysis in R using real Philippine Statistical Authority (PSA) data to explore land rent gradients, human capital distribution, and urban-regional economic networks in the Philippines.

---

## Course Context

Urban and regional economics asks: *why do cities exist, how do they grow, and what makes some places more productive than others?* These workshops give you the tools to answer those questions empirically — using actual Philippine data, real maps, and spatial statistical methods.

By the end of the three workshops, you will be able to:
- Load, clean, and join spatial data in R
- Produce publication-quality choropleth maps of Philippine cities
- Test the Alonso–Muth–Mills land rent gradient model with FIES data
- Run basic spatial econometric models
- Visualize urban-regional economic networks

---

## Workshops

| # | Week | Topic | Status |
|---|---|---|---|
| 1 | Week 3 | Mapping Philippine Cities — land rent gradients and human capital | ✅ Available |
| 2 | Week 7 | Spatial Econometrics and Road Networks | 🔜 Coming soon |
| 3 | Week 10 | Urban-Regional Economic Networks | 🔜 Coming soon |

Access the workshops at: **https://jmnariodlsu.github.io/SPECTO2_R_Workshop1/**

---

## Workshop 1 — Mapping Philippine Cities

**Topics covered:**
- Introduction to spatial data structures in R (`sf` package)
- Downloading and joining GADM shapefiles to tabular PSA data
- Choropleth maps of NCR cities using `ggplot2`
- The land rent gradient — testing the Alonso–Muth–Mills model
- Human capital distribution as a proxy for urban productivity
- Education expenditure and wage income patterns across Metro Manila

**Key concepts:**
- Land rent gradient
- Monocentric city model
- Agglomeration economies
- Human capital and urban productivity

---

## Data

The training dataset combines two PSA data sources aggregated to the city/municipality level for all 17 NCR local government units.

| File | Description |
|---|---|
| `data/ncr_city_training.RData` | R data file — loads as `ncr_city` (17 rows × 22 variables) |
| `data/ncr_city_training.csv` | Flat CSV version for inspection |

### Variable reference

| Variable | Source | Description |
|---|---|---|
| `city` | — | City/municipality name |
| `lat`, `lon` | — | City centroid coordinates (WGS84) |
| `dist_cbd_km` | — | Distance from Makati CBD (Ayala Ave), km |
| `mean_rentval` | FIES 2023 | Mean household rent value (PHP/year) |
| `mean_actrent` | FIES 2023 | Mean actual rent paid by renters |
| `mean_inc` | FIES 2023 | Mean total household income (PHP/year) |
| `mean_wage_inc` | FIES 2023 | Mean wage income (PHP/year) |
| `mean_educ_exp` | FIES 2023 | Mean education expenditure (PHP/year) |
| `rent_inc_ratio` | FIES 2023 | Rent-to-income ratio |
| `wage_inc_share` | FIES 2023 | Wage share of total income |
| `pct_renters_fies` | FIES 2023 | % households paying actual rent |
| `n_hh` | CPH 2020 | Total housing units |
| `pct_renter` | CPH 2020 | % renting house and lot |
| `pct_any_rent` | CPH 2020 | % with any rent burden |
| `pct_makeshift_wall` | CPH 2020 | % with makeshift outer walls (informality proxy) |
| `pct_strong_wall` | CPH 2020 | % with concrete/brick walls |
| `pct_makeshift_roof` | CPH 2020 | % with makeshift roof |
| `pct_college_grad` | CPH 2020 | % adults 25+ with college degree |
| `pct_some_college` | CPH 2020 | % adults 25+ with any college education |
| `pct_literate` | CPH 2020 | % literate population |
| `pct_ofw` | CPH 2020 | % overseas workers |

### Data notes
- FIES 2023 estimates are **weighted** using the `RFACT` expansion weight
- CPH 2020 education variables are restricted to **adults aged 25 and above** to avoid confounding with students still enrolled
- City coordinates are approximate centroids (WGS84)
- Distance from CBD is computed using the haversine formula with Ayala Avenue, Makati as the reference point

---

## Prerequisites

Before the workshops, make sure you have the following installed:

**Software:**
- [R](https://cran.r-project.org/) (version 4.3 or higher)
- [RStudio](https://posit.co/download/rstudio-desktop/)
- [Quarto](https://quarto.org/docs/get-started/) (for rendering workshop documents)

**R packages** (run this once in R):
```r
install.packages(c(
  "sf",          # spatial data
  "ggplot2",     # plotting
  "ggrepel",     # non-overlapping labels
  "dplyr",       # data wrangling
  "scales",      # axis formatting
  "patchwork",   # combining plots
  "geodata",     # GADM shapefiles
  "tmap"         # thematic maps (optional)
))
```

---

## How to Use

### Option 1 — Read online (recommended for most students)
Go to **https://jmnariodlsu.github.io/SPECTO2_R_Workshop1/** and click on the workshop. All outputs are pre-rendered — no R installation needed to read the notes.

### Option 2 — Run the code yourself
1. Download `data/ncr_city_training.RData` and `data/ncr_city_training.csv`
2. Download `workshop1.qmd`
3. Open RStudio → create a new project in the folder where you saved the files
4. Make sure the `data/` folder is in the same directory as the `.qmd`
5. Open `workshop1.qmd` and click **Render**, or run code chunks interactively

### Option 3 — Clone the full repository
```r
# In RStudio Terminal:
git clone https://github.com/jmnariodlsu/SPECTO2_R_Workshop1.git
```
Then open `SPECTO2_R_Workshop1.Rproj` in RStudio.

---

## References

- Alonso, W. (1964). *Location and Land Use*. Harvard University Press.
- Mills, E. S. (1967). An aggregative model of resource allocation in a metropolitan area. *American Economic Review*, 57(2), 197–210.
- Muth, R. F. (1969). *Cities and Housing*. University of Chicago Press.
- Glaeser, E. L., Scheinkman, J., & Shleifer, A. (1995). Economic growth in a cross-section of cities. *Journal of Monetary Economics*, 36(1), 117–143.
- Philippine Statistics Authority (PSA). (2023). *Family Income and Expenditure Survey 2023*. PSA.
- Philippine Statistics Authority (PSA). (2020). *Census of Population and Housing 2020*. PSA.

---

## Data Sources

- **FIES 2023** — [PSA Data Archive](https://psada.psa.gov.ph/catalog/FIES)
- **CPH 2020** — [PSA Data Archive](https://psada.psa.gov.ph/catalog/CPH)
- **GADM Shapefiles** — [gadm.org](https://gadm.org)

*Proper attribution to PSA should be made in any report or output using this data.*

---

*SPECTO2 · Urban and Regional Economics · undergraduate course*
