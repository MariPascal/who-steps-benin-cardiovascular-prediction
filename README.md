# Risques cardiovasculaires et AVC au Bénin — Machine Learning sur WHO STEPS 2015

## 1. Contexte de l'étude
Les maladies non transmissibles (MNT), en particulier les accidents vasculaires cérébraux (AVC),
représentent un défi croissant de santé publique dans les pays en développement. L'hypertension
artérielle et les facteurs métaboliques associés comptent parmi les principaux facteurs de risque
de ces pathologies.

Ce projet de Machine Learning analyse des données de santé pour estimer, à partir de
caractéristiques sociodémographiques, comportementales et cliniques, la probabilité qu'un individu
appartienne au groupe des personnes déclarant un antécédent cardiovasculaire (crise cardiaque,
angine de poitrine ou AVC).

## 2. À propos du jeu de données
Le projet s'appuie sur l'enquête nationale **WHO STEPS 2015** réalisée au Bénin par le Ministère de
la Santé avec l'appui de l'Organisation mondiale de la Santé (OMS), auprès d'un échantillon
représentatif de la population adulte (5 126 participants de 18 à 69 ans). Le fichier compte
**235 variables** et couvre les trois volets de l'approche STEPS :
* **STEPS 1 :** données comportementales et sociodémographiques par questionnaire (tabagisme, alcool, alimentation, activité physique).
* **STEPS 2 :** mesures physiques (poids, taille, tour de taille, pression artérielle).
* **STEPS 3 :** mesures biochimiques sur prélèvement sanguin (glycémie à jeun, cholestérol).

### Variable cible
`h17` : « Avez-vous déjà eu une crise cardiaque ou une douleur à la poitrine due à une maladie
cardiaque (angine de poitrine) ou un accident vasculaire cérébral ? » (1 = Oui, 2 = Non).
Il s'agit d'un antécédent cardiovasculaire **déclaré**, et non d'un AVC isolé.

## 3. Blocs de variables
* **Démographie et profil de base** (`pid`, `sex`, `age`, `agerange`, `c4`–`c11`) : facteurs non modifiables et statut socio-économique.
* **Facteurs comportementaux** (`t`/`tp`, `a`, `d`, `p`) : tabac, alcool, alimentation, activité physique.
* **Antécédents médicaux** (`h`) : hypertension, diabète, antécédents cardiovasculaires. `h17` est la cible ; `h18` et `h19` (aspirine, statines) sont des conséquences de la maladie et ne doivent pas servir de variables explicatives.
* **Mesures physiques** (`m`) : IMC, tension artérielle (systolique, diastolique), tour de taille.
* **Analyses biochimiques** (`b`) : glycémie, cholestérol.
* **Paramètres d'enquête** (`wstep1`–`wstep3`, `psu`, `stratum`) : poids statistiques et strates du plan de sondage.
* Autres blocs présents dans le fichier (`cx`, `o`) : Non identifiés dans l'instrument (`docs/enquete/`).

## 4. Données non incluses dans ce dépôt
Le fichier `ben2015.csv` **n'est pas publié ici**. Il est accessible sous conditions d'accès du dépôt
NCD Microdata de l'OMS, et sa redistribution n'est pas confirmée : il est donc exclu du dépôt
(`.gitignore`). Le reste du projet est reproductible une fois le fichier obtenu.

**Pour reproduire :**
1. Ouvrir la page du jeu de données *BEN_2015_STEPS_v01* du dépôt NCD Microdata de l'OMS.
2. Demander l'accès (« Get Microdata ») et accepter les conditions d'utilisation.
3. Télécharger le fichier de données et le placer dans `data/raw/ben2015.csv`.

**Citation :** This paper uses data from the Benin 2015 STEPS survey, implemented by the Ministry of
Health with the support of the World Health Organization.

## 5. Structure
| Dossier | Contenu |
|---|---|
| `data/raw/` | Fichier d'origine `ben2015.csv` (local, non versionné) |
| `data/processed/` | Données nettoyées générées par les notebooks (non versionnées) |
| `data/dictionary/` | Résumé des variables |
| `docs/enquete/` | Rapport, factsheet et instruments de l'enquête |
| `notebooks/` | Exploration, nettoyage, modélisation |
| `src/` | Fonctions réutilisables |
| `reports/figures/` | Graphiques exportés |

## 6. Démarrage
```bash
python -m venv .venv
source .venv/bin/activate      # Windows : .venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook
```

## 7. Limites
Enquête transversale : le modèle estime une association avec un antécédent déclaré, il ne prédit
pas un AVC futur et ne constitue pas un outil de diagnostic médical.
