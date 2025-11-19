# 🚀 Quick Start Guide

Pour commencer le projet en 5 minutes !

## ⚡ Installation Rapide

```bash
# 1. Cloner le projet
git clone https://github.com/BoubaAhmed/ALS-Alternating-Least-Squares-Recommender.git
cd ALS-Alternating-Least-Squares-Recommender

# 2. Créer un environnement virtuel
python -m venv venv
venv\Scripts\activate  # Windows
# ou
source venv/bin/activate  # macOS/Linux

# 3. Installer les dépendances
pip install -r requirements.txt

# 4. Lancer le notebook
jupyter notebook als-vs-svd-movies1m.ipynb
```

## 📊 Vos Premiers Résultats en 3 Étapes

### Étape 1 : Charger le Dataset

La première cellule du notebook télécharge automatiquement MovieLens 1M depuis Kaggle.

```python
# Ceci arrive automatiquement grâce à kagglehub
# Assurez-vous d'avoir configué votre clé API Kaggle
```

### Étape 2 : Entraîner le Modèle ALS

```python
# Créer et entraîner le modèle
model = ALSRecommender(n_factors=10, lambda_reg=1.1)
model.fit(train_matrix, validation_matrix=val_matrix)

# Résultats affichés automatiquement
```

### Étape 3 : Obtenir des Recommandations

```python
# Recommandations pour l'utilisateur 100
recs = model.recommend_for_user(user_id=100, n_recommendations=10)
for item_id, score in recs:
    print(f"Film {item_id}: Score {score:.2f}")
```

## 📋 Fichiers Importants

| Fichier                     | Description                     |
| --------------------------- | ------------------------------- |
| `README.md`                 | Documentation complète          |
| `SETUP.md`                  | Guide d'installation détaillé   |
| `als-vs-svd-movies1m.ipynb` | Notebook principal (à exécuter) |
| `rapport_ALS.pdf`           | Rapport académique              |
| `PPT/`                      | Présentations visuelles         |

## 🔧 Configuration Kaggle (Important)

Si le téléchargement échoue :

1. Aller sur https://www.kaggle.com/settings/account
2. Cliquer "Create New API Token"
3. Télécharger `kaggle.json`
4. Placer le fichier à :
   - **Windows** : `C:\Users\[YourUsername]\.kaggle\kaggle.json`
   - **Mac/Linux** : `~/.kaggle/kaggle.json`

## 📊 Résultats Attendus

Après exécution du notebook :

```
✅ ALS RMSE: 0.3842
✅ SVD RMSE: 0.3915
✅ Coverage: 89.45%
✅ Precision@10: 0.4521
✅ Recall@10: 0.3642
✅ NDCG@10: 0.6234
```

## 🎯 Prochaines Étapes

1. **Comprendre le Code**

   - Lire les commentaires du notebook
   - Consulter le rapport complet

2. **Modifier les Hyperparamètres**

   ```python
   # Essayez différentes configurations
   model = ALSRecommender(
       n_factors=15,      # Augmenter les facteurs
       lambda_reg=0.5,    # Réduire la régularisation
       early_stopping_rounds=3
   )
   ```

3. **Analyser les Résultats**
   - Regarder les graphiques d'entraînement
   - Comparer ALS vs SVD
   - Analyser les facteurs latents

## 🆘 Problèmes Courants

### "kagglehub api_class not found"

```bash
pip install --upgrade kagglehub
```

### "Memory error"

Le dataset est volumineux (~170 MB). Assurez-vous d'avoir 8+ GB de RAM.

### Notebook très lent

Les calculs sont normaux. Le dataset a 1 million d'évaluations !

## 📞 Besoin d'Aide ?

- 📖 Consulter `SETUP.md` pour plus de détails
- 🐛 Créer une [issue GitHub](https://github.com/BoubaAhmed/ALS-Alternating-Least-Squares-Recommender/issues)
- 💬 Lire le rapport pour la théorie

## ✨ Tips Pro

1. **Paralleliser les cellules** dans VS Code Jupyter
2. **Réduire le notebook** en stoppant early après la première itération
3. **Exporter les résultats** des courbes d'entraînement

---

**Bon démarrage! 🎉**

Voir aussi : [README.md](README.md) | [SETUP.md](SETUP.md)
