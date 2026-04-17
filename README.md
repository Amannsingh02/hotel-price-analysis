# Hotel Price Analysis (2012–2016)

End-to-end analysis of hotel pricing data to uncover **seasonality patterns**, detect **outliers**, and **forecast future prices**.

---

## 📌 Problem Statement

Given daily hotel price data (2012–2016), the objectives were:

1. Identify **year-over-year repeating patterns**
2. Detect **outliers** (visually + programmatically)
3. *(Bonus)* Forecast daily prices for **February 2022**

---

## 🧠 Approach

### 1. Seasonality Analysis
- Created **year-over-year overlay line chart** to compare patterns across years
- Built a **heatmap (Year × Month)** for quick pattern recognition

**Insight:**
- Feb–Mar → consistently highest prices  
- Sep–Nov → lowest demand period  
- Clear **upward trend YoY**

---

### 2. Outlier Detection

Used a **hybrid approach**:
- **IQR (Interquartile Range)** → robust to non-normal data
- **Z-Score** → statistical extremeness

**Strategy:**
- Flagged outliers using both methods
- Considered only **overlapping points as high-confidence outliers**

**Findings:**
- 46 (IQR), 19 (Z-score), 19 confirmed
- Strong cluster in **Feb–Apr 2015 → real demand spike**
- Isolated spike (Mar 13, 2015) → likely **data error**

---

### 3. Forecasting (Feb 2022)

Used **Facebook Prophet** with:
- Multiplicative seasonality
- Default changepoint tuning (0.05)

**Why Prophet?**
- Handles **trend + seasonality natively**
- Robust to missing data & outliers
- Produces **confidence intervals**

**Output:**
- Predicted prices: ~$234–$274 range  
- Wide confidence interval due to long forecast horizon

---

## 📊 Key Insights

- Strong **yearly seasonality** driven by demand cycles
- **March 2015 anomaly** indicates real-world event impact
- Data contains **both real anomalies + data errors**
- Forecast reflects **trend continuation**, not external shocks (e.g., COVID)

---

## 📁 Project Structure

- `hotel_price_analysis.ipynb` — Full analysis
- `data/` — Raw dataset
- `requirements.txt` — Dependencies

---

## ⚙️ How to Run

```bash
pip install -r requirements.txt
jupyter notebook