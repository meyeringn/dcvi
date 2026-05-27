# Philadelphia Methodology Notes

This document details data sourcing decisions, known gaps, and interpretive notes specific to the Philadelphia, PA case study for the Disability Climate Vulnerability Index.

-----

## Why Philadelphia?

Philadelphia is a high-stakes case study for disability and climate vulnerability for four reasons:

1. **High disability prevalence.** Approximately 300,000 Philadelphia residents — roughly 19% of the city’s population — have a disability per ACS 2022 estimates. This is above the national average of 13%.
1. **Concentrated poverty.** Philadelphia has one of the highest poverty rates of any large American city (over 23% as of 2022). Poverty and disability co-occur at high rates; this amplifies climate vulnerability significantly.
1. **Aging housing stock.** Over 65% of Philadelphia’s housing units were built before 1980. Poor insulation and lack of central air conditioning in older rowhouses is a direct heat risk.
1. **Rapid urban warming.** Philadelphia is among the fastest-warming cities on the East Coast. The city has experienced multiple extreme heat events in recent years and its urban heat island effect is pronounced in dense North and West Philadelphia neighborhoods.

-----

## Data Sources Used for Philadelphia

|Dimension|Variable                  |Source Used                          |Notes                                             |
|---------|--------------------------|-------------------------------------|--------------------------------------------------|
|DPS      |Disability prevalence     |ACS 2022 5-Year, Table S1810         |Tract-level, Philadelphia County                  |
|DPS      |Disability poverty        |ACS 2022 5-Year, Table B18130        |Tract-level, Philadelphia County                  |
|CHES     |Extreme heat EAL          |FEMA NRI 2023 Release                |Tract-level download                              |
|CHES     |Flood EAL                 |FEMA NRI 2023 Release                |Tract-level download                              |
|CHES     |UHI intensity             |EPA EnviroAtlas Philadelphia Metro   |Block group, aggregated to tract                  |
|ACS      |Zero-vehicle households   |ACS 2022 5-Year, Table B08201        |Tract-level                                       |
|ACS      |Cooling center distance   |OpenDataPhilly — Cooling Centers 2023|Point data; haversine distance from tract centroid|
|ACS      |Emergency medical distance|CMS Provider of Services 2024        |Hospitals and ERs only                            |
|ACS      |Broadband access          |FCC BDC June 2024 Release            |Block level, aggregated to tract                  |
|ACS      |Rental housing            |ACS 2022 5-Year, Table B25003        |Tract-level                                       |
|ACS      |Health insurance          |ACS 2022 5-Year, Table S2701         |Tract-level                                       |

-----

## Known Data Gaps

### Cooling Center Data

OpenDataPhilly’s cooling center dataset reflects officially designated City OEM cooling sites. It does not include:

- Library branches (which informally serve as cooling spaces)
- Community centers with inconsistent seasonal hours
- Private cooling sites (e.g., some faith communities open their facilities)

**Impact:** Cooling center distance may be overstated in some tracts. Treat as a conservative estimate of access.

### UHI Data

EPA EnviroAtlas UHI data for Philadelphia is based on Landsat imagery from a specific summer period. It may not capture year-over-year variation or the increased UHI intensity observed during recent extreme heat events.

**Impact:** CHES scores may underestimate heat risk in rapidly developing or densifying areas.

### Disability Data Reliability

ACS disability estimates carry significant margins of error at the tract level, particularly for tracts with small populations. Tracts with populations under 500 should be interpreted with caution.

**Impact:** DPS scores in low-population tracts (especially Center City) may be unreliable.

-----

## Preliminary High-Priority Tracts

Based on available data, the following Philadelphia census tracts are likely to score in the Critical or High DCVI tier. Full scored results will be published in a subsequent release.

|Census Tract|Zip Code|Neighborhood                        |Preliminary Risk Tier|Key Factors                                              |
|------------|--------|------------------------------------|---------------------|---------------------------------------------------------|
|036100      |19132   |North Philadelphia West             |🔴 Critical           |High disability prevalence, high UHI, low vehicle access |
|037800      |19133   |North Philadelphia East             |🔴 Critical           |High disability + poverty, limited cooling infrastructure|
|013400      |19143   |Kingsessing / Southwest Philadelphia|🟠 High               |Ambulatory disability concentration, heat island         |
|017900      |19134   |Port Richmond                       |🟠 High               |Aging population, flood exposure, high renter rate       |
|029600      |19139   |West Philadelphia / Haddington      |🟠 High               |High poverty + disability, aging housing stock           |

*Note: Census tract numbers are approximate and subject to correction in full data release.*

-----

## Interpretive Notes

**The paradox of transit access:** Philadelphia’s relatively high transit coverage (82% of residents within ¼ mile of frequent service) partially buffers the city’s Adaptive Capacity score. However, SEPTA’s chronic elevator and escalator failures significantly undermine this advantage for Disabled riders specifically — an effect not fully captured by coverage statistics alone. See [UpLift](https://github.com/meyeringn/uplift-transit) for analysis of this failure rate.

**North vs. South Philadelphia divide:** North Philadelphia consistently scores worse across all three DCVI dimensions than South Philadelphia, even controlling for overall poverty rates. This reflects deeper disinvestment, older housing stock, and higher disability prevalence in specific North Philadelphia zip codes.

**The Center City exception:** Center City Philadelphia has low disability prevalence and high adaptive capacity (good transit, healthcare access, low poverty). However, it has high UHI intensity due to dense built environment and limited tree canopy. This means it can score moderate on CHES while scoring low on DPS — a profile that will likely rank as Moderate overall but warrants attention for heat risk to Disabled visitors and workers.

-----

## Future Work

- Full tract-level DCVI scoring for all 384 Philadelphia census tracts
- Comparison with Philadelphia’s existing SVI scores to identify tracts where disability vulnerability is underweighted in current federal metrics
- Time-series analysis: how has disability vulnerability changed in Philadelphia between 2010–2024 ACS vintages?
- Neighborhood-level policy brief for City Council and Mayor’s Office of Sustainability
