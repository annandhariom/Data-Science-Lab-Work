# 📊 Economic Recession Prediction Using Machine Learning

## 📌 Overview
This project builds a machine learning pipeline to **predict U.S. economic recessions 3 months in advance** using macroeconomic data from the Federal Reserve (FRED-MD dataset).  

Recessions have major economic impact, and early prediction helps governments, businesses, and investors make better decisions.

---

## 🎯 Objectives
- Build a **reproducible ML pipeline** for recession prediction  
- Handle **severe class imbalance (~12% recession months)**  
- Compare multiple ML models fairly  
- Identify **key economic indicators** driving recession predictions  

---

## 📂 Dataset
Two datasets were used:

1. **FRED-MD Dataset**
   - 143 macroeconomic variables  
   - Monthly data (1959–2024)  
   - Covers labor, interest rates, housing, inflation, etc.

2. **USREC (Target Variable)**
   - Binary indicator  
   - `1 = Recession`, `0 = Expansion`

---

## 📊 Data Summary
- Total observations: **791 months**  
- Final dataset: **774 rows × 170 features**  
- Recession months: **~12%**  
- Forecast horizon: **3 months ahead**

---

## ⚙️ Data Preprocessing
- Applied **stationarity transformations (tcode 1–7)**  
- Removed outliers using **10×IQR rule**  
- Handled missing values using:
  - Forward fill  
  - Backward fill  
  - Zero fill  
- Converted dates using `pd.to_datetime()`  
- Merged datasets on time index  

---

## 🧠 Feature Engineering (27 Features)
To capture time-based patterns:

### 🔹 Lag Features (20)
For:
- UNRATE (unemployment)  
- GS10 (10-year yield)  
- INDPRO (industrial production)  
- TB3SMFFM (yield spread)  
- CPIAUCSL (inflation)  

At lags: **1, 3, 6, 12 months**

---

### 🔹 Rolling Features (6)
- UNRATE rolling mean (3, 6, 12 months)  
- UNRATE rolling std (3, 6, 12 months)

---

### 🔹 Binary Feature (1)
- `YieldSpread_negative` (1 if yield curve inverted)

---

## 🤖 Models Used
- Logistic Regression ✅ (Best Model)
- Random Forest  
- Gradient Boosting  
- Support Vector Machine (SVM)

---

## ⚖️ Handling Class Imbalance
- Used `class_weight='balanced'`  
- Threshold optimization (0.05 → 0.90 search)  
- Evaluated using:
  - AUC-ROC (primary)
  - Recall
  - Precision
  - F1-score  

---

## 📈 Results

| Model                | AUC-ROC | Recall | Precision | F1 Score |
|---------------------|--------|--------|----------|---------|
| Logistic Regression | 0.9739 | 1.00   | 0.25     | 0.40    |
| Random Forest       | 0.1928 | 0.00   | 0.00     | 0.00    |
| Gradient Boosting   | 0.5098 | 0.00   | 0.00     | 0.00    |
| SVM                 | 0.8072 | 1.00   | 0.03     | 0.06    |

---

## 🏆 Key Findings
- Logistic Regression outperformed complex models  
- Threshold optimization was **critical**  
- Top predictors:
  - Rolling unemployment rate  
  - Yield curve spread  

---

## 📊 Key Visualizations
- Class distribution  
- ROC curves  
- Confusion matrices  
- Feature importance  
- Recession probability timeline  

---

## 🚨 Challenges
- Severe class imbalance  
- Very few recession samples (only 9 episodes)  
- Models biased toward predicting expansion  

---

## ⚠️ Limitations
- Used **revised data (not real-time)**  
- Small number of recession events  
- No SHAP interpretability  
- Single forecast horizon (3 months)

---

## 🔮 Future Work
- Use **ALFRED real-time data**  
- Apply **SHAP for explainability**  
- Try **LSTM / deep learning models**  
- Test multiple forecast horizons  

---

## 🛠️ Technologies Used
- Python  
- Pandas, NumPy  
- Scikit-learn  
- Matplotlib, Seaborn  

---

## 📁 Project Structure
Advance Project/
│
├── Recession_Prediction_Notebook.ipynb
├── Final_Report.docx
├── model_results.csv
├── feature_importance.csv
└── README.md


---

## 🧠 Key Learning
> Proper handling of class imbalance and threshold tuning is more important than model complexity in rare-event prediction problems.

---

## 📜 References
- McCracken & Ng (2016) – FRED-MD Dataset  
- Papadopoulos et al. (2020) – ML for recession prediction  
- Estrella & Mishkin (1998) – Yield curve indicator  

---

## 👤 Author
**Hariom Anand**  
Golden Gate University  
DATA110 – Machine Learning Project  

---

## ⭐ Acknowledgment
Guided by **Dr. Durga Sharma**
