# Projecte de Clustering de Jugadors de Bàsquet (FEB)

Aquest projecte té com a objectiu analitzar estadístiques de jugadors de bàsquet de la FEB mitjançant tècniques de *Machine Learning* no supervisat, concretament **clustering**, amb la finalitat d’identificar diferents perfils de jugadors segons el seu rendiment i estil de joc.

Les dades utilitzades provenen d’una base de dades **MongoDB**, que conté estadístiques detallades de partits i jugadors de la competició **Liga EBA**.

---

## 🧩 Estructura del repositori

El projecte està organitzat en tres parts principals, que corresponen a les diferents fases del treball:

### 📁 PART 1 – ETL i EDA
En aquesta part es duu a terme tot el procés de preparació de les dades:

- Connexió a MongoDB mitjançant *pymongo*
- Extracció selectiva de dades (temporada i competició)
- Neteja i transformació de les dades
- Tractament de valors nuls, minuts iguals a zero i jugadors amb poca mostra
- Creació de noves variables estadístiques
- Anàlisi exploratòria de dades (EDA)
- Generació del dataset final preparat per a *Machine Learning*

📌 **Resultat:** un dataset net i coherent a nivell de jugador.

---

### 📁 PART 2 – Clustering
En aquesta part s’aplica el model de clustering:

- Normalització i estandardització de les dades
- Elecció del nombre òptim de clústers
- Aplicació de l’algoritme **K-Means**
- Assignació de cada jugador a un clúster

📌 **Objectiu:** identificar grups de jugadors amb perfils similars.

---

### 📁 PART 3 – Interpretació i conclusions
En l’última part s’analitzen els resultats obtinguts:

- Interpretació dels clústers
- Anàlisi dels diferents perfils de jugador
- Comparació entre clústers
- Conclusions finals del projecte

---

## 🛠️ Tecnologies utilitzades

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

## 📌 Autor

Projecte realitzat com a part d’un treball acadèmic de **Big Data / Intel·ligència Artificial**, utilitzant dades reals de competicions de bàsquet.
