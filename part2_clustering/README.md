# PART 2 – Clustering de jugadors

En aquesta segona part del projecte s’apliquen tècniques de Machine Learning no supervisat per agrupar els jugadors segons les seves estadístiques individuals. L’objectiu és identificar diferents perfils de jugador a partir del dataset generat a la Part 1.

El procés de clustering permet analitzar patrons i similituds entre jugadors sense disposar d’etiquetes prèvies, basant-se únicament en el seu comportament estadístic dins del joc.

---

## Dataset utilitzat

El dataset utilitzat en aquesta part prové del procés d’ETL realitzat a la Part 1 del projecte.

- Fitxer d’entrada: `FEB3_Playbook2_ready.csv`

Aquest fitxer conté les estadístiques agregades a nivell de jugador i serveix com a base per a l’entrenament del model de clustering.

---

## Preparació de les dades

Abans d’aplicar el model de clustering, es duen a terme diverses tasques de preparació de les dades:

- Selecció de les variables més rellevants per al clustering  
- Eliminació de valors nuls i infinits  
- Filtratge de jugadors amb poca mostra  
- Estandardització de les dades per igualar l’escala de totes les variables  
- Preparació del dataset final per a l’entrenament del model  

Aquest procés garanteix que el model treballi amb dades netes i comparables.

---

## Entrenament del model

Per a l’agrupació dels jugadors s’utilitza l’algoritme **K-Means**.

Durant el procés s’han analitzat diferents configuracions del nombre de clústers mitjançant mètriques com *Inertia* i *Silhouette*, amb l’objectiu d’avaluar el comportament del model. Finalment, s’ha escollit una configuració amb **6 clústers**, ja que permet identificar perfils de jugador més específics i amb una interpretació esportiva més rica.

Aquesta elecció prioritza la capacitat d’anàlisi i interpretació dels perfils per sobre d’una simplificació excessiva del model.

---

## Resultat del clustering

Un cop entrenat el model:

- Cada jugador és assignat a un dels 6 clústers  
- Es genera un dataset final amb la informació del clúster associat a cada jugador  
- Es calculen les mitjanes de les variables per clúster  
- S’assignen noms esportius als clústers segons les seves característiques predominants  

Aquest dataset s’utilitza posteriorment per a l’anàlisi i visualització a la Part 3 del projecte.

---

## Playbook de clustering

Tot el procés descrit en aquesta part es pot consultar i executar al notebook següent:

- `FEB3_Part2.ipynb`

---

## Comparació entre diferents configuracions

Durant el desenvolupament del model s’han provat diferents configuracions del nombre de clústers per analitzar com variava la separació entre perfils. Aquest anàlisi ha permès observar que configuracions amb més clústers ofereixen una segmentació més detallada dels jugadors, mentre que configuracions amb menys clústers tendeixen a agrupar perfils diferents sota una mateixa categoria.

Finalment, s’ha optat per una configuració amb 6 clústers, ja que permet una millor diferenciació dels rols dels jugadors sense perdre coherència en els resultats.

---

## Criteris d’assignació dels perfils de jugador

Els perfils de jugador s’han definit a partir de l’anàlisi de les mitjanes de cada clúster i de la comparació entre variables clau com assistències, rebots i ús del tir exterior. Això permet identificar perfils com ara:

- Jugadors amb major participació en la generació de joc  
- Jugadors amb més presència interior  
- Perfils amb ús elevat del tir exterior  
- Jugadors més equilibrats en diferents facetes del joc  

Aquesta classificació facilita la interpretació esportiva dels resultats obtinguts.

---

## Connexió amb la Part 3

Les dades generades en aquesta part serveixen com a base per a la interpretació i visualització final dels perfils de jugador, que es desenvolupa a la **Part 3 del projecte**, on s’analitzen els clústers mitjançant gràfiques i projeccions en dues dimensions.
