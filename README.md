# Smart Urban Mobility and Traffic Intelligence Dashboard

An end-to-end Power BI analytics solution that integrates transit, traffic, ride-hailing and weather data into a single data model and a set of interactive dashboards for urban mobility analysis.

**Program:** Infosys Springboard Virtual Internship
**Tool:** Microsoft Power BI
**Data sources:** Kaggle - Smart City Transit, Bangalore Traffic and Ride-Hailing datasets

---

## Table of Contents

1. [Overview](#overview)
2. [Key Features](#key-features)
3. [Dashboards](#dashboards)
4. [Project Roadmap](#project-roadmap)
5. [Data Model](#data-model)
6. [Key DAX Measures](#key-dax-measures)
7. [Key Insights](#key-insights)
8. [Tech Stack](#tech-stack)
9. [Repository Structure](#repository-structure)
10. [Getting Started](#getting-started)
11. [Limitations and Future Scope](#limitations-and-future-scope)
12. [Author](#author)

---

## Overview

Cities generate large volumes of mobility data, including public transport ridership, road traffic, ride-hailing trips, weather and population. These sources are usually stored separately and are difficult to interpret together.

This project combines them into a single, validated star-schema data model in Power BI and delivers four interactive dashboards. The dashboards help city planners and transit analysts examine demand, reliability, accessibility and equity across urban areas.

| Item | Detail |
|---|---|
| Dashboards | 4 interactive report pages |
| Milestones | 4 (data foundation, geospatial analytics, demand intelligence, equity and forecasting) |
| Data volume | 5,000-row transit dataset (11 New York locations, 1-18 March 2024) plus Bangalore traffic and ride-hailing data |

---

## Key Features

- ETL and data cleansing in Power Query: duplicate and null removal, type conversion, and standardised weather and location values
- Star-schema data model with a fact table and Date, Location and Weather dimensions
- Geospatial analysis with traffic-demand and mobility heat maps of Bengaluru
- Route performance and reliability analysis with drill-down by area, route and weather
- Demand intelligence comparing ride-hailing, active mobility and public transport
- Weather sensitivity analysis and demand forecasting using Power BI forecasting
- Mobility Access Index (MAI) with area-wise equity reporting
- Traffic anomaly detection covering January 2022 to July 2024
- Interactive slicers for date, location, vehicle type, weather and route

---

## Dashboards

### Dashboard 1: Smart City Public Transportation Analysis

KPI cards (total passengers, average temperature, total population, average passengers), passenger count by location, passenger share by weather condition, and a temperature versus demand scatter plot.

![Dashboard 1](images/dashboard-1-transit-analysis.jpg)

### Dashboard 2: Smart Urban Mobility and Traffic Intelligence

Traffic demand and mobility heat maps, route-wise passenger performance, weather comparison, and headline KPIs for total traffic, average speed, public transport usage and incident reports.

![Dashboard 2](images/dashboard-2-traffic-intelligence.jpg)

### Dashboard 3: Smart Mobility and Demand Intelligence

Ride-hailing demand by area, pedestrian and cyclist treemap, public transport versus active mobility comparison, weather sensitivity analysis and passenger demand forecast.

![Dashboard 3](images/dashboard-3-demand-intelligence.jpg)

### Dashboard 4: Mobility Equity and Executive Intelligence

Mobility Access Index, area-wise equity report, ride-hailing demand by vehicle type, traffic anomaly detection and executive KPIs.

![Dashboard 4](images/dashboard-4-equity-executive.jpg)

---

## Project Roadmap

| Milestone | Focus | Deliverables |
|---|---|---|
| 1 | Data foundation | Dataset acquisition, ETL pipelines, data cleansing, star-schema model, validation in Power BI |
| 2 | Geospatial and transit analytics | Demand heat maps, route performance and reliability, drill-down geographic analysis, weather and temporal filters |
| 3 | Demand intelligence and mobility analytics | Ride-hailing dashboards, cycling and micromobility analytics, modal comparison, weather sensitivity and forecasting |
| 4 | Equity, forecasting and finalisation | Mobility Access Index, equity and executive dashboards, anomaly detection, performance optimisation |

---

## Data Model

The model follows a star schema to keep calculations simple and visuals responsive.

```
                 +--------------+
                 |  DateTable   |
                 +------+-------+
                        |
+-------------+  +------+--------------+  +-------------+
|  Location   |--|  Transit / Traffic  |--|   Weather   |
| (lat, lon)  |  |    (fact tables)    |  |  (lookup)   |
+-------------+  +---------------------+  +-------------+
```

Fact table fields include Route ID, Location, Passenger Count, Temperature, Weather, Population, Population Density, Date, Traffic Volume, Average Speed and Public Transport Usage.

---

## Key DAX Measures

```dax
Total Passenger = SUM ( Transit[Passenger Count] )

Average Passenger = AVERAGE ( Transit[Passenger Count] )

Mobility Access Index =
DIVIDE (
    [Accessibility Score] + [Reliability Score] + [Bike Availability Score],
    3
)
```

---

## Key Insights

- 2.11 million total passengers were analysed, with an average of 422.97 passengers per record.
- Queens - Flushing / Jamaica has the highest passenger count and Manhattan - Downtown the lowest.
- Demand is spread fairly evenly across weather conditions: Rain 25.64%, Snow 25.15%, Clear 25.07% and Fog 24.14%.
- Active mobility accounts for 71.75% of the combined active mobility and public transport total, against 28.25% for public transport.
- Koramangala and Indiranagar lead ride-hailing demand, and bikes are the most-used ride-hailing vehicle type (32.18%).
- The overall Mobility Access Index is 0.30, indicating scope for improved access.
- The dashboards cover 261 million in total traffic volume, 84 thousand ride-hailing trips and 14 thousand incident reports.

---

## Tech Stack

| Layer | Tools |
|---|---|
| Data preparation | Power Query, Microsoft Excel |
| Modelling | Power BI, star schema |
| Calculations | DAX |
| Visualisation | Power BI: maps, KPI cards, treemap, donut, scatter, line and bar charts, slicers |
| Analytics | Power BI forecasting and anomaly detection |

---

## Repository Structure

```
.
|-- README.md
|-- data/                     Source and cleaned datasets
|-- powerbi/
|   `-- Smart_Urban_Mobility.pbix
|-- images/                   Dashboard screenshots
|-- docs/
|   `-- Final_Project_Report.docx
`-- LICENSE
```

---

## Getting Started

**Prerequisite:** Power BI Desktop (Windows)

1. Clone the repository:
   ```bash
   git clone https://github.com/<username>/<repository>.git
   ```
2. Open `powerbi/Smart_Urban_Mobility.pbix` in Power BI Desktop.
3. If prompted, update the data source path under Home > Transform data > Data source settings so that it points to the `data/` folder.
4. Select Refresh, then explore the four report pages using the slicers.

---

## Limitations and Future Scope

- The project combines separately sourced datasets (New York transit, Bengaluru traffic and ride-hailing), so some cross-dataset visuals use aggregate totals rather than area-level joins. As a result, the area-wise equity table shows the same totals for every area.
- A shared Location dimension across all datasets would enable true area-level equity comparison.
- Future work includes real-time data feeds, publishing to the Power BI Service and scheduled data refresh.

---

## Author

**V Priyadharshini**
B.Tech Information Technology, SRMIST
Infosys Springboard Virtual Internship, Batch 3
Mentor: Kalaiyarasi
