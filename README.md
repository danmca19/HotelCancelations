# 🏨 Hotel Booking Cancellation Prediction Project

## 📌 Overview

This project analyzes hotel booking data to understand what drives cancellations and builds a machine learning model to **predict whether a booking will be canceled**. Accurate predictions empower hotels to:

- **Reduce revenue loss**
- **Optimize operational resources**
- **Improve customer satisfaction**

---

## 🎯 Project Goal

Develop a machine learning model to predict booking cancellations, enabling:

- 💰 **Revenue Management**: Adjust pricing dynamically and manage overbooking smartly.
- ⚙️ **Operational Efficiency**: Allocate staff and rooms effectively based on likely occupancy.
- ❤️ **Customer Engagement**: Intervene proactively with guests likely to cancel.

---

## 📂 Dataset Description

The dataset (`hotel.csv`) contains detailed information about hotel bookings. Key features include:

| Column Name                          | Type        | Description                                                               |
|-------------------------------------|-------------|---------------------------------------------------------------------------|
| `Booking_ID`                        | object      | Unique booking identifier (not used in modeling)                         |
| `no_of_adults`                      | int64       | Number of adults in the booking                                          |
| `no_of_children`                    | int64       | Number of children                                                       |
| `no_of_weekend_nights`             | int64       | Nights stayed on weekends                                                |
| `no_of_week_nights`                | int64       | Nights stayed on weekdays                                                |
| `type_of_meal_plan`                | object      | Meal plan selected                                                       |
| `required_car_parking_space`       | int64       | Binary flag for parking space needed                                     |
| `room_type_reserved`               | object      | Type of room booked                                                      |
| `lead_time`                        | int64       | Days between booking and check-in                                        |
| `arrival_year`, `arrival_month`, `arrival_date` | int64 | Arrival date breakdown                                                 |
| `market_segment_type`              | object      | Channel through which booking was made                                   |
| `repeated_guest`                   | int64       | Binary flag: is the guest a repeat customer                              |
| `no_of_previous_cancellations`     | int64       | Guest’s history of prior cancellations                                   |
| `no_of_previous_bookings_not_canceled` | int64   | Guest’s history of successful bookings                                   |
| `avg_price_per_room`               | float64     | Average price per night                                                  |
| `no_of_special_requests`           | int64       | Number of special requests made                                          |
| `booking_status`                   | object      | Target: "Canceled" or "Not_Canceled"                                     |

---

## 📊 Exploratory Data Analysis (EDA)

### Key Insights:

- **Lead Time**: Long lead times show higher cancellation likelihood.
- **Market Segment**: Online channels present higher cancellation rates.
- **Guest History**: Guests with prior cancellations are more likely to cancel again.
- **Special Requests**: More requests may indicate higher commitment (lower cancellations).
- **Room Price**: Very high or very low prices may affect cancellation behavior.
- **Arrival Dates**: Seasonal patterns (month/year) influence cancellations.

---

## 🧹 Preprocessing Steps

- Created a working copy (`df_model`) to preserve raw data.
- Transformed `booking_status` into binary:  
  - `1` = Canceled  
  - `0` = Not_Canceled
- Applied `LabelEncoder` to categorical variables.
- Removed `Booking_ID` as it's non-informative.
- Split the data into training (80%) and test (20%) sets using `stratify=y`.

---

## 🤖 Modeling

### Model Used: `RandomForestClassifier`

- Chosen for its robustness and ability to handle both categorical and numeric data.
- Config: `n_estimators=100`, `random_state=42`, `n_jobs=-1`

### Performance Metrics:

| Metric                 | Value      |
|------------------------|------------|
| **Accuracy**           | 90.78%     |
| **Precision (Canceled)** | 89.39%   |
| **Recall (Canceled)**    | 81.53%   |
| **F1 Score (Canceled)**  | 85.28%   |


---

## 📌 Feature Importance (Top Drivers)

Key factors that influence cancellations:

- `lead_time`
- `market_segment_type`
- `avg_price_per_room`
- `no_of_previous_cancellations`
- `no_of_special_requests`

These features can be directly used to create business strategies (e.g., identify high-risk segments).

---

## 💼 Business Insights & Recommendations

### 🛑 Identify High-Risk Bookings

Use model predictions to:

- **Contact guests proactively** (confirmation or special offers)
- **Apply stricter cancellation policies** on high-risk segments

### 💡 Revenue Optimization

- Use **dynamic pricing** for bookings with high cancellation probability
- Offer **non-refundable discounts** for long lead-time bookings

### ⚙️ Operational Planning

- Improve **staff scheduling** and **inventory management** based on likely occupancy

### 🎯 Targeted Marketing

- Create loyalty programs for guests with no history of cancellations
- Adjust cancellation policies for segments with consistently high cancellation rates

---
## 📌 Strategic Recommendations

| Factor               | Insight                                 | Action                             |
|----------------------|------------------------------------------|------------------------------------|
| Lead Time            | High risk with long booking windows      | Stricter cancellation policies     |
| Online Segment       | High cancellation rate                   | Require pre-payment or confirmation |
| Special Requests     | Indicate commitment                      | Offer small perks to encourage     |
| Guest History        | Strong predictor of behavior             | Adjust rules for risky profiles    |
| Price Extremes       | Both high and low values risky           | Limit flexibility for cheap rates  |

---

## ✅ Benefits

- 🎯 Predict high-risk bookings and act early
- 💰 Optimize pricing and overbooking
- 📊 Improve staff and inventory planning
- 🤝 Build loyalty with reliable guests

## 📌 Project Parameters (based on real dataset)

| Item                                       | Value           |
| ----------------------------------------- | --------------- |
| Total bookings analyzed                   | 39,142          |
| Total cancellations identified            | 11,885          |
| **Average cost per avoidable cancellation** | R$ 3,500.00     |
| **Estimated project cost**                | R$ 150,000.00   |

---

## 📐 ROI Formula

ROI= Net Return / Total Project Cost × 100

Where:

- **Net Return** = Estimated savings from avoided cancellations – Project cost  
- **Total Project Cost** = Financial investment required for model development, testing, and deployment

---

## 📊 ROI Scenarios

| Scenario         | Total Cancellations | Avoided Cancellations | Estimated Savings (R$) | Project Cost (R$) | ROI (%)       |
| ---------------- | ------------------- | ---------------------- | ----------------------- | ------------------ | ------------- |
| Conservative (5%)| 11,885              | 594                    | R$ 2,079,875.00         | R$ 150,000         | **1286.58%**  |
| Moderate (10%)   | 11,885              | 1,188                  | R$ 4,159,750.00         | R$ 150,000         | **2673.17%**  |
| Optimistic (20%) | 11,885              | 2,377                  | R$ 8,319,500.00         | R$ 150,000         | **5446.33%**  |


## 🔮 Next Steps

- 🔧 **Hyperparameter Tuning** with GridSearchCV
- ✨ **Feature Engineering** (e.g., total nights, weekday vs weekend ratio)
- 🚀 **Advanced Algorithms**: Try XGBoost, LightGBM, etc.
- ⚖️ **Handle Class Imbalance** with SMOTE or class weights
- 📈 **Time Series Extension**: Capture seasonality
- 🌐 **Model Deployment**: Flask API or cloud-based serving for real-time predictions



