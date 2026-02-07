# Final Project — Census (Adult) Dataset (Tasks 1–5)

Proiect de Machine Learning aplicat pe datasetul **UCI Adult (Census)**.  
Problema principală: **regresie**, cu variabila țintă **`hours-per-week`**.  
Sunt explorate atât metode de **învățare supervizată** (regresie), cât și **nesupervizată** (clustering).

---

## Structura proiectului

- `Final_Project_Task_1_Census_Data_Preprocess.ipynb`
- `Final_Project_Task_2_Census_EDA.ipynb`
- `Final_Project_Task_3_Census_Modeling_Regression.ipynb`
- `Final_Project_Task_4_Census_Modeling_Clustering.ipynb`
- `Final_Project_Task_5_Census_Modeling_NN_Regression - Optional.ipynb`
- `preprocessed_train_task1.csv`
- `preprocessed_test_task1.csv`

---

## Task 1 — Data Preprocessing

**Obiectiv:** pregătirea datelor pentru regresie.

**Pași principali:**
- încărcare dataset UCI Adult
- inspecție inițială (tipuri de date, valori lipsă, duplicate)
- eliminare duplicate (**24 rânduri**)
- eliminare coloana `income` (nu este folosită în regresie)
- curățare variabile categorice (strip)
- feature engineering:
  - `capital_total`
  - `experience_estimate`
  - `has_capital`
- tratarea outlierilor prin **IQR winsorization**
- split train/test (80/20) înainte de preprocessing
- pipeline:
  - numeric: `SimpleImputer(median)` + `StandardScaler`
  - categoric: `SimpleImputer(most_frequent)` + `OneHotEncoder`
- export date preprocesate:
  - `preprocessed_train_task1.csv`
  - `preprocessed_test_task1.csv`

---

## Task 2 — Exploratory Data Analysis (EDA)

**Obiectiv:** înțelegerea distribuțiilor și relațiilor din date.

**Analize realizate:**
- distribuția variabilei țintă `hours-per-week` (histogramă, boxplot, violin)
- statistici descriptive
- verificare valori lipsă
- identificare outlieri pe variabile numerice
- corelații numerice cu targetul
- relații între variabile categorice și orele lucrate
- EDA repetat pe datasetul preprocesat (Task 1)

**Concluzie:**  
`hours-per-week` este concentrat în jurul valorii 40; relațiile liniare sunt slabe, indicând o problemă socio-economică complexă.

---

## Task 3 — Modeling: Regresie clasică

**Date:** seturile preprocesate din Task 1 + split train/validation.

**Modele evaluate:**
- SGDRegressor
- Linear Regression
- Decision Tree Regressor
- Random Forest Regressor
- Ridge Regression
- Lasso Regression

**Metrici:** MAE, MSE, RMSE, R²  
**Metrică principală:** RMSE

**Rezultat:**
- **Random Forest** a obținut cele mai bune rezultate pe setul de test  
  (MAE ≈ 4.3, RMSE ≈ 5.5, R² ≈ 0.21)

Sunt analizate și importanțele feature-urilor, precum și relația Actual vs Predicted.

---

## Task 4 — Modeling: Clustering

**Obiectiv:** identificarea unor tipare nesupervizate în date.

**Date:** train set preprocesat (fără `hours-per-week`).

**Metode utilizate:**
- **K-Means**
  - selecția lui K prin metoda Elbow (K = 5)
  - Silhouette Score ≈ 0.11
  - vizualizare 2D cu PCA
- **Hierarchical Clustering**
  - dendrogramă (subset)
  - Agglomerative Clustering (K = 5)
- **DBSCAN**
  - identifică multe puncte de tip noise
  - performanță slabă pentru acest set de date

**Concluzie:**  
K-Means oferă cea mai interpretabilă soluție; clusterele diferă în principal prin vârstă, experiență și numărul de ore lucrate.

---

## Task 5 — Neural Networks Regression (Opțional)

**Obiectiv:** compararea modelelor clasice cu rețele neuronale.

**Modele testate:**
- baseline NN (Dense 64, ReLU, loss=MSE)
- arhitecturi mai adânci cu Dropout și EarlyStopping
- comparație loss: MSE vs Huber
- tuning pentru learning rate și batch size

**Rezultat final:**
- cel mai bun model NN:
  - RMSE ≈ 5.34
  - R² ≈ 0.26

Modelele NN oferă un mic câștig față de regresia clasică, dar fără îmbunătățiri majore.

---

## Concluzie generală

Datasetul Census prezintă relații socio-economice complexe și zgomotoase.  
Modelele obțin performanțe moderate, iar diferențele dintre abordările clasice și cele neurale sunt limitate. Clusteringul confirmă existența unor grupuri coerente, dar cu separare parțială.