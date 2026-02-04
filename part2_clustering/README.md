# PART 2 – Clustering de jugadors

En aquesta segona part del projecte s’apliquen tècniques de *Machine Learning* no supervisat per agrupar els jugadors segons les seves estadístiques. L’objectiu és identificar diferents perfils de jugador a partir del dataset generat a la Part 1.

El procés de clustering permet analitzar patrons i similituds entre jugadors sense disposar d’etiquetes prèvies.

---

## 📥 Dataset utilitzat

El dataset utilitzat en aquesta part prové del procés d’ETL realitzat a la Part 1 del projecte.

- Fitxer d’entrada: `FEB3_Playbook2_ready.csv`

Aquest fitxer conté les estadístiques agregades a nivell de jugador i és la base per a l’entrenament del model de clustering.

---

## 🔧 Preparació de les dades

Abans d’aplicar el model, es realitzen diverses tasques de preparació:

- Selecció de les variables més rellevants per al clustering
- Eliminació de valors nuls i infinits
- Estandardització de les dades
- Preparació del dataset final per a l’entrenament del model

---

## 📊 Entrenament del model

Per a l’agrupació dels jugadors s’utilitza l’algoritme **K-Means**.

S’han provat diferents valors del nombre de clústers (*k*) per trobar una configuració adequada. Tot i que s’ha analitzat l’opció de **k = 4**, finalment s’ha escollit **k = 2**, ja que ofereix una separació més clara i resultats més coherents amb les dades.

---

## 🏷️ Resultat del clustering

Un cop entrenat el model:

- Cada jugador és assignat a un clúster
- Es genera un dataset final amb la informació del clúster associat a cada jugador
- S’assignen noms esportius als clústers segons les seves característiques predominants

Aquest dataset s’utilitza posteriorment per a l’anàlisi i visualització a Power BI.

---

## 📓 Playbook de clustering

Tot el procés descrit en aquesta part es pot consultar i executar al notebook:

- `FEB3_Part2.ipynb`

---

## ➡️ Connexió amb la Part 3

Les dades generades en aquesta part serveixen com a base per a la interpretació final dels perfils de jugador, que es desenvolupa a la **Part 3 del projecte**.
