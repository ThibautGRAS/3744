# Surfaces de mesure ISO 3744 — visualisation AR · CETIM

Appli web (iPhone, Safari ou Chrome iOS, HTTPS) qui affiche en réalité augmentée, **à l'échelle réelle 1:1**, les antennes microphoniques de l'**ISO 3744:2010** :

- **Hémisphère r = 1 m — Table B.2** (large bande) : antenne clé 10 positions, antenne étendue 20 positions
- **Hémisphère r = 1 m — Table B.1** (toutes sources, anti-interférences) : 10 et 20 positions
- **Parallélépipède — Annexe C** : 9 positions clés (boîte réf. 1×1×1 m, d = 1 m, surface 3×3×2 m)

## Fonctionnement

`index.html` est la seule page : chaque configuration est un lien `<a rel="ar">` vers un fichier
**USDZ pré-généré**, ouvert directement dans **AR Quick Look** (ARKit natif — détection du sol
markerless, sans LiDAR requis ; LiDAR utilisé automatiquement s'il est présent). Le modèle
s'ouvre à l'échelle 1:1 et reste **redimensionnable au pincement** (le verrou
`#allowsContentScaling=0` a été retiré pour permettre l'ouverture directe en caméra sur Safari).

Choix technique validé par recherche multi-sources : WebXR est absent d'iOS Safari et le SLAM
JavaScript est trop instable sans échelle métrique fiable → AR Quick Look est la seule voie robuste.

## Options (interrupteurs de la page)

Deux interrupteurs combinables sélectionnent la variante USDZ via un suffixe de fichier :

| Technicien | Ancrage cible | Suffixe | Contenu |
|---|---|---|---|
| off | off | *(aucun)* | modèle de base |
| on | off | `-ph` | fils à plomb, pastilles à marquer au sol, hauteurs micro sur étiquettes |
| off | on | `-a` | modèle verrouillé sur la cible imprimée, gestes désactivés |
| on | on | `-pha` | les deux |

Fichiers : `usdz/hemi-{b1,b2}-{10,20}[-suffixe].usdz`, `usdz/para-9[-suffixe].usdz`.

**Cible d'ancrage** (`assets/cible-ancrage.pdf`, visible quand l'interrupteur ancrage est actif) :
imprimer en A4 à **100 %** — vérifier **160 mm au réglet** ; la croix = centre de la source.
Poser la feuille au centre de la zone et la viser avec la caméra : zéro dérive, position répétable.

## Pièges connus

- Ne pas ouvrir les liens depuis **Teams, Outlook ou LinkedIn** : leurs navigateurs intégrés
  affichent le fichier USDZ brut au lieu de lancer AR Quick Look. Safari ou Chrome iOS uniquement.
- Impression de la cible : l'option « ajuster à la page » fausse l'échelle → toujours 100 %.

## Déploiement

Site statique (GitHub Pages) — HTTPS obligatoire. Aucun build, aucune dépendance.

```
index.html   page unique
usdz/        modèles 3D pré-générés (24 variantes)
assets/      badges, logo CETIM, cible d'ancrage PDF
```
