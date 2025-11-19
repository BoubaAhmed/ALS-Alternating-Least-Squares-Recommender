# Guide de Contribution

Merci de votre intérêt pour ce projet ! Voici les directives pour contribuer efficacement.

## Comment Contribuer

### 1. Signaler un Bug

- Vérifier que le bug n'a pas déjà été signalé dans les **Issues**
- Créer une nouvelle issue avec un titre descriptif
- Décrire le bug en détail avec les étapes pour le reproduire
- Inclure des captures d'écran ou des logs si pertinent
- Spécifier votre environnement (OS, version Python, etc.)

### 2. Proposer une Amélioration

- Créer une issue avec le label `enhancement`
- Décrire clairement la fonctionnalité proposée et son utilité
- Expliquer pourquoi cette amélioration serait bénéfique

### 3. Soumettre un Pull Request (PR)

1. **Fork** le repository
2. **Créer une branche** pour votre feature:
   ```bash
   git checkout -b feature/ma-nouvelle-feature
   ```
3. **Commiter vos changements**:
   ```bash
   git commit -m "Décrire brièvement les changements"
   ```
4. **Push la branche**:
   ```bash
   git push origin feature/ma-nouvelle-feature
   ```
5. **Créer un Pull Request** sur GitHub

### 4. Conventions de Code

#### Python

- Suivre la **PEP 8**
- Utiliser des noms de variables explicites
- Ajouter des docstrings pour les fonctions
- Limiter les lignes à 88 caractères (Black formatter)

Exemple:

```python
def calculate_rmse(predicted, actual):
    """
    Calcule la Root Mean Square Error entre les valeurs prédites et réelles.

    Args:
        predicted (np.ndarray): Valeurs prédites
        actual (np.ndarray): Valeurs réelles

    Returns:
        float: La valeur RMSE
    """
    return np.sqrt(np.mean((predicted - actual) ** 2))
```

#### Jupyter Notebook

- Garder les cellules bien documentées
- Ajouter des commentaires explicatifs
- Éviter les résultats volumineux
- Utiliser des markdown cells pour expliquer les étapes

### 5. Tests

- Tester votre code localement avant de proposer un PR
- Vérifier que le notebook s'exécute sans erreur
- Inclure des tests unitaires pour les nouvelles fonctions

### 6. Documentation

- Mettre à jour le README si nécessaire
- Ajouter des commentaires clairs dans le code
- Mettre à jour les docstrings
- Documenter tout paramètre nouveau ou modifié

---

## Standards de Qualité

### Code Quality

- ✅ Code lisible et maintenable
- ✅ Pas de code dupliqué
- ✅ Gestion appropriée des erreurs
- ✅ Performance raisonnable

### Documentation

- ✅ README mis à jour
- ✅ Commentaires explicatifs
- ✅ Docstrings complets
- ✅ Exemples d'utilisation

### Performance

- ✅ Utiliser des structures de données efficaces
- ✅ Éviter les boucles imbrées inutiles
- ✅ Vectoriser quand possible avec NumPy

---

## Processus de Review

Chaque PR sera reviewed pour:

1. **Correction** : Le code résout-il le problème/ajoute-t-il la feature ?
2. **Qualité** : Le code suit-il les standards ?
3. **Documentation** : Est-ce bien documenté ?
4. **Tests** : Les tests passent-ils ?

---

## Questions ?

- 📝 Créer une issue avec le label `question`
- 💬 Discuter dans les issues existantes
- 📧 Contacter directement les auteurs

---

## Merci !

Votre contribution aide à rendre ce projet meilleur pour la communauté. 🙏

**Dernière mise à jour** : Novembre 2025
