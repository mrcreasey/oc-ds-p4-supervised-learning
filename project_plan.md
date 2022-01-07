# Plan du projet

Ce document note les idées pour structurer le projet

- Les sections sont remplis itérativement, pas nécessairement en ordre

# 1. Compréhension du problème

## L'énoncé du problème

## Objectifs commerciaux

## Critères de réussite

## Contraintes

## Outils

# 2. Compréhension des données

## Sources des données

## Définition des données (metadata)

## Import des données

## Décrire des données

## Nettoyage des données

- Colonnes non-pertinentes
- Valeurs manquantes
- Outliers 

# 3. Analyse exploratoire des données

## Analyses descriptives

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

Choisir entre plusieurs models de machine learning (probablement une sélection entre des modèles ci-dessous)

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
