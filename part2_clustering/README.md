# PART 2 – Clustering de jugadors

En aquesta segona part del projecte s’apliquen tècniques de *Machine Learning* no supervisat per agrupar els jugadors segons les seves estadístiques. L’objectiu és identificar diferents perfils de jugador a partir del dataset generat a la Part 1.

El procés de clustering permet analitzar patrons i similituds entre jugadors sense disposar d’etiquetes prèvies.

---

## 📥 Dataset utilitzat

El dataset utilitzat en aquesta part prové del procés d’ETL realitzat a la Part 1 del projecte.

- Fitxer: `FEB3_Playbook2_ready.csv`

Aquest fitxer conté les estadístiques agregades a nivell de jugador i és la base per a l’entrenament del model de clustering.

---

## 🔧 Preparació de les dades

Abans d’aplicar el model, es realitzen diverses tasques de preparació:

- Selecció de les variables més rellevants per al clustering
- Eliminació de valors nuls i infinits
- Estandardització de les dades mitjançant `StandardScaler`

Aquests passos són necessaris per garantir un funcionament correcte de l’algoritme K-Means.

---

## 📊 Entrenament del model

Per a l’agrupació dels jugadors s’utilitza l’algoritme **K-Means**.  
S’han provat diferents valors del nombre de clústers (*k*) per trobar una configuració adequada:

- Mètode Elbow (inèrcia)
- Mètrica Silhouette

Tot i que s’han analitzat diversos valors de *k*, finalment s’ha escollit **k = 2**, ja que ofereix una separació més clara i resultats més coherents amb les dades.

---

## 🏷️ Assignació i interpretació dels clústers

Un cop entrenat el model:

- Cada jugador és assignat a un clúster
- Es calcula una taula resum amb les mitjanes de cada variable per clúster
- S’assignen noms esportius als clústers segons les característiques predominants

Aquesta interpretació permet entendre millor quin tipus de jugador representa cada grup.

---

## 📈 Visualització dels resultats

Per facilitar la interpretació visual del clustering, s’utilitza una reducció de dimensions mitjançant **PCA (2 components)**.  
Aquesta visualització permet observar com es distribueixen els jugadors segons el clúster assignat.

---

## 📓 Playbook de clustering

Tot el procés descrit en aquesta part es pot consultar i executar al notebook:

- `FEB3_Part2.ipynb`

Aquest playbook inclou la preparació de dades, entrenament del model, visualitzacions i comentaris finals dels resultats.

---

## ➡️ Connexió amb la Part 3

Els resultats obtinguts en aquesta part serveixen de base per a la interpretació final dels perfils de jugador, que es desenvolupa a la **Part 3 del projecte**.

