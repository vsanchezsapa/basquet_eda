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

Aquest dataset s’utilitza posteriorment per a l’anàlisi i visualització a un altre playbook a la plart 3.

---

## 📓 Playbook de clustering

Tot el procés descrit en aquesta part es pot consultar i executar al notebook:

- `FEB3_Part2.ipynb`

---

## 🔍 Comparació entre diferents valors de k

Durant el procés de clustering s’han provat diferents valors del nombre de clústers (*k*), concretament *k = 2* i *k = 4*, amb l’objectiu d’analitzar si apareixien perfils de jugador més específics.

Amb *k = 4* s’obtenen subperfils més detallats, com ara jugadors interiors més ofensius o exteriors amb major ús del tir de tres punts. Tot i això, alguns d’aquests clústers presenten comportaments similars i una separació menys clara entre grups.

Per aquest motiu, s’ha optat per *k = 2* com a configuració final, ja que permet identificar dos grans perfils de jugador de manera més clara, coherent i fàcil d’interpretar.

---

## 🏷️ Criteris d’assignació dels perfils de jugador


- **Jugadors físics**
  - Valors elevats en minuts jugats
  - Major nombre de rebots per partit
  - Ús predominant del tir de dos punts
  - Presència constant a pista i joc proper a cistella

- **Jugadors equilibrats**
  - Valors més repartits entre les diferents variables
  - Participació en diverses facetes del joc (rebot, assistències, tir)
  - Absència d’una estadística clarament dominant
  - Perfil polivalent i adaptable


## ➡️ Connexió amb la Part 3

Les dades generades en aquesta part serveixen com a base per a la interpretació final dels perfils de jugador, que es desenvolupa a la **Part 3 del projecte**.
