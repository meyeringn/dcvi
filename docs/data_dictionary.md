# DCVI Data Dictionary

This document defines every variable used in the Disability Climate Vulnerability Index, including its source, download location, table or layer reference, geographic resolution, and transformation notes.

-----

## Dimension 1: Disability Prevalence Score (DPS)

### Variable: % Population with Any Disability

- **Source:** U.S. Census Bureau American Community Survey (ACS) 5-Year Estimates
- **Table:** S1810 — Disability Characteristics
- **Column:** S1810_C03_001E (% with a disability, total civilian noninstitutionalized population)
- **Geographic resolution:** Census tract
- **Download:** [data.census.gov](https://data.census.gov) → Table S1810 → Select Geography: Census Tracts → All States
- **Transformation:** No transformation needed; values are already percentages 0–100
- **Weight in DPS:** 30%

### Variable: % Population with Ambulatory Difficulty

- **Source:** ACS 5-Year Estimates
- **Table:** S1810
- **Column:** S1810_C03_004E (% with ambulatory difficulty)
- **Geographic resolution:** Census tract
- **Transformation:** No transformation needed
- **Weight in DPS:** 15%

### Variable: % Population with Self-Care Difficulty

- **Source:** ACS 5-Year Estimates
- **Table:** S1810
- **Column:** S1810_C03_006E (% with self-care difficulty)
- **Geographic resolution:** Census tract
- **Transformation:** No transformation needed
- **Weight in DPS:** 10%

### Variable: % Population with Independent Living Difficulty

- **Source:** ACS 5-Year Estimates
- **Table:** S1810
- **Column:** S1810_C03_007E (% with independent living difficulty)
- **Geographic resolution:** Census tract
- **Transformation:** No transformation needed
- **Weight in DPS:** 10%

### Variable: % Disability Population Below Poverty Line

- **Source:** ACS 5-Year Estimates
- **Table:** B18130 — Poverty Status in the Past 12 Months by Disability Status and Type
- **Column:** Calculated as (B18130_004E + B18130_011E + B18130_018E + B18130_025E + B18130_032E + B18130_039E) / B18130_001E
- **Geographic resolution:** Census tract
- **Transformation:** Calculate as a percentage of total population with disability
- **Weight in DPS:** 35%
- **Notes:** This is the highest-weighted DPS variable because economic vulnerability substantially amplifies climate risk for Disabled people

-----

## Dimension 2: Climate Hazard Exposure Score (CHES)

### Variable: Extreme Heat Expected Annual Loss

- **Source:** FEMA National Risk Index (NRI)
- **Layer:** Heat Wave — Expected Annual Loss
- **Field:** HWAVE_EALA (Expected Annual Loss — Agriculture, Building, and Population combined)
- **Geographic resolution:** Census tract
- **Download:** [hazards.fema.gov/nri/map](https://hazards.fema.gov/nri/map) → Download → Census Tract level → All Counties
- **Transformation:** Normalize to 0–100 within national dataset using min-max scaling
- **Weight in CHES:** 30%

### Variable: Flood Expected Annual Loss

- **Source:** FEMA National Risk Index
- **Layer:** Riverine Flooding — Expected Annual Loss
- **Field:** RFLD_EALA
- **Geographic resolution:** Census tract
- **Transformation:** Normalize to 0–100 using min-max scaling
- **Weight in CHES:** 25%

### Variable: Wildfire Risk Rating

- **Source:** FEMA National Risk Index
- **Layer:** Wildfire — Risk Index Score
- **Field:** WFIR_RISKS
- **Geographic resolution:** Census tract
- **Transformation:** Already scored 0–100 in NRI data
- **Weight in CHES:** 10%

### Variable: Winter Storm Risk Rating

- **Source:** FEMA National Risk Index
- **Layer:** Winter Storm — Risk Index Score
- **Field:** WNTST_RISKS
- **Geographic resolution:** Census tract
- **Transformation:** Already scored 0–100 in NRI data
- **Weight in CHES:** 10%

### Variable: Urban Heat Island Intensity

- **Source:** EPA EnviroAtlas / Landsat Land Surface Temperature (LST)
- **Download:** [epa.gov/enviroatlas](https://www.epa.gov/enviroatlas) → EnviroAtlas Data → Urban Heat Island
- **Geographic resolution:** Census block group (aggregated to tract)
- **Transformation:** Calculate mean summer LST deviation from rural baseline (°F); normalize to 0–100
- **Weight in CHES:** 25%
- **Notes:** For cities without EnviroAtlas coverage, USGS Landsat LST data can be substituted

-----

## Dimension 3: Adaptive Capacity Score (ACS)

*Note: ACS scores are inverted — higher raw values indicate lower adaptive capacity, meaning higher vulnerability. Scores are inverted before weighting.*

### Variable: % Households without Vehicle

- **Source:** ACS 5-Year Estimates
- **Table:** B08201 — Household Size by Vehicles Available
- **Column:** B08201_002E / B08201_001E (% zero-vehicle households)
- **Geographic resolution:** Census tract
- **Transformation:** Already a percentage; invert for scoring (higher = more vulnerable)
- **Weight in ACS:** 20%

### Variable: Distance to Nearest Cooling Center (km)

- **Source:** Local government open data (varies by city)
  - Philadelphia: [opendataphilly.org](https://opendataphilly.org) → “Cooling Centers”
  - National: No standardized federal dataset exists; use city OEM data
- **Geographic resolution:** Calculated from tract centroid to nearest cooling center point
- **Transformation:** Calculate using haversine distance; normalize to 0–100 (higher distance = more vulnerable)
- **Weight in ACS:** 20%
- **Notes:** This is the most data-scarce indicator. If cooling center data is unavailable for a tract’s municipality, flag as missing and weight remaining indicators proportionally.

### Variable: Distance to Nearest Emergency Medical Facility (km)

- **Source:** CMS Medicare Provider Data
- **Download:** [data.cms.gov](https://data.cms.gov) → Provider of Services File
- **Geographic resolution:** Calculated from tract centroid to nearest facility point
- **Transformation:** Calculate using haversine distance; normalize to 0–100
- **Weight in ACS:** 20%

### Variable: Broadband Access Rate

- **Source:** FCC Broadband Data Collection (BDC)
- **Download:** [broadbandmap.fcc.gov](https://broadbandmap.fcc.gov)
- **Geographic resolution:** Census block (aggregated to tract)
- **Transformation:** % of households with fixed broadband access at 25/3 Mbps or faster; invert for scoring
- **Weight in ACS:** 15%

### Variable: % Rental Housing

- **Source:** ACS 5-Year Estimates
- **Table:** B25003 — Tenure
- **Column:** B25003_003E / B25003_001E (% renter-occupied)
- **Geographic resolution:** Census tract
- **Transformation:** Already a percentage; used as housing instability proxy
- **Weight in ACS:** 15%

### Variable: Healthcare Coverage Rate

- **Source:** ACS 5-Year Estimates
- **Table:** S2701 — Selected Characteristics of Health Insurance Coverage
- **Column:** S2701_C03_001E (% without health insurance coverage)
- **Geographic resolution:** Census tract
- **Transformation:** Invert (higher uninsured rate = more vulnerable)
- **Weight in ACS:** 10%

-----

## Composite DCVI Score

```
DPS = (var1 × 0.30) + (var2 × 0.15) + (var3 × 0.10) + (var4 × 0.10) + (var5 × 0.35)
CHES = (var1 × 0.30) + (var2 × 0.25) + (var3 × 0.10) + (var4 × 0.10) + (var5 × 0.25)
ACS_inv = (var1_inv × 0.20) + (var2_inv × 0.20) + (var3_inv × 0.20) + (var4_inv × 0.15) + (var5 × 0.15) + (var6_inv × 0.10)

DCVI = (DPS × 0.40) + (CHES × 0.35) + (ACS_inv × 0.25)
```

All dimension scores and the final DCVI score are on a 0–100 scale, normalized within the national dataset.

-----

## Notes on Data Vintage

All ACS data should use the most recent 5-year estimates available. FEMA NRI data is updated periodically; check [hazards.fema.gov/nri/](https://hazards.fema.gov/nri/) for the current release. FCC BDC data is released biannually.

For reproducibility, document the vintage of each dataset used in your analysis in a `data/metadata.json` file.
