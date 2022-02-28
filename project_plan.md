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

### TODO

- automated feature selection
  - <https://machinelearningmastery.com/feature-selection-with-real-and-categorical-data/>

#### How do I choose the right feature selection algorithm?

There are 3 classes of feature selection algorithms (Feature selection -
Wikipedia)[https://en.wikipedia.org/wiki/Feature_selection]:

- Filter methods - you filter potential features before fitting your model using criteria that may
  be unrelated to the model.
- Wrapper methods - you test out various combinations of features and fit different versions of your
  model.
- Embedded methods - your model has a way of automatically selecting features built in, typically
  using L1 regularisation.

Usually, what you want to consider are the following ideas when selecting one of the 3:

- How slow is your model fitting process? 
  - Wrapper methods tend to overfit, necessitating cross validation, which requires even more CPU cycles.

- How complex is the model you are trying to learn?
  - Filter (ex: correlation feature vs. target) might not capture the nonlinear relationship.

- Does your chosen machine learning method admit an embedded feature selection routine? 
  - L1 regularised model has embedded feature selection, but may have low fit quality
  - L2 regularisation won’t do feature selection, but may have better fit 

Wwrapper methods don’t sacrifice accuracy and are easy to implement. 
Embedded feature selection constrains the type of model and thus potential performance. 

Filters would be a total last resort, because I generallycan’t think of a theoretical basis for a filter to work outside linear regression.

Feature selection : must understand what the variables mean and why they are the way they are, the
distribution, the units, etc.

Some general strategies which you can use :

- Drop features with based on missing values: iff you’re sure that the feature is not super
  important.
- Build a tree-based model and select features based on how the model prioritizes the variables.
- Step-wise regression: Either perform forward regression or backward regression and select the
  combination of variables which have the lowest BIC or AIC. Mallow’s Cp can also be used. Best
  subsets regression is also an alternative. But this method is computationally intensive.
- Regularization: Use a technique like LASSO or Ridge or ElasticNet regression and let the algorithm
  decide the importance of variables.
- Use other feature selection algorithms like Boruta.

- heteroscedascity of residuals

  - White Test
  - Pagan Test

- Learning Curves

  - Rationale
    - Bias-Variance trade-off
    - Overfitting / under-fitting
  - number of iterations
  - number of samples
  - number of features

- Hyperparameter optimisations

- Create performance table
  - time, metric, residuals
- Interprebility
  - SHAP / LIME

# 8. Conclusion

# 9. Réferences
