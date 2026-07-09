# Tests d'hypothèses avec des matchs de football masculin et féminin

Projet d'analyse statistique réalisé dans le cadre de ma certification **Data Analyst Associate (DataCamp)**, résolu **deux fois avec deux langages différents** : **Python** et **R**. Les deux analyses répondent à la même question de recherche, avec la même méthodologie statistique, afin de démontrer une maîtrise transversale des outils d'analyse de données.

## Contexte

En tant que journaliste sportif spécialisé dans l'analyse et le reportage sur le football, je souhaite vérifier une intuition récurrente : **se marque-t-il plus de buts lors des matchs internationaux féminins que lors des matchs masculins ?**

Pour répondre à cette question de manière rigoureuse, l'analyse est menée sous forme d'un **test d'hypothèse statistique**, en se limitant aux matchs officiels de la **FIFA World Cup** (hors qualifications) disputés depuis le **2002-01-01**, afin de neutraliser l'effet de l'évolution du football au fil du temps.

## Question de recherche

> Marque-t-on plus de buts lors des matchs internationaux féminins que masculins ?

## Hypothèses

Seuil de signification retenu : **α = 10 %**

- **H₀** : Le nombre moyen de buts marqués lors des matchs internationaux féminins est identique à celui des matchs masculins.
- **H_A** : Le nombre moyen de buts marqués lors des matchs internationaux féminins est **supérieur** à celui des matchs masculins.

##  Données

| Fichier | Description |
|---|---|
| `women_results.csv` | Résultats de tous les matchs internationaux officiels féminins depuis le XIXe siècle |
| `men_results.csv` | Résultats de tous les matchs internationaux officiels masculins depuis le XIXe siècle |

Colonnes principales utilisées : `date`, `tournament`, `home_score`, `away_score`.

## 🔬 Méthodologie (commune aux deux versions)

1. **Filtrage** des deux jeux de données sur les matchs de la FIFA World Cup depuis le 2002-01-01.
2. **Calcul** du nombre total de buts marqués par match (`home_score + away_score`).
3. **Choix du test statistique** : la distribution du nombre de buts par match est asymétrique (right-skewed) et non normale — un test t classique n'est donc pas approprié. J'utilise un **test de Mann-Whitney U** (test non paramétrique), avec l'hypothèse alternative `"greater"`.
4. **Décision** : si la p-value obtenue est ≤ 0.10, on rejette H₀.

##  Structure du dépôt

- `python-analysis/` — Analyse en Python (pandas + pingouin)
  - `notebook.ipynb`
  - `women_results.csv`
  - `men_results.csv`
  - `soccer-pitch.jpg`
  - `requirements.txt`
- `r-analysis/` — Analyse en R (tidyverse + wilcox.test)
  - `notebook.ipynb`
  - `women_results.csv`
  - `men_results.csv`
  - `soccer-pitch.jpg`
- `README.md`



## Résultats

| Langage | Outil statistique | p-value | Décision |
|---|---|---|---|
| Python | `pingouin.mwu` (Mann-Whitney U) | 0.005107 | reject |
| R | `wilcox.test` (Mann-Whitney/Wilcoxon) | 0.005107 | reject |

Les deux implémentations, bien qu'utilisant des librairies différentes, produisent une **p-value identique**, ce qui confirme la cohérence et la robustesse du test statistique.

## Interprétation

La p-value obtenue (≈ 0.0051) est largement inférieure au seuil de signification de 10 %. On rejette donc l'hypothèse nulle H₀ en faveur de l'hypothèse alternative H_A.

**Conclusion :** au regard des matchs officiels de la FIFA World Cup joués depuis 2002, le nombre moyen de buts marqués lors des matchs internationaux **féminins** est **statistiquement significativement supérieur** à celui des matchs **masculins**. Ce résultat confirme l'intuition initiale avec un niveau de confiance élevé — la p-value est d'ailleurs assez faible pour rester significative même à un seuil bien plus strict (1 %).

## Outils utilisés

- **Python** : pandas, pingouin
- **R** : tidyverse, wilcox.test (base R)

##  Reproduire l'analyse

**Python**
```bash
cd python-analysis
pip install -r requirements.txt
jupyter notebook notebook.ipynb
```

**R**
```r
# Dans R ou RStudio, depuis le dossier r-analysis
install.packages("tidyverse")
# Puis ouvrir notebook.ipynb avec Jupyter + noyau IRkernel, ou exécuter le code équivalent en script .R
```

## Auteur

**Mustakeem Adémola Arèmou LATOUNDJI**
Master 1 Statistiques Appliquées au Vivant — CIPMA, Chaire UNESCO, UAC (Bénin)
Certifié Data Analyst Associate (DataCamp) & Google Data Analytics Professional

- GitHub : [ademolatoundji-svg](https://github.com/ademolatoundji-svg)
- Email : mustakeemlatoundji@gmail.com
