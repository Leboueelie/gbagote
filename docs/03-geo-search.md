# Recherche géographique universelle — Architecture

## 1. Fournisseur effectivement intégré

- **Principal (si configuré)** : Google Places API (New) via REST.
  - Autocomplete : `POST https://places.googleapis.com/v1/places:autocomplete`
  - Place Details : `GET https://places.googleapis.com/v1/places/{placeId}`
- **Secours libre (toujours disponible)** : Photon (Komoot, basé sur OpenStreetMap) — aucune clé requise.
- **Fallback final** : arrêts locaux SQLite (`LocalStopsProvider`).
- **Géolocalisation** : `expo-location` (foreground permission).

Chaînage : Google → Photon → arrêts locaux (sur vide ou erreur).

Aucun SDK natif Google Maps n'est requis pour la recherche ; l'affichage cartographique (MapLibre) reste à intégrer.

## 2. Architecture indépendante du fournisseur

```
src/geo/
  types.ts              # Place, PlaceSuggestion, PlaceSearchProvider, LocationProvider, ...
  providers/
    GooglePlacesProvider.ts   # REST Google Places (New), gated by API key
    LocalStopsProvider.ts     # arrêts locaux SQLite (fallback)
    ExpoLocationProvider.ts   # expo-location
  nearestStops.ts       # recherche des arrêts les plus proches d'un point
```

Contrats :
- `PlaceSearchProvider` : `isConfigured()`, `search()`, `getDetails()`.
- `LocationProvider` : `requestPermission()`, `getPermissionStatus()`, `getCurrentPosition()`.

L'UI ne parle qu'aux contrats. Changer de fournisseur = remplacer l'implémentation.

## 3. Configuration Google Cloud requise

1. Créer un projet Google Cloud.
2. Activer **Places API (New)**.
3. Créer une clé API **restreinte** :
   - Type : application Android (package `com....` + empreinte SHA-1) pour la prod.
   - Ou clé HTTP avec restriction de référent pour le dev.
4. Définir des quotas et alertes de facturation.
5. Renseigner la clé dans `app.json` → `expo.extra.googleMapsApiKey` (ou variable d'environnement `EXPO_PUBLIC_GOOGLE_MAPS_API_KEY`).

Sans clé, l'application bascule automatiquement sur la recherche locale d'arrêts (pas de résultats Google simulés).

## 4. Règles de conservation appliquées

- Les résultats Google ne sont **pas** copiés dans SQLite.
- Seule la sélection de l'utilisateur (Place ID + nom + coordonnées) est transmise à l'écran de résultats.
- Les favoris géographiques stockent le Place ID et le libellé (usage personnel), conformément aux conditions Google.
- Google Directions n'est **pas** utilisé pour fabriquer des itinéraires de transports publics.

## 5. Fonctionnement réel de la recherche

- Debounce 250 ms + annulation des requêtes obsolètes (AbortController).
- Recherche limitée à la région d'Abidjan (locationBias + includedRegionCodes ci).
- Suggestions avec nom, adresse descriptive et type de lieu.
- Sélection → `getDetails` → objet `Place` normalisé.
- Bouton « Ma position » : demande de permission, récupération de la position, reverse geocoding (expo-location), création d'un `Place` de type « Position ».
- Gestion des permissions : accordée / refusée / services désactivés / erreur.

## 6. Frontière avec le moteur de transport

- L'écran transmet un départ et une destination géographiques (lat/lon + nom + placeId + provider).
- `result.tsx` trouve les arrêts les plus proches (haversine, max 2 km) et lance `findRoute`.
- Si aucun arrêt à proximité : message honnête.
- Aucune ligne, arrêt, correspondance ou tarif n'est inventé.

## 7. Tests réalisés

- `tsc --noEmit` : ✅
- `eslint` : ✅ 0 erreur
- `expo export --platform android` : ✅
- `expo-doctor` : 20/20 ✅

## 8. Coûts potentiels et limites

- Google Places API (New) est facturé par requête (Autocomplete + Place Details). Configurer des quotas.
- Sans clé Google, la recherche se limite aux arrêts locaux.
- La carte réelle (MapLibre) n'est pas encore intégrée (build natif requis).
- Le moteur d'itinéraires utilise des données d'exemple (seed non vérifié).
- L'historique de recherche et les favoris géographiques ne sont pas encore persistés.
