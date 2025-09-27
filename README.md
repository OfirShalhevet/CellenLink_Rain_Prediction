## 📌 Introduction
This project explores environmental sensing with a focus on **rain detection in urban environments** using an alternative to traditional rain gauges.  
We apply **opportunistic sensing** – leveraging existing cellular infrastructure as a cost-effective, real-time monitoring system.  

Rain causes **signal attenuation** in Commercial Microwave Links (CMLs).  
By monitoring this attenuation, we treat CMLs as **virtual rain sensors**.

---

## 🌍 Motivation
Traditional rainfall monitoring tools (gauges, radars) face challenges:
- Limited spatial coverage  
- High deployment and maintenance cost  

CMLs offer key advantages:
- Widespread availability in both urban and rural areas  
- Natural attenuation effect by rain → indirect yet effective sensing  
- Cost-efficient and scalable  
- Real-time estimation at large spatial scales  

---

## 🎯 Project Goals
- **Detect rainfall** from microwave link attenuation  
- **Classify rainfall intensity** into categories (no rain, light, moderate, heavy)  
- **Aggregate multiple links** to improve spatial accuracy across several kilometers  

---

## 🛠 Methodology
- **Data:** CML attenuation and rain gauge data from Sweden  
- **Feature Engineering:**  
  - Attenuation change rate  
  - Rolling mean (3)  
  - Lagged attenuation (2)  
  - Variance change rate  
- **Classification Method:**  
  - Multiclass Logistic Regression (L1 regularization)  
  - Decision based on maximum probability per category  

### Spatial Models
- **Median-Based Multi-Link Model:** Aggregates individual link predictions using the median.  
- **Unified Spatial Network Model:** Uses combined probability distribution for higher spatial robustness.  

---

## 🤖 Final Model
Our best-performing model: **Spatial Logistic Regression with L1 regularization**  
- Aggregates predictions across multiple links → robust against local noise  
- Covers rainfall across **kilometers**, unlike gauges that only measure at a single point  
- Provides **multiclass classification**:  
  - (0) No rain: 0 mm/h  
  - (1) Light: 0–2.5 mm/h  
  - (2) Moderate: 2.5–10 mm/h  
  - (3) Heavy: >10 mm/h  

---

## 📊 Results
- Both Median and Unified models achieved **high QWK (>0.8)**, **low RMSE (<0.05)**, and **low MAE (~0.1)** across gauges and periods.  
- **Median model:** Simple, robust, comparable accuracy to the unified model.  
- **Unified model:** Slightly better RMSE & MAE, better at capturing spatial patterns, but more complex.  
- Both models under-detect light rain during very dry periods.  
- Logistic Regression **outperformed the Power Law baseline**, especially in noisy, complex environments.  

---

## 🔮 Future Work
- Enhance feature engineering for spatial models  
- Add binary correction mechanism for light rain detection  
- Incorporate link direction, length, and multi-gauge data  
- Apply adaptive time windows (short for high variability, long for stable signals)  
- Move towards **real-time rainfall nowcasting** with live CML networks  

---

## 📂 Repository Contents
- `notebooks/` → Jupyter Notebook with full code & experiments  
- `Poster.png` → Final academic poster  
- `Report.pdf` → Detailed written report  
- `README.md` → Project overview  

---

✨ This project combines **feature engineering, spatial processing, and machine learning** into a robust framework for rainfall monitoring.  
It offers a promising foundation for **environmental forecasting applications**, especially where real-time, area-wide rainfall detection is required.  
