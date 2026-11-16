# ATLAS — Urban Mobility Interface

## 1. Concept visuel

ATLAS combine la rigueur de la signalétique des transports (wayfinding) avec la qualité d'un design éditorial contemporain. L'application doit ressembler à un « plan de métro premium » : lignes nettes, codes lisibles, hiérarchie typographique forte, surfaces maîtrisées.

Principes :

1. **La carte est la surface principale.** Le reste de l'interface s'articule autour, pas l'inverse.
2. **La ligne est un objet visuel.** Chaque ligne a un identifiant fort (code en mono, couleur dédiée) reconnaissable dans les listes, les étapes et sur la carte.
3. **L'information est hiérarchisée.** Titres éditoriaux, métadonnées en mono, labels discrets.
4. **La fiabilité est visible.** Statut de vérification, source, date — jamais de données inventées.
5. **Le citron sert les actions.** Pas d'ornement : uniquement les actions principales et les éléments actifs.

## 2. Palette (ATLAS)

| Token | Hex | Rôle |
|---|---|---|
| `brand.primary` | #172A35 | Structure, texte principal, en-têtes |
| `brand.accent` | #D8F05A | Action principale, sélection, indicateur actif |
| `surface.canvas` | #F4F1E8 | Fond de l'application (clair) |
| `surface.primary` | #FFFFFF | Cartes, panneaux, champs |
| `surface.secondary` | #EAE7DE | Surfaces secondaires, chips, lignes séparatrices |
| `surface.elevated` | #FFFFFF | Panneaux flottants (bottom sheet) |
| `text.primary` | #172A35 | Texte principal |
| `text.secondary` | #75838A | Texte secondaire, métadonnées |
| `text.muted` | #9AA3A8 | Placeholders, labels discrets |
| `text.inverse` | #FFFFFF | Texte sur surfaces sombres |
| `border.subtle` | #DDDAD1 | Bordures fines |
| `border.strong` | #A9ADA9 | Bordures marquées |
| `status.success` | #237A57 | Données vérifiées |
| `status.warning` | #B7791F | À confirmer |
| `status.danger` | #C44747 | Erreur |
| `transport.bus` | #2F6FED | Bus |
| `transport.boat` | #0E8A8A | Bateaux-bus |
| `transport.gbaka` | #C44747 | Gbakas |
| `transport.walk` | #75838A | Marche |
| `ink` | #101B22 | Fond sombre, surfaces inversées |

Thème sombre : fond #101B22, surfaces #1A252C, texte #F4F1E8, secondaire #8A96A0, bordures #2A343B. Accent citron conservé.

## 3. Typographie

| Usage | Famille | Poids | Tailles |
|---|---|---|---|
| Titres éditoriaux, grands nombres | Space Grotesk | 500–700 | 28 / 22 / 18 |
| Interface, corps | Inter | 400 / 500 / 600 | 16 / 14 / 12 |
| Codes de ligne, distances, métadonnées | IBM Plex Mono | 400 / 500 | 12–14 |

Règles :

- Un code de ligne s'écrit toujours en IBM Plex Mono (ex. « 1 », « SOTRA-BUS-12 »).
- Les durées/distances utilisent IBM Plex Mono.
- Les titres utilisent Space Grotesk, jamais de graisse > 700.
- Inter pour tout le reste.

## 4. Composition

- Grille de 4 pt (espacements 4/8/12/16/20/24/32/48).
- Marges latérales 20–24.
- Rayons : 4/8/12/20 (pas de coins arrondis systématiques).
- Bordures fines 1 px sur les cartes, pas d'ombres lourdes.
- Surfaces éditoriales : fond ivoire, cartes blanches, séparateurs en #DDDAD1.
- Panneau inférieur (bottom sheet) : fond blanc, coin supérieur 20, poignée discrète.

## 5. Iconographie

- Icônes de transport dédiées et cohérentes (bus, bateau, gbaka, marche).
- Icônes de navigation : SymbolView (SF Symbols / Material), tailles 20–24.
- Pas d'icônes décoratives : chaque icône a une fonction.
- Les pictogrammes de transport peuvent être personnalisés plus tard.

## 6. Traitement cartographique

- Carte en plein écran avec contrôles (zoom, position) en overlay.
- Lignes colorées par mode, épaisseur variable selon zoom.
- Arrêts : points pleins, stations : cercles, terminaux : losanges/carrés.
- Itinéraire sélectionné : ligne continue + étapes numérotées.
- Panneau inférieur : informations du point sélectionné, actions.

## 7. États et accessibilité

- Chaque composant possède des états : normal, pressé, sélectionné, désactivé, chargement, erreur.
- Contrastes vérifiés (texte sur fond, accent sur fond sombre).
- Informations non dépendantes uniquement de la couleur (label + icône).
- Zones tactiles ≥ 44 pt.
