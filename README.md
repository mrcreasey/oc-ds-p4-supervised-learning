# Anticipate the energy consumption of new commercial buildings

## Overview

To achieve its goal of being a carbon-neutral city by 2050, careful readings of total energy
consumption were carried out by Seattle city officials. However, these statements are expensive to
obtain.

The aim of this project is to:

- **predict CO2 emissions and total energy consumption of new commercial buildings** in Seattle,
  based on :
  - data available before commercial operation (size and use of buildings, date of construction,
    etc.).
  - (expensive) surveys already carried out in 2015 and 2016 on existing buildings.
- **evaluate the interest of the
  [ENERGY STAR Score](https://www.energystar.gov/buildings/facility-owners-and-managers/existing-buildings/use-portfolio-manager/interpret-your-results/what)
  for the prediction of emissions**.

## Motivation

This is project 4 for the **Master in Data Science** (in French, BAC+5) from OpenClassrooms. The
project tests the performance and compares baseline, linear, non-linear and ensemble methods of
supervised regression:

- feature engineering, log/quantile transformation and scaling the data
- splitting the data into train and test sets, avoiding data leakage
- using filter, wrapper and embedded methods for feature selection
- L1, L2 regularization and hyperparameter tuning
- creating pipelines to preprocess, select features and tune the models
- performing gridsearch and cross-validation
- evaluating feature importance, model learning curves

## Requirements

To run the notebooks, the dataset must be placed in a DATA_FOLDER ('data/raw'). Python libraries are
listed in `requirements.txt`. Each notebook also includes a list of its own requirements, and a
procedure for `pip install` of any missing libraries.

**Data** : The dataset (2 data files CSV, 2 metadata files JSON) can be downloaded (~3Mb) from the
site <https://www.kaggle.com/datasets/city-of-seattle/sea-building-energy-benchmarking>

**Python libraries** :
`numpy, pandas, matplotlib, seaborn, scikit-learn, scipy, missingno, dython, shap`

## Files

_Note:_ Files are in French. _Custom functions created in this project for data preprocessing,
statistical analysis and data visualisation are encapsulated within each notebook, to avoid
importing and versioning custom libraries. Open https://nbviewer.org/ and paste notebook GitHub url
if GitHub takes too long to render._

- [Pélec_01_notebook.ipynb](./Pélec_01_notebook.ipynb): Data cleaning and exploratory analysis
<a href="https://colab.research.google.com/github/mrcreasey/oc-ds-p4-supervised-learning/blob/main/Pélec_01_notebook.ipynb" target="blank"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open in Colab"/></a>
  
- [Pélec_02_code.ipynb](./Pélec_02_code.ipynb): Feature engineering, modelling, hyperparameter tuning, cross-validation
<a href="https://colab.research.google.com/github/mrcreasey/oc-ds-p4-supervised-learning/blob/main/Pélec_02_code.ipynb" target="blank"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open in Colab"/></a>
  
- [Pélec_03_support.pdf](./Pélec_03_support.pdf) : Presentation and conclusion

## Approach

### Data cleaning

- data merge, elimination of non-compliant/missing data
- selection of target columns and only features available for new buildings
- correction of whitespace, standardise formatting (upper/lower case)

### Data exploration and Feature Engineering

- dimension reduction for categorical columns and one-hot encoding
- creation of new categories via binning
- log transformations of X and target regressor

### Feature selection

Features were selected to reduce overfitting (high variance), improve confidence in predictions,
simplify the models and speed up training.

- **Filter**
  - numerical: elimination of colinearities (pearson >0.7, variance inflation factor >5)
  - categorical: Cramer’s V (Chi-squared), Thiel’s U (conditional entropy)
- **Embedded**
  - L1 (Lasso), L2(Ridge), L1 & L2 (ElasticNet) regularisation
  - Feature importance (decision trees)
- **Wrapper** (KBest)

### Regression Models

GridSearch with cross-validation was used to test the following regressors:

- Baseline (DummyRegressor)
- Linear (Ridge, Lasso, ElasticNet)
- Non-Linear (Support Vectors, Kernel Ridge)
- Ensemble methods (RandomForest, Bagging)

### Selection of model

For this set of data, the best performing model was Kernel Ridge (non-linear):

- Performance metric - low RMSE
- Faster than ensemble methods
- Learning curves show training of this model may not be scalable above 3000 buildings.
- Residuals analysis show under estimation for hospitals and data centers

### Conclusion

- Log transformation of X and Y variables was needed to reduce the influence of outliers (hospitals
  and data centers)
- Binning, simplification and one-hot encoding of categorical variables improved the performance of
  the model.
- The best performance overall was using Kernel Ridge regression
- Residual analysis showed that the energy consumption of hospitals and data centers tends to be
  under-estimated by the model
- The ENERGY STAR Score reduced the performance on total energy consumption prediction, having no
  impact on total CO2 emissions: The property usage type and age of construction were more important
  features.

### Suggestions for Improvement

- Create new features (datacenter_floor_area, hospital_floor_area, unheated_floor_area,...)
- Use Recursive Feature Elimination
- Improve interpretability using SHAPely values

## Features (keywords)

- Data cleaning (merge, missing values, outliers, whitespace)
- Feature engineering (log, quantile, binning, one-hot encoding)
- Scikit-learn processing pipelines, column transformers, transform target regressor
- Feature selection (Filter, Wrapper, Embedded)
- Supervised learning (gridsearch, cross-validation, hyperparameter tuning)
- Linear regression with L1 and L2 regularization (Ridge, Lasso, ElasticNet)
- Non-linear regression (support vector (SVR), Kernel Ridge)
- Ensemble methods: Random Forest, Bagging
- Performance evaluation, learning curves, residuals analysis
- Feature importance, permutation importance, SHAPley values

## Skills acquired

- Set up the supervised learning model adapted to the business problem
- Evaluate the performance of a supervised learning model
- Adapt the hyperparameters of a supervised learning algorithm in order to improve it
- Transform the relevant variables of a supervised learning model
