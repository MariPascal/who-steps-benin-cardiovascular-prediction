# Données — Enquête STEPS Bénin 2015

## Source
Enquête STEPS (approche par étapes de l'OMS pour la surveillance des facteurs de risque
des maladies non transmissibles), Bénin, 2015. Données obtenues via le dépôt
NCD Microdata de l'OMS.

**Mention de citation à conserver :**
> This paper uses data from the Benin 2015 STEPS survey, implemented by [organisme d'exécution]
> with the support of the World Health Organization.

## Fichier
- `raw/ben2015.csv` : 5 126 participants (18-69 ans), 235 variables, identifiant `pid`.
  Fichier d'origine, **ne jamais le modifier** : tout nettoyage va dans `processed/`.

## Variable cible envisagée
`h17` — question H17 de l'instrument : « Avez-vous déjà eu une crise cardiaque ou une douleur à la
poitrine due à une maladie cardiaque (angine de poitrine) ou un accident vasculaire cérébral ? »
Codage d'origine : 1 = Oui, 2 = Non. Il s'agit d'un antécédent cardiovasculaire **déclaré**,
pas d'un AVC isolé.

## Dictionnaire
`dictionary/variables_resume.csv` : type, valeurs valides/manquantes et nombre de modalités par
variable. La signification de chaque code se lit dans l'instrument (`../docs/enquete/`).

## Conditions d'accès (OMS, BEN_2015_STEPS_v01)
L'utilisateur s'engage :
1. à citer la source des données ;
2. à communiquer à l'OMS toute publication prévue, avant sa publication ;
3. à proposer la co-signature de tout rapport ou publication utilisant les résultats de l'enquête au
   coordonnateur de l'enquête ;
4. à n'utiliser les données qu'à des fins de santé publique, non commerciales et à but non lucratif.

Contacts : équipe STEPS de l'OMS (Steps@who.int) et coordonnateur pays STEPS, indiqué dans
`../docs/enquete/rapport_steps_benin_2015.pdf`.

## Statut de publication (à tenir à jour)
- [ ] Projet présenté à l'OMS et au coordonnateur de l'enquête (conditions 2 et 3)
- [ ] Réponse reçue sur le statut du dépôt public et de l'application
- Tant que ces cases ne sont pas cochées, garder le dépôt **privé**.

Le fichier brut `raw/ben2015.csv` n'est pas versionné (`.gitignore`) : chaque utilisateur doit le
télécharger lui-même via « Get Microdata » sur la page du jeu de données.
