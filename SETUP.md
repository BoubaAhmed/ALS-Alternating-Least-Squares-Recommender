# Guide de Configuration et d'Installation Détaillé

Ce guide fournit des instructions étape par étape pour installer et configurer le projet ALS vs SVD.

## Table des Matières

1. [Prérequis Système](#prérequis-système)
2. [Installation Rapide](#installation-rapide)
3. [Installation Détaillée](#installation-détaillée)
4. [Configuration Kaggle](#configuration-kaggle)
5. [Troubleshooting](#troubleshooting)
6. [Vérification de l'Installation](#vérification-de-linstallation)

---

## Prérequis Système

### Système d'Exploitation

- Windows 10+, macOS 10.14+, ou Linux (Ubuntu 18.04+)

### Logiciels Requis

1. **Python 3.8 ou supérieur**

   - Vérifier : `python --version`
   - [Télécharger Python](https://www.python.org/downloads/)

2. **Git** (optionnel mais recommandé)

   - Vérifier : `git --version`
   - [Télécharger Git](https://git-scm.com/downloads)

3. **Pip** (généralement inclus avec Python)
   - Vérifier : `pip --version`

### Ressources Matérielles Recommandées

- **RAM** : 8 GB minimum (16 GB recommandé)
- **Espace disque** : 2-3 GB pour le dataset et dépendances
- **CPU** : Processeur multi-cœurs pour meilleure performance

---

## Installation Rapide

Pour les utilisateurs expérimentés :

```bash
# 1. Cloner le repository
git clone https://github.com/BoubaAhmed/ALS-Alternating-Least-Squares-Recommender.git
cd ALS-Alternating-Least-Squares-Recommender

# 2. Créer environnement virtuel
python -m venv venv

# 3. Activer l'environnement
# Windows
venv\Scripts\activate
# macOS/Linux
source venv/bin/activate

# 4. Installer dépendances
pip install -r requirements.txt

# 5. Lancer Jupyter
jupyter notebook als-vs-svd-movies1m.ipynb
```

---

## Installation Détaillée

### Étape 1 : Préparer l'Environnement

#### Windows

```cmd
# Ouvrir Command Prompt en tant qu'administrateur
# Créer un dossier pour le projet
mkdir C:\projects
cd C:\projects

# Cloner le repository
git clone https://github.com/BoubaAhmed/ALS-Alternating-Least-Squares-Recommender.git
cd ALS-Alternating-Least-Squares-Recommender
```

#### macOS/Linux

```bash
# Ouvrir Terminal
# Créer un dossier pour le projet
mkdir ~/projects
cd ~/projects

# Cloner le repository
git clone https://github.com/BoubaAhmed/ALS-Alternating-Least-Squares-Recommender.git
cd ALS-Alternating-Least-Squares-Recommender
```

### Étape 2 : Créer un Environnement Virtuel

L'environnement virtuel isole les dépendances du projet.

#### Windows

```cmd
# Créer l'environnement virtuel
python -m venv venv

# Activer l'environnement
venv\Scripts\activate

# Vous verrez (venv) dans votre prompt
```

#### macOS/Linux

```bash
# Créer l'environnement virtuel
python3 -m venv venv

# Activer l'environnement
source venv/bin/activate

# Vous verrez (venv) dans votre prompt
```

### Étape 3 : Mettre à Jour Pip

```bash
# Pour tous les systèmes (avec venv activé)
pip install --upgrade pip setuptools wheel
```

### Étape 4 : Installer les Dépendances

```bash
# Avec venv activé
pip install -r requirements.txt

# ✅ L'installation prend 5-10 minutes
# Cela inclut :
# - NumPy : Calculs numériques
# - Pandas : Manipulation de données
# - SciPy : Algèbre linéaire
# - Scikit-Learn : ML utilities
# - Matplotlib : Visualisation
# - Scikit-Surprise : Algorithme SVD
# - Implicit : Libraries optimisées
# - Kagglehub : Download dataset
# - Jupyter : Notebooks interactifs
```

### Étape 5 : Vérifier l'Installation

```bash
# Vérifier que tous les packages sont installés
pip list

# Vérifier les versions principales
python -c "import numpy; print(f'NumPy: {numpy.__version__}')"
python -c "import pandas; print(f'Pandas: {pandas.__version__}')"
python -c "import sklearn; print(f'Scikit-Learn: {sklearn.__version__}')"
```

---

## Configuration Kaggle

### Obtenir votre Clé API Kaggle

1. **Aller sur [Kaggle.com](https://www.kaggle.com/)**

   - Créer un compte si nécessaire
   - Se connecter à votre compte

2. **Accéder aux Paramètres**

   - Cliquer sur le profil (coin supérieur droit)
   - Sélectionner "Settings"
   - Aller à "API"

3. **Télécharger la Clé**

   - Cliquer "Create New API Token"
   - Un fichier `kaggle.json` sera téléchargé

4. **Configurer Kaggle Localement**

   **Windows:**

   ```
   C:\Users\[YourUsername]\.kaggle\kaggle.json
   ```

   **macOS/Linux:**

   ```
   ~/.kaggle/kaggle.json
   ```

   - Copier le fichier `kaggle.json` à la bonne localisation
   - Modifier les permissions (macOS/Linux) :

   ```bash
   chmod 600 ~/.kaggle/kaggle.json
   ```

5. **Tester la Configuration**
   ```bash
   kagglehub api_class datasets download -d sherinclaudia/movielens --unzip
   ```

---

## Lancer le Notebook

### Démarrer Jupyter Notebook

```bash
# Avec l'environnement virtuel activé
jupyter notebook als-vs-svd-movies1m.ipynb
```

Cela ouvrira automatiquement votre navigateur à `http://localhost:8888`

### Alternative : Jupyter Lab (interface moderne)

```bash
# Installer Jupyter Lab
pip install jupyterlab

# Démarrer Jupyter Lab
jupyter lab als-vs-svd-movies1m.ipynb
```

### Utiliser VSCode (optionnel)

1. Installer l'extension Jupyter dans VSCode
2. Ouvrir le fichier `.ipynb`
3. Sélectionner le kernel Python (l'environnement venv)
4. Exécuter les cellules

---

## Troubleshooting

### Problème : "Python n'est pas trouvé"

**Cause** : Python n'est pas dans le PATH

**Solution Windows** :

- Réinstaller Python
- Cocher "Add Python to PATH" pendant l'installation

**Solution macOS/Linux** :

```bash
which python3
# Si introuvable, installer via Homebrew
brew install python3
```

### Problème : "Permissions denied on kaggle.json"

**Solution** :

```bash
# macOS/Linux
chmod 600 ~/.kaggle/kaggle.json
chmod 700 ~/.kaggle/

# Windows : Ignorer, les permissions sont différentes
```

### Problème : "ModuleNotFoundError: No module named 'X'"

**Cause** : Oubli d'installer les dépendances

**Solution** :

```bash
# Vérifier que venv est activé (devrait voir (venv) dans le prompt)
# Réinstaller
pip install -r requirements.txt
```

### Problème : "Jupyter not found"

**Solution** :

```bash
# Réinstaller Jupyter
pip install jupyter notebook

# Puis lancer
jupyter notebook als-vs-svd-movies1m.ipynb
```

### Problème : "Memory Error" lors du download du dataset

**Cause** : RAM insuffisante

**Solutions** :

1. Fermer autres applications
2. Utiliser un subset du dataset dans le notebook
3. Augmenter la RAM disponible

### Problème : Réseau - Téléchargement du dataset échoue

**Cause** : Connexion Internet instable

**Solutions** :

1. Vérifier la connexion
2. Relancer la cellule
3. Télécharger manuellement sur [GroupLens](https://grouplens.org/datasets/movielens/1m/)

---

## Vérification de l'Installation

### Exécuter un Test Simple

Créer un fichier `test_setup.py` :

```python
#!/usr/bin/env python3
"""Script de vérification de l'installation"""

import sys

packages = {
    'numpy': 'Calculs numériques',
    'pandas': 'Manipulation de données',
    'scipy': 'Algèbre linéaire',
    'sklearn': 'Machine Learning',
    'matplotlib': 'Visualisation',
    'surprise': 'Algorithmes recommandation',
    'jupyter': 'Notebooks interactifs',
}

print("=" * 50)
print("VÉRIFICATION DE L'INSTALLATION")
print("=" * 50)
print(f"Python: {sys.version}\n")

failed = []
for package, description in packages.items():
    try:
        mod = __import__(package)
        version = getattr(mod, '__version__', 'Unknown')
        print(f"✅ {package:15} {version:10} - {description}")
    except ImportError:
        print(f"❌ {package:15} NOT INSTALLED  - {description}")
        failed.append(package)

print("\n" + "=" * 50)
if not failed:
    print("✅ TOUS LES PACKAGES SONT INSTALLÉS!")
else:
    print(f"❌ Packages manquants: {', '.join(failed)}")
    print("   Exécutez: pip install -r requirements.txt")
print("=" * 50)
```

**Exécuter le test** :

```bash
python test_setup.py
```

### Tester le Notebook

- Ouvrir le notebook
- Exécuter les 3 premières cellules
- Vérifier qu'aucune erreur n'apparaît

---

## Optimisations Optionnelles

### Installer des Packages Supplémentaires

**Pour plus de fonctionnalités** :

```bash
# Analyse interactive
pip install plotly

# Calculs plus rapides (optionnel)
pip install numba

# Parallélisation
pip install joblib
```

### Configurer VS Code (optionnel)

1. Installer VS Code
2. Installer extensions :

   - Python (Microsoft)
   - Jupyter (Microsoft)
   - Python Type Hint

3. Sélectionner l'interpréteur Python :
   - Ctrl+Shift+P
   - "Python: Select Interpreter"
   - Choisir le venv créé

---

## Prochaines Étapes

✅ Installation complète  
▶️ [Lire le README](README.md)  
▶️ [Exécuter le Notebook](als-vs-svd-movies1m.ipynb)  
▶️ [Consulter le Rapport](rapport_ALS.pdf)

---

## Support

Pour des problèmes :

- 🔍 Consulter la section Troubleshooting ci-dessus
- 🐛 Créer une issue sur GitHub
- 📧 Contacter les auteurs

---

**Dernière mise à jour** : Novembre 2025
