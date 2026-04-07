# 🏥 MedBridge-AI

[![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![NLP](https://img.shields.io/badge/Domain-NLP%20%2F%20ASR-red.svg)]()

**MedBridge-AI** est un projet de recherche et développement (module APS) visant à briser les barrières linguistiques en milieu hospitalier. Le système propose un pipeline de traduction multilingue spécialisé, facilitant la communication entre patients parlant des langues à faibles ressources (Ewé, Dioula, etc.) et professionnels de santé.

## 🚀 Objectif Technique
L'objectif est de mettre en œuvre un pipeline robuste de bout en bout :
`Audio (Patient) ➔ ASR (Reconnaissance vocale) ➔ Texte ➔ MT (Traduction Médicale) ➔ Résultat (Praticien)`

---

## 📂 Structure du Dépôt

```text
MedBridge-AI/
├── configs/          # Fichiers YAML (hyperparamètres, modèles, chemins)
├── data/             # Gestion des données (non versionnées)
│   ├── raw/          # Données brutes (audio/texte)
│   └── processed/    # Données nettoyées et préparées
├── notebooks/        # Exploration, analyse de données et prototypage
├── src/              # Code source modulaire
│   ├── data/         # Scripts de chargement et preprocessing
│   ├── models/       # Définition des modèles (ASR, NLLB, etc.)
│   ├── pipelines/    # Orchestration du flux ASR → MT
│   └── utils/        # Fonctions utilitaires (logs, paths, metrics)
├── scripts/          # Scripts d'exécution (entraînement, inférence)
├── cluster/          # Scripts de soumission HPC (SLURM)
├── tests/            # Tests unitaires et d'intégration
├── outputs/          # Logs, checkpoints et résultats (non versionnés)
├── requirements.txt  # Dépendances du projet
└── README.md         # Documentation principale
```

---

## 🛠️ Rôles des Dossiers

### ⚙️ Configuration (`configs/`)
Tous les paramètres sont centralisés dans des fichiers YAML. 
* **Règle :** Aucun paramètre important (taux d'apprentissage, noms des modèles Hugging Face) ne doit être écrit en dur dans le code.

### 🧠 Code Source (`src/`)
Le projet est structuré pour être modulaire :
* **`data/`** : Scripts pour transformer les données brutes en formats utilisables par les modèles.
* **`models/`** : Contient l'instanciation des architectures IA.
* **`pipelines/`** : Gère l'enchaînement logique entre les différents modules.

### ⚡ Calcul Haute Performance (`cluster/`)
Contient les scripts nécessaires pour lancer les calculs sur le cluster de l'université (SLURM).
Exemple de lancement :
```bash
sbatch cluster/train_asr.sh
```

---

## 💻 Installation & Usage

### 1. Configuration de l'environnement
```bash
# Via pip
pip install -r requirements.txt

# Ou via Conda
conda env create -f environment.yml
conda activate medbridge-ai
```

### 2. Exécution du pipeline
```bash
python scripts/run_pipeline.py --config configs/default_config.yaml
```

---

## 📏 Bonnes Pratiques & Workflow

Afin de garantir la reproductibilité et la propreté du dépôt :

1.  **Gestion Git :** Ne jamais versionner les dossiers `data/`, `outputs/` et `checkpoints/`. Utilisez le `.gitignore`.
2.  **Modularité :** Dès qu'une fonction dans un `notebook` est validée, déplacez-la dans le module correspondant dans `src/`.
3.  **Chemins :** N'utilisez jamais de chemins absolus (ex: `C:/Users/...`). Utilisez les utilitaires de gestion de chemins dans `src/utils/`.
4.  **Collaboration :**
    * Travaillez sur des branches : `git checkout -b feature/nom-de-la-tache`.
    * Documentez vos fonctions (docstrings).

---

## 👥 Équipe
Projet réalisé dans le cadre du module **APS** (Master IA - Avignon Université).

---

## 📝 Licence
Ce projet est sous licence MIT. Voir le fichier `LICENSE` pour plus de détails.
```
