# 🏬 Integrated Retail Analytics for Store Optimization & Demand Forecasting

> **An End-to-End Machine Learning & Data Analytics Project for Retail Decision Optimization**

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![Machine Learning](https://img.shields.io/badge/Machine%20Learning-Enabled-brightgreen)
![Data Analysis](https://img.shields.io/badge/Data%20Analysis-Complete-orange)
![Forecasting](https://img.shields.io/badge/Demand%20Forecasting-Active-blueviolet)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

---

## 🎯 **Project Goal**

To leverage **machine learning and data analysis** to:
- Optimize **store performance**
- **Forecast demand** accurately
- Enhance **customer experience** through **segmentation** and **personalized marketing strategies**

---

## 🧩 **Project Overview**

This project integrates **three retail datasets** — *sales*, *store information*, and *economic indicators* — to create a unified analytics pipeline.  
It demonstrates advanced **data preprocessing**, **anomaly detection**, **time-series forecasting**, **customer segmentation**, and **strategic insights generation** for store-level optimization.

---

## 📊 **Datasets**

| Dataset | Description | Key Columns |
|----------|--------------|--------------|
| `sales_data_set.csv` | Weekly department-level sales per store | Store, Dept, Date, Weekly_Sales, IsHoliday |
| `stores_data_set.csv` | Store details and type | Store, Type, Size |
| `featres_data_se.csv` | External factors and markdown data | Date, Temperature, Fuel_Price, CPI, Unemployment, MarkDown1–5 |

---

## 🔧 **Data Preprocessing & Feature Engineering**

1. **Datetime Conversion & Sorting**  
   Converted and sorted by `Store`, `Dept`, and `Date` for time-series modeling.

2. **Dataset Merging**  
   Combined all datasets → unified `merged_df` with **(421,570 rows × 17 columns)**.

3. **Missing Value Handling**  
   - Filled missing `MarkDown` values with `0` (assumed inactive markdowns).  
   - Forward/backward-filled economic indicators (CPI, Unemployment, Fuel Price).

4. **Feature Engineering**  
   - Derived `Year`, `Month`, `Week`, `Rolling_Avg_4wk`, and lag features.  
   - Added `markdown_any` flag and `is_anomaly` indicators.

5. **Encoding & Scaling**  
   - Converted categorical fields (`Type`, `IsHoliday`) → numeric/one-hot encoded.  
   - Scaled continuous variables using `StandardScaler`.

---

## 🧠 **Exploratory Data Analysis (EDA)**

### 🔍 1. Anomaly Detection
- Identified **35,521 anomalies** using IQR.
- Outliers corresponded to **holiday spikes**, markdowns, or reporting issues.  
📈 *Visual:* `boxplot_weekly_sales.png`

### 🕒 2. Time Series Trend Analysis
- Strong **seasonality** (peaks in November–December).
- Post-holiday dips observed consistently.  
📈 *Visual:* `total_weekly_sales_trend.png`

### 🎉 3. Holiday vs Non-Holiday Sales
- Holidays significantly **boost weekly sales** across all store types.  
📈 *Visual:* `holiday_sales_comparison.png`

### 🔥 4. Feature Correlation
- `CPI`, `Unemployment`, and `Fuel_Price` had mild correlations with `Weekly_Sales`.
- High multicollinearity avoided by scaling and PCA.  
📈 *Visual:* `correlation_heatmap.png`

### 🛒 5. Department Co-Occurrence (Market Basket Inference)
- Departments with correlated weekly sales hint at **cross-selling potential**.  
📈 *Visual:* `department_co_occurrence_heatmap.png`

---

## 🤖 **Modeling & Forecasting**

### ⚙️ **Train-Test Split**
- 80% training | 20% testing (temporal split by date).

### 📈 **Baseline Model – Linear Regression**
| Metric | Score |
|---------|--------|
| MAE | 1693.66 |
| MSE | 24,388,776.07 |
| R² | **0.9532** |

> Linear Regression explained 95% of variance — a strong baseline.

### 🌲 **Advanced Model – Random Forest Regressor**
| Metric | Score |
|---------|--------|
| MAE | 1446.92 |
| MSE | 14,299,629.13 |
| R² | **0.9726** |

> Improved accuracy and generalization, capturing complex non-linear effects.

### ⭐ **Feature Importance (Top Drivers)**
1. Rolling 4-week sales average  
2. MarkDown1–3  
3. CPI  
4. Store Size  
5. Holiday flag  
📊 *Visual:* `feature_importance.png`

---

## 🏬 **Store Segmentation (K-Means Clustering)**

- Segmented stores into **3 clusters** using sales, size, and economic indicators.
- PCA visualization shows **distinct operational profiles**.  
📈 *Visual:* `store_clusters_pca.png`

| Cluster | Avg Weekly Sales | Store Size | CPI | Unemployment | Profile |
|:--------:|:----------------:|:-----------:|:----:|:-------------:|:--------|
| 0 | 14,842 | Medium | Low | Moderate | Balanced |
| 1 | 23,301 | Large | High | Low | High-performing |
| 2 | 9,095 | Small | High | Low | Growth Potential |

**Silhouette Score:** `0.3345` (moderate, distinct segments)  
**Inertia:** `107.18` (tight clusters)

---

## 💡 **Strategic Insights & Business Recommendations**

| Area | Insight | Recommendation |
|------|----------|----------------|
| 📦 **Demand Forecasting** | Weekly forecast guides stock allocation | Use RF predictions for top-selling departments |
| 🏬 **Store Clusters** | Each segment behaves differently | Large stores → markdowns; small stores → promotions |
| 💰 **Markdown Optimization** | Strong impact on sales uplift | Schedule near holidays & CPI dips |
| ⛽ **Economic Sensitivity** | CPI & Fuel Price influence demand | Adjust pricing & inventory in high-sensitivity zones |
| 🛍 **Cross-Selling** | Related departments found via correlation | Bundle & co-market frequently paired items |
| 🎯 **Personalization** | Cluster-specific targeting improves ROI | Tailor markdowns, regional ads, and inventory |

---

## 🧰 **Tech Stack**

| Category | Tools / Libraries |
|-----------|------------------|
| Programming | Python 3.10+, Jupyter Notebook |
| Data Handling | Pandas, NumPy |
| Visualization | Matplotlib, Seaborn |
| Machine Learning | Scikit-learn, RandomForest, Linear Regression |
| Forecasting | LightGBM, Time-series Lags |
| Clustering | K-Means, PCA |
| Scaling | StandardScaler |
| Deployment | Ngrok / Streamlit (optional dashboard) |

---

## 🧾 **Project Deliverables**

✅ Cleaned & merged datasets  
✅ Exploratory visualizations & anomaly insights  
✅ Forecasting models (baseline + advanced)  
✅ Store segmentation results  
✅ Feature importance analysis  
✅ Business strategy report (`report.pdf`)  
✅ Executable code & reproducible pipeline  

---

## 🏁 **Conclusion**

This project demonstrates how **integrated data analytics and ML models** can drive smarter retail decisions.  
By combining **sales forecasting**, **store segmentation**, and **economic insights**, we achieve data-driven optimization for:
- **Inventory planning**
- **Marketing personalization**
- **Revenue growth**

---


