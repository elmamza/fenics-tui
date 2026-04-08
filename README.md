# Beam Solver – TUI pour l'analyse de poutres avec FEniCS

Projet personnel de démonstration pour l'analyse de poutres utilisant FEniCS, exécuté via un pod Jupyter sur Kubernetes.

![Demo](./demo.gif)

## ✨ Fonctionnalités

### Sélection interactive de poutres
Choix parmi 6 types de poutres (console, bi-encastré, encastré-rotulé), avec charges ponctuelles ou réparties

### Configuration de section
6 types disponibles : rectangulaire, circulaire, creuse, poutre en I, en U

### Propriétés des matériaux
Saisie du module de Young (E) et du coefficient de Poisson (ν)

### Définition des charges
Position et intensité des forces

### Intégration Kubernetes
Envoi automatique du fichier problem.json vers un pod Jupyter
Exécution du notebook via papermill

### Visualisation des résultats
Affichage des contraintes, déformations et comparaison avec les solutions analytiques

## ⚙️ Installation

### Prérequis
- Cluster Kubernetes avec accès à un service Jupyter Notebook
- `kubectl` configuré et fonctionnel

### Option 1 : Binaire précompilé
```bash
wget https://github.com/yourusername/fenics-tui/releases/latest/download/beam_app
chmod +x beam_app
./beam_app
```

### Option 2 : Compiler depuis les sources
```bash
git clone https://github.com/yourusername/fenics-tui.git
cd fenics-tui
go mod download
go build -o beam_app main.go
./beam_app
```

## 🚀 Utilisation

1. **Lancer l'application** :
   ```bash
   ./beam_app
   ```

2. **Navigation** :
   - Flèches directionnelles (↑↓←→)
   - ou touches Vim (h, j, k, l)
   - Appuyer sur **Entrée** pour valider chaque étape

3. **Saisir les valeurs numériques** demandées

4. **Après validation** :
   - Envoi de problem.json vers le pod Jupyter
   - Exécution du notebook FEniCS
   - Récupération et affichage des résultats

## 🔧 Configuration

Le binaire/notebook est préconfiguré pour un environnement Kubernetes spécifique. Pour l'adapter, modifier le code source :

- **Namespace Kubernetes** : `-n namespace`
- **Nom du pod Jupyter** : `jupyter-name`
- **Notebook exécuté** : `poutre.ipynb`

## 📁 Structure du projet

```
fenics-tui/
├── main.go              # Code source Go
├── go.mod               # Dépendances Go
├── go.sum               # Checksums des dépendances
├── beam_app             # Binaire précompilé (optionnel)
├── docs/
│   └── poutre.ipynb     # Notebook FEniCS
├── LICENSE              # Licence MIT
└── README.md            # Documentation
```

## 📜 Licence

Licence MIT – voir le fichier LICENSE pour plus de détails.

## 🙌 Crédits

Construit avec [Bubble Tea](https://github.com/charmbracelet/bubbletea) — un framework puissant pour créer des interfaces terminal en Go
