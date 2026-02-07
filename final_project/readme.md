Final Project - Census Data Modeling

Acest proiect are ca scop analiza și modelarea unui set de date de tip Census, utilizând tehnici de preprocesare a datelor, regresie clasică, clustering și rețele neuronale. Proiectul este structurat în 5 task-uri principale, fiecare abordând o etapă diferită din pipeline-ul de analiză de date și machine learning.

Structura proiectului:

Task 1 – Preprocesarea datelor Census
Task 2 – Analiză exploratorie a datelor (EDA)
Task 3 – Modelare prin regresie (ML clasic)
Task 4 – Clustering (KMeans, Hierarchical, DBSCAN)
Task 5 – Regresie cu Rețele Neuronale (Neural Networks)

Fiecare task este implementat într-un notebook separat și conține:

•	cod rulabil fără erori,
•	explicații teoretice,
•	interpretarea rezultatelor,
•	concluzii intermediare.

Task 1 – Data Preprocessing (Census)

Obiectiv:

Pregătirea setului de date Census pentru modelare prin:

•	curățare date,
•	tratarea valorilor lipsă,
•	codificarea variabilelor categorice,
•	scalarea variabilelor numerice.

Pași realizați: 

•	Încărcarea dataset-ului original
•	Separarea variabilelor numerice și categorice

Aplicarea:

•	StandardScaler / MinMaxScaler pentru variabile numerice
•	One-Hot Encoding pentru variabile categorice

Salvarea seturilor:

•	X_train, X_val, X_test
•	y_train, y_val, y_test

Concluzie Task 1:

Datele au fost aduse într-un format compatibil cu algoritmii de Machine Learning și Deep Learning, eliminând problemele legate de scale diferite și variabile categoriale neprocesate.

Task 2  Exploratory Data Analysis (EDA)

Obiectiv:

Înțelegerea structurii datelor și a relațiilor dintre variabile.

Pași realizați:

•	Analiza distribuțiilor pentru variabilele numerice
•	Analiza frecvențelor pentru variabilele categorice
•	Identificarea posibilelor relații între:
•	vârstă,
•	educație,
•	capital gain/loss,
•	hours-per-week
•	Observarea dezechilibrelor și a variabilității din date

Concluzie Task 2:

Datele Census sunt complexe, eterogene și cu relații neliniare, ceea ce sugerează că:
•	modelele simple liniare pot fi limitate,
•	modelele mai flexibile (arbori, NN, clustering) pot surprinde mai bine structura datelor.

Task 3 – Regression Modeling (ML Clasic)

Obiectiv:

Construirea și compararea mai multor modele de regresie pentru a prezice hours-per-week.

Modele folosite:

•	SGDRegressor
•	Linear Regression
•	Decision Tree Regressor
•	Ridge Regression

Metrică de evaluare principală:

•	Mean Squared Error (MSE)
(au mai fost raportate și MAE, RMSE, R²)

Experimente:

•	Modele baseline pentru fiecare algoritm
•	Experimente cu:
•	limitarea adâncimii arborilor,
•	regularizare (Ridge),
•	ajustare hiperparametri pentru SGD

Rezultat cheie:

Cel mai bun model pe setul de validare:
Decision Tree Regressor – EXP1 (max_depth=5, min_samples_leaf=20)
Acesta a obținut cel mai mic MSE, reducând overfitting-ul față de varianta baseline.

Concluzie Task 3

•	Modelele liniare au performanțe similare, dar limitate.
•	Decision Tree optimizat surprinde mai bine relațiile neliniare din date.
•	SGDRegressor s-a dovedit instabil și sensibil la hiperparametri.
•	Alegerea modelului final: Decision Tree Regressor (tuned).

Task 4 – Clustering (Census Modeling Clustering)

Obiectiv:

Identificarea grupurilor naturale din datele Census folosind metode de clustering.

Tehnici folosite:

•	KMeans
•	Hierarchical (Agglomerative) Clustering
•	(Opțional) DBSCAN

Determinarea numărului de clustere:

•	Metoda Elbow
•	Vizualizare cu Yellowbrick KElbowVisualizer
•	Valoare aleasă: k = 6

Evaluare clustering:

•	Silhouette Score
•	Scor obținut pentru KMeans (k=6): ~ 0.075
•	Indică separare slabă între clustere, dar acceptabilă pentru date socio-demografice complexe

Vizualizare:

•	Reducerea dimensionalității cu PCA (2 componente)
•	Plot 2D al clusterelor pentru interpretare vizuală

Interpretare:

Există:

•   2 clustere dominante,
•	mai multe clustere mici,
•	un cluster foarte mic (posibil outlieri / profile rare)
•	Structura confirmă eterogenitatea populației Census

Comparație cu Hierarchical Clustering:

•	Silhouette Score mai mic decât KMeans

Concluzie Task 4:

•	KMeans cu k=6 oferă un compromis rezonabil între compactitate și separare
•	Clustering-ul pe date Census este dificil din cauza complexității și dimensionalității ridicate
•	Rezultatele sunt exploratorii, dar utile pentru segmentare socio-demografică

Task 5 – Neural Network Regression

Obiectiv:

Construirea unui model de regresie cu rețea neuronală pentru a prezice hours-per-week și compararea cu un baseline.
Modele construite

1.	Baseline Neural Network (MLPRegressor simplu)
2.	Model mai complex (mai multe straturi / neuroni)

Metrici evaluate:

•	MAE
•	MSE
•	RMSE
•	R² Score

Rezultate:

•	Modelul mai complex:
•	reduce eroarea față de baseline,
•	obține un R² mai bun,
•	arată o capacitate mai mare de a surprinde relații neliniare

Tabel final de comparație

A fost construit un tabel cu:

•	numele modelului,
•	MAE, MSE, RMSE, R²,
•	pentru compararea clară a performanțelor.

Concluzie Task 5:

•	Rețelele neuronale pot depăși modelele simple, dar:
•	necesită tuning atent,
•	sunt mai greu de interpretat,
•	pot overfitta fără regularizare
•	Modelul NN mai complex a fost ales ca model final pentru acest task.

Concluzie Generală:

Acest proiect demonstrează un pipeline complet de:

•	preprocesare date,
•	analiză exploratorie,
•	modelare prin ML clasic,
•	clustering nesupravegheat,
•	modelare cu rețele neuronale.

Pentru datele Census:

•	relațiile sunt complexe și neliniare,
•	modelele bazate pe arbori și rețele neuronale oferă performanțe superioare,
•	clustering-ul oferă insight-uri exploratorii, nu separări perfecte.




