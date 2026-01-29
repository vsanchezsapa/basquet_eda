# Creació de vistes MongoDB (FEB3)

Aquest directori conté **tot el codi necessari** perquè el professor pugui
**copiar i enganxar directament a la shell de MongoDB (`mongosh`)** i recrear
exactament les vistes utilitzades a la **Part 1 (ETL + EDA)** del projecte.

L’objectiu és evitar exportacions massives a CSV i treballar amb **vistes netes**
que permetin carregar les dades directament a Python per fer l’EDA i,
posteriorment, el clustering.

---

## 🎯 Objectiu de les vistes
Les vistes permeten:
- Filtrar només **FEB3 (LIGA EBA)**  
- Limitar-nos a **3 temporades concretes**
- Normalitzar camps (booleans, majúscules/minúscules)
- Preparar una **vista agregada final (1 fila = jugador + temporada)**  
- Facilitar el treball d’EDA i Machine Learning

---

## 📁 Vistes creades

### 1️⃣ `vw_FEB3_shots_clean_3y`
Vista de **tirs (shots)** neta:
- Coordenades (x, y)
- Zona de pista
- Tipus de tir
- Encistellat o no  
Utilitzada per EDA espacial i anàlisi de tirs.

---

### 2️⃣ `vw_FEB3_players_stats_clean_3y`
Vista d’**estadístiques jugador–partit**:
- Només jugadors amb minuts jugats
- Conversió de minuts a minuts reals
- Estadístiques bàsiques netes  
Base per a l’agregació posterior.

---

### 3️⃣ `vw_FEB3_players_base_3y`
Vista **final agregada**:
- 1 fila = 1 jugador + 1 temporada
- Mitjanes per partit
- Percentatges de tir
- Filtrat de jugadors amb suficients partits

👉 Aquesta és la vista que es carrega a Python per fer l’EDA final i generar el
CSV per al **Playbook 2 (Clustering)**.

---

## ▶️ Com executar el codi (pas a pas)

### 0️⃣ Entrar a la base de dades
```
use feb_db
```
### Definir les temporades a analitzar
```
const SEASONS = ["2025", "2024-2025", "2023-2024"];
```
### Vista 1 — Shots nets (3 temporades)
```
db.createView(
  "vw_FEB3_shots_clean_3y",
  "FEB3_players_shots",
  [
    {
      $match: {
        season_id: { $in: SEASONS },
        player_feb_id: { $ne: null }
      }
    },
    {
      $addFields: {
        competition_name_norm: { $toUpper: "$competition_name" },
        type_norm: { $toLower: "$type" },
        made_norm: { $toBool: "$made" }
      }
    },
    {
      $project: {
        _id: 0,
        player_feb_id: 1,
        season_id: 1,
        team_feb_id: 1,
        match_feb_id: 1,
        court_region: 1,
        x: 1,
        y: 1,
        type: "$type_norm",
        made: "$made_norm",
        competition_name: "$competition_name_norm",
        data: 1,
        hora: 1
      }
    },
    {
      $match: { competition_name: "LIGA EBA" }
    }
  ]
)

```
### Vista 2 — Estadístiques jugador-partit netes
```
db.createView(
  "vw_FEB3_players_stats_clean_3y",
  "FEB3_players_statistics",
  [
    {
      $match: {
        season_id: { $in: SEASONS },
        minutes: { $gt: 0 },
        player_feb_id: { $ne: null }
      }
    },
    {
      $addFields: {
        minutes_played: { $divide: ["$minutes", 60] }
      }
    },
    {
      $project: {
        _id: 0,
        player_feb_id: 1,
        season_id: 1,
        team_feb_id: 1,
        match_feb_id: 1,
        minutes_played: 1,
        pts: 1,
        ast: 1,
        trb: 1,
        tov: 1,
        "2pm": 1,
        "2pa": 1,
        "3pm": 1,
        "3pa": 1,
        fta: 1,
        ftm: 1,
        stl: 1,
        blk: 1,
        pf: 1,
        eff_spanish: 1
      }
    }
  ]
)

```
### Vista 3 — Vista final agregada (base EDA + ML)
```
db.createView(
  "vw_FEB3_players_base_3y",
  "vw_FEB3_players_stats_clean_3y",
  [
    {
      $group: {
        _id: {
          player_feb_id: "$player_feb_id",
          season_id: "$season_id"
        },
        games: { $sum: 1 },
        avg_min: { $avg: "$minutes_played" },
        avg_pts: { $avg: "$pts" },
        avg_ast: { $avg: "$ast" },
        avg_trb: { $avg: "$trb" },
        avg_tov: { $avg: "$tov" },
        avg_2pa: { $avg: "$2pa" },
        avg_3pa: { $avg: "$3pa" },
        fg2_pct: {
          $avg: {
            $cond: [
              { $gt: ["$2pa", 0] },
              { $divide: ["$2pm", "$2pa"] },
              null
            ]
          }
        },
        fg3_pct: {
          $avg: {
            $cond: [
              { $gt: ["$3pa", 0] },
              { $divide: ["$3pm", "$3pa"] },
              null
            ]
          }
        },
        avg_eff: { $avg: "$eff_spanish" }
      }
    },
    {
      $match: { games: { $gte: 8 } }
    },
    {
      $project: {
        _id: 0,
        player_feb_id: "$_id.player_feb_id",
        season_id: "$_id.season_id",
        games: 1,
        avg_min: 1,
        avg_pts: 1,
        avg_ast: 1,
        avg_trb: 1,
        avg_tov: 1,
        avg_2pa: 1,
        avg_3pa: 1,
        fg2_pct: 1,
        fg3_pct: 1,
        avg_eff: 1
      }
    }
  ]
)

