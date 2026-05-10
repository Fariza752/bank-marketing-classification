# 🏦 Bank Marketing Classification

## 📌 Problem
Bankın telefon kampaniyası datasına əsasən müştərinin müddətli əmanətə (term deposit) abunə olub-olmayacağını proqnozlaşdırmaq.

## 📊 Dataset
- 41,188 müştəri, 20 feature
- Mənbə: Kaggle — henriqueyamahata/bank-marketing
- Hədəf dəyişən: `y` (yes/no)
- Dataset imbalanced: yes — 11%, no — 89%

## 🗂️ Addımlar
1. **EDA** — korrelyasiya, paylanma, boxplot, countplot analizi
2. **Feature Selection** — multikollinearlik, data leakage və zəif siqnal əsasında silmə
3. **Outlier Təmizləmə** — IQR metodu ilə clip
4. **Preprocessing Pipeline** — StandardScaler + OneHotEncoder
5. **Modelling** — Logistic Regression, Random Forest, XGBoost
6. **Model Qiymətləndirmə** — Confusion Matrix, ROC Curve, Feature Importance

## 🔍 Feature Selection Qərarları
| Sütun | Səbəb |
|---|---|
| `emp.var.rate` | `euribor3m` ilə 0.97 korrelyasiya |
| `nr.employed` | `euribor3m` ilə 0.91 korrelyasiya |
| `pdays` | ~96% dəyəri 999, real məlumat yoxdur |
| `duration` | Data leakage riski |
| `default` | `yes` kateqoriyası demək olar ki, sıfır |
| `day_of_week` | Hədəflə əlaqəsi yoxdur |

## 📋 Model Nəticələri
| Model | F1 Score | ROC AUC |
|---|---|---|
| Logistic Regression | 0.44 | 0.78 |
| Random Forest | 0.47 | 0.79 |
| **XGBoost** | **0.48** | **0.79** |

## ✅ Nəticə
41,188 müştəridən 4,640-ı abunə oldu (11%).
XGBoost modeli test setindəki həqiqi abunəçilərin 57.65%-ni əvvəlcədən müəyyən edə bildi.
Bank bütün bazaya zəng etmək əvəzinə modelin göstərdiyi müştərilərə
fokuslanaraq kampaniya xərclərini əhəmiyyətli dərəcədə azalda bilər.

## 📦 Kitabxanalar
pandas, numpy, scikit-learn, xgboost, matplotlib, seaborn
