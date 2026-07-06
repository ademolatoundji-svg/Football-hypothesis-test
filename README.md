# ⚽ Tests d'hypothèses avec des matchs de football masculin et féminin

Projet d'analyse statistique réalisé dans le cadre de ma certification **Data Analyst Associate (DataCamp)**.

## 🎯 Contexte

En tant que journaliste sportif spécialisé dans l'analyse et le reportage sur le football, je souhaite vérifier une intuition récurrente : **se marque-t-il plus de buts lors des matchs internationaux féminins que lors des matchs masculins ?**

Pour répondre à cette question de manière rigoureuse, l'analyse est menée sous forme d'un **test d'hypothèse statistique**, en se limitant aux matchs officiels de la **FIFA World Cup** (hors qualifications) disputés depuis le **2002-01-01**, afin de neutraliser l'effet de l'évolution du football au fil du temps.

## ❓ Question de recherche

> Marque-t-on plus de buts lors des matchs internationaux féminins que masculins ?

## 🧪 Hypothèses

Seuil de signification retenu : **α = 10 %**

- **H₀** : Le nombre moyen de buts marqués lors des matchs internationaux féminins est identique à celui des matchs masculins.
- **H_A** : Le nombre moyen de buts marqués lors des matchs internationaux féminins est **supérieur** à celui des matchs masculins.

## 📊 Données

| Fichier | Description |
|---|---|
| `women_results.csv` | Résultats de tous les matchs internationaux officiels féminins depuis le XIXe siècle |
| `men_results.csv` | Résultats de tous les matchs internationaux officiels masculins depuis le XIXe siècle |

Colonnes principales utilisées : `date`, `tournament`, `home_score`, `away_score`.

## 🔬 Méthodologie

1. **Filtrage** des deux jeux de données sur les matchs de la FIFA World Cup depuis le 2002-01-01.
2. **Calcul** du nombre total de buts marqués par match (`home_score + away_score`).
3. **Choix du test statistique** : la distribution du nombre de buts par match est asymétrique (right-skewed) et non normale — un test t classique n'est donc pas approprié. J'utilise le **test de Mann-Whitney U** (test non paramétrique), avec l'hypothèse alternative `"greater"`.
4. **Décision** : si la p-value obtenue est ≤ 0.10, on rejette H₀.

## 📈 Résultats

```python
result_dict = {'p_val': 0.005106609825443641, 'result': 'reject'}
```

- **p-value ≈ 0.0051 (0.51 %)**
- **Décision : reject** — on rejette H₀

## 💡 Interprétation

La p-value obtenue (0.0051) est largement inférieure au seuil de signification de 10 %. On rejette donc l'hypothèse nulle H₀ en faveur de l'hypothèse alternative H_A.

**Conclusion :** au regard des matchs officiels de la FIFA World Cup joués depuis 2002, le nombre moyen de buts marqués lors des matchs internationaux **féminins** est **statistiquement significativement supérieur** à celui des matchs **masculins**. Ce résultat confirme l'intuition initiale avec un niveau de confiance élevé — la p-value est d'ailleurs assez faible pour rester significative même à un seuil bien plus strict (1 %).

## 🛠️ Outils utilisés

- Python
- pandas
- pingouin (test de Mann-Whitney U)

## 📁 Structure du dépôt

```
.
└── python-analysis/
    ├── notebook.ipynb     # Notebook Jupyter avec l'analyse complète
    ├── women_results.csv  # Données des matchs féminins
    ├── men_results.csv    # Données des matchs masculins
    ├── soccer-pitch.jpg    # Image d'illustration
    └── requirements.txt   # Dépendances Python
```

## ▶️ Reproduire l'analyse

```bash
cd python-analysis
pip install -r requirements.txt
jupyter notebook notebook.ipynb
```

## 👤 Auteur

**Mustakeem Adémola Arèmou LATOUNDJI**
Master 1 Statistiques Appliquées au Vivant — CIPMA, Chaire UNESCO, UAC (Bénin)
Certifié Data Analyst Associate (DataCamp) & Google Data Analytics Professional

- GitHub : [ademolatoundji-svg](https://github.com/ademolatoundji-svg)
- Email : mustakeemlatoundji@gmail.com
