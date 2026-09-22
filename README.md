# Cadencier

Mod de liaison entre **Courseplay** et **AutoDrive** pour Farming Simulator 25 : il enchaîne automatiquement les travaux de champ (broyage, semis, herbicide, engrais, plombage, etc.) en orchestrant les véhicules et les outils de la ferme.

Courseplay sait exécuter une course de travail sur un champ, AutoDrive sait faire circuler un véhicule d'un point à un autre — mais aucun des deux ne sait enchaîner plusieurs courses sur un même champ, ni arbitrer entre plusieurs champs qui se disputent les mêmes véhicules et outils. Cadencier ajoute cette couche d'orchestration au-dessus des deux, sans les remplacer.

## Fonctionnalités

- Gestion simultanée de **tous les champs possédés par le joueur**, chacun avec sa propre séquence de courses et son propre ordre de priorité.
- Séquences de courses **configurables et réordonnables**, enchaînement automatique dès qu'une course se termine.
- **Sélection automatique du véhicule** pour chaque course, selon sa puissance, sa disponibilité, sa proximité de l'outil et son état d'usure.
- **Pool d'outils partagé** entre tous les champs : chaque outil retourne automatiquement à un point de stockage dédié après usage, attelage/dételage entièrement automatisés.
- **HUD dédié** : configuration des séquences et cadre de supervision listant les champs en attente ou en erreur.
- Résolution automatique des incidents courants (ex. ravitaillement en carburant) quand c'est possible, sinon mise en pause du champ concerné avec motif affiché.
- Compatible avec **toutes les cartes** (aucune configuration de ferme codée en dur).

## Prérequis

- Farming Simulator 25
- [Courseplay_FS25](https://github.com/Courseplay/Courseplay_FS25)
- [FS25_AutoDrive](https://github.com/Stephan-S/FS25_AutoDrive)

Cadencier ne génère pas de trajets : il orchestre des courses Courseplay et des trajets AutoDrive déjà enregistrés par le joueur.

## Installation

*(à compléter une fois le mod packagé — procédure standard FS25 : copier le `.zip` dans le dossier `mods` du jeu, activer les trois mods dans le menu des mods)*

## Utilisation rapide

1. Enregistrer les courses souhaitées dans Courseplay et les trajets dans AutoDrive, comme d'habitude.
2. Définir un point de stockage pour chaque outil de la ferme.
3. Dans l'onglet Cadencier, construire la séquence de courses de chaque champ (outil + course associée) et fixer l'ordre de priorité entre champs.
4. Laisser tourner : Cadencier attelle, exécute, dételle et range automatiquement.

## Architecture

- **Orchestrateur** — état et séquence de chaque champ.
- **Moteur de sélection véhicule** — algorithme puissance/distance/usure.
- **Gestionnaire de pool d'outils** — verrouillage, points de stockage.
- **Adaptateurs Courseplay / AutoDrive** — seule couche qui appelle directement les API des deux mods.
- **Module de supervision** — détection d'incidents, alimentation du HUD.

Le détail complet des spécifications (algorithmes, cas d'erreur, plan de tests) est dans le cahier des charges du projet.

## Limites connues (V1)

- Usage **solo uniquement** — pas de synchronisation multijoueur pour l'instant.
- Pas de génération de trajet : les courses/trajets doivent déjà exister dans Courseplay/AutoDrive.
- Dépend des API de Courseplay_FS25 et FS25_AutoDrive, tous deux en développement actif (bêta).

## Feuille de route

- Support multijoueur
- Génération automatique de trajets
- Gestion avancée de la maintenance préventive

## Contribuer

Les issues et pull requests sont les bienvenues. Merci de vérifier la licence de Courseplay_FS25 et FS25_AutoDrive avant toute reprise de code depuis ces projets.

## Licence

À définir.

## Remerciements

- L'équipe [Courseplay](https://github.com/Courseplay/Courseplay_FS25)
- [Stephan-S](https://github.com/Stephan-S/FS25_AutoDrive) pour AutoDrive
