# ALS vs SVD - Systèmes de Recommandation MovieLens

Un projet académique comparatif implémentant **Alternating Least Squares (ALS)** et **Singular Value Decomposition (SVD)** pour les systèmes de recommandation sur le dataset MovieLens 1M.

## 📋 À Propos

Ce projet explore deux algorithmes fondamentaux de recommandation collaborative :

- **ALS** : Implémentation personnalisée avec early stopping, optimisation itérative, et régularisation
- **SVD** : Implémentation via la bibliothèque Surprise avec comparaison directe

### Objectifs du Projet

✅ Implémenter ALS from scratch avec optimisation avancée  
✅ Comparer les performances avec SVD de référence  
✅ Analyser les facteurs latents et l'espace des représentations  
✅ Évaluer avec des métriques de ranking (Precision@k, Recall@k, NDCG@k)  
✅ Fournir une analyse approfondie du comportement des deux modèles

---

## 🎯 Auteurs

- **Mohamed LKHALIDI**
- **Ahmed BOUBA**

**Institution** : Master Intelligent Systems, Université Moulay Ismail  
**Date** : Novembre 2025  
**Contexte** : Cours "Systèmes de Recommandation et Blockchain"

---

## 📁 Structure du Projet

```
als-vs-svd-movies1m/
├── als-vs-svd-movies1m.ipynb          # Notebook Jupyter principal
├── rapport_ALS.pdf                     # Rapport détaillé (PDF)
├── README.md                           # Ce fichier
├── .gitignore                          # Configuration Git
├── requirements.txt                    # Dépendances Python
├── LICENSE                             # Licence du projet
└── PPT/
    ├── PPT_ALS_Systemes_de_recommandation (5).pdf
    ├── PPT_ALS_Systemes_de_recommandation (8).pdf
    └── [présentations supplémentaires]
```

---

## 🚀 Installation et Configuration

### Prérequis

- Python 3.8+
- pip ou conda
- Jupyter Notebook

### Étapes d'Installation

1. **Cloner le repository**

```bash
git clone https://github.com/BoubaAhmed/ALS-Alternating-Least-Squares-Recommender.git
cd ALS-Alternating-Least-Squares-Recommender
```

2. **Créer un environnement virtuel** (optionnel mais recommandé)

```bash
python -m venv venv
# Windows
venv\Scripts\activate
# macOS/Linux
source venv/bin/activate
```

3. **Installer les dépendances**

```bash
pip install -r requirements.txt
```

4. **Lancer le notebook Jupyter**

```bash
jupyter notebook als-vs-svd-movies1m.ipynb
```

---

## 📊 Dataset

**MovieLens 1M** - Téléchargement automatique via Kaggle

### Caractéristiques

- **6,040 utilisateurs**
- **3,706 films**
- **1,000,209 notes** (échelle 1-5)
- **Sparsité : ~95.64%**
- **Densité : ~4.36%**

### Fichiers Utilisés

- `ratings.dat` : Combinaison UserID, MovieID, Rating
- `movies.dat` : Métadonnées des films (titres, genres)
- `users.dat` : Informations utilisateurs (âge, genre, occupation)

---

## 🧠 Méthodologie

### 1. Prétraitement des Données

- **Normalisation** : Conversion des notes 1-5 → 0-1
- **Matrices Creuses** : Utilisation de CSR (Compressed Sparse Row) pour l'efficacité mémoire
- **Split Train/Test** : 75% train / 25% test, préservant la structure par utilisateur

### 2. Implémentation ALS

#### Algorithme

```
Pour chaque itération:
  1. Optimiser les vecteurs utilisateurs (résolution système linéaire)
  2. Optimiser les vecteurs items (résolution système linéaire)
  3. Évaluer RMSE/MAE sur validation
  4. Appliquer early stopping si pas d'amélioration
```

#### Caractéristiques Avancées

- **Early Stopping** : Arrêt automatique après 5 itérations sans amélioration
- **Régularisation L2** : λ = 1.1 pour éviter l'overfitting
- **Optimisation Vectorisée** : Calculs batch pour les évaluations
- **Tolerance** : ε = 1e-4 pour convergence

### 3. Algorithme SVD (Surprise)

- **Factorisation de matrices** via descente de gradient
- **Facteurs latents** : 10 dimensions
- **Learning rate** : 0.005
- **Epochs** : 30 itérations

### 4. Split des Données

```
Dataset original (1M ratings)
    ↓
Train (75%) + Test (25%)
    ↓
Train → Train split (90%) + Validation (10%)
    ↓
Entraînement ALS avec early stopping
```

---

## 📈 Résultats

### Performances Quantitatives

| Modèle  | RMSE   | MAE    | Précision@10 | Recall@10 | NDCG@10 | Coverage@10 |
| ------- | ------ | ------ | ------------ | --------- | ------- | ----------- |
| **ALS** | 0.3842 | 0.2567 | 0.4521       | 0.3642    | 0.6234  | 0.8945      |
| **SVD** | 0.3915 | 0.2614 | 0.4389       | 0.3521    | 0.6105  | 0.8876      |

### Conclusions

✅ **ALS légèrement supérieur** en RMSE et métriques de ranking  
✅ **Convergence rapide** : early stopping actif après ~8 itérations  
✅ **Coverage excellente** : 89%+ du catalogue recommandé  
✅ **Gain temps** : ~73% d'économies avec early stopping

---

## 📊 Analyse des Facteurs Latents

### Visualisation PCA 2D

- Réduction de 10 dimensions → 2 dimensions principales
- Coloration par genre de film
- Variance expliquée : ~62%
- Révèle les clusters de films similaires

### Interprétations

- Films du même genre se groupent naturellement
- Les facteurs latents capturent les préférences utilisateurs
- Structure cohérente confirmant l'apprentissage efficace

---

## 🔍 Métriques d'Évaluation

### Métriques Utilisées

1. **RMSE** (Root Mean Square Error)

   - Mesure globale de précision
   - Sensible aux grosses erreurs
   - Échelle normalisée 0-1

2. **MAE** (Mean Absolute Error)

   - Erreur moyenne absolue
   - Interprétation directe en notes 1-5

3. **Precision@k**

   - Proportion de recommandations pertinentes
   - k=10 : top-10 recommandations

4. **Recall@k**

   - Capacité à retrouver tous les items pertinents
   - Important pour la complétude

5. **NDCG@k** (Normalized Discounted Cumulative Gain)

   - Qualité du ranking
   - Récompense les items pertinents en haut de liste
   - Normalisation pour comparabilité

6. **Coverage@k**
   - Pourcentage du catalogue utilisé
   - Diversité des recommandations

---

## 💻 Utilisation

### Faire des Recommandations

```python
# Charger le modèle entraîné
model = ALSRecommender(n_factors=10, lambda_reg=1.1)
model.fit(train_matrix, validation_matrix=val_matrix)

# Obtenir 10 recommandations pour l'utilisateur 100
recs = model.recommend_for_user(user_id=100, n_recommendations=10)
for item_id, pred_score in recs:
    print(f"Item {item_id}: Score prédite {pred_score:.2f}")
```

### Évaluer le Modèle

```python
# RMSE sur ensemble de test
test_rmse = model.calculate_rmse(test_matrix)
test_mae = model.calculate_mae(test_matrix)

print(f"Test RMSE: {test_rmse:.4f}")
print(f"Test MAE: {test_mae:.4f}")
```

### Visualiser l'Apprentissage

```python
# Afficher courbes de convergence
model.plot_training_history()
model.plot_combined_training_history()
```

---

## 📚 Contenu du Notebook

Le notebook Jupyter couvre :

1. ✅ Installation et importation des dépendances
2. ✅ Téléchargement automatique de MovieLens 1M
3. ✅ Exploration et analyse du dataset
4. ✅ Prétraitement et normalisation
5. ✅ Construction de matrices creuses CSR
6. ✅ Split train/test/validation
7. ✅ **Implémentation complète d'ALS**
8. ✅ Entraînement avec early stopping
9. ✅ **Implémentation SVD (Surprise)**
10. ✅ Comparaison détaillée des deux modèles
11. ✅ Visualisation des facteurs latents (PCA)
12. ✅ Évaluation multi-critères
13. ✅ Génération d'exemples de recommandations
14. ✅ Graphiques comparatifs

---

## 📖 Ressources Complémentaires

### Fichiers du Projet

- **`rapport_ALS.pdf`** : Rapport académique détaillé (17+ pages)

  - Introduction théorique
  - Formulation mathématique complète
  - Résultats expérimentaux
  - Conclusion et perspectives

- **`PPT/`** : Présentations PowerPoint
  - Slides de synthèse du projet
  - Illustrations visuelles
  - Résultats clés

---

## 🎓 Concepts Clés

### Factorisation de Matrices

La factorisation vise à décomposer la matrice utilisateur×item R :

R ≈ U × V^T

Où :

- **U** : Matrice utilisateurs (m × k)
- **V** : Matrice items (n × k)
- **k** : Nombre de facteurs latents

### Optimisation ALS

Pour chaque facteur, résoudre le système linéaire :

(V^T V + λI) u_i = V^T r_i

### Early Stopping

- Monitorer RMSE de validation
- Arrêter si pas d'amélioration pendant N itérations
- Restaurer les meilleurs paramètres

---

## ⚙️ Hyperparamètres

### Configuration Optimale ALS

```python
n_factors = 10              # Dimensions latentes
lambda_reg = 1.1            # Régularisation L2
n_iterations = 30           # Maximum d'itérations
early_stopping_rounds = 5   # Patience early stopping
tolerance = 1e-4           # Seuil d'amélioration
```

### Configuration SVD

```python
n_factors = 10
n_epochs = 30
lr_all = 0.005            # Learning rate
reg_all = 1.1             # Régularisation
```

---

## 🔧 Dépendances

```
numpy>=1.21.0
pandas>=1.3.0
scipy>=1.7.0
scikit-learn>=0.24.0
matplotlib>=3.4.0
scikit-surprise>=1.1.0
implicit>=0.5.2
kagglehub>=0.1.0
```

Installation via `requirements.txt` fourni.

---

## 📝 Licence

Ce projet est sous licence MIT. Voir `LICENSE` pour plus de détails.

---

## 🙏 Remerciements

- MovieLens pour le dataset
- Bibliothèque Surprise pour l'implémentation SVD de référence
- Université Moulay Ismail pour le contexte académique

---

## 📞 Contact

Pour des questions sur le projet :

- **GitHub Issues** : Utiliser le système d'issues du repository

---

## 🔮 Améliorations Futures

- [ ] Parallélisation des calculs ALS
- [ ] Support des GPU pour les matrices volumineuses
- [ ] API REST pour les recommandations en temps réel
- [ ] Interface web avec Streamlit/Flask
- [ ] Intégration de données auxiliaires (contenu films)
- [ ] Évaluation cross-validation k-fold
- [ ] Optimisation des hyperparamètres (grid search)

---

**Dernière mise à jour** : Novembre 2025
