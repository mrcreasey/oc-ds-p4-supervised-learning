# Plan du projet

Ce document note les idées pour structurer le projet

- Les sections sont remplis itérativement, pas nécessairement en ordre

# 1. Compréhension du problème

## L'énoncé du problème

Les relevés sont coûteux à obtenir, et à partir de ceux déjà réalisés, vous voulez tenter de prédire
les émissions de CO2 et la consommation totale d’énergie de bâtiments pour lesquels elles n’ont pas
encore été mesurées.

## Objectifs commerciaux

- **Prédire les émissions de CO2 et la consommation totale d’énergie** de bâtiments commerciales en
  Seattle pour lesquels elles n’ont pas encore été mesurées, basé sur :

  - [les relevés réalisés sur d'autres bâtiments en 2015 et 2016](https://www.kaggle.com/city-of-seattle/sea-building-energy-benchmarking#2015-building-energy-benchmarking.csv)
    ;
  - les données déclaratives du permis d'exploitation commerciale (taille et usage des bâtiments,
    mention de travaux récents, date de construction...)

- **évaluer l’intérêt de
  l’[ENERGY STAR Score](https://www.energystar.gov/buildings/facility-owners-and-managers/existing-buildings/use-portfolio-manager/interpret-your-results/what)
  pour la prédiction d’émissions**

## 1.3 Les objectifs d'analyse pré-exploratoire

## Critères de réussite

- les variables cibles sont identifiées

## Portée de la solution

- les

## Contraintes

- Limiter à des algorithmes supervisés de machine learning

## Parties prenantes

## Outils

## Source d'information

# 2. Compréhension des données

**Sources des données**

Les données de consommation sont à télécharger à
[cette adresse](https://www.kaggle.com/city-of-seattle/sea-building-energy-benchmarking#2015-building-energy-benchmarking.csv).

## 2.1 Définition des données (metadata)

- read json metadata

## 2.2 Import des données

## 2.3 Décrire des données

- Evaluation de la qualité des données

## 2.4 Nettoyage des données

- Colonnes non-pertinentes
- Valeurs manquantes
- Outliers

# 3. Analyse exploratoire des données

## Analyses descriptives

## Analyses graphiques

## Valeurs aberrantes et anomalies

## Explorer les relations de données

# 4. Feature engineering

## Ajout de variables

## Métriques d'évaluation

- `np.sqrt(metrics.mean_squared_error(y_test, y_pred))`

# 5. Données d'entrainement et test

## Encodage des variables catégoriques

## Standardisation des variables numériques

## Division en jeux de données d'entraînement et de test

## Stratégies de Cross-validation / Hyperparamètres

# 6. Modélisation

Choisir entre plusieurs models de machine learning (probablement une sélection entre des modèles
ci-dessous)

## Dummy mean

`sklearn.dummy.DummyRegressor(strategy='mean')`

## Regression (Lineaire, Lasso, Ridge, ElasticNet)

- `sklearn.linear_model.LinearRegression`
- `sklearn.linear_model.LassoCV`
- `sklearn.linear_model.RidgeCV`
- `sklearn.linear_model.ElasticNet`

## SVM

- `sklearn.svm.SVR`

## Kernel Ridge Regression

- `sklearn.kernel_ridge.KernelRidge`

## Bagging

- `sklearn.ensemble.BaggingRegressor`

## Random Forest

- `sklearn.ensemble.RandomForestRegressor`

## Adaboost / XGBoost

- `sklearn.ensemble.GradientBoostingRegressor`

# 7. Résultats

## Comparaison des perfomances des modèles

# 8. Conclusion

# 9. Réferences
