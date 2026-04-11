# Follow The Lacrosse — règles sous-dossier articles/

## Contexte
Ce dossier contient les articles individuels déplacés depuis la racine du projet lors du lot articles.html (Couche 1, 2026-04-02).

## Fichiers présents
- `article-berlin-clubs-transition.html`
- `article-detail.html`
- `article-elf-spring-2026-preview.html`
- `article-england-box-goalie-duel.html`
- `article-olympic-lacrosse-2028-europe.html`
- `article-sixes-rome-italy.html`

## Règles de chemins relatifs
Tous les liens et assets dans ces fichiers utilisent le préfixe `../` pour remonter à la racine :
- `href="../index.html"` — homepage
- `href="../articles.html"` — page listing
- `href="../countries.html"` — pays
- `href="../tournaments.html"` — tournois
- `src="../assets/logo.png"` — logo
- `href="../assets/style.css"` — feuille de style partagée si applicable

Les liens inter-articles (vers d'autres fichiers dans ce même dossier) n'ont pas de préfixe.

## Interdictions
- Ne pas déplacer ces fichiers sans mettre à jour tous les href entrants dans index.html et articles.html.
- Ne pas modifier les chemins relatifs sans vérifier l'impact sur les 6 fichiers.
- Ne pas rouvrir articles.html, index.html ou les pages country-* sauf contrainte technique absolument indispensable.

## Reports
Les reports de lot pour ce sous-dossier sont dans `_reports/`.
