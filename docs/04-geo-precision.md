# Audit et renforcement de la précision géographique

## 1. Faiblesses constatées

### 1.1 Modèle géographique (`src/geo/types.ts`)
- `Place` ne porte qu'une `location: { latitude, longitude }`.
- Pas de distinction entre `place_location`, `building_location`, `entrance_location`, `street_location`, `transit_stop_location`.
- Pas de rayon d'incertitude, pas de source de précision, pas de statut de vérification.
- Pas de type de géométrie (point, polygone, viewport).

### 1.2 Fournisseurs
- **GooglePlacesProvider** : field mask limité à `id, displayName, formattedAddress, location, types`. Pas de `viewport`, pas de `addressComponents` détaillés, pas d'indicateur de correspondance partielle. La position retournée est le centre du lieu (pas l'entrée). Pas de rayon d'incertitude.
- **LocalStopsProvider** : coordonnées issues de SQLite sans précision ni source de vérification.
- **ExpoLocationProvider** : `getCurrentPositionAsync` avec `Accuracy.Balanced` (précision ~100 m). Pas de distinction foreground/background. Pas de détection de position mockée.
- **Photon** : coordonnées de centroid, pas de précision.

### 1.3 nearestStops
- Distance à vol d'oiseau (haversine) uniquement.
- Rayon arbitraire de 2 km.
- Pas de prise en compte de la distance piétonne réelle, des accès, des obstacles.
- Peut sélectionner un arrêt éloigné simplement parce qu'il est dans le rayon.

### 1.4 Recherche
- Pas de sélection manuelle sur la carte (repère ajustable).
- Pas d'indication claire quand une position a été ajustée manuellement.
- Pas de distinction visuelle entre types de lieux (bâtiment vs arrêt vs POI).

### 1.5 Réseau piétonnier
- Aucune source de données piétonnières intégrée.
- Le moteur d'itinéraires suppose que la marche est possible en ligne droite (haversine) dans un rayon de 900 m.
- Pas de prise en compte des rues, ponts, passages, obstacles.

## 2. Modèle géographique proposé

### 2.1 Types de position

| Type | Description | Source typique |
|---|---|---|
| `place_location` | Position représentative d'un lieu (centre) | Google Places, Photon |
| `building_location` | Position d'un bâtiment | Google Places, OSM |
| `entrance_location` | Point d'accès physique (porte, entrée) | OSM, relevé terrain |
| `street_location` | Position sur une rue (adresse interpolée) | Geocoding |
| `transit_stop_location` | Emplacement d'un arrêt/station | SQLite (vérifié terrain) |

### 2.2 Structure proposée pour `Place`

```typescript
interface GeoPoint {
  latitude: number;
  longitude: number;
  accuracyM?: number | null;        // rayon d'incertitude (null si inconnu)
  source: 'google' | 'photon' | 'osm' | 'device' | 'manual' | 'local';
  geometryType: 'point' | 'centroid' | 'entrance' | 'interpolated' | 'viewport_center';
  locationType: 'place' | 'building' | 'entrance' | 'street' | 'transit_stop';
  verificationStatus: 'verified' | 'to_confirm' | 'unverified';
  verifiedAt?: string | null;
  externalId?: string;               // Place ID, OSM ID, etc.
}
```

### 2.3 Règles

- Ne jamais inventer une précision en mètres si le fournisseur ne la communique pas (`accuracyM = null`).
- Ne jamais présenter un centre de bâtiment comme une entrée.
- Ne jamais présenter une position interpolée comme une position de porte.
- Respecter les conditions de stockage et d'utilisation de chaque fournisseur (pas de copie Google dans SQLite).

## 3. Évaluation de Google Places et Geocoding

### 3.1 Métadonnées disponibles (Places API New)

- `location` : lat/lng (centre du lieu).
- `viewport` : rectangle englobant (peut servir à estimer la taille).
- `types` : types de lieu (ex. `point_of_interest`, `establishment`, `transit_station`).
- `addressComponents` : composants d'adresse (rue, numéro, quartier, commune, etc.).
- `formattedAddress` : adresse complète.
- `partialMatch` : indicateur de correspondance partielle (Geocoding API).

### 3.2 Limites à Abidjan

- Couverture des adresses précises variable selon les quartiers.
- Les résultats pour les rues secondaires et les marchés peuvent être approximatifs.
- Le centre d'un lieu n'est pas son entrée.
- Les plus codes (ex. `8WVW+H8V`) peuvent apparaître à la place d'une adresse.

### 3.3 Stratégie

- Enrichir le field mask Google pour inclure `viewport` et `addressComponents`.
- Distinguer les résultats par type (`transit_station`, `point_of_interest`, `establishment`, etc.).
- Afficher un indicateur de précision (« Position approximative ») quand `accuracyM` est élevé ou `geometryType` est `centroid`/`interpolated`.
- Ne pas traiter un centre de quartier comme une adresse.

## 4. Recherche sur la carte (sélection manuelle)

### 4.1 Concept

1. L'utilisateur recherche un lieu → la carte affiche le résultat.
2. Un repère (pin) est placé à la position retournée.
3. L'utilisateur peut déplacer le repère pour ajuster le point.
4. Il confirme le point de départ ou de destination.
5. L'application conserve la position sélectionnée (avec `source: 'manual'`).

### 4.2 Indication visuelle

- Repère déplaçable avec animation de « snap ».
- Affichage des coordonnées et de l'adresse approximative.
- Badge « Position ajustée manuellement ».
- Bouton « Confirmer ce point ».

### 4.3 Quand l'imposer

- Uniquement lorsque la précision est insuffisante (ex. `accuracyM > 100 m` ou `geometryType` = `centroid`).
- Optionnel sinon (l'utilisateur peut toujours ajuster).

## 5. Réseau de rues et chemins piétonniers

### 5.1 Source : OpenStreetMap

- Licence : ODbL (ouverture, attribution requise).
- Couverture à Abidjan : rues principales et secondaires bien couvertes, ruelles et chemins piétonniers partiellement.
- Données : ways (routes, footways, steps, bridges), nodes, relations.

### 5.2 Stratégie d'intégration

- Télécharger les données OSM pour la zone d'Abidjan (Overpass API) au format GeoJSON.
- Stocker localement (fichier GeoJSON ou SQLite avec extension spatiale).
- Utiliser pour le calcul de distance piétonne réelle (routing piéton).
- Ne pas intégrer aveuglément un itinéraire à travers une route privée ou un obstacle.

### 5.3 Limites

- Couverture incomplète pour les ruelles et passages.
- Données potentiellement obsolètes.
- Nécessite une vérification terrain pour les zones critiques (marchés, embarcadères).

## 6. Correction de nearestStops

### 6.1 Règle actuelle (à corriger)

- Distance à vol d'oiseau (haversine) uniquement.
- Rayon arbitraire de 2 km.
- Sélection des 3 plus proches.

### 6.2 Règle proposée

1. Rechercher les arrêts dans un rayon de 1 km (au lieu de 2 km).
2. Calculer la distance piétonne réelle si le réseau OSM est disponible.
3. Si le réseau piétonnier est incomplet, afficher « Distance indicative » et ne pas garantir l'accessibilité.
4. Ne pas choisir automatiquement un arrêt éloigné.
5. Afficher la distance à vol d'oiseau et la distance piétonne (si disponible) séparément.
6. Permettre à l'utilisateur de choisir un arrêt différent parmi les candidats.

### 6.3 Affichage

- « Arrêt le plus proche : X m (à vol d'oiseau) »
- Si distance piétonne disponible : « Distance à pied estimée : Y m »
- Si réseau piétonnier incomplet : « Distance piétonne non garantie »

## 7. Architecture géographique cible

```
┌─────────────────────────────────────────────┐
│  A. Référentiel des lieux et adresses       │
│     (Google Places, Photon, données locales) │
├─────────────────────────────────────────────┤
│  B. Réseau des rues et chemins piétonniers  │
│     (OpenStreetMap, données locales)         │
├─────────────────────────────────────────────┤
│  C. Réseau de transport public               │
│     (SQLite : lignes, parcours, arrêts)      │
└─────────────────────────────────────────────┘
```

Reliés par des identifiants et des coordonnées cohérents. Enrichissement progressif sur le terrain.

## 8. Protocole de test de précision

### 8.1 Lieux de test (Abidjan)

| Zone | Type de lieu | Coordonnées approx. |
|---|---|---|
| Plateau — Gare Sud | Terminal de transport | 5.319, -4.016 |
| Adjamé — Marché | Marché | 5.352, -4.026 |
| Cocody — Riviera | Quartier résidentiel | 5.360, -3.970 |
| Treichville — Embarcadère | Embarcadère lagunaire | 5.300, -4.010 |
| Yopougon — Sicogi | Zone dense | 5.340, -4.090 |
| Université Félix Houphouët-Boigny | Université | 5.345, -3.990 |
| CHU de Treichville | Hôpital | 5.295, -4.012 |
| Rue secondaire à Cocody | Rue résidentielle | 5.355, -3.975 |

### 8.2 Méthode

1. Relever la position de référence avec un GPS de précision (ou Google Maps sur le terrain).
2. Comparer avec la position retournée par Google Places, Photon et expo-location.
3. Mesurer l'écart en mètres.
4. Documenter les résultats par type de lieu et par zone.

### 8.3 Résultats attendus

- Ne pas inventer de résultats de précision si les relevés terrain n'ont pas été effectués.
- Documenter les écarts réels mesurés.
- Identifier les zones où la précision est insuffisante.

## 9. Fichiers concernés (audit, pas de modification)

- `src/geo/types.ts` — modèle à enrichir.
- `src/geo/providers/GooglePlacesProvider.ts` — field mask à enrichir (viewport, addressComponents).
- `src/geo/providers/LocalStopsProvider.ts` — ajouter précision/source.
- `src/geo/providers/ExpoLocationProvider.ts` — améliorer la précision (Accuracy.High).
- `src/geo/nearestStops.ts` — corriger la règle de sélection.
- `src/app/search.tsx` — ajouter la sélection manuelle sur la carte.
- `src/app/results.tsx` — afficher la précision des arrêts sélectionnés.
- `src/routing/graph.ts` — utiliser le réseau piétonnier si disponible.

## 10. Limites nécessitant une collecte réelle à Abidjan

- Couverture OSM des ruelles et chemins piétonniers.
- Précision des adresses Google dans les quartiers secondaires.
- Emplacements exacts des embarcadères et entrées de bâtiments.
- Accessibilité réelle des arrêts (chemins praticables).
- Mise à jour des données OSM (délai de propagation).

**J'attends ta validation explicite avant de commencer l'implémentation de cette mission.**
