# QRT-Asset-Allocation-Performance-forecasting
QRT Grand Data Challenge 

08/10

Feature engineering : mean of ret, std of ret, mean/std ratio = strengh of the signal, turnover * std(RET)
differents models (train/test 0.8 split en groupant par TS, scaling, features benchmark):
Classification results (arrondi à 0.001):
{'RidgeClassifier': 0.517, 'RandomForest': 0.518, 'LightGBM': 0.513, 'XGBoost': 0.517, 'CatBoost': 0.518}

Regression->Classification results (arrondi à 0.001):
{'Ridge': 0.514, 'RandomForestRegressor': 0.518, 'LightGBMRegressor': 0.509, 'XGBoostRegressor': 0.513, 'CatBoostRegressor': 0.513}
=> classification est meilleur que regression puis classifi (logique)
=> eux ils avaient fait regression>classification donc ca devrait ameliorer le benchmark

Attention: mauvais resultats quand train/tune/test (separatiob de X train en 3 pour jeu d entraineemnt, de validation interne et de test final pour avoir la metrique) puis prediction pour submission 
=> il faut faire ca pour trouver le meilleur modele mais ensuite la submission doit etre faite sur toutes les donnees, sinon il manque le test (20% du dataset) dans l entrainement
