# CAHIER DES CHARGES FONCTIONNEL ET TECHNIQUE
## Application mobile de mobilité urbaine – Abidjan

**Version :** 1.0  
**Périmètre :** MVP – Première version  
**Plateformes :** Android en priorité, iOS prévu  
**Architecture :** Application mobile autonome, sans backend  
**Zone géographique :** District autonome d'Abidjan

---

# 1. Présentation du projet

## 1.1. Contexte

Se déplacer dans le District autonome d'Abidjan peut être difficile, particulièrement pour les personnes qui ne connaissent pas bien les lignes de transport, les points d'embarquement, les arrêts ou les correspondances.

Les informations sur les transports sont dispersées entre différents opérateurs, supports et habitudes locales. Un voyageur peut connaître sa destination sans savoir quel moyen de transport utiliser, où monter, où descendre ou comment poursuivre son trajet.

Le projet consiste à développer une application mobile qui facilite la compréhension et l'utilisation des transports publics à Abidjan.

## 1.2. Vision

Construire une plateforme numérique de référence permettant à toute personne de comprendre et de préparer ses déplacements dans le District autonome d'Abidjan.

L'application doit devenir un outil pratique d'orientation dans les transports urbains, en tenant compte des réalités locales.

## 1.3. Proposition de valeur

Permettre à un voyageur de savoir :

- Comment rejoindre une destination.
- Où prendre son transport.
- Quelle ligne ou quel moyen de transport emprunter.
- Où descendre.
- Où effectuer une correspondance.
- Combien d'étapes comporte son trajet.
- Quelles informations sont fiables ou restent à confirmer.

L'objectif n'est pas de reproduire une application de VTC ou de navigation généraliste. La priorité est la connaissance et l'organisation des transports publics locaux.

---

# 2. Objectifs du projet

## 2.1. Objectif général

Développer une application mobile permettant aux voyageurs de rechercher, comprendre et préparer leurs déplacements à travers les réseaux de transport disponibles dans le District autonome d'Abidjan.

## 2.2. Objectifs spécifiques

1. Centraliser les informations relatives aux transports publics ciblés.
2. Afficher les lignes et les points de transport sur une carte.
3. Permettre la recherche d'un lieu de départ et d'une destination.
4. Proposer des itinéraires multimodaux lorsque les données le permettent.
5. Présenter les déplacements sous forme d'étapes simples et compréhensibles.
6. Permettre l'enregistrement local des lieux et itinéraires favoris.
7. Permettre la mise à jour des données de transport par importation de fichiers.
8. Fournir une expérience utilisable sans connexion permanente à Internet, sous réserve des fonctionnalités nécessitant des ressources en ligne.

---

# 3. Périmètre fonctionnel du MVP

## 3.1. Utilisateur concerné

Le premier MVP est exclusivement destiné au **Voyageur**.

Le voyageur peut utiliser l'application pour rechercher des lieux, explorer les transports et préparer ses déplacements.

L'application doit être accessible sans création obligatoire de compte.

### Fonctionnement sans compte

- Consultation de la carte.
- Recherche de lieux.
- Exploration des lignes et des arrêts.
- Recherche d'itinéraires.
- Consultation des détails d'un trajet.
- Enregistrement de favoris sur le téléphone.
- Gestion des préférences locales.

La création de comptes en ligne, la synchronisation entre appareils et la gestion des utilisateurs sont reportées à une version ultérieure nécessitant une infrastructure distante.

## 3.2. Moyens de transport pris en charge

Le MVP prend en charge les catégories suivantes :

| Moyen de transport | Inclusion |
|---|---|
| Bus SOTRA | Oui |
| Bateaux-bus SOTRA | Oui |
| Bateaux-bus STL | Oui |
| Bateaux-bus CITRANS | Oui |
| Gbakas | Oui |
| Marche à pied | Oui, comme liaison entre deux étapes |

Les wôrô-wôrô et les taxis avec compteur ne font pas partie du périmètre du premier MVP.

## 3.3. Zone géographique

La zone cible est l'ensemble du District autonome d'Abidjan.

La couverture sera construite progressivement selon la disponibilité et la qualité des données.

L'application ne devra pas laisser croire qu'une zone est entièrement couverte lorsque seules certaines lignes ou certains arrêts ont été documentés.

---

# 4. Fonctionnalités de l'application

## 4.1. Accueil

L'écran d'accueil constitue le point d'entrée principal.

Il doit proposer :

- Un accès à la recherche d'itinéraire.
- Une carte permettant d'explorer les environs.
- Un accès aux lieux et itinéraires favoris.
- Des raccourcis vers les informations sur les transports.
- Un accès aux paramètres.

La recherche de destination doit être immédiatement visible.

## 4.2. Carte interactive

La carte est un élément central de l'application.

Elle doit permettre de :

- Visualiser les zones géographiques couvertes.
- Afficher les arrêts et points d'embarquement connus.
- Afficher les stations et terminaux lagunaires.
- Visualiser les lignes disponibles.
- Consulter les informations d'un point en le sélectionnant.
- Explorer les transports à proximité.
- Afficher un itinéraire sélectionné.

La carte doit pouvoir être déplacée, agrandie et réduite.

Les informations affichées doivent être adaptées à l'échelle de la carte afin d'éviter une surcharge visuelle.

**Important :** le fond cartographique et les données de transport constituent deux sources distinctes. L'utilisation d'une carte OpenStreetMap ne fournit pas automatiquement les lignes et arrêts des opérateurs.

## 4.3. Recherche de lieux

Le voyageur doit pouvoir rechercher :

- Un quartier.
- Une commune.
- Un lieu public.
- Un établissement ou un point d'intérêt.
- Un arrêt ou une station.
- Un terminal lagunaire.

La recherche doit proposer des suggestions pertinentes et permettre de sélectionner un résultat comme point de départ ou destination.

La possibilité de sélectionner directement un point sur la carte doit également être étudiée.

## 4.4. Recherche d'itinéraire

Le voyageur doit pouvoir renseigner :

- Son point de départ.
- Sa destination.

Le point de départ pourra être sa position actuelle si l'autorisation de localisation est accordée.

L'application devra calculer les itinéraires à partir des données locales disponibles.

Elle devra prendre en compte :

- Les lignes de bus.
- Les lignes de bateaux-bus.
- Les lignes de gbakas.
- Les correspondances entre les moyens de transport.
- Les segments de marche nécessaires.

### Présentation des résultats

Lorsque les données sont suffisamment fiables, l'application pourra proposer plusieurs itinéraires selon des critères tels que :

- Temps estimé du déplacement.
- Nombre de correspondances.
- Distance à parcourir à pied.

Ces critères ne doivent pas donner lieu à des comparaisons trompeuses lorsque les données sont insuffisantes.

## 4.5. Détails d'un itinéraire

Chaque itinéraire doit être présenté de manière compréhensible.

Exemple de structure :

**Étape 1 – Rejoindre le point d'embarquement**
- Marcher jusqu'au point de départ.
- Afficher la distance lorsque celle-ci est disponible.

**Étape 2 – Prendre un transport**
- Nom ou numéro de la ligne.
- Opérateur.
- Direction ou terminus.
- Point d'embarquement.
- Point de descente.

**Étape 3 – Effectuer une correspondance**
- Expliquer où descendre.
- Indiquer le prochain point d'embarquement.
- Présenter le moyen de transport suivant.

**Étape 4 – Rejoindre la destination**
- Afficher le dernier segment à pied lorsque nécessaire.

La carte doit accompagner les instructions afin que le voyageur puisse comprendre son déplacement.

Les estimations de durée, de distance et de coût ne seront affichées que lorsque les données disponibles permettent de les calculer de manière raisonnable.

## 4.6. Informations sur les lignes

Chaque ligne doit disposer d'une fiche contenant, selon les informations disponibles :

- Nom ou numéro de ligne.
- Opérateur.
- Moyen de transport.
- Point de départ.
- Terminus.
- Liste des arrêts.
- Parcours géographique.
- Direction.
- Informations complémentaires.
- Source des données.
- Date de dernière vérification.
- Niveau de fiabilité.

## 4.7. Informations sur les arrêts et stations

Chaque point de transport peut présenter :

- Nom du point.
- Type de point.
- Coordonnées géographiques.
- Lignes qui le desservent.
- Opérateur concerné.
- Informations pratiques.
- Source et date de vérification.

Les points d'embarquement doivent être représentés aussi précisément que possible.

## 4.8. Favoris

Le voyageur peut enregistrer :

- Des lieux.
- Des points de transport.
- Des itinéraires.

Les favoris sont enregistrés localement sur l'appareil.

Ils doivent rester disponibles après fermeture et réouverture de l'application.

## 4.9. Paramètres

L'écran des paramètres doit permettre :

- De consulter les informations de l'application.
- De gérer les préférences.
- De consulter la version des données installées.
- D'importer un fichier de mise à jour.
- De consulter l'état de validation du dernier fichier importé.
- De gérer les données locales de l'application.

## 4.10. Mise à jour des données par fichiers

Cette fonctionnalité est une exigence importante du MVP.

L'application doit pouvoir recevoir de nouvelles données de transport sans nécessiter la publication d'une nouvelle version de l'application.

Le processus d'importation doit comprendre :

1. Sélection du fichier sur le téléphone.
2. Vérification du format.
3. Vérification de la version et de la compatibilité.
4. Vérification de l'intégrité des données.
5. Contrôle des références entre les lignes, arrêts et autres éléments.
6. Présentation du résultat de validation.
7. Confirmation de l'importation.
8. Remplacement des données précédentes uniquement si l'importation est valide.

En cas d'échec, les données précédentes doivent rester intactes.

L'application doit permettre de connaître la version des données actuellement installées.

---

# 5. Architecture technique

## 5.1. Principe général

Le premier MVP sera une application mobile autonome.

Il ne nécessitera pas de backend applicatif distant.

L'architecture sera organisée autour de trois éléments :

1. L'application mobile.
2. Le moteur local de recherche et de calcul d'itinéraires.
3. Le stockage local des données et préférences.

## 5.2. Technologies envisagées

| Composant | Technologie envisagée |
|---|---|
| Application mobile | React Native |
| Environnement de développement | Expo |
| Langage | TypeScript |
| Cartographie | MapLibre ou solution cartographique compatible |
| Fond cartographique | OpenStreetMap ou fournisseur compatible |
| Stockage local structuré | SQLite |
| Préférences simples | Stockage local adapté |
| Données d'échange | Fichiers versionnés, notamment JSON ou GTFS selon le besoin |
| Calcul d'itinéraires | Moteur local développé pour le projet |

Ces choix constituent la base technique proposée. Ils pourront être ajustés après les tests de faisabilité.

## 5.3. Organisation logique

### Module mobile
Responsable de l'interface, de la navigation, de la carte et des interactions.

### Module cartographique
Responsable de l'affichage des fonds cartographiques, des lignes, des arrêts et des itinéraires.

### Moteur local
Responsable de la recherche, de la sélection des lignes, des correspondances et de la construction des itinéraires.

### Module de données
Responsable de la lecture, de la validation, de l'importation et de la gestion des versions des fichiers de transport.

### Stockage local
Responsable de la conservation des données structurées, des favoris et des préférences.

## 5.4. Absence de backend

Le MVP ne comprend pas :

- API métier distante.
- Serveur applicatif.
- Base de données distante.
- Authentification en ligne.
- Gestion de comptes utilisateurs.
- Synchronisation entre appareils.
- Tableau de bord administrateur connecté.
- Interface de gestion des agents.
- Système distant de validation des données.

Ces fonctionnalités pourront être introduites dans une version ultérieure.

---

# 6. Organisation des données

## 6.1. Catégories de données

Le référentiel local devra organiser les informations suivantes :

- Opérateurs.
- Moyens de transport.
- Lignes.
- Parcours et variantes de parcours.
- Arrêts.
- Stations.
- Terminaux lagunaires.
- Ordre des arrêts sur les lignes.
- Informations tarifaires vérifiées.
- Sources des informations.
- Dates de collecte et de vérification.

## 6.2. Format des données

Le système devra utiliser des fichiers structurés et versionnés.

Le format exact sera défini lors de la conception du modèle de données.

Le format GTFS pourra être utilisé lorsqu'il est adapté aux informations disponibles. Des fichiers JSON complémentaires pourront servir aux données spécifiques qui ne sont pas suffisamment représentées dans GTFS.

## 6.3. Traçabilité

Chaque information importante doit pouvoir être associée à :

- Une source.
- Une date de collecte.
- Une date de dernière vérification.
- Un statut de validation.
- Un niveau de confiance lorsque cela est pertinent.

## 6.4. Qualité des données

L'application ne doit jamais présenter une information incertaine comme une vérité confirmée.

Les statuts possibles pourront être :

- Vérifiée.
- À confirmer.
- Ancienne ou potentiellement obsolète.
- Indisponible.

Une donnée absente ne signifie pas nécessairement qu'un transport n'existe pas.

## 6.5. Tarification

Les tarifs ne seront intégrés que lorsqu'ils sont issus de sources identifiables et suffisamment récentes.

Chaque tarif devra être associé à sa source et à sa date de vérification.

Aucun prix ne devra être inventé ou déduit sans justification.

---

# 7. Expérience utilisateur et exigences d'interface

L'application doit être conçue prioritairement pour les smartphones.

Les principes suivants sont retenus :

- Interface simple et moderne.
- Navigation intuitive.
- Recherche accessible rapidement.
- Carte facile à manipuler.
- Instructions de trajet compréhensibles.
- Affichage adapté aux petits écrans.
- Textes courts et utiles.
- Distinction visuelle claire entre les moyens de transport.
- Gestion des états de chargement, d'erreur et d'absence de données.

L'application doit éviter de surcharger l'utilisateur avec des informations techniques.

Le voyageur doit pouvoir comprendre son itinéraire sans connaissances préalables du réseau de transport.

---

# 8. Exigences non fonctionnelles

## 8.1. Performance

- L'ouverture des principaux écrans doit être fluide.
- Les recherches locales doivent être rapides.
- La carte doit rester utilisable sur des appareils Android modestes.
- Les opérations d'importation doivent éviter de bloquer inutilement l'interface.

## 8.2. Fonctionnement hors connexion

Les données de transport installées localement doivent rester consultables sans connexion Internet.

Le calcul d'itinéraires doit fonctionner à partir des données locales.

Certaines fonctions pourront nécessiter Internet, notamment le téléchargement de fonds cartographiques non mis en cache ou l'obtention de ressources externes.

L'application devra informer l'utilisateur lorsque ces ressources ne sont pas disponibles.

## 8.3. Sécurité et intégrité

- Valider les fichiers avant leur importation.
- Rejeter les fichiers incompatibles ou malformés.
- Protéger les données précédentes en cas d'échec.
- Éviter l'exécution de contenu fourni dans les fichiers.
- Vérifier les références et la cohérence des données.
- Ne pas exposer inutilement les informations personnelles de localisation.

## 8.4. Compatibilité

Android est la plateforme prioritaire du MVP.

L'architecture devra néanmoins faciliter une future publication sur iOS.

---

# 9. Éléments exclus du premier MVP

Afin de conserver un périmètre maîtrisable, les éléments suivants ne seront pas développés dans cette première version :

- Comptes voyageurs en ligne.
- Connexion Google, Apple ou par SMS.
- Synchronisation des favoris entre appareils.
- Backend et API métier.
- Interface d'administration.
- Comptes administrateurs.
- Comptes d'agents de vérification.
- Gestion centralisée des données.
- Signalements communautaires avec modération distante.
- Données de circulation en temps réel.
- Horaires en temps réel.
- Suivi GPS en temps réel des véhicules.
- Réservation ou paiement de transport.
- Wôrô-wôrô.
- Taxis avec compteur.

Ces éléments pourront faire l'objet de versions ultérieures après validation du MVP.

---

# 10. Critères d'acceptation du MVP

Le MVP sera considéré comme fonctionnel lorsque les conditions suivantes seront satisfaites :

1. Le voyageur peut ouvrir et utiliser l'application sans créer de compte.
2. Il peut consulter une carte et explorer les données disponibles.
3. Il peut rechercher un lieu et sélectionner un point de départ et une destination.
4. Le moteur local peut calculer un itinéraire lorsque les données nécessaires existent.
5. Le résultat présente clairement les étapes du déplacement.
6. Les correspondances sont compréhensibles.
7. Les favoris sont conservés localement.
8. L'application peut importer un fichier de données compatible.
9. Un fichier invalide est rejeté sans détruire les données précédentes.
10. La version des données installées est consultable.
11. Les informations incertaines ou anciennes sont identifiables.
12. Les fonctions principales restent accessibles hors connexion avec les ressources locales disponibles.

La couverture géographique et le nombre de lignes ne seront pas considérés comme validés simplement parce que des données ont été importées. Ils devront faire l'objet d'un contrôle de qualité distinct.

---

# 11. Plan de réalisation

## Phase 1 – Conception fonctionnelle
- Définir le parcours complet du voyageur.
- Définir les écrans.
- Définir les interactions.
- Concevoir les maquettes mobiles.
- Valider la navigation générale.

## Phase 2 – Préparation des données
- Identifier les sources disponibles.
- Vérifier les conditions d'utilisation et licences.
- Collecter les données exploitables.
- Définir le modèle de données local.
- Concevoir le format des fichiers.
- Tester la cohérence des données.

## Phase 3 – Développement de l'application
- Initialiser le projet React Native et Expo.
- Construire la navigation.
- Développer l'accueil.
- Intégrer la carte.
- Développer la recherche de lieux.
- Développer les fiches de lignes et d'arrêts.
- Développer les favoris.

## Phase 4 – Moteur local d'itinéraires
- Modéliser les réseaux.
- Développer la recherche de parcours.
- Gérer les correspondances.
- Intégrer les segments de marche.
- Présenter les instructions étape par étape.
- Tester les résultats avec des trajets réels.

## Phase 5 – Gestion des données locales
- Développer l'importation de fichiers.
- Développer la validation.
- Gérer les versions.
- Prévoir la restauration en cas d'échec.
- Tester les mises à jour.

## Phase 6 – Tests et validation
- Tester sur plusieurs appareils Android.
- Tester les parcours disponibles.
- Vérifier les données sur le terrain.
- Tester le fonctionnement hors connexion.
- Tester les fichiers valides et invalides.
- Corriger les problèmes d'ergonomie et de performance.

## Phase 7 – Publication du MVP
- Préparer la version Android.
- Constituer un premier périmètre de couverture fiable.
- Faire tester l'application par des voyageurs.
- Recueillir les retours.
- Préparer les améliorations de la version suivante.

---

# 12. Évolutions futures

Après validation du premier MVP, le projet pourra évoluer vers une plateforme plus complète.

Les évolutions envisagées comprennent :

- Backend centralisé.
- Comptes voyageurs facultatifs.
- Connexion Google, Apple ou téléphone.
- Synchronisation des favoris.
- Espace d'administration.
- Gestion des opérateurs et des lignes.
- Gestion des agents de collecte et de vérification.
- Signalements des voyageurs.
- Processus de validation des signalements.
- Actualisation centralisée des données.
- Données de transport en temps réel lorsque les opérateurs les rendent disponibles.
- Extension progressive des fonctionnalités et de la couverture géographique.

Ces évolutions ne doivent pas retarder la livraison du premier MVP.

---

# 13. Résultat attendu

À la fin du premier MVP, nous devons disposer d'une application mobile utilisable par un voyageur qui ne connaît pas nécessairement Abidjan.

Ce voyageur doit pouvoir :

- Explorer les transports disponibles.
- Rechercher une destination.
- Comprendre comment s'y rendre.
- Identifier les lignes et les points d'embarquement.
- Effectuer les correspondances nécessaires.
- Suivre les différentes étapes de son déplacement.
- Conserver ses lieux et itinéraires favoris.
- Utiliser les données installées sans dépendre d'un backend.

**La priorité est de livrer une expérience de déplacement réellement utile, fondée sur des données locales suffisamment fiables, avant de construire une infrastructure plus complexe.**
