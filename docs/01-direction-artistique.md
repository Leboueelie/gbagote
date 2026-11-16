# CONTEMPORARY LIFESTYLE — Direction artistique

## 1. Concept créatif

Mobilité Abidjan n'est pas un outil administratif : c'est un compagnon quotidien pour se déplacer dans une ville vivante, lagunaire et dense. L'identité **Contemporary Lifestyle** traduit cette énergie : chaleureuse, lumineuse, raffinée, immédiatement compréhensible. On s'inspire de la qualité de composition d'Airbnb, de la clarté des déplacements de Citymapper, de la cartographie d'Apple Maps et de la personnalité de Headspace — sans copier aucune interface.

L'application doit donner envie d'être ouverte plusieurs fois par jour, tout en restant un outil de précision.

## 2. Références retenues et apports

- **Airbnb** — compositions aérées, hiérarchie claire, chaleur.
- **Citymapper** — représentation des transports, codes de ligne, comparaison d'itinéraires.
- **Apple Maps** — cartographie élégante, panneaux contextuels, hiérarchie spatiale.
- **Headspace** — personnalité graphique, cohérence, identité mémorable.
- **City guides premium** — photographie urbaine soignée, éditorial.

## 3. Palette complète (HEX)

| Token | HEX (clair) | HEX (sombre) | Rôle |
|---|---|---|---|
| brand.primary | #0F766E | #2DD4BF | Identité, actions principales, liens |
| brand.secondary | #F97316 | #FB923C | Accent secondaire, énergie, CTA ponctuels |
| brand.accent | #FBBF24 | #FCD34D | Mise en avant, badges, sélection |
| surface.canvas | #FAF7F2 | #0F172A | Fond de l'application |
| surface.primary | #FFFFFF | #1E293B | Cartes, panneaux, champs |
| surface.secondary | #F2EDE4 | #334155 | Surfaces secondaires, chips |
| surface.elevated | #FFFFFF | #1E293B | Bottom sheets, modales |
| text.primary | #18181B | #F8FAFC | Texte principal |
| text.secondary | #52525B | #CBD5E1 | Texte secondaire, métadonnées |
| text.muted | #A1A1AA | #64748B | Placeholders, labels discrets |
| text.inverse | #FFFFFF | #0F172A | Texte sur surfaces sombres |
| border.subtle | #E4DFD6 | #334155 | Bordures fines |
| border.strong | #C9C2B6 | #475569 | Bordures marquées |
| status.success | #16A34A | #4ADE80 | Données vérifiées |
| status.warning | #D97706 | #FBBF24 | À confirmer |
| status.danger | #DC2626 | #F87171 | Erreur |
| status.info | #2563EB | #60A5FA | Information |
| transport.bus | #2563EB | — | Bus |
| transport.boat | #0891B2 | — | Bateaux-bus |
| transport.gbaka | #F97316 | — | Gbakas |
| transport.walk | #71717A | — | Marche |

Justification : le teal évoque la lagune Ébrié et la fraîcheur ; l'orange évoque l'énergie et le soleil d'Abidjan ; le fond crème donne de la chaleur et de la lumière. Les couleurs restent suffisamment sobres pour la crédibilité.

## 4. Système typographique

| Usage | Famille | Poids | Tailles |
|---|---|---|---|
| Grands titres | Manrope | 700/800 | 32 / 26 / 22 |
| Titres de section | Manrope | 600 | 20 / 18 |
| Titres de cartes | Manrope | 600 | 16 |
| Texte courant | Inter | 400/500 | 15 / 14 |
| Informations secondaires | Inter | 400 | 13 / 12 |
| Codes de ligne, durées, distances | DM Mono | 400/500 | 12–14 |
| Eyebrow / labels | Inter | 600 | 11 (uppercase, tracking) |

## 5. Règles d'espacement, formes, surfaces

- Grille de 4 pt : 4/8/12/16/20/24/32/48.
- Marges latérales : 20–24.
- Rayons : 8 (champs/boutons), 12 (cartes), 16 (surfaces majeures), 20 (bottom sheets), 999 (chips/pastilles).
- Ombres : discrètes, une seule niveau (0 4px 16px rgba(0,0,0,.06)).
- Bordures : 1 px, couleur border.subtle.
- Compositions asymétriques autorisées lorsque pertinentes (ex. hero avec titre à gauche et illustration à droite).

## 6. Icônes et cartographie

- Icônes : SymbolView (SF Symbols / Material) pour la navigation ; icônes de transport personnalisées possibles.
- Carte : fond crème/sable, eau en teal doux, lignes de transport colorées par mode, arrêts en points, stations en cercles pleins, terminaux en carrés. Itinéraire sélectionné en pétrole épais avec pastilles numérotées citron.

## 7. Animations et accessibilité

- Transitions douces (200–300 ms), easing ease-out.
- Panneaux qui s'étendent naturellement.
- Respect des préférences de réduction des animations.
- Contrastes vérifiés, zones tactiles ≥ 44 pt, informations non dépendantes uniquement de la couleur.

## 8. Limites avant implémentation

- MapLibre nécessite un build natif (pas Expo Go).
- Photographies urbaines : utiliser des ressources vérifiées et accessibles, avec fallback.
- Données fictives dans les maquettes clairement identifiées comme démonstration.
- Pas de NativeWind/Gluestack obligatoires : styling via StyleSheet + tokens centralisés, migration progressive si justifiée.
