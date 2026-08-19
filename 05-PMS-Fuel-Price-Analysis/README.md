# PROJECT REPORT: FUEL PRICE ANALYSIS ACROSS NIGERIAN STATES
**Period**: Jan 2024 – Dec 2025

## Objective 
Assess YoY changes in PMS prices across Nigeria’s 36 states + FCT.

## Data Source 
**National Bureau of Statistics, Nigeria** — [www.nigerianstat.gov.ng](https://www.nigerianstat.gov.ng) 
**Scope**: State-level average PMS prices, 2024 & 2025 [37 records/year]

## Methodology 
**1. Excel & MS SQL**: Cleaned inconsistencies, standardized prices, validated ranges.

**2. MS SQL**: Created `Geopolitical_Zone` and merged years.
```sql
UPDATE [dbo].[PMS PRICE TREND FROM SQL]
SET Geopolitical_Zone =
    CASE
        WHEN State IN ('Benue','Abuja','FCT','Kogi','Kwara','Nasarawa','Niger','Plateau') THEN 'North Central'
        WHEN State IN ('Adamawa','Bauchi','Borno','Gombe','Taraba','Yobe') THEN 'North East'
        WHEN State IN ('Jigawa','Kaduna','Kano','Katsina','Kebbi','Sokoto','Zamfara') THEN 'North West'
        WHEN State IN ('Abia','Anambra','Ebonyi','Enugu','Imo') THEN 'South East'
        WHEN State IN ('Akwa Ibom','Bayelsa','Cross River','Delta','Edo','Rivers') THEN 'South South'
        WHEN State IN ('Ekiti','Lagos','Ogun','Ondo','Osun','Oyo') THEN 'South West'
        ELSE Geopolitical_Zone
    END;
