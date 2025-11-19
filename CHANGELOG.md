# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2025-11-19

### Added

- ✅ **Implémentation complète d'ALS** avec optimisation itérative
- ✅ **Early Stopping** pour éviter l'overfitting
- ✅ **Comparaison SVD** via bibliothèque Surprise
- ✅ **Métriques avancées** : RMSE, MAE, Precision@k, Recall@k, NDCG@k, Coverage@k
- ✅ **Visualisation PCA** des facteurs latents
- ✅ **Analyse complète du dataset** MovieLens 1M
- ✅ **Rapport académique détaillé** (PDF)
- ✅ **Présentations PowerPoint** du projet
- ✅ **Documentation complète** du README
- ✅ **Fichiers de configuration** (.gitignore, LICENSE, requirements.txt)

### Fichiers Principaux

- `als-vs-svd-movies1m.ipynb` : Notebook Jupyter principal (2000+ lignes)
- `rapport_ALS.pdf` : Rapport académique (17+ pages)
- `PPT/` : Présentations visuelles
- Configuration GitHub : `README.md`, `LICENSE`, `.gitignore`

### Performance Initiale

- **ALS RMSE** : 0.3842
- **SVD RMSE** : 0.3915
- **Gain temps early stopping** : 73%
- **Coverage** : 89%+ du catalogue

### Known Limitations

- Téléchargement du dataset via Kaggle (nécessite clé API)
- Calculs optimisés mais sans support GPU
- Évaluation sur dataset MovieLens 1M uniquement

---

## Roadmap Futures

### v1.1.0 (Planifié)

- [ ] Parallélisation des calculs ALS
- [ ] Support GPU avec CuPy/Numba
- [ ] Optimisation hyperparamètres automatique
- [ ] Tests unitaires complets
- [ ] CLI pour utilisation facile

### v1.2.0 (Planifié)

- [ ] API REST avec FastAPI
- [ ] Interface web avec Streamlit
- [ ] Export des modèles (pickle/joblib)
- [ ] Batch recommendations

### v2.0.0 (Futur)

- [ ] Recommandations hybrides (contenu + collaboratif)
- [ ] Support multi-datasets
- [ ] Évaluation cross-validation
- [ ] Visualisations interactives

---

## Historique des Commits

### Initial Release (v1.0.0)

```
- feat: Implémentation ALS complète
- feat: Intégration SVD Surprise
- feat: Métriques d'évaluation avancées
- docs: Documentation complète
- chore: Configuration GitHub
```

---

## Notes de Compatibilité

### Versions Python Supportées

- Python 3.8+
- Python 3.9 ✅ (Testé)
- Python 3.10 ✅ (Testé)
- Python 3.11 ✅ (Recommandé)

### Dépendances Clés

| Package         | Version  | Status    |
| --------------- | -------- | --------- |
| numpy           | >=1.21.0 | ✅ Stable |
| pandas          | >=1.3.0  | ✅ Stable |
| scipy           | >=1.7.0  | ✅ Stable |
| scikit-learn    | >=0.24.0 | ✅ Stable |
| scikit-surprise | >=1.1.0  | ✅ Stable |

---

## Problèmes Connus et Solutions

### Problème : Téléchargement du dataset échoue

**Cause** : Clé API Kaggle manquante  
**Solution** : Configurer kagglehub avec votre clé

### Problème : Memory error sur gros datasets

**Cause** : Insuffisance RAM  
**Solution** : Réduire batch size ou utiliser subset du dataset

### Problème : Convergence lente

**Cause** : Hyperparamètres sous-optimaux  
**Solution** : Ajuster lambda_reg et n_factors

---

## Contribution et Feedback

Pour signaler des bugs ou proposer des améliorations :

- 🐛 [GitHub Issues](https://github.com/BoubaAhmed/ALS-Alternating-Least-Squares-Recommender/issues)
- 💬 Discussions dans les Pull Requests
- 📧 Contact direct aux auteurs

---

## Crédits

- **Auteurs** : Mohamed LKHALIDI, Ahmed BOUBA
- **Université** : Moulay Ismail, Master Intelligent Systems
- **Dataset** : GroupLens Research (MovieLens)
- **Bibliothèques** : NumPy, Pandas, Scikit-Learn, Scikit-Surprise

---

**Dernière mise à jour** : Novembre 2025
