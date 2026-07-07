# Proyecto 2 — PageRank sobre redes reales (IMT2230)

PageRank aplicado a la red dirigida de hipervínculos entre **1 224 blogs políticos de EE.UU.** durante la elección presidencial de 2004 (KONECT: [`moreno_blogs`](http://konect.cc/networks/moreno_blogs/); origen: Adamic & Glance, 2005, *"The political blogosphere and the 2004 U.S. election: divided they blog"*).

**Integrantes:** [COMPLETAR]

## Contenido

| Archivo | Descripción |
|---|---|
| `proyecto_pagerank.ipynb` | Notebook con todo el desarrollo (P1–P8): descarga de datos, exploración, construcción de H, S y G, iteración de potencias, comparación con in-degree, visualizaciones e interpretación. |
| `informe_pagerank.pdf` | Informe final del proyecto. |
| `figs/` | Figuras generadas por el notebook (se crean al ejecutarlo). |
| `data/` | Dataset (se descarga automáticamente al ejecutar el notebook, ≈1 MB). |

## Cómo ejecutar

```bash
pip install numpy scipy networkx matplotlib pandas jupyter
jupyter notebook proyecto_pagerank.ipynb
```

Luego `Kernel → Restart & Run All`. También funciona directamente en **Google Colab** (subir el `.ipynb`). La primera celda descarga el dataset automáticamente; no hay pasos manuales. Los resultados son reproducibles (semillas fijas en los layouts).

## Datos

- Red catalogada en KONECT como `moreno_blogs`: http://konect.cc/networks/moreno_blogs/
- El notebook descarga el GML original de Adamic & Glance (espejo público), que además de las aristas incluye la **URL** y la **orientación política** (0 = liberal, 1 = conservador) de cada blog, atributos usados en la interpretación (P7).

## Resultados principales

- Convergencia de la iteración de potencias en **107 iteraciones** (ε = 10⁻¹⁰, α = 0.85), con decaimiento geométrico de razón empírica 0.8498 ≈ α.
- Top-1 de PageRank: **dailykos.com**; correlación Pearson PageRank vs. in-degree: **0.957**.
- Masa de PageRank: 51.6 % comunidad conservadora vs 48.4 % liberal; top-20 con mayoría conservadora (14/20).
- El subgrafo de la élite reproduce la polarización de *"divided they blog"* (81.9 % de aristas intra-grupo).
