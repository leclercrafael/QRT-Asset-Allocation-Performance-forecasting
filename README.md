# 🧠 QRT Grand Data Challenge 2025

## 🎯 Objectif du projet  
Ce projet a été réalisé dans le cadre du **QRT Grand Data Challenge**, un hackathon de modélisation prédictive en finance de marché.  
L’objectif est de construire un modèle capable de **prédire le signal de trading (target)** à partir de séries temporelles de données de marché, tout en gérant un très grand volume de features et un historique temporel complexe.

---

## ⚙️ Approche générale  

L’ensemble du travail repose sur une approche structurée en plusieurs étapes :  

1. **Exploration du dataset**
   - Analyse des distributions et corrélations.
   - Étude des colonnes temporelles, notamment les variables à l’échelle des jours.  
   - Gestion des valeurs manquantes et détection des features non pertinentes.

2. **Feature Engineering**
   - Création de **lags sur 20 jours** pour capturer la dépendance temporelle.  
   - Ajout de **moyennes glissantes**, **ratios dynamiques** et **écarts normalisés**.  
   - Réduction de la dimension via un **auto-encoder** (Keras / PyTorch).  
   - Encodage ciblé (`Target Encoding`) pour certaines variables catégorielles.

3. **Modélisation**
   - Entraînement de modèles classiques et gradient boosting :  
     - `LightGBMRegressor` (modèle principal)  
     - `XGBoost` pour comparaison  
     - `Ridge` et `LinearRegression` comme baselines.  
   - Utilisation de **callbacks LightGBM** pour suivre la loss et éviter l’overfitting.  
   - Optimisation des hyperparamètres avec **Optuna**.

4. **Évaluation**
   - Validation croisée temporelle (split par période).  
   - Métrique principale : **accuracy / corrélation du signal**.  
   - Analyse des erreurs et importance des features (via SHAP / gain).  

---

## 🧩 Architecture du projet  

```bash
├── data/
│   ├── train.csv
│   ├── test.csv
│   └── sample_submission.csv
│
├── notebooks/
│   ├── 01_data_exploration.ipynb
│   ├── 02_feature_engineering_lags.ipynb
│   ├── 03_autoencoder_dim_reduction.ipynb
│   ├── 04_model_training_lgbm.ipynb
│   ├── 05_optuna_tuning.ipynb
│   └── 06_final_submission.ipynb
│
├── src/
│   ├── preprocessing.py        # Fonctions de nettoyage et génération des lags
│   ├── autoencoder.py          # Réduction de dimension avec Keras
│   ├── modeling.py             # Entraînement des modèles et callbacks
│   └── utils.py                # Fonctions auxiliaires (scoring, plots, etc.)
│
├── requirements.txt
├── README.md
└── submission.csv
