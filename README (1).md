# 🛡️ Insurance Cost Prediction

Kaggle dataseti istifadə edilərək müştərinin sığorta xərci (`cost`) proqnozlaşdırılır.  
Linear Regression, Random Forest və XGBoost modelləri müqayisə edilib, ən yaxşı nəticəni **XGBoost** göstərib.

---

## 📊 Dataset

- **Mənbə:** [Kaggle — Insurance Product Purchase Prediction](https://www.kaggle.com/datasets/akhilups/insurance-product-purchase-prediction)
- **Hədəf dəyişən:** `cost` (sığorta xərci)
- **Tip:** Regression

---

## 🔍 İş axını

1. **Data yükləmə və ilkin analiz** — `df.info()`, `df.describe()`
2. **Filtrasiya** — yalnız `record_type == 1` olan müştərilər saxlanıldı (son alış nöqtəsi)
3. **EDA (Kəşfiyyat Analizi)** — boxplot, lineplot, heatmap, histplot
4. **Sütunların silinməsi** — aşağıda izah edilib
5. **Outlier handling** — IQR metodu ilə
6.  **Modeling** — Sklearn Pipeline ilə 3 model quruldu:
   - Numeric features: `SimpleImputer (median)` → `StandardScaler`
   - Categorical features: `SimpleImputer (most_frequent)` → `OneHotEncoder`
   - `ColumnTransformer` ilə preprocessing birləşdirildi
   - Hər model ayrıca Pipeline-a sarıldı

---

## 🗑️ Niyə bəzi sütunlar silindi?

| Sütun | Silinmə səbəbi |
|-------|----------------|
| `age_oldest` | `age_youngest` ilə korrelyasiyası çox yüksək idi (~0.97), ikisi eyni məlumatı daşıyırdı |
| `C_previous` | `cost` ilə boxplot quruldu, qruplar arasında demək olar ki fərq yox idi — proqnoza töhfəsi yox idi |
| `married_couple` | `cost` ilə boxplot quruldu, medianlar demək olar eyni idi — fərqləndirici deyildi |
| `location` | Çox geniş dağılım, boxplot-da heç bir aydın pattern yox idi |
| `time` | Həddindən artıq dağınıq dağılım — model üçün səs-küy yaradırdı |
| `day` | Günlər arasında qiymət fərqi yox idi — boxplot bunu göstərdi |

---

## 📈 EDA — Maraqlı Nəticələr

**Yaş və Risk:**  
Gənc sürücülərin risk faktoru daha yüksəkdir, yaş artdıqca risk azalır. Bu sığorta sənayesinin ümumi məntiqi ilə üst-üstə düşür.

**Maşın yaşı və qiymət:**  
Təzə maşınlar daha baha sığortalanır, köhnəldikcə qiymət aşağı düşür. 60 yaşdan yuxarı maşınlarda isə qeyri-müəyyənlik artır — nadir avtomobil effekti ola bilər.

**Evlilik vəziyyəti:**  
Evli cütlüklər orta hesabla subaylara nisbətən bir qədər az sığorta haqqı ödəyirlər — lakin fərq o qədər də böyük deyil ki, model üçün əhəmiyyətli olsun.

**Ştatlar:**  
Ştatlar arasında qiymət fərqi var, lakin daxili dağılım çox genişdir — yəni eyni ştatda çox fərqli qiymətlər mövcuddur.

---

## 🤖 Modellər və Nəticələr

| Model | R2 Score | RMSE | MAE |
|-------|----------|------|-----|
| Linear Regression | 0.447 | 32.11 | 25.15 |
| Random Forest | 0.539 | 29.33 | 22.75 |
| **XGBoost** ✅ | **0.596** | **27.45** | **21.10** |

> Ən yaxşı nəticəni **XGBoost** göstərdi.

---

## 💡 Niyə nəticələr o qədər yüksək deyil?

R2 ~0.60 orta səviyyədir və bu gözləniləndir, çünki:
- Sığorta qiyməti yalnız datasettəki featurlardan asılı deyil — tibbi tarix, sürüş rekordları, şəxsi kredit tarixi kimi məlumatlar yoxdur
- `cost` sütununun dağılımı geniş və qeyri-bərabərdir, bu da modelin proqnoz dəqiqliyini aşağı salır
- Silinən sütunların əksəriyyəti `cost` ilə zəif əlaqə göstərdi — yəni datasetin özündə məhdudiyyət var

Bu layihədən əsas dərs: **yaxşı data olmadan yaxşı model olmur.**

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

GitHub: [@Fariza752](https://github.com/Fariza752)
