# 🌍💨 Air Pollution Analytics and Visualization Dashboard

An interactive and insightful **Air Quality Intelligence Dashboard** built entirely using **Power Query and Power BI**, integrated with **AQI Classification Logic** to analyze environmental pollution across India.  
Designed with a **clean white modern theme** to deliver insights with clarity and professionalism.

---

## 🧩 **1. Project Workflow Overview**

This project follows a structured **ETL workflow** inside Power BI:

- **Power Query**: Data cleaning, preprocessing, transformation  
- **Dim–Fact Modeling**: Created star schema for analytical reporting  
- **Power BI Dashboard**: Built with AQI-driven color logic, KPIs, slicers, maps & charts  

---

## 🧹 **2. Data Cleaning & Preparation (Power Query)**

✅ **Dataset Used:**  
- [Real-Time Air Quality Index – DataGov](https://www.data.gov.in/resource/real-time-air-quality-index-various-locations)

### 🔧 **Cleaning Steps**
- Removed nulls & duplicate records  
- Standardized text fields using Trim, Clean, Format  
- Converted `last_update` column to proper DateTime  
- Created **AQI Category column** using pollutant threshold logic  
- Split dataset into **three relational tables**:

| 🗃 **Table Name** | 🔍 **Description** |
|------------------|---------------------|
| **Fact Table** | Pollutant Min, Max, Avg, Location ID, Pollutant ID |
| **Dim Location** | Country, State, City, Station, Latitude, Longitude |
| **Dim Pollutant** | Pollutant ID, Pollutant Name |

✅ Structured using **primary & foreign keys** for clean BI modeling  

---

## 🗄️ **3. Data Model & Relationship Testing**

- Built a clean **Star Schema**  
- Established **one-to-many (1:*)** relationships:  
  - Dim Location → Fact Table  
  - Dim Pollutant → Fact Table  
- Ensured **single-direction filters** for performance  
- No inactive / ambiguous relationships  

---

## 📊 **4. Power BI Dashboard**

### 🎨 **Theme**
- **Background:** Clean white canvas  
- **Design Goal:** Minimalistic + AQI-based dynamic colors  

---

### 🔷 **Dashboard Elements**

## 🧮 **KPI Cards**
- Total Stations  
- Average Pollutant  
- Min Pollutant  
- Max Pollutant  

---

## 🧭 **Gauge Chart – Overall AQI Index**
- Min = 0  
- Max = 300  
- Target = 100  
- Needle = `Avg Pollutant`  
- Dynamic fill color using AQI Color measure  

---

## 🗺️ **Geo-Spatial Map**
- Plots cities using Latitude & Longitude  
- Bubble colors based on AQI category  
- Interactive zoom, panning, and tooltips  

---

## 📈 **Charts & Visuals**
- **Bar Chart:** Top 10 most polluted cities  
- **Donut Chart:** Pollutant distribution  
- **Clustered Column Chart:** Min vs Avg vs Max pollutant levels  
- **Gauge Chart:** Real-time AQI indicator  

---

## 🎛 **Filters & Slicers**
- Country  
- State  
- City  
- Station  
- Pollutant Name  

---

## 🔘 **Buttons**
- **Reset to Default** (Bookmark-driven filter reset)  

---

## 🧠 **5. DAX Measures Implemented**

### 🔷 Core Measures
- `Avg Pollutant`  
- `Min Pollutant`  
- `Max Pollutant`  
- `Total Stations`  
- `Total Readings`  

### 🔷 AQI Category Logic  
(Good → Moderate → Unhealthy (Sensitive) → Unhealthy → Very Unhealthy → Hazardous)

### 🔷 AQI Color Logic  
Used for conditional formatting in:
- Map  
- Bar charts  
- Gauge  
- KPI cards  

---

## 📁 **6. Dataset Overview**

The dataset contains:

- **Pollutants:** PM2.5, PM10, NO2, SO2, CO, OZONE, NH3  
- **Location:** Country, State, City, Station  
- **Coordinates:** Latitude & Longitude  
- **Metrics:** pollutant_min, pollutant_max, pollutant_avg  
- **Timestamp:** last_update  

---

## 📌 **7. Final Thoughts & Future Scope**

✅ Fully interactive dashboard  
✅ Clean Star Schema  
✅ AQI-based insights  
✅ Professional BI layout  

### 🔮 Future Enhancements
- Add drillthrough pages  
- Add mobile layout  
- Include ML-based AQI prediction  
- API integration for real-time updates  

---

> 🙌 **Built with accuracy, environmental awareness, and BI excellence to visualize India’s air quality.**

---

### 🔗 **Connect**
Open to feedback, suggestions, and collaboration.
