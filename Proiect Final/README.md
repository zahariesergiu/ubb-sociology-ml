 # Raport final — Census (Adult) Dataset (Tasks 1–5)

Structura proiectului
- Final_Project_Task_1_Census_Data_Preprocess.ipynb
- Final_Project_Task_2_Census_EDA.ipynb
- Final_Project_Task_3_Census_Modeling_Regression.ipynb
- Final_Project_Task_4_Census_Modeling_Clustering.ipynb
- Final_Project_Task_5_Census_Modeling_NN_Regression.ipynb
- test_preprocessed.csv
- train_preprocessed.csv

### Final_Project_Task_1_Census_Data_Preprocess.ipynb

În acest task a fost realizată etapa completă de preprocesare a datelor pentru setul de date Adult Census, în vederea construirii unui model de regresie.

### Descriere generală

Datasetul conține 48.842 observații și 15 variabile socio-demografice. Variabila țintă a proiectului este hours-per-week, o variabilă numerică continuă ce reprezintă numărul de ore lucrate pe săptămână.

Pași realizați:

- Încărcarea și inspectarea datelorȘDatasetul a fost încărcat din UCI / OpenML, iar structura, tipurile de date și distribuția variabilei țintă au fost analizate.
- Curățarea datelor
- Standardizarea valorilor categorice (eliminarea spațiilor inutile).
- Eliminarea observațiilor duplicate.
- Verificarea și gestionarea valorilor lipsă (după curățare, datasetul nu conține valori lipsă).
- Detectarea și tratarea outlierilor
- Identificarea outlierilor folosind regula IQR (1.5 × IQR).
- Aplicarea capping (winsorization) pe variabilele numerice explicative.
- Variabila țintă hours-per-week nu a fost modificată.
- Datele au fost separate în set de antrenare (80%) și set de testare (20%).
- Standardizare și encoding
- Variabilele numerice au fost standardizate cu StandardScaler.
- Variabilele categorice au fost transformate prin OneHotEncoder.
- Transformările au fost învățate exclusiv pe setul de antrenare pentru a evita data leakage.
- Feature Engineering
- Crearea de variabile derivate (ex: capital_net, has_capital, high_edu).
- Discretizarea vârstei (age_bin).
- Simplificarea relațiilor familiale și a statutului marital.
- Salvarea rezultatelor

După preprocesare, setul de antrenare conține 26.029 observații și 122 coloane, iar setul de test 6.508 observații cu aceeași structură. Datele sunt complet numerice și pregătite pentru etapele de modelare și evaluare.

### Final_Project_Task_2_Census_EDA.ipynb

În acest task a fost realizată analiza exploratorie a datelor (EDA) pentru setul de date Adult Census, cu scopul de a înțelege distribuțiile variabilelor și relațiile dintre acestea înainte de etapa de modelare.

Pași realizați:
- Am analizat structura datasetului și tipurile de variabile (numerice și categorice).
- Am studiat distribuția variabilei țintă hours-per-week și principalele caracteristici statistice.
- Am analizat distribuțiile variabilelor numerice (ex: age, education-num, capital-gain, capital-loss).
- Am explorat variabilele categorice (ex: workclass, education, marital-status, occupation) folosind frecvențe și vizualizări.
- Am investigat relațiile dintre variabilele explicative și variabila țintă pentru a identifica tipare relevante.
- Am evidențiat prezența valorilor extreme și dezechilibrele din date, motivate ulterior în etapa de preprocessing.

Analiza EDA a oferit o înțelegere clară a structurii și distribuției datelor, confirmând ipotezele necesare pentru alegerea tehnicilor de preprocesare și pentru pașii următori de modelare.


### Final_Project_Task_3_Census_Modeling_Regression.ipynb

În acest task a fost realizată etapa de modelare și evaluare pentru problema de regresie, având ca obiectiv prezicerea variabilei hours-per-week pe baza datelor preprocesate în Task 1.

Pași realizați:
- Încărcarea datelor preprocesate
- Definirea modelelor de regresie
- A fost antrenat un model de bază (Linear Regression) pentru stabilirea unui baseline.
- Au fost testate modele de regresie regularizată:Ridge Regression. Lasso Regression.
- Modelele au fost comparate pentru a evalua impactul regularizării asupra performanței.
- Antrenare și validare
- Modelele au fost antrenate pe setul de antrenare.
- A fost utilizată validarea încrucișată (cross-validation) pentru evaluarea stabilității modelelor.
- Selecția modelului final
- Performanțele modelelor au fost comparate pe setul de test.
A fost ales modelul cu cel mai bun compromis între eroare și capacitatea de generalizare.


Modelul selectat oferă o performanță superioară față de baseline și este capabil să surprindă relațiile dintre caracteristicile socio-demografice și numărul de ore lucrate pe săptămână.
Acesta poate fi utilizat în etape ulterioare pentru îmbunătățiri sau pentru interpretarea coeficienților.

### Final_Project_Task_4_Census_Modeling_Clustering.ipynb

În acest task a fost realizată o analiză de învățare nesupravegheată (clustering) pe setul de date Adult Census, cu scopul de a identifica grupuri naturale de indivizi pe baza caracteristicilor socio-demografice.

Pași realizați

- Pregătirea datelor pentru clustering
- Au fost utilizate datele numerice preprocesate din Task 1.
- Variabilele au fost standardizate pentru a evita influența disproporționată a scalelor diferite.
- Variabila țintă nu a fost utilizată, conform principiilor de învățare nesupravegheată.
- Alegerea numărului de clustere
- A fost aplicată metoda Elbow pentru a analiza variația inerției în funcție de numărul de clustere.
- A fost utilizat Silhouette Score pentru evaluarea calității clusterelor.
- Numărul optim de clustere a fost ales pe baza ambelor criterii.
- Aplicarea algoritmilor de clustering
- A fost aplicat algoritmul K-Means pentru segmentarea observațiilor.
- Modelul a fost antrenat folosind numărul optim de clustere identificat anterior.
- Analiza și interpretarea clusterelor
- A fost analizată distribuția observațiilor în fiecare cluster.
- Au fost comparate valorile medii ale caracteristicilor pentru fiecare cluster.
- Au fost identificate tipare socio-demografice distincte între clustere.
- Rezultatele clusteringului au fost vizualizate folosind proiecții 2D ale datelor (ex: PCA).
- Vizualizările au fost utilizate pentru a evalua separabilitatea clusterelor.

Clusteringul a evidențiat grupuri distincte de indivizi cu caracteristici similare, oferind o perspectivă suplimentară asupra structurii interne a datelor.
Aceste rezultate pot fi utilizate pentru segmentare, analiză comportamentală sau ca suport pentru modele predictive viitoare.


### Final_Project_Task_5_Census_Modeling_NN_Regression.ipynb

În acest task a fost implementat un model de regresie bazat pe rețele neuronale artificiale, cu scopul de a prezice variabila hours-per-week folosind datele preprocesate din task-urile anterioare.

Pași realizați

- Au fost utilizate datele preprocesate (complet numerice).
- Datele au fost împărțite în set de antrenare și set de test.
- A fost aplicată standardizarea caracteristicilor pentru a asigura stabilitatea antrenării rețelei neuronale.
- Definirea arhitecturii rețelei neuronale
- A fost construit un model de tip feedforward (Multilayer Perceptron).
- A fost utilizată funcția de pierdere Mean Squared Error (MSE).
- Antrenarea modelului
- Modelul a fost antrenat pe setul de antrenare pentru un număr fix de epoci.
- A fost monitorizată evoluția erorii pe datele de antrenare și validare.
- Au fost utilizate tehnici de regularizare implicită (ex: optimizator adaptiv).
- Evaluarea performanței
- Performanța rețelei neuronale a fost comparată cu modelele clasice de regresie din Task 3.


Modelul bazat pe rețea neuronală a reușit să capteze relații neliniare dintre variabilele de intrare și variabila țintă, obținând o performanță comparabilă sau superioară modelelor liniare.
