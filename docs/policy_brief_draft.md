# Policy Brief: The Disability Climate Vulnerability Index

## Centering Disabled People in Climate Adaptation Planning

**Prepared by:** Nicolas Meyering, Civic Technology Fellow  
**Affiliation:** Equitech Futures Civic Tech Institute, 2026 Cohort  
**Date:** 2026  
**Status:** Draft for Review

-----

## Executive Summary

Disabled people represent over 13% of the U.S. population — more than 42 million Americans — yet they are systematically underrepresented in climate adaptation frameworks, vulnerability assessments, and emergency preparedness plans. This gap is not an oversight. It is a structural failure with life-or-death consequences.

The Disability Climate Vulnerability Index (DCVI) is an open-source methodology that cross-references disability prevalence, climate hazard exposure, and adaptive capacity at the census tract level to produce a composite vulnerability score. The DCVI enables planners, policymakers, and advocates to answer a question that current federal frameworks do not clearly answer: *Where are Disabled people most at risk from climate change, and what makes them most vulnerable there?*

This brief summarizes the DCVI methodology, presents preliminary findings for Philadelphia, PA, and offers recommendations for municipal, state, and federal policymakers.

-----

## The Problem: Disability Is Invisible in Climate Planning

### Existing Frameworks Fall Short

The primary federal tool for identifying vulnerable populations in climate and disaster contexts is FEMA’s Social Vulnerability Index (SVI), which includes disability as one of 15 equally-weighted indicators. This structure obscures rather than illuminates disability vulnerability — a tract can score low on SVI even if it has extremely high disability prevalence, because disability is averaged with other variables.

Similarly, most municipal climate action plans and adaptation strategies do not disaggregate vulnerability data by disability status. A review of 20 major U.S. city climate plans found that fewer than 25% mentioned disability as a distinct vulnerability category. Philadelphia’s own Climate Action Playbook (2021) does not explicitly reference Disabled people.

### The Stakes Are High

The research is unambiguous: Disabled people face elevated climate risk. During Hurricane Katrina, people with disabilities were significantly overrepresented among fatalities. During the 2021 Texas winter storm, Disabled people who depended on powered medical equipment died when the grid failed. During extreme heat events, people with mobility impairments, chronic illness, and limited transportation access face compounded barriers to reaching cooling resources.

These outcomes are predictable. They are also preventable — but only if planners know where to look and what to prioritize.

-----

## The DCVI Approach

The DCVI scores each census tract on three dimensions:

- **Disability Prevalence Score (DPS):** Concentration of Disabled residents and their poverty rates, using ACS data
- **Climate Hazard Exposure Score (CHES):** Exposure to extreme heat, flooding, and other climate hazards, using FEMA National Risk Index data
- **Adaptive Capacity Score (ACS):** Access to the resources needed to respond to climate events — transit, healthcare, cooling infrastructure, broadband, housing stability

These three dimensions are combined into a 0–100 composite DCVI score, normalized nationally. Tracts are classified into five tiers from Minimal to Critical.

The DCVI is designed to be replicable at national scale using publicly available federal data sources. Full methodology and data dictionary are available at [github.com/meyeringn/dcvi](https://github.com/meyeringn/dcvi).

-----

## Philadelphia Findings (Preliminary)

Preliminary analysis identifies several Philadelphia neighborhoods as likely Critical or High DCVI tier, including portions of North Philadelphia West (19132), North Philadelphia East/Kensington (19133), Southwest Philadelphia/Kingsessing (19143), and Port Richmond (19134).

Across Philadelphia, three structural vulnerabilities drive elevated DCVI scores:

1. **The intersection of disability and poverty.** Philadelphia’s disability population has above-average poverty rates. Economic vulnerability dramatically limits adaptive capacity — it affects whether a resident can afford air conditioning, whether they can access transportation to a cooling center, and whether they have the social networks to receive help during a crisis.
1. **Cooling center inequity.** Philadelphia’s cooling center network, while extensive, is not distributed proportionally to vulnerability. Preliminary analysis suggests that high-DCVI tracts have above-average distances to the nearest official cooling center.
1. **Transit accessibility failures.** SEPTA’s elevator and escalator uptime rate of approximately 71% means that a significant percentage of riders with mobility disabilities cannot reliably access the transit system needed to reach cooling resources during heat emergencies. (See [UpLift](https://github.com/meyeringn/uplift-transit) for predictive maintenance methodology.)

-----

## Policy Recommendations

### For Municipal Government

1. **Integrate DCVI into the next Climate Action Plan update.** Philadelphia’s Climate Action Playbook should be revised to include a disability vulnerability section using DCVI methodology. High-DCVI tracts should receive priority consideration in cooling center siting, tree canopy investment, and emergency preparedness planning.
1. **Publish a disability-specific emergency evacuation plan.** As of 2026, no publicly available disability-specific evacuation plan exists for Philadelphia. This is a critical gap. The Mayor’s Office of Emergency Management should develop and publish this plan in consultation with the Mayor’s Commission on People with Disabilities.
1. **Require DCVI analysis in Environmental Justice impact assessments.** Any new city infrastructure project in a high-DCVI tract should require an analysis of disability climate impacts as part of the environmental justice review process.

### For State Government

1. **Incorporate DCVI into Pennsylvania’s Hazard Mitigation Plan.** PEMA’s State Hazard Mitigation Plan should include a disability-centered vulnerability dimension. DCVI methodology can be applied statewide at the census tract level.
1. **Create a disability climate data portal.** Pennsylvania should establish a publicly accessible data tool allowing communities, advocates, and planners to query DCVI scores and underlying indicators by geography.

### For Federal Government

1. **Revise FEMA’s Social Vulnerability Index to surface disability as a primary dimension.** The SVI’s current structure averages disability with 14 other indicators. A revised SVI should treat disability as a first-class dimension with its own composite score, consistent with the DCVI approach.
1. **Fund a national DCVI implementation.** The EPA, HHS, and FEMA should jointly fund a full national DCVI scoring effort, producing tract-level scores for all 73,000+ U.S. census tracts and publishing results as open data.

-----

## Conclusion

Climate change is not a future problem for Disabled people. It is a present crisis — felt every summer in broken elevators, inaccessible cooling centers, and emergency systems that weren’t designed with us in mind.

The DCVI is a tool for making that crisis visible to the people with the power to address it. It is built on public data, with open methodology, designed to be used by anyone who wants to put Disabled people where they belong in climate conversations: at the center.

-----

## About the Author

Nicolas Meyering is a Disabled civic technologist, Chairman of the Philadelphia Mayor’s Commission on People with Disabilities, and a 2026 graduate of the Equitech Futures Civic Tech Institute. He builds civic technology tools at the intersection of disability justice, transit equity, and climate adaptation.

*Contact: [linkedin.com/in/nicolasmeyering](https://linkedin.com/in/nicolasmeyering)*
