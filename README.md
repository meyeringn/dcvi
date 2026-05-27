# Disability Climate Vulnerability Index (DCVI)

> *Disabled people are among the most climate-vulnerable populations in the United States — yet almost no climate adaptation frameworks treat disability as a primary variable. This project aims to change that.*

[![Status](https://img.shields.io/badge/status-in%20development-yellow)](https://github.com/meyeringn/dcvi)
[![Audience](https://img.shields.io/badge/audience-policy%20%26%20government-blue)](https://github.com/meyeringn/dcvi)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)

-----

## 🧭 What Is This?

The **Disability Climate Vulnerability Index (DCVI)** is an open-source policy framework and data methodology that cross-references **disability prevalence** with **climate hazard exposure** and **social vulnerability** at the U.S. census tract level.

The goal: give planners, policymakers, and climate equity advocates a replicable tool to identify which communities face compounded risk — where Disabled residents are most concentrated *and* most exposed to climate hazards — so that adaptation resources reach the people who need them most.

**Philadelphia, PA** serves as the primary case study.

-----

## 🔥 The Problem

When Hurricane Katrina struck New Orleans in 2005, people with disabilities died at disproportionate rates. When Texas experienced its 2021 grid failure, Disabled residents who depended on powered medical equipment were among the first to die. When extreme heat events strike cities, Disabled people — particularly those with mobility impairments, chronic illness, or limited access to transportation — face barriers to reaching cooling centers that their non-disabled neighbors do not.

Despite this, **most federal and municipal climate adaptation frameworks do not disaggregate vulnerability data by disability status.** FEMA’s Social Vulnerability Index (SVI) includes a disability variable, but it is weighted equally among 15 other indicators — not surfaced as a priority dimension.

The DCVI treats disability as a **first-class variable** in climate vulnerability analysis.

-----

## 📐 Index Methodology

The DCVI scores each census tract on three dimensions, then produces a composite vulnerability score.

### Dimension 1: Disability Prevalence Score (DPS)

|Variable                                       |Source                             |Weight|
|-----------------------------------------------|-----------------------------------|------|
|% population with any disability               |ACS 5-Year Estimates (Table S1810) |30%   |
|% population with ambulatory difficulty        |ACS 5-Year Estimates (Table S1810) |15%   |
|% population with self-care difficulty         |ACS 5-Year Estimates (Table S1810) |10%   |
|% population with independent living difficulty|ACS 5-Year Estimates (Table S1810) |10%   |
|% disability population below poverty line     |ACS 5-Year Estimates (Table B18130)|35%   |

### Dimension 2: Climate Hazard Exposure Score (CHES)

|Variable                         |Source                       |Weight|
|---------------------------------|-----------------------------|------|
|Extreme heat expected annual loss|FEMA National Risk Index     |30%   |
|Flood expected annual loss       |FEMA National Risk Index     |25%   |
|Wildfire risk rating             |FEMA National Risk Index     |10%   |
|Winter storm risk rating         |FEMA National Risk Index     |10%   |
|Urban Heat Island intensity      |EPA EnviroAtlas / Landsat LST|25%   |

### Dimension 3: Adaptive Capacity Score (ACS) *(inverse — higher = more vulnerable)*

|Variable                                      |Source                       |Weight|
|----------------------------------------------|-----------------------------|------|
|% households without vehicle                  |ACS 5-Year Estimates         |20%   |
|Distance to nearest cooling center (km)       |Local government open data   |20%   |
|Distance to nearest emergency medical facility|CMS Provider Data            |20%   |
|Broadband access rate                         |FCC Broadband Data Collection|15%   |
|% rental housing (housing instability proxy)  |ACS 5-Year Estimates         |15%   |
|Healthcare coverage rate                      |ACS 5-Year Estimates         |10%   |

### Composite DCVI Score

```
DCVI = (DPS × 0.40) + (CHES × 0.35) + (ACS × 0.25)
```

Scores are normalized 0–100 at the national level. Tracts are then classified:

|DCVI Score|Tier      |Interpretation                                                   |
|----------|----------|-----------------------------------------------------------------|
|80–100    |🔴 Critical|Highest compound risk; priority for climate adaptation investment|
|60–79     |🟠 High    |Significant compound risk; targeted intervention warranted       |
|40–59     |🟡 Moderate|Emerging risk; monitoring and planning recommended               |
|20–39     |🟢 Low     |Lower compound risk; standard planning applies                   |
|0–19      |⚪ Minimal |Lowest compound risk                                             |

-----

## 🏙️ Philadelphia Case Study

Philadelphia offers a high-stakes case study: it is one of the most rapidly warming cities on the East Coast, has a Disabled population of approximately **300,000 residents** (ACS 2022), and faces concentrated poverty and aging housing stock in the same neighborhoods where disability prevalence is highest.

Preliminary analysis identifies the following Philadelphia zip codes as likely **Critical or High DCVI tier** based on available ACS and FEMA NRI data:

- **19132** (North Philadelphia West) — high disability prevalence, elevated heat risk, low vehicle access
- **19133** (North Philadelphia East / Kensington) — high disability + poverty concentration, limited cooling infrastructure
- **19143** (Southwest Philadelphia / Kingsessing) — significant ambulatory disability, heat island intensity
- **19134** (Port Richmond / Fishtown North) — aging population, high renter concentration, flood exposure

> 📌 *Full tract-level scoring for Philadelphia will be published in a subsequent release. See `/docs/philly_methodology_notes.md` for data sourcing details.*

-----

## 🌍 National Application

The DCVI methodology is designed to be **replicable at national scale** using publicly available federal datasets. Any municipality or researcher can apply this framework using:

- [U.S. Census Bureau American Community Survey](https://www.census.gov/programs-surveys/acs)
- [FEMA National Risk Index](https://hazards.fema.gov/nri/)
- [CDC/ATSDR Social Vulnerability Index](https://www.atsdr.cdc.gov/placeandhealth/svi/index.html)
- [EPA EnviroAtlas](https://www.epa.gov/enviroatlas)
- [CMS Medicare Provider Data](https://data.cms.gov/)

See `/docs/data_dictionary.md` for full variable definitions and download instructions.

-----

## 🔗 Related Projects

The DCVI Adaptive Capacity dimension feeds directly into the **ClimateReady Score** framework ([github.com/meyeringn/climateready-score](https://github.com/meyeringn/climateready-score)), which evaluates city-level climate preparedness across transit, housing, health, and equity dimensions. Philadelphia’s DCVI performance is a scored input in that rubric.

-----

## 📂 Repository Structure

```
dcvi/
├── README.md                        # This file
├── docs/
│   ├── data_dictionary.md           # Variable definitions and data sources
│   ├── philly_methodology_notes.md  # Philadelphia-specific sourcing notes
│   └── policy_brief_draft.md        # Draft policy brief for government audiences
├── data/
│   ├── schema/
│   │   └── dcvi_tract_schema.csv    # Expected data schema for tract-level input
│   └── sample/
│       └── philly_sample_tracts.csv # Sample data for 10 Philadelphia tracts
└── notebooks/
    └── 01_dcvi_methodology_walkthrough.ipynb  # Methodology notebook (in development)
```

-----

## 🤝 Contributing & Partnership

This project is actively seeking:

- **Transit agencies** with accessibility equipment and ridership data
- **Municipal OEMs / emergency management offices** with cooling center and resource data
- **Public health researchers** with heat illness hospitalization datasets
- **Climate equity organizations** interested in co-publishing findings

Open an issue or reach out via [LinkedIn](https://linkedin.com/in/nicolasmeyering).

-----

## 👤 About

Built by **Nicolas Meyering** — Disabled civic technologist, Chairman of the Philadelphia Mayor’s Commission on People with Disabilities, and 2026 graduate of the Equitech Futures Civic Tech Institute. This project emerged from coursework in the CTI and reflects a commitment to centering disability in climate justice conversations where it has historically been absent.

*“If your climate adaptation plan doesn’t mention disabled people, it isn’t finished.”*
