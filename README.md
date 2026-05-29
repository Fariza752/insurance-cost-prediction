# 🛡️ Insurance Cost Prediction

Sığorta məhsulu alış proqnozu üzrə machine learning layihəsi.  
Kaggle dataseti istifadə edilərək müştərinin sığorta xərci (`cost`) proqnozlaşdırılır.

---

## 📊 Dataset

- **Mənbə:** [Kaggle — Insurance Product Purchase Prediction](https://www.kaggle.com/datasets/akhilups/insurance-product-purchase-prediction)
- **Hədəf dəyişən:** `cost` (sığorta xərci)
- **Tip:** Regression

---

## 🔍 İş axını

1. **Data yükləmə və ilkin analiz** — `df.info()`, `df.describe()`
2. **Filtrasiya** — yalnız `record_type == 1` olan müştərilər saxlanıldı
3. **EDA (Kəşfiyyat Analizi)**
   - Yaş, maşın yaşı, risk faktoru paylanmaları
   - Evli/subay, ev sahibi olmağın qiymətə təsiri
   - Ştatlar, günlər üzrə qiymət fərqləri
   - Correlation heatmap
4. **Feature Engineering** — yüksək korrelyasiyalı və zəif sütunlar silindi
5. **Outlier handling** — IQR metodu ilə
6. **Modeling** — Sklearn Pipeline ilə

---

## 🤖 Modellər və Nəticələr

| Model | R2 Score | RMSE | MAE |
|-------|----------|------|-----|
| Linear Regression | 0.447 | 32.11 | 25.15 |
| Random Forest | 0.539 | 29.33 | 22.75 |
| **XGBoost** ✅ | **0.596** | **27.45** | **21.10** |

> Ən yaxşı nəticəni **XGBoost** göstərdi.

---

## 🛠️ İstifadə olunan texnologiyalar

![Python](https://img.shields.io/badge/Python-3.x-blue)
![Sklearn](https://img.shields.io/badge/Scikit--Learn-Pipeline-orange)
![XGBoost](https://img.shields.io/badge/XGBoost-Regressor-green)
![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-lightblue)

- Python, Pandas, NumPy
- Scikit-learn (Pipeline, ColumnTransformer, StandardScaler, OneHotEncoder)
- XGBoost, Random Forest, Linear Regression
- Matplotlib, Seaborn

---

## 📁 Fayllar

```
├── insurance_product_purchase_prediction.ipynb   # Əsas notebook
└── README.md
```

---

## 👤 Müəllif

GitHub: [@sənin_adın](https://github.com/sənin_adın)
