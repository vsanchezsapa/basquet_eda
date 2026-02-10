# Projecte de Clustering de Jugadors de Bàsquet (FEB)

Aquest projecte té com a objectiu analitzar estadístiques de jugadors de bàsquet de la FEB mitjançant tècniques de Machine Learning no supervisat, concretament clustering, amb la finalitat d’identificar diferents perfils de jugadors segons el seu estil de joc i rendiment.

Les dades utilitzades provenen d’una base de dades MongoDB, que conté estadístiques detallades de partits i jugadors de la competició Liga EBA.

---

## Estructura del repositori

El projecte està dividit en tres parts principals, que corresponen a les diferents fases del treball:

part1_etl_eda  
part2_clustering  
part3_interpretacio  
README.md  

---

## PART 1 – ETL i EDA

En aquesta primera part es realitza tot el procés de preparació i exploració de les dades:

- Connexió a MongoDB mitjançant pymongo  
- Extracció selectiva de dades per temporada i competició  
- Neteja i transformació de les dades  
- Tractament de valors nuls, minuts iguals a zero i jugadors amb poca mostra  
- Creació de variables estadístiques agregades a nivell de jugador  
- Anàlisi exploratòria de dades (EDA)  
- Generació del dataset final preparat per aplicar models de Machine Learning  

Resultat: un dataset net, coherent i estructurat a nivell de jugador.

---

## PART 2 – Clustering

En aquesta fase s’aplica el model de clustering utilitzant l’algoritme K-Means:

- Selecció de variables rellevants per al clustering  
- Neteja mínima i filtres de qualitat  
- Normalització de les dades amb StandardScaler  
- Avaluació de diferents configuracions mitjançant mètriques com Inertia i Silhouette  
- Entrenament del model final amb 6 clústers  
- Assignació d’un clúster a cada jugador  
- Creació d’una taula resum amb les mitjanes per clúster  
- Assignació d’un nom esportiu a cada clúster per facilitar la interpretació  

Objectiu: identificar grups de jugadors amb perfils estadístics similars.

---

## PART 3 – Interpretació i visualització

En l’última part s’analitzen i visualitzen els resultats del clustering:

- Taules resum amb variables clau per clúster  
- Gràfiques de barres i boxplots per comparar perfils  
- Projecció en dues dimensions mitjançant PCA per visualitzar els clústers  
- Interpretació esportiva dels perfils obtinguts  
- Conclusions finals basades en les visualitzacions  

Resultat: una interpretació clara i visual dels diferents tipus de jugadors identificats.

---

## Tecnologies utilitzades

- Python  
- MongoDB  
- pymongo  
- pandas  
- numpy  
- matplotlib  
- seaborn  
- scikit-learn  
- Jupyter Notebook  

---

## Autor

Projecte realitzat com a part d’un treball acadèmic de Big Data / Intel·ligència Artificial, utilitzant dades reals de competicions de bàsquet de la FEB.
