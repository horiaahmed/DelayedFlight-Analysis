# ✈️ Flight Delays Analysis Dashboard

## 📌 Project Overview

This project analyzes airline flight delays using Python for data cleaning and Power BI for interactive dashboards. The objective is to identify delay patterns, operational performance, and key factors contributing to flight delays.

---

## 📂 Dataset

- Dataset: Delayed Flights Dataset
- Rows: 444,469
- Columns: 29

### Features
- Flight Information
- Airline
- Origin & Destination
- Departure & Arrival Times
- Delay Reasons
- Cancellation Status
- Diversion Status

---

## 🛠️ Tools & Technologies

- Python
- Pandas
- NumPy
- Google Colab
- Power BI

---

# 🧹 Data Cleaning

### 1. Removed Unnecessary Columns

```python
df.drop(['Unnamed: 0'], axis=1, inplace=True)
```

### 2. Checked Data Structure

```python
df.info()
df.shape
```

### 3. Checked Missing Values

```python
df.isnull().sum()
```

### 4. Checked Duplicate Rows

```python
df.duplicated().sum()
```

### 5. Removed Cancelled & Diverted Flights

```python
df = df[(df["Cancelled"] == 0) & (df["Diverted"] == 0)]
```

### 6. Filled Missing Delay Values

```python
delay_cols = [
    "CarrierDelay",
    "WeatherDelay",
    "NASDelay",
    "SecurityDelay",
    "LateAircraftDelay"
]

df[delay_cols] = df[delay_cols].fillna(0)
```

### 7. Created On-Time Feature

```python
df["OnTime"] = (df["ArrDelay"] <= 15).astype(int)
```

### 8. Created Delay Categories

```python
df["DelayCategory"] = pd.cut(
    df["ArrDelay"],
    bins=[-1000,0,15,60,10000],
    labels=["Early","OnTime","Minor","Major"]
)
```

### 9. Exported Clean Dataset

```python
df.to_csv("Cleaned_DelayFlight.csv", index=False)
```

---

# 📊 Dashboard

## 🏠 Home

A landing page providing navigation across the report.

Features:

Project title
Navigation buttons
![](https://github.com/horiaahmed/DelayedFlight-Analysis/blob/main/Fleight%20home.png)

---

## 📈 Overview

KPIs:

- Total Flights
- On-Time Flights
- Delayed Flights
- Average Arrival Delay
- Average Departure Delay

Visuals:

- Monthly Delay Trend
- Delay Categories
- Flights by Airline
- Flights by Day
![](https://github.com/horiaahmed/DelayedFlight-Analysis/blob/main/overview.png)
---

## ✈️ Operational

Visuals:

- Taxi In Time
- Taxi Out Time
- Flight Distance
- Airline Performance
- Airport Performance

---

## ⚠️ Delay Analysis

Visuals:

- Carrier Delay
- Weather Delay
- NAS Delay
- Security Delay
- Late Aircraft Delay
![](https://github.com/horiaahmed/DelayedFlight-Analysis/blob/main/overview.png)
---

# 📈 Project Workflow

```text
Raw Dataset
     │
     ▼
Data Cleaning
     │
     ▼
Feature Engineering
     │
     ▼
Clean Dataset
     │
     ▼
Power BI
     │
     ▼
Interactive Dashboards
```

---

# 💡 Key Insights

- Identified the airlines with the highest delay rates.
- Measured overall on-time performance using the 15-minute industry standard.
- Analyzed the contribution of carrier, weather, NAS, security, and late aircraft delays.
- Compared operational efficiency across airlines and airports.
- Examined monthly and weekly delay patterns to identify peak disruption periods.

---
# 👤 Author

**Horia Ahmed**
