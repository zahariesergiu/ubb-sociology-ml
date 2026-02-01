Raport task 1 Census Data Preprocess:
Acest fișier realizează preprocesarea completă a datasetului Adult Income (UCI) pentru o problemă de regresie, având ca variabilă țintă hours-per-week. Scopul este obținerea unui set de date curat, numeric și gata pentru antrenarea modelelor de machine learning.
Pașii de preprocesare:
1. Încărcarea datelor
2. Curățarea datelor
-Eliminarea rândurilor duplicate
-Curățarea string-urilor (eliminare spații inutile)
3. Tratarea valorilor lipsă
--Variabile numerice: imputare cu mediana
-Variabile categorice: imputare cu moda
4. Tratarea outlierilor
-Detectare folosind metoda IQR
-Limitarea valorilor extreme (capping)
5. Feature Engineering
-Eliminarea coloanei redundante education
-Transformarea variabilei income în format binar
-Aplicarea transformării logaritmice pentru capital-gain și capital-loss
6. Encoding și scalare
-One-Hot Encoding pentru variabilele categorice
-Standardizare (mean = 0, std = 1) pentru variabilele numerice
7. Împărțirea datelor
-80% date pentru antrenare
-20% date pentru testare

Raport task 2 EDA:
Pașii EDA (dataset brut)
- Tratarea valorilor lipsă codificate ca "?"
- Analiza distribuției variabilei "hours-per-week" (histograme, boxplot)
- Calculul statisticilor descriptive (mean, median, std)
- Identificarea valorilor lipsă și a outlierilor
- Analiza distribuțiilor pentru variabile numerice și categorice
- Explorarea corelațiilor dintre variabilele numerice

Concluzii principale:
- Variabila "hours-per-week" este concentrată în jurul valorii de 40 de ore, indicând un model dominant de muncă full-time
- Dataset-ul brut conține valori lipsă în variabile categorice și outlieri semnificativi
- Distribuția este asimetrică, cu outlieri semnificativi

Raport task 3 Census Modelling Regression:
Am utilizat seturile de date preprocesat din task 1 train_preprocessed.csv și test_preprocessed.csv.
Setul de antrenare a fost împărțit în train (80%) și validation (20%), iar setul de test a fost păstrat separat pentru evaluarea finală.
Modelele implementate și comparate sunt:
-Linear Regression (baseline)
-SGD Regressor (gradient descent)
-Decision Tree Regressor
-Random Forest Regressor
-Ridge Regression
-Lasso Regression
-Polynomial SGD (experimentare)
Performanța modelelor a fost evaluată folosind MAE, MSE, RMSE și R².
RMSE am ales ca metrică principală, deoarece este ușor de interpretat în unitățile variabilei țintă (ore/săptămână).

Rezultate:
-Modelele liniare (Linear, Ridge, Lasso) au avut performanțe stabile, dar limitate.
-Modelele bazate pe SGD și Decision Tree au avut performanțe slabe în configurația actuală.
-Random Forest Regressor a obținut cele mai bune rezultate pe setul de validare și a fost selectat ca model final.

Raport task 4 Census Modelling Clustering:
Am utilizat setul de date obținut în task 1: train_preprocessed.csv
Setul de date conține informații demografice și economice despre indivizi (vârstă, educație, ore lucrate etc.).

Pentru clustering au fost selectate doar variabile numerice, deoarece algoritmii utilizați se bazează pe distanțe:
-age
-education-num
-capital-gain
-capital-loss
-hours-per-week
Toate variabilele au fost standardizate folosind StandardScaler.

K-Means
Algoritmul K-Means a fost aplicat pe datele standardizate.
Numărul optim de clustere a fost determinat folosind Elbow Method (implementată manual, fără yellowbrick, pentru compatibilitate cu Python ≥ 3.12).
Analiza grafică indică K = 4 ca valoare optimă.
Evaluare:
Silhouette Score: 0.33
Separare moderată a clusterelor, specifică datelor socio-economice reale.

A fost aplicată PCA pentru reducerea dimensionalității.
Clusterele au fost proiectate în 2D pentru o interpretare vizuală.
Rezultatele confirmă structura identificată de K-Means.

Metode alternative:
A fost aplicat Agglomerative Clustering.
Silhouette Score: 0.309
Rezultate comparabile cu K-Means, dar ușor inferioare.
DBSCAN nu a identificat suficiente clustere distincte.
Datele nu prezintă structuri de densitate clar delimitate.
Metoda nu este potrivită pentru acest dataset.

Concluzii:
-K-Means (K = 4) oferă cea mai bună soluție pentru acest set de date.
-Metoda este eficientă, ușor de interpretat și susținută de metrici.
-Clusteringul ierarhic este o alternativă validă, dar nu superioară.
-DBSCAN nu este adecvat pentru structura datelor analizate.