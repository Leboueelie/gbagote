# DOCUMENT FONDATEUR DU PRODUIT
## Plateforme de connaissance et d'orientation de la mobilité publique du District autonome d'Abidjan

**Version :** 1.0  
**Statut :** Document de cadrage initial  
**Zone géographique :** District autonome d'Abidjan  
**Nom du produit :** À définir

---

# 1. Vision du produit

Construire une plateforme numérique de référence permettant à toute personne de comprendre, explorer et utiliser les transports publics du District autonome d'Abidjan.

Notre ambition dépasse la simple création d'une application de navigation.

Nous voulons rendre la mobilité urbaine plus compréhensible, plus accessible et plus prévisible grâce à une connaissance structurée des réseaux de transport, des itinéraires, des points d'embarquement, des correspondances et des informations pratiques.

À terme, la plateforme doit devenir une infrastructure numérique de connaissance de la mobilité urbaine, capable de représenter le fonctionnement réel des transports et d'accompagner les déplacements quotidiens de la population.

# 2. Le problème que nous voulons résoudre

Se déplacer à Abidjan peut être compliqué, particulièrement pour les personnes qui ne connaissent pas bien la ville.

Plusieurs difficultés se présentent :

- Il est difficile de connaître tous les moyens de transport disponibles pour rejoindre une destination.
- Les informations sur les lignes et leurs itinéraires sont dispersées.
- Les points d'embarquement et de débarquement ne sont pas toujours faciles à identifier.
- Les correspondances entre différents moyens de transport sont parfois difficiles à comprendre.
- Les tarifs et les conditions de déplacement ne sont pas toujours accessibles ou vérifiables.
- Les personnes nouvellement arrivées à Abidjan peuvent avoir du mal à se repérer dans le réseau de transport.

Le problème n'est donc pas uniquement de trouver un chemin entre deux endroits.

**Le véritable problème est le manque d'une représentation accessible, structurée et suffisamment fiable du fonctionnement des transports publics à Abidjan.**

# 3. Notre proposition de valeur

Nous voulons permettre à chacun de répondre facilement à trois questions :

1. Quels moyens de transport puis-je utiliser pour rejoindre ma destination ?
2. Où dois-je monter, descendre et effectuer mes correspondances ?
3. Quelles informations dois-je connaître avant et pendant mon déplacement ?

Notre proposition de valeur :

**Comprendre les transports d'Abidjan, trouver les possibilités de déplacement et être guidé tout au long de son trajet grâce à une plateforme construite autour des réalités locales.**

La plateforme ne doit pas simplement afficher une ligne sur une carte. Elle doit expliquer concrètement comment utiliser cette ligne.

# 4. Les utilisateurs cibles

La plateforme s'adresse à plusieurs catégories d'utilisateurs.

### 4.1. Les habitants d'Abidjan

Des personnes qui utilisent quotidiennement les transports publics et souhaitent découvrir de nouveaux itinéraires, comparer les possibilités de déplacement ou gagner du temps.

### 4.2. Les nouveaux habitants

Des personnes qui viennent de s'installer à Abidjan et ne maîtrisent pas encore le fonctionnement des transports.

### 4.3. Les étudiants et travailleurs

Des personnes qui effectuent régulièrement les mêmes déplacements et cherchent à mieux organiser leurs trajets.

### 4.4. Les visiteurs

Des personnes qui découvrent Abidjan et ont besoin d'informations compréhensibles pour se déplacer sans dépendre systématiquement de l'aide d'autrui.

### 4.5. Les acteurs de la mobilité

À terme, les opérateurs, institutions, chercheurs et organisations intéressés par la connaissance des réseaux de transport pourront également exploiter certaines données de la plateforme, selon les droits d'accès et les licences applicables.

# 5. Le périmètre géographique et opérationnel

Dès sa conception, le produit vise l'ensemble du District autonome d'Abidjan.

Il ne sera pas pensé comme une application limitée à une seule commune ou à un seul quartier.

### 5.1. Modes de transport du MVP

Le premier périmètre opérationnel comprend :

| Mode | Réseau concerné |
|---|---|
| Bus | SOTRA |
| Bateaux-bus | SOTRA, STL et CITRANS |
| Transport collectif informel | Gbakas |
| Déplacement complémentaire | Marche à pied |

Les wôrô-wôrô et les taxis compteurs ne font pas partie du MVP.

### 5.2. Principe d'évolution géographique

Le produit est conçu pour couvrir tout le District, mais la qualité des données sera construite progressivement.

Une zone ne sera pas considérée comme correctement couverte simplement parce qu'elle apparaît sur la carte. La couverture devra être mesurée selon la disponibilité, la qualité et le niveau de vérification des informations.

# 6. Les grandes composantes du produit

Le produit repose sur trois composantes fondamentales.

## 6.1. La carte de mobilité

Une carte interactive permettant d'explorer les infrastructures et les réseaux de transport.

Elle doit notamment afficher :

- Les gares et stations.
- Les arrêts de bus.
- Les embarcadères.
- Les lignes et leurs tracés.
- Les directions et destinations des lignes.
- Les zones desservies.
- Les points de correspondance.

La carte constitue la représentation géographique du réseau de mobilité.

## 6.2. Le moteur d'orientation et d'itinéraires

Un utilisateur doit pouvoir renseigner son point de départ et sa destination.

La plateforme doit ensuite rechercher les possibilités de déplacement en combinant les moyens de transport disponibles.

Les résultats pourront proposer plusieurs variantes :

- Le trajet le plus rapide, lorsque les données permettent de l'estimer.
- Le trajet avec le moins de correspondances.
- Le trajet avec le moins de changements de mode.
- D'autres variantes pertinentes selon les données disponibles.

Chaque proposition doit expliquer les étapes du déplacement :

1. Le point de départ.
2. Le lieu où prendre le premier transport.
3. La ligne ou le moyen de transport à emprunter.
4. Le point de descente.
5. La correspondance éventuelle.
6. Le transport suivant.
7. Le chemin à parcourir à pied jusqu'à la destination.

L'objectif est qu'une personne qui ne connaît pas Abidjan puisse comprendre son trajet sans devoir demander son chemin à plusieurs personnes.

## 6.3. Le référentiel de données de mobilité

Cette composante est le socle stratégique du produit.

Elle centralise et structure les informations relatives :

- Aux opérateurs.
- Aux moyens de transport.
- Aux lignes.
- Aux arrêts et stations.
- Aux itinéraires et variantes de parcours.
- Aux correspondances.
- Aux tarifs disponibles.
- Aux sources des données.
- Aux vérifications effectuées.

Chaque information importante doit pouvoir être associée à une source et à un état de fiabilité.

Le référentiel doit conserver l'historique des modifications afin de suivre l'évolution des réseaux.

# 7. Notre différenciation

Nous ne cherchons pas à reproduire Yango, Google Maps ou une autre application de navigation.

Nous cherchons à résoudre un problème local avec une connaissance approfondie de la mobilité abidjanaise.

Notre différenciation repose sur cinq principes.

### 7.1. Une connaissance locale

La plateforme doit représenter les réalités des transports d'Abidjan, notamment les réseaux formels, les gbakas et les déplacements lagunaires.

### 7.2. Une orientation compréhensible

Nous ne voulons pas seulement afficher des itinéraires. Nous voulons expliquer les déplacements et les correspondances de manière concrète.

### 7.3. Une approche multimodale

Un déplacement peut nécessiter plusieurs moyens de transport. La plateforme doit être capable de les combiner intelligemment.

### 7.4. La transparence des informations

Une information incertaine ne doit jamais être présentée comme une certitude.

Les données doivent pouvoir être distinguées selon leur niveau de confiance :

- Information officielle.
- Information vérifiée sur le terrain.
- Information issue d'une source secondaire.
- Information à confirmer.

Les tarifs doivent être accompagnés de leur source et de leur date de vérification. Aucun prix ne doit être inventé.

Les horaires exacts et les informations en temps réel ne seront affichés que lorsqu'une source fiable permet de les justifier.

### 7.5. Une plateforme qui s'améliore avec la ville

La plateforme doit pouvoir recevoir des signalements et intégrer de nouvelles observations.

Par exemple :

- Un arrêt a été déplacé.
- Une ligne a changé de parcours.
- Un embarcadère n'est plus accessible.
- Une correspondance indiquée est incorrecte.
- Une information tarifaire doit être actualisée.

Les signalements ne deviennent pas automatiquement des données officielles : ils doivent être examinés et vérifiés avant publication.

# 8. Le périmètre du MVP

Le MVP doit démontrer que notre proposition de valeur fonctionne réellement.

Il ne s'agit pas de construire immédiatement toutes les fonctionnalités imaginables.

### Fonctionnalités indispensables

**A. Exploration**
- Afficher une carte du District autonome d'Abidjan.
- Afficher les lignes, arrêts, gares et embarcadères disponibles.
- Consulter les informations relatives à une ligne.
- Consulter les informations relatives à un arrêt.

**B. Recherche**
- Rechercher un lieu ou une destination.
- Définir un point de départ et une destination.
- Obtenir des itinéraires utilisant les données disponibles.

**C. Orientation**
- Afficher les étapes détaillées du déplacement.
- Identifier les lieux d'embarquement et de débarquement.
- Afficher les correspondances.
- Combiner bus, gbaka, bateaux-bus et marche lorsque les données le permettent.

**D. Fiabilité**
- Afficher la provenance des informations.
- Indiquer les informations non vérifiées.
- Gérer les tarifs uniquement lorsqu'ils sont suffisamment fiables.
- Permettre la correction des données depuis un espace d'administration.

**E. Administration**
- Ajouter et modifier les lignes.
- Gérer les arrêts et les gares.
- Gérer les opérateurs.
- Contrôler les sources.
- Valider les modifications et conserver leur historique.

### Fonctionnalités non prioritaires au lancement

- Suivi GPS en temps réel des véhicules.
- Prédiction précise des heures d'arrivée.
- Paiement des titres de transport.
- Réservation de transport.
- Réseau social entre voyageurs.
- Intelligence artificielle conversationnelle complexe.

Ces possibilités ne seront étudiées que lorsqu'elles répondront à un besoin réel et que les données ou partenariats nécessaires seront disponibles.

# 9. Nos principes de conception

Les décisions de conception et de développement devront respecter les principes suivants :

1. **L'utilité avant l'accumulation de fonctionnalités.** Chaque fonctionnalité doit résoudre un problème identifié.
2. **La fiabilité avant la quantité.** Mieux vaut une information limitée mais vérifiée qu'une carte remplie de données erronées.
3. **Le terrain avant les suppositions.** Les données numériques doivent être confrontées aux réalités de la ville.
4. **La simplicité pour l'utilisateur.** Le fonctionnement interne peut être complexe, mais l'expérience doit rester compréhensible.
5. **La traçabilité.** Toute donnée importante doit avoir une provenance identifiable.
6. **L'évolutivité.** Le système doit pouvoir intégrer de nouvelles données, zones et fonctionnalités sans devoir être reconstruit.
7. **L'indépendance stratégique.** Le produit doit construire et maîtriser son propre référentiel de données, dans le respect des licences et des droits des fournisseurs.

# 10. Notre stratégie de développement

Nous adopterons une construction progressive en cinq phases.

### Phase 1 — Connaissance des données

- Identifier les jeux de données disponibles.
- Récupérer les données géographiques et de transport.
- Étudier les licences.
- Auditer les lignes, arrêts et tracés.
- Identifier les données obsolètes ou incomplètes.

### Phase 2 — Construction du référentiel

- Définir le modèle de données.
- Construire la base géographique.
- Intégrer les réseaux disponibles.
- Mettre en place la provenance et l'historique.
- Développer les outils d'administration.

### Phase 3 — Cartographie

- Afficher les réseaux de transport.
- Permettre l'exploration des lignes et des arrêts.
- Contrôler la cohérence géographique.
- Améliorer progressivement la couverture du District.

### Phase 4 — Calcul d'itinéraires

- Développer ou intégrer un moteur de calcul adapté.
- Combiner les différents modes.
- Gérer les correspondances.
- Fournir des instructions de déplacement.
- Évaluer la pertinence des résultats sur des trajets réels.

### Phase 5 — Validation et lancement

- Effectuer des tests sur le terrain.
- Corriger les erreurs.
- Mesurer la couverture et la fiabilité des données.
- Tester le produit avec de vrais utilisateurs.
- Publier une première version utilisable.

# 11. Notre vision à long terme

La plateforme ne doit pas rester un simple outil de recherche d'itinéraires.

À long terme, elle pourrait devenir une infrastructure numérique de référence pour la connaissance de la mobilité urbaine.

Elle pourrait notamment permettre :

- De mieux comprendre la couverture des transports publics.
- D'identifier les zones insuffisamment desservies.
- D'observer l'évolution des réseaux.
- De faciliter l'accès aux données de mobilité.
- De fournir des outils d'analyse aux acteurs publics et privés.
- D'accompagner les projets d'amélioration de la mobilité urbaine.

Cette évolution dépendra de la qualité des données, des partenariats et des usages réellement observés.

# 12. Notre définition du succès

Le succès du MVP ne se mesurera pas au nombre de fonctionnalités développées.

Il se mesurera à notre capacité à démontrer les résultats suivants :

- Un utilisateur peut trouver un trajet entre deux lieux du District.
- Il comprend les différents moyens de transport à utiliser.
- Il sait où monter, descendre et effectuer ses correspondances.
- Les informations affichées sont traçables et leur fiabilité est identifiable.
- Les itinéraires proposés correspondent suffisamment à la réalité du terrain.
- L'équipe peut actualiser les données sans reconstruire l'application.

**Notre premier grand objectif : permettre à une personne qui ne connaît pas Abidjan de rejoindre une destination en transports publics en comprenant chaque étape de son déplacement.**

---

# Conclusion

Nous ne construisons pas une application supplémentaire pour concurrencer les grandes plateformes de navigation.

Nous construisons un outil qui part d'une réalité locale : la complexité de la mobilité urbaine à Abidjan et le manque d'une connaissance centralisée, accessible et vérifiable de ses réseaux.

Notre force doit venir de la qualité de notre connaissance du territoire, de notre capacité à structurer les données et de notre aptitude à transformer ces informations en une expérience réellement utile.

**Notre ambition : rendre les transports publics d'Abidjan compréhensibles et accessibles à tous.**
