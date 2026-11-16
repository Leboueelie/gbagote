# Rapport d'audit — Interface actuelle

## 1. Inventaire

| Zone | État | Observations |
|---|---|---|
| Racine `_layout.tsx` | Fonctionnel | Stack + SQLiteProvider + migration OK. Thème clair/sombre via `ThemeProvider` expo-router. |
| Onglets `(tabs)` | Fonctionnel mais générique | Icônes SymbolView basiques, pas d'identité forte, barre standard. |
| Accueil | Fonctionnel | Hero + stats DB + bouton recherche. Layout correct mais fade, hiérarchie faible. |
| Carte | Placeholder | Aucune carte réelle. Écran vide avec message. |
| Recherche | Fonctionnel | Champs + suggestions + validation. Comportement OK, visuel générique. |
| Résultats | Fonctionnel | En-tête + étapes. Lisible mais pas d'identité visuelle, pas de distinction visuelle des modes. |
| Détail itinéraire | Inexistant | L'écran `result.tsx` fait résultat + détail à la fois, pas de détail pas-à-pas. |
| Ligne / Station | Inexistant | Pas de fiches. |
| Favoris | Placeholder | Écran vide. |
| Paramètres | Placeholder | Écran vide. |
| Design system | Incomplet | `src/theme/tokens.ts` existe (couleurs, espacements, rayons, typographie, élévations) mais pas de composants centralisés ni de thème sombre. |
| Composants | Templates Expo | `themed-text`, `themed-view`, `hint-row`, etc. — hérités du template, pas adaptés au produit. |
| Fonts | Installées | Space Grotesk, Inter, IBM Plex Mono présents mais non chargés. |

## 2. Points à conserver

- Architecture Expo Router + SQLiteProvider + migration idempotente.
- Séparation déjà amorcée : `db/`, `routing/`, `repositories/`, `types/`.
- Graphe + Dijkstra fonctionnels (données d'exemple).
- Chargement des données au démarrage.

## 3. Points à reconstruire

1. Design system complet (tokens ATLAS, thème clair/sombre, composants).
2. Identité visuelle : titres éditoriaux, codes de ligne en mono, distinction visuelle des modes.
3. Écran d'accueil : recherche de destination en premier, accès carte, favoris, récents.
4. Écran de carte : plein écran, contrôles, panneau inférieur, lignes/arrêts.
5. Écran de recherche : sélecteur départ/destination, inversion, suggestions.
6. Écran de résultats : comparatif, badges de fiabilité, tri.
7. Écran de détail : guidage étape par étape + carte du parcours.
8. Fiches ligne et station.
9. Favoris et paramètres fonctionnels.

## 4. Risques / contraintes

- MapLibre nécessite un build natif (pas Expo Go) : intégration à prévoir après validation de l'UI.
- Performances Android modestes : éviter effets lourds, shadows excessives, animations complexes.
- Ne jamais afficher d'informations inventées : badges de fiabilité partout.
