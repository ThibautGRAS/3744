# Demi-sphère ISO 3744 — visualisation AR

Appli web (Safari iPhone, HTTPS) qui affiche les **10 positions micro de la demi-sphère ISO 3744**
(rayon 1 m réglable, coordonnées normalisées `x/r, y/r, z/r`) en réalité augmentée sur le sol.

Ouvre `index.html` → choix entre deux modes.

## Mode marqueur (`ar-marker.html`) — ancrage fixe

La caméra reconnaît un **marqueur imprimé** posé au sol et y ancre la demi-sphère.
Elle reste fixe dans l'espace **même quand tu te déplaces**, tant que le marqueur est visible.

À faire : imprime le marqueur **Hiro** (motif standard AR.js) et pose-le au centre de la zone.
Marqueur à imprimer : https://raw.githack.com/AR-js-org/AR.js/master/data/images/hiro.png
(ou cherche « AR.js Hiro marker pattern » — imprimer sur une feuille A4, à plat).

Le centre du marqueur = point de référence au sol (centre de la demi-sphère).

## Mode sans marqueur (`sans-marqueur.html`) — rapide

Aucun marqueur. Vise le sol, tape l'écran pour poser le centre. Renseigne la hauteur du
téléphone pour caler le plan du sol. Stable en rotation, **dérive si tu marches**
(limite d'iOS Safari : pas de WebXR ni d'accès LiDAR en web).

## Déploiement

GitHub Pages ou Netlify (HTTPS obligatoire pour caméra + capteurs). `index.html` à la racine.
