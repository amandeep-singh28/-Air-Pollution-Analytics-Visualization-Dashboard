# Air Pollution Analytics and Visualization Dashboard

An interactive and insight-driven **Air Quality Intelligence Dashboard** built using **Power Query and Power BI**, integrated with **AQI-based classification logic** to analyze air pollution patterns across India.

The project follows industry-standard **data modeling practices**, uses a **Star Schema architecture**, and applies **dynamic DAX-driven visual logic** to deliver clear, actionable insights.

---

## 1. Project Workflow Overview

This project follows a structured **end-to-end Business Intelligence workflow** inside Power BI:

- **Power Query**
  - Data cleaning
  - Data transformation
  - Table preparation

- **Star Schema Modeling**
  - Dim–Fact architecture
  - Surrogate key generation
  - Relationship optimization

- **DAX Measures**
  - KPI calculations
  - AQI categorization
  - Conditional formatting logic

- **Power BI Dashboard**
  - Interactive KPIs
  - Filters and slicers
  - Geo-spatial and analytical visuals

---

## 2. Data Cleaning and Preparation (Power Query)

### Dataset Used

- **Real-Time Air Quality Index – DataGov India**  
  https://www.data.gov.in/resource/real-time-air-quality-index-various-locations

### Initial Main Table Structure

- Country  
- State  
- City  
- Station  
- Last_Update  
- Latitude  
- Longitude  
- Pollutant_ID  
- Pollutant_Min  
- Pollutant_Max  
- Pollutant_Avg  

### Data Cleaning Steps

- Removed null and duplicate records  
- Standardized text fields using Trim, Clean, and Format  
- Converted `Last_Update` column to proper DateTime format  
- Ensured numeric consistency for pollutant values  
- Prepared dataset for dimensional modeling  

---

## 3. Star Schema Design

A clean **Star Schema** was implemented to improve performance, scalability, and analytical efficiency.

---

### Fact Table

**Columns**

- Location ID  
- Pollutant ID  
- pollutant_min  
- pollutant_max  
- pollutant_avg  

**Steps Performed**

- Duplicated the main dataset  
- Merged with Dim Location to obtain Location ID  
- Merged with Dim Pollutant to obtain Pollutant ID  
- Removed descriptive text columns  
- Filtered out rows with null pollutant values  
- Converted pollutant metrics to Whole Number  

---

### Dim Location

**Columns**

- Location ID  
- Country  
- State  
- City  
- Station  
- Last_Update  
- Latitude  
- Longitude  

**Steps Performed**

- Duplicated the main dataset  
- Removed all pollutant-related columns  
- Created Location ID using Index Column  

---

### Dim Pollutant

**Columns**

- Pollutant ID  
- Pollutant Name  

**Steps Performed**

- Duplicated the main dataset  
- Retained only Pollutant_ID  
- Removed duplicate pollutant values  
- Renamed Pollutant_ID to Pollutant Name  
- Created Pollutant ID using Index Column  

---

## 4. Data Model and Relationships

- Implemented a **Star Schema architecture**
- Relationships:
  - Dim Location[Location ID] → Fact Table[Location ID] (1:*)
  - Dim Pollutant[Pollutant ID] → Fact Table[Pollutant ID] (1:*)
- Single-direction filtering applied
- No circular or inactive relationships
- Optimized model for analytical queries

---

## 5. DAX Measures Implemented

### Core Measures

```DAX
Total Stations =
DISTINCTCOUNT ( 'Dim Location'[Station] )

Avg Pollutant =
AVERAGE ( 'Fact Table'[pollutant_avg] )

Min Pollutant =
MIN ( 'Fact Table'[pollutant_min] )

Max Pollutant =
MAX ( 'Fact Table'[pollutant_max] )

Total Readings =
COUNTROWS ( 'Fact Table' )
```

```Gauge Chart Measures
Minimum Value = 0
Maximum Value = 300
Target Value = 100
```

```AQI Category
AQI Category =
SWITCH(
    TRUE(),
    [Avg Pollutant] <= 50, "Good",
    [Avg Pollutant] <= 100, "Moderate",
    [Avg Pollutant] <= 150, "Unhealthy (Sensitive)",
    [Avg Pollutant] <= 200, "Unhealthy",
    [Avg Pollutant] <= 300, "Very Unhealthy",
    "Hazardous"
)
```

```AQI Color (Conditional Formatting)
AQI Color =
SWITCH(
    TRUE(),
    [Avg Pollutant] <= 50, "#00A65A",
    [Avg Pollutant] <= 100, "#F39C12",
    [Avg Pollutant] <= 150, "#FF851B",
    [Avg Pollutant] <= 200, "#DD4B39",
    [Avg Pollutant] <= 300, "#8E24AA",
    "#4A148C"
)
```

Used for:
- KPI Cards
- Gauge Chart
- Bar and Column Charts
- Geo-spatial Maps

## 6. Power BI Dashboard

### KPI Cards
- Total Stations
- Average Pollutant
- Minimum Pollutant
- Maximum Pollutant

### Gauge Chart – Overall AQI
- Dynamic value using Avg Pollutant
- Threshold-based coloring using AQI Color
- Min, Max, and Target controlled via DAX

### Geo-Spatial Visualization
- Shape Map (India – State level)
- State-wise average pollutant concentration
- Fully interactive with slicers

### Charts and Visuals
- Bar Chart: Top 10 most polluted cities
- Donut Chart: Pollutant distribution
- Clustered Column Chart: Min vs Avg vs Max pollutant levels
- Funnel Chart: Top pollutants by average concentration

## 7. Filters and Interactivity
- Pollutant Name
- State

### Reset to Default
- Bookmark-driven reset button
- Instantly clears all slicers

## 8. Dataset Overview
- Pollutants: PM2.5, PM10, NO2, SO2, CO, OZONE, NH3
- Locations: Country, State, City, Station
- Metrics: pollutant_min, pollutant_max, pollutant_avg
- Coordinates: Latitude and Longitude
- Timestamp: Last_Update

9. Final Thoughts and Future Scope
Key Highlights

End-to-end Power BI project

Clean Star Schema implementation

AQI-based insights with dynamic coloring

Professional, interactive dashboard

Future Enhancements

Drill-through analysis pages

Mobile-optimized dashboard layout

Real-time API integration

Advanced AQI trend and seasonality analysis
