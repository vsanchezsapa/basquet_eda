# PART 3 – Interpretació i visualització dels resultats

En aquesta tercera part del projecte s’analitzen i interpreten els resultats obtinguts a partir del procés de clustering realitzat a la Part 2. L’objectiu és entendre els diferents perfils de jugador identificats i comunicar els resultats de manera clara mitjançant visualitzacions.

En aquesta fase s’utilitzen eines de visualització en Python dins de Jupyter Notebook, que permeten analitzar les diferències entre clústers i facilitar la interpretació esportiva dels resultats.

---

## Dataset utilitzat

Per a la visualització i l’anàlisi s’utilitza el dataset final generat a la Part 2 del projecte:

- Fitxer: `FEB3_players_clustered_k6.csv`

Aquest fitxer conté les estadístiques agregades de cada jugador, el clúster assignat i el nom del perfil esportiu associat.

---

## Visualització dels resultats

Per analitzar els clústers obtinguts s’han utilitzat diferents tipus de visualitzacions:

- Distribució de jugadors per clúster mitjançant gràfiques de barres  
- Comparació de mitjanes estadístiques entre clústers  
- Boxplots per analitzar la distribució de variables clau dins de cada clúster  
- Projecció en dues dimensions mitjançant PCA per visualitzar la separació entre clústers  

Aquestes visualitzacions permeten comparar els perfils de jugador i detectar diferències clares en variables com les assistències, els rebots o l’ús del tir exterior.

---

## Anàlisi i interpretació dels clústers

A partir de les visualitzacions generades, s’analitzen les característiques principals de cada clúster, observant com varien les estadístiques entre perfils. Tot i que alguns clústers presenten cert solapament, s’identifiquen diferències consistents que permeten associar cada grup amb un tipus de jugador concret.

La interpretació esportiva es basa en l’anàlisi de les mitjanes per clúster i en la comparació visual entre grups, fet que facilita la comprensió dels resultats obtinguts.

---

## Projecció en dues dimensions amb PCA

La projecció mitjançant PCA permet representar els jugadors en un espai de dues dimensions, mantenint una part significativa de la variabilitat de les dades originals. Aquesta visualització ajuda a entendre com es distribueixen els clústers i a comprovar que el clustering capta diferències reals entre jugadors, tot i la presència de solapaments habituals en dades reals.

---

## Conclusions finals

Les visualitzacions realitzades confirmen que el procés de clustering ha permès identificar diferents perfils de jugador de manera coherent. L’ús de gràfiques i projeccions facilita la interpretació dels resultats i permet comunicar de forma clara les diferències entre clústers.

En conjunt, aquesta part del projecte demostra que les tècniques de *Machine Learning* no supervisat combinades amb una bona visualització són útils per analitzar dades esportives i extreure conclusions rellevants sobre els perfils de jugador.
