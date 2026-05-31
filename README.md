# 🧠 Centre Neurologique – Prédiction du Risque d'AVC
### Modèle Hybride **TabNet-MLP** | SHAP & LIME | Déploiement Streamlit Cloud

> **Auteurs :** Dauris · Bouchra · Amine  
> **Stack :** Google Colab · GitHub · Streamlit Cloud  
> **Modèle :** Hybride TabNet (attention sélective) + MLP (branches profondes)

---

## 🚀 Déploiement Rapide

### 1. Streamlit Cloud (recommandé)
[![Open in Streamlit](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io)

1. Aller sur [share.streamlit.io](https://share.streamlit.io)
2. `New app` → sélectionner ce repo
3. Main file : `app.py`
4. Cliquer `Deploy!`

### 2. Google Colab (entraînement + déploiement)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com)

Ouvrir `notebooks/DeploiementAVC_TabNetMLP.ipynb`

### 3. Local
```bash
pip install -r requirements.txt
streamlit run app.py
```

---

## 🏗️ Architecture du Modèle

```
Input (10 features)
       │
  ┌────┴────┐
  │         │
TabNet    MLP
(Attention) (Deep)
  │         │
  └────┬────┘
     Fusion
       │
   Sigmoid → Risque AVC [0,1]
```

### TabNet
- Mécanisme d'attention séquentielle (n_steps=4)
- Sélection sparse des features pertinentes
- Interprétabilité native via poids d'attention

### MLP
- Architecture : 10 → 128 → 64 → 32 → 16
- Activation GELU + BatchNorm + Dropout
- Capture les interactions non-linéaires complexes

---

## ✨ Fonctionnalités

| Module | Description |
|--------|-------------|
| 🔐 Authentification | Login/Register patients & admin (SQLite) |
| 🔬 Prédiction | Formulaire 10 facteurs → score risque TabNet-MLP |
| 👁️ Attention TabNet | Visualisation des poids d'attention par feature |
| 📊 Dashboard | Analytics Plotly : distribution, scatter, histogrammes |
| 📋 Historique | Stockage & export CSV de toutes les prédictions |
| 🧬 SHAP | Explication globale des contributions des features |
| 🔍 LIME | Interprétation locale pour chaque patient |
| 📄 Rapport PDF | Génération de rapports médicaux téléchargeables |

---

## 📊 Performances

| Métrique | Score |
|----------|-------|
| AUC-ROC | ~0.87 |
| Architecture | TabNet-4steps + MLP-128 |
| Features | 10 facteurs cliniques |
| Dataset | Stroke Prediction (Kaggle) / Synthétique |

---

## 📁 Structure

```
├── app.py                    # Application Streamlit principale
├── requirements.txt          # Dépendances Python
├── .streamlit/
│   └── config.toml          # Thème dark personnalisé
├── notebooks/
│   └── DeploiementAVC_TabNetMLP.ipynb  # Notebook Colab complet
└── assets/
    ├── training_curves.png   # Courbes d'entraînement
    └── evaluation_results.png # Résultats d'évaluation
```

---

## 🔑 Compte de Test

| Identifiant | Mot de passe | Rôle |
|-------------|--------------|------|
| `admin` | `admin123` | Administrateur |

---

## ⚕️ Avertissement Médical

> Ce système est un **outil d'aide à la décision** basé sur l'IA. Il **ne remplace pas** l'avis d'un professionnel de santé qualifié. Toute décision thérapeutique doit être prise en consultation avec un médecin neurologue.

---

*Centre Neurologique · Dauris · Bouchra · Amine · 2024*
