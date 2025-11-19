# 🔧 Commandes Git Essentielles

Guide rapide pour utiliser Git avec votre projet GitHub.

## 📋 Prérequis

- Git installé : `git --version`
- GitHub account
- Repository créé sur GitHub
- SSH ou HTTPS configuré

---

## 🚀 Configuration Initiale (Une fois)

### 1. Configurer Git Globalement

```bash
# Configurez votre identité (remplacez par vos infos)
git config --global user.name "Votre Nom"
git config --global user.email "votre.email@example.com"

# Vérifier la configuration
git config --global --list
```

### 2. Cloner le Repository

**Via HTTPS** (plus simple) :
```bash
git clone https://github.com/BoubaAhmed/ALS-Alternating-Least-Squares-Recommender.git
cd ALS-Alternating-Least-Squares-Recommender
```

**Via SSH** (plus sécurisé) :
```bash
git clone git@github.com:BoubaAhmed/ALS-Alternating-Least-Squares-Recommender.git
cd ALS-Alternating-Least-Squares-Recommender
```

---

## 💼 Workflow Quotidien

### Avant de Commencer

```bash
# Mettre à jour votre copie locale
git pull origin main

# Créer une branche pour votre travail
git checkout -b feature/ma-feature
```

### Pendant le Développement

```bash
# Voir l'état des fichiers
git status

# Ajouter des fichiers spécifiques
git add chemin/vers/fichier

# Ou ajouter tous les fichiers modifiés
git add -A

# Vérifier ce qui sera commité
git diff --staged

# Faire un commit
git commit -m "feat: Description de vos changements"

# Voir l'historique
git log --oneline -10
```

### Avant de Pousser

```bash
# Récupérer les derniers changements
git pull origin main

# Résoudre les conflits si nécessaire
# (Éditer les fichiers, puis)
git add <fichiers>
git commit -m "fix: Resolve merge conflicts"

# Pousser votre branche
git push origin feature/ma-feature
```

---

## 📤 Soumettre un Pull Request

```bash
# 1. Pousser votre branche
git push origin feature/ma-feature

# 2. Sur GitHub, créer un PR
# - Aller sur le repository
# - Cliquer "Compare & pull request"
# - Ajouter description
# - Soumettre

# 3. Après approbation, fusionner sur GitHub
# (ou depuis la ligne de commande)

# 4. Mettre à jour localement
git checkout main
git pull origin main

# 5. Supprimer votre branche locale
git branch -d feature/ma-feature
```

---

## 🔍 Commandes Utiles Quotidiennes

### Vérifier le Statut

```bash
# Status détaillé
git status

# Voir les branches
git branch -a

# Voir les changements non committés
git diff

# Voir les changements stagiés
git diff --staged

# Voir l'historique complet
git log --oneline
```

### Annuler/Revenir

```bash
# Annuler modifications d'un fichier
git restore <fichier>

# Enlever un fichier du staging
git restore --staged <fichier>

# Annuler le dernier commit (garder changements)
git reset --soft HEAD~1

# Annuler le dernier commit (perdre changements)
git reset --hard HEAD~1

# Revenir à un commit spécifique
git checkout <commit-hash>
```

### Mettre à Jour

```bash
# Récupérer sans fusionner
git fetch origin

# Fusionner les changements distants
git merge origin/main

# Ou en une seule commande
git pull origin main

# Fusionner avec rebase (historique linéaire)
git pull --rebase origin main
```

---

## 🔀 Travailler avec les Branches

### Créer et Basculer

```bash
# Créer une nouvelle branche
git branch feature/nouvelle-feature

# Basculer vers la branche
git checkout feature/nouvelle-feature

# Ou les deux en une commande
git checkout -b feature/nouvelle-feature

# Renommer une branche
git branch -m feature/ancien-nom feature/nouveau-nom

# Supprimer une branche locale
git branch -d feature/ancienne-feature

# Supprimer une branche distante
git push origin --delete feature/ancienne-feature
```

### Voir les Branches

```bash
# Voir branches locales
git branch

# Voir branches distantes
git branch -r

# Voir toutes les branches
git branch -a

# Voir branche actuelle
git branch --show-current
```

---

## 📝 Messages de Commit

### Convention Recommandée

```
<type>(<scope>): <description courte>

<description détaillée>

Fixes #<issue-number>
```

### Types Courants

```
feat:     Nouvelle feature
fix:      Correction de bug
docs:     Documentation
style:    Formatage (pas de changement code)
refactor: Refactorisation
perf:     Optimisation performance
test:     Tests
chore:    Maintenance
```

### Exemples

```bash
# Feature simple
git commit -m "feat: Add ALS early stopping"

# Fix avec détails
git commit -m "fix: Resolve memory leak in matrix operations

- Improved sparse matrix handling
- Added garbage collection
- Fixes #42"

# Documentation
git commit -m "docs: Update README with GPU support info"

# Refactoring
git commit -m "refactor: Simplify recommendation function

- Reduced code complexity from O(n²) to O(n)
- Improved readability
- Maintained API compatibility"
```

---

## 🔗 Synchroniser avec Main

### Mettre à Jour avec Main

```bash
# Option 1 : Merge (préserve historique)
git checkout ma-branche
git merge main

# Option 2 : Rebase (historique linéaire)
git checkout ma-branche
git rebase main
```

### Conflits de Merge

```bash
# Voir les fichiers en conflit
git status

# Éditer les fichiers manuellement
# Puis marquer comme résolu
git add <fichier-résolu>

# Finaliser le merge
git commit -m "fix: Resolve merge conflicts"

# Ou annuler le merge
git merge --abort
```

---

## 📊 Voir l'Historique

### Visualiser les Logs

```bash
# Format simple et court
git log --oneline

# Avec détails
git log --pretty=fuller

# Graphique avec branches
git log --graph --oneline --all

# Avec statistiques
git log --stat

# Dernier commit
git log -1

# Derniers N commits
git log -n 5

# Commits d'un auteur
git log --author="Nom"

# Commits d'aujourd'hui
git log --since="2025-11-19"
```

### Comparer les Versions

```bash
# Diff entre branche et main
git diff main..ma-branche

# Diff entre commits
git diff <commit1>..<commit2>

# Voir qui a modifié une ligne
git blame <fichier>
```

---

## 🚨 Cas d'Urgence

### J'ai commité quelque chose que je ne voulais pas

```bash
# Annuler le dernier commit (garde les changements)
git reset --soft HEAD~1

# Ou récupérer un ancien commit
git revert <commit-hash>
```

### J'ai push du code cassé

```bash
# Faire un commit correcteur
git commit -m "fix: Revert broken changes"
git push origin main

# Ou revenir en arrière (attention, utilisateurs affectés)
git revert <commit-hash>
git push origin main
```

### J'ai perdu mon travail

```bash
# Voir tous les commits supprimés
git reflog

# Récupérer le commit
git checkout <commit-hash>

# Créer une branche pour le récupérer
git checkout -b recovered-work <commit-hash>
```

### Je veux ignorer des changements

```bash
# Ignorer un fichier temporairement (le garder en local)
git update-index --assume-unchanged <fichier>

# Le re-tracker
git update-index --no-assume-unchanged <fichier>

# Ajouter à .gitignore
echo "*.tmp" >> .gitignore
git add .gitignore
git commit -m "chore: Update .gitignore"
```

---

## 🔐 Sécurité

### Secrets et Credentials

```bash
# NE JAMAIS commiter
.env
*.key
*.pem
secrets/
config/passwords.txt

# Vérifier avant de pousser
git diff HEAD

# Enlever un fichier de Git (mais le garder localement)
git rm --cached <fichier>
```

### Si un Secret est Commité

```bash
# Option 1 : Utiliser BFG (recommandé)
bfg --delete-files <nom-fichier> .

# Option 2 : Git filter-branch (avancé)
git filter-branch --tree-filter 'rm -f <fichier>' HEAD

# Option 3 : Simplement faire un nouveau commit
# (Mais le secret restera dans l'historique!)
```

---

## 📚 Ressources Additionnelles

### Documentation Officielle
- [Git Official Docs](https://git-scm.com/doc)
- [GitHub Guides](https://guides.github.com/)
- [GitHub Docs](https://docs.github.com/)

### Outils Visuels
- [GitKraken](https://www.gitkraken.com/) - GUI pour Git
- [VS Code Git Integration](https://code.visualstudio.com/docs/editor/versioncontrol)
- [GitHub Desktop](https://desktop.github.com/)

### Cheatsheets
```bash
# Imprimer une cheatsheet simple
git help -g
```

---

## ✨ Tips Pro

### Alias Utiles

```bash
# Ajouter à votre .gitconfig
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.unstage 'reset HEAD --'
git config --global alias.last 'log -1 HEAD'
git config --global alias.visual 'log --graph --oneline --all'

# Puis utiliser
git st      # Au lieu de git status
git co      # Au lieu de git checkout
git ci      # Au lieu de git commit
```

### Configuration Utile

```bash
# Activer les couleurs
git config --global color.ui true

# Éditeur par défaut
git config --global core.editor "vim"  # ou "nano", "notepad", etc

# Pager (pour voir les longs output)
git config --global core.pager "less -R"
```

---

**Dernière mise à jour** : Novembre 2025

Bon travail avec Git ! 🚀
