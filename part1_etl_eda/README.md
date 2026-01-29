# PART 1 – ETL i EDA

En aquesta primera part del projecte es realitza tot el procés d’extracció, neteja i preparació de les dades a partir d’una base de dades MongoDB, amb l’objectiu d’obtenir un dataset final preparat per a tècniques de Machine Learning.

Les dades corresponen a estadístiques de jugadors de la competició FEB3 / Liga EBA.

---

## PAS 0 — Definició de les temporades

En primer lloc es defineix una constant amb les temporades més recents disponibles per a la competició FEB3.

Aquesta selecció permet:
- Limitar el volum de dades
- Treballar només amb informació actual
- Garantir coherència en totes les vistes creades posteriorment

📸 *Captura: definició de les temporades utilitzades*

![Definició temporades](img/pas0_temporades.jpeg)

---

## PAS 1 — Vista de tirs neta

### Objectiu
Crear una vista amb tots els tirs realitzats a FEB3 durant les temporades seleccionades, amb els camps normalitzats i preparats per a l’anàlisi exploratòria (EDA).

### Procés realitzat

- **$match inicial**  
  Es filtren únicament:
  - Les temporades seleccionades
  - Registres amb `player_feb_id` vàlid

- **$addFields**  
  Es normalitzen alguns camps per evitar inconsistències:
  - `competition_name` es passa a majúscules
  - El tipus de tir (2p / 3p) es normalitza
  - El camp `made` es converteix en un booleà real (`true / false`)

- **$project**  
  Es descarten camps innecessaris i es mantenen només aquells rellevants per:
  - Anàlisi espacial (coordenades X/Y)
  - Anàlisi per zones de tir
  - Càlcul de percentatges d’encert

- **$match final**  
  Comprovació final per assegurar que totes les dades compleixen els criteris definits.

📸 *Captures: vista de tirs neta i comprovació de dades*

![Vista tirs neta](img/pas1_vista_tirs.png)

![Comprovació vista tirs](img/pas1_comprovacio_tirs.png)

---

## PAS 2 — Vista d’estadístiques jugador-partit neta

### Objectiu
Crear una vista amb les estadístiques reals dels jugadors en els partits disputats, preparada per ser agregada posteriorment a nivell de jugador.

### Procés realitzat

- **$match**
  S’eliminen:
  - Jugadors amb `minutes = 0` (no han participat)
  - Registres sense identificador de jugador
  - Temporades fora del període d’estudi

- **$addFields**
  Es converteixen els minuts jugats a un format més interpretable per facilitar l’anàlisi posterior.

- **$project**
  Es seleccionen únicament les variables necessàries per:
  - L’EDA
  - El clustering
  - La creació de noves mètriques

📸 *Captures: vista d’estadístiques jugador-partit i comprovació*

![Vista estadístiques jugador-partit](img/pas2_vista_stats.png)

![Comprovació vista estadístiques](img/pas2_comprovacio_stats.png)

---

## PAS 3 — Vista final agregada per jugador

### Objectiu
Obtenir un dataset final a nivell de jugador, amb una fila per jugador i temporada.

### Procés realitzat

- **$group**
  Es realitza una agregació per jugador, calculant:
  - Mitjanes per partit de les principals estadístiques

- **Filtrat per mostra mínima**
  Es descarten els jugadors amb un nombre de partits inferior a un llindar mínim, per evitar soroll en el clustering.

El resultat és un **dataset final net, coherent i preparat per EDA, escalat i entrenament de models**.

📸 *Captura: dataset final obtingut*

![Dataset final agregat](img/pas3_dataset_final.png)

---

## Resultat final

El procés ETL finalitza amb la generació d’un dataset estructurat a nivell de jugador, que serveix com a base per a la fase de clustering de la Part 2 del projecte.
