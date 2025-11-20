# 📦 Delivery-TAT-Optimization-Engine-O2D-O2S-S2A

## 🚚 Delivery TAT Optimization Engine  
**O2D (Order → Dispatch) | O2S (Order → Seller) | S2A (Seller → Attempt)**  
**Lane-Level Forecasting & SLA Optimization for E-Commerce Logistics**

This repository contains a complete **Delivery Turn-Around-Time (TAT) Optimization Engine** designed to forecast, simulate, and optimize delivery performance across three major first-mile logistics legs:

- **O2D — Order to Dispatch**
- **O2S — Order to Seller**
- **S2A — Seller to Attempt**

The goal is to **minimize Breach%**, **boost On-Promise (OP%)**, and keep **2+ Day Before Promise (2+BP%) within business thresholds**, while recommending the **optimal airhdtat per lane**.

This framework mirrors real-world supply-chain modeling used by major e-commerce companies.

---

## 🧩 Why This Project Matters

Small delays in O2D/O2S/S2A legs create downstream failures:

- ❌ Higher breach & CX complaints  
- ❌ SLA misses on promise date  
- ❌ Increased support/ops costs  
- ❌ Last-mile bottlenecks  

This engine solves it by:

- ✔ Predicting lane-wise delivery KPIs  
- ✔ Simulating effects of TAT adjustments  
- ✔ Optimizing TAT with business constraints  
- ✔ Producing ready-to-use recommendations  

---

## ✨ Key Features

### **1. Lane-Level Forecasting Models**
Each leg (O2D, O2S, S2A) includes its own ML pipeline using:

- `RandomForestRegressor`  
- Lane-level encoding  
- Historical KPIs  
- Feature importance  

The models forecast:

- **On-Promise%**  
- **1 Day Before Promise%**  
- **2+ Day Before Promise%**  
- **Breach%**

---

### **2. Constraint-Driven TAT Optimization Engine**

The optimizer evaluates candidate TAT values per lane based on strict business rules.

#### 🔹 Primary Goals

- Drive **Breach% to ~7.5%** (acceptable range: **7.5–11%**)  
- Maintain **2+BP% in the 20–25% band**  
- Improve **OP% whenever possible**

#### 🔹 Smart Adjustment Logic

- Low-volume lanes with high breach → *carefully increase TAT*  
- High-performing lanes → *reduce TAT*, allowing slight breach increase (≤ 11%)  
- High-breach lanes (>9%) → optimize into acceptable range  
- Network constraint → total **2+BP must stay within allowed threshold**  

---

### **3. Simulation Engine**

For each lane, the engine:

- Runs predictions across multiple TAT options  
- Rejects options violating constraints  
- Selects best TAT based on OP, 1BP, 2BP, Breach  
- Produces clean Excel reporting  

---

### **4. Clean Excel Output for Business Teams**

Exports a single Excel file containing:

- Baseline KPIs  
- Optimized KPIs  
- Recommended TAT  
- Percentage shifts  
- Notes & insights  

---

## 🔬 Methodology Overview

### **1. Data Engineering**

- Clean & standardize delivery events  
- Enrich with clusters, logistics partner, metadata  
- Create unique `lane_id`  
- Label encode lanes  
- Compute KPIs at daily & monthly levels  

### **2. Machine Learning Models**

Random Forest regressors trained for:

- Breach%  
- 1BP%  
- 2+BP%  
- On-Promise%  

Includes:

- Hyperparameter tuning  
- Model validation  
- Feature importance plots  

### **3. Optimization Logic**

For each lane:

- Simulate multiple TATs  
- Predict delivery KPIs  
- Apply constraints  
- Select best TAT  
- Maintain network-level feasibility  

### **4. Reporting & Outputs**

Automated Excel export includes:

- Current vs optimized TAT  
- KPI deltas  
- Lane-level recommendations  
- Flags for manual review  

---

## 🛠️ Tech Stack

- **Python 3.x**  
- **pandas, numpy**  
- **scikit-learn**  
- **openpyxl**  
- **matplotlib / seaborn**  
- **RandomForestRegressor**  
- **Jupyter Notebook**

---

## ▶️ How to Use

### **1. Explore the Notebooks**

Each folder (`O2D/`, `O2S/`, `S2A/`) includes a complete pipeline:

- Data preprocessing  
- KPI generation  
- Model training  
- TAT simulation  
- Optimization logic  
- Visualizations  

### **2. Run TAT Optimization**

Use notebook functions to compute:

- Baseline KPIs  
- Optimized KPIs  
- Final TAT recommendations  

### **3. Export Results**

Automatic Excel output includes:

- Lane ID  
- Current vs recommended TAT  
- KPI improvements  
- Reasoning notes  

---

## 📁 Repository Structure (Recommended)

