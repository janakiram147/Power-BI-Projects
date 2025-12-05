# 🚖 Uber Rides Analytics Dashboard – Power BI

This repository contains a complete, end-to-end **Uber Rides Analytics Dashboard** built using Power BI.  
The project delivers actionable insights into ride demand patterns, geographic trends, performance KPIs, and customer behavior using real-world style Uber trip data.

---

## 📊 Project Overview

The **Uber Power BI Dashboard** helps understand operational and customer trends within ride-sharing data.  
It provides:

- Time-series trends (hourly, daily, monthly)
- Ride type distribution (UberX, Pool, XL, etc.)
- Geographic pickup/dropoff analysis
- Key business metrics such as total rides, revenue, duration, distance
- Interactive filters, drill-throughs, and dynamic visuals

This dashboard is valuable for transportation companies, mobility analysts, and BI professionals.

---


---

## 🗂 Dataset Requirements

Your dataset should ideally include fields such as:

- `ride_id`
- `request_time`
- `pickup_time`
- `dropoff_time`
- `pickup_lat`, `pickup_lng`
- `dropoff_lat`, `dropoff_lng`
- `ride_type` (UberX, Pool, XL…)
- `fare`, `distance_km`, `duration_min`
- `city`, `zone`, `zipcode`

**Note:** Ensure all datetime fields are in a valid format (ISO recommended).

---

## 🛠 Data Preparation Steps (Power BI)

### 1. Import & Clean Data
- Load CSV(s) into Power BI  
- Remove duplicates  
- Standardize ride type names  
- Convert date/time formats  
- Handle missing coordinates/values  

### 2. Create a Date Table
In Power BI, generate a Calendar table with:

- Date  
- Year  
- Quarter  
- Month  
- Week  
- Day  
- Hour  

Mark this as the **official date table**.

### 3. Build Data Model
- Connect Date → Ride Data through datetime fields  
- Build relationships for city/zone if applicable  

### 4. Create DAX Measures
Include KPIs, YoY comparisons, totals, averages, and time intelligence functions.

---

## 📐 Example DAX Measures

```dax
Total Rides = COUNTROWS('Rides')

Total Fare = SUM('Rides'[fare])

Average Fare = DIVIDE([Total Fare], [Total Rides], 0)

Average Duration (Min) = AVERAGE('Rides'[duration_min])

Rides This Month =
CALCULATE(
    [Total Rides],
    DATESINPERIOD('Date'[Date], MAX('Date'[Date]), -1, MONTH)
)

Rides YoY % =
VAR PrevYear =
    CALCULATE([Total Rides], SAMEPERIODLASTYEAR('Date'[Date]))
RETURN
    DIVIDE([Total Rides] - PrevYear, PrevYear)
```
---

## 📌 Dashboard Pages & Features

### **1. Overview Page**
- Total Rides  
- Total Fare  
- Average Fare  
- Avg Distance / Duration  
- Monthly & Daily trend lines  
- Key performance KPIs  

### **2. Time Analysis**
- Hourly heatmap  
- Day-of-week breakdown  
- Month-over-month demand  

### **3. Ride Type Insights**
- Ride type segmentation (UberX, Pool, XL…)  
- Category-level performance metrics  

### **4. Geographic Insights**
- Pickup/Dropoff map visualization  
- Heatmap showing ride density  
- City/Zone-level ride distribution

### **5. Driver / Fleet Performance (Optional)**
- Driver KPIs  
- Utilization trends  

---

## 🚀 How to Use This Project

1. Download or clone this repository.  
2. Place your dataset(s) inside the `/data/` folder.  
3. Open the `.pbix` file located in `/reports/` using **Power BI Desktop**.  
4. Refresh the data sources.  
5. Review or modify the Power Query transformations.  
6. Explore and customize the dashboard as needed.  
7. Publish to Power BI Service (optional).  

---

## 👤 Author

**Y Janaki Ram**  
-Data Analyst
