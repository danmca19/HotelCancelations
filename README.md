# 🏨 Hotel Booking Cancellation Prediction Project

## 📌 Overview

This project explores hotel booking data to understand the key factors that influence cancellations and develops a machine learning model to **predict whether a reservation will be canceled**.

By anticipating likely cancellations, hotel managers can:
- Take proactive measures to retain bookings
- Optimize staff and inventory planning
- Reduce financial loss associated with last-minute cancellations

---

## 🎯 Objective

Build a machine learning classification model to support hotel decision-making by:
- Identifying high-risk reservations
- Reducing overbooking uncertainty
- Supporting smarter pricing and cancellation policies

---

## 📂 Dataset Description

The dataset (`hotel.csv`) includes 39,142 bookings. Key features include:

- `lead_time`: time between booking and check-in
- `market_segment_type`: channel of reservation (e.g., online, corporate)
- `avg_price_per_room`: price paid
- `no_of_special_requests`: a proxy for customer engagement
- `no_of_previous_cancellations`: historical behavior
- `booking_status`: target label (Canceled / Not_Canceled)

---

## 📊 Key Insights from Exploratory Data Analysis (EDA)

- Longer lead times are strongly associated with higher cancellation rates
- Online bookings tend to cancel more than corporate or offline bookings
- Guests with **no prior bookings** are more likely to cancel
- Customers who make **special requests** are less likely to cancel
- Cancellation patterns vary by season, suggesting opportunities for dynamic strategy

---

## 🧹 Data Preparation

- Transformed `booking_status` to binary format (`1 = Canceled`)
- Removed booking ID (non-informative)
- Encoded categorical variables using `LabelEncoder`
- Split into 80% training and 20% test using stratified sampling

---

## 🤖 Modeling Overview

**Model Used**: `RandomForestClassifier`  
Configuration: 100 trees, parallel processing enabled, `random_state=42`

### Evaluation Results:

| Metric                  | Score       |
|-------------------------|-------------|
| Accuracy                | 90.78%      |
| Precision (Canceled)    | 89.39%      |
| Recall (Canceled)       | 81.53%      |
| F1 Score (Canceled)     | 85.28%      |

The model is well-balanced and particularly good at catching cancellations with high precision.

---

## 🔍 Top Predictors of Cancellation

- `lead_time`
- `market_segment_type`
- `avg_price_per_room`
- `no_of_previous_cancellations`
- `no_of_special_requests`

These features can be used to flag risky bookings or segment customers for different cancellation policies or incentives.

---

## 💼 Business Use Cases

| Use Case                        | Action                                                      |
|----------------------------------|-------------------------------------------------------------|
| Long lead time + online booking | Offer special promotions or reminders to reduce no-shows    |
| Repeat cancellers               | Add friction to the booking process (e.g., upfront deposit) |
| High price but no engagement    | Confirm manually or follow-up                                |
| Reliable guests                 | Incentivize with loyalty programs                            |

---

## 💸 Project Parameters

| Metric                                      | Value          |
|---------------------------------------------|----------------|
| Bookings analyzed                           | 39,142         |
| Total cancellations                         | 11,885         |
| **Estimated avoidable loss per cancellation** | R$ 350,00     |
| **Estimated project cost**                  | R$ 150,000,00  |

---

## 📐 ROI Estimation

**ROI = (Avoided Losses – Project Cost) / Project Cost × 100**

---

### ROI Scenarios (Conservative)

| Scenario             | Avoided Cancellations | Estimated Savings (R$) | Project Cost (R$) | ROI (%)   |
|----------------------|------------------------|--------------------------|-------------------|-----------|
| Minimal (1%)         | 119                    | R$ 41,650                | R$ 150,000        | **-72.2%**|
| Conservative (3%)    | 356                    | R$ 124,600               | R$ 150,000        | **-16.9%**|
| Moderate (5%)        | 594                    | R$ 207,900               | R$ 150,000        | **38.6%** |
| Realistic (8%)       | 951                    | R$ 332,850               | R$ 150,000        | **121.9%**|

> These are **projections based on estimated impact**. ROI is highly dependent on execution, operational integration, and the percentage of high-risk bookings that can truly be retained.

---

## 🧠 Strategic Takeaways (Even If ROI Is Low)

1. **Early Warning is Strategic**: Even a modest prediction capability gives your teams **lead time to act**, especially during high-occupancy periods.
2. **Not Just About ROI**: The model supports **guest segmentation**, smarter **policy design**, and **better staff planning** — even if it doesn’t yield huge financial returns up front.
3. **Mitigating Risks**:
   - Run a **pilot** before full deployment
   - Focus on **specific market segments** (e.g., online bookings with long lead times)
   - Use predictions in **CRM triggers** (emails, offers) to measure incremental impact
   - Track results via **A/B testing** to validate business outcomes

---

## ✅ Benefits Summary

- 🧠 Better understanding of guest behavior
- 🎯 Precise targeting of risky bookings
- 💰 Potential revenue retention when scaled
- 📊 Enhanced KPIs: occupancy rate, cancellation %, operational margin

---

## 📈 Next Steps

- 🔍 Tune hyperparameters with `GridSearchCV`
- 📉 Handle class imbalance with SMOTE
- ⚙️ Build a daily prediction pipeline
- 📢 Deploy via Flask API or integrate with CRM tools
- 📊 Create monitoring dashboard in Power BI or Looker

---

## 🔚 Final Note

Even when ROI appears modest or negative at first glance, the **strategic value of cancellation prediction models** includes:

- Avoiding overbooking crises  
- Improving service predictability  
- Building customer trust with personalized actions  
- Laying the groundwork for broader **data-driven operations** in hospitality

If scaled smartly, even a few percentage points in cancellation avoidance can justify the investment over time.


