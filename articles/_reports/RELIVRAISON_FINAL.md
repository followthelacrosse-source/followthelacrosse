# Mini report — Re-livraison finale · Lot articles.html Couche 1
**Follow The Lacrosse · 2026-04-02**

---

## Ce qui a été corrigé dans la re-livraison

| Correction | Fichier | Nature |
|-----------|---------|--------|
| JS — scope filtre restreint à `#latest .card[data-country]` | articles.html | Bug fonctionnel : Featured était filtrée |
| CSS `.card-stack` ajouté | articles.html | Manquant : side column Featured sans style de stack |
| CSS `.card-title-sm` ajouté | articles.html | Manquant : classe utilisée sans définition CSS |
| G5 badge `<span class="tf">` vide → `tf tf-fi` + "Field" | articles.html | Incohérence visuelle : card `data-fmt="field"` sans badge format |
| G6 badge `<span class="tf">` vide supprimé | articles.html | Span orphelin : `data-fmt="general"` n'a pas de badge format |
| REPORT_ARTICLES_CURRENT.md réécrit | articles/_reports/ | Alignement sur l'état réel final |

---

## Ce qui reste volontairement en dette

- **Links brisés dans country-*.html et tournament-detail.html** : ces pages pointent encore vers `article-*.html` à la racine. Hors périmètre lot 1 — à corriger dans les lots countries et tournaments.
- **article-detail.html** : contenu générique, assumé comme placeholder structurel jusqu'au lot éditorial Couche 2.
- **interview-sophie-laurent-france.html** : référencé dans G6 mais n'existe pas encore. Lien fictif assumé.
- **Images Unsplash et noms d'auteurs fictifs** : placeholders visuels et éditoriaux assumés.

---

## Source de vérité du lot

| Fichier | Ce qu'il dit |
|---------|-------------|
| `articles.html` | État de référence de la page listing — structure, CSS, JS, HTML |
| `articles/_reports/REPORT_ARTICLES_CURRENT.md` | État final auditable complet, vérifications, dettes |
| `articles/_reports/PLACEHOLDER_LEDGER_ARTICLES.csv` | Inventaire exhaustif des placeholders et liens fictifs |
| `articles/_reports/PENDING_REVIEW_ARTICLES.md` | Questions ouvertes pour les lots suivants |

---

## État du lot

**Stable. Validable pour passer au lot suivant.**

Périmètre respecté : seuls `articles.html`, `index.html` (17 hrefs) et `articles/` ont été modifiés. Aucune page hors périmètre touchée.
