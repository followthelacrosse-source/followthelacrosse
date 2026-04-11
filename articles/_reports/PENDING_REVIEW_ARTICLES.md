# PENDING REVIEW — articles/ · Couche 2
**Follow The Lacrosse · 2026-04-07**

---

## Questions ouvertes héritées de Couche 1, toujours actives

| Question | Impact | Lot cible |
|----------|--------|-----------|
| country-*.html ont des `href="article-*.html"` non préfixés | Liens brisés depuis pages pays | Lot countries |
| tournament-detail.html a des `href="article-*.html"` non préfixés | Liens brisés | Lot tournaments |
| article-detail.html — contenu générique (France 9-8 England) | Placeholder structurel | Éditorial Couche 3 |
| G4 (Italy's club scene) pointe vers article-sixes-rome-italy.html | Incohérence titre/contenu | Couche 3 |
| G5 (ELF 2026 rules) pointe vers article-elf-spring-2026-preview.html | Incohérence titre/contenu | Couche 3 |
| G6 pointe vers interview-sophie-laurent-france.html (inexistant) | Lien fictif | Lot interviews |

---

## Questions ouvertes issues de Couche 2

### 1. fts-block : steps "Interview" et "Tournament" manquants sur 5 articles
- article-detail.html a des steps vers interview-detail.html et tournament-detail.html
- Les 5 autres articles n'ont que 3-4 steps vers country/format/countries
- Cet écart est assumé tant que les pages interviews/tournaments n'existent pas
- **Action requise** : enrichir les fts-blocks quand les pages cibles existent

### 2. data-gender toujours présent sur les cartes mais non filtré
- Le filtre genre a été supprimé de la surface
- Les attributs `data-gender` restent sur F1/F2/F3 et G1-G6 comme métadonnée
- **À décider** : réintroduire le filtre genre quand le volume éditorial le justifie

### 3. Contenu du see-all dans Latest
- `<a href="articles.html" class="see-all">View All →</a>` pointe vers articles.html lui-même
- Ce lien est redondant si l'utilisateur est déjà sur articles.html
- **À décider** : supprimer le see-all ou le faire pointer vers une page de listing paginée

---

## Actifs éditoriaux à préserver

| Composant | Fichier | Valeur |
|-----------|---------|--------|
| fts-block ("Follow the Story") | tous les 6 articles | Bloc premium de navigation éditoriale — ne pas supprimer |
| art-community (React to this article) | tous les 6 articles | CTA communautaire — liens vers about.html#contact valides |
| art-nl (FTL Weekly) | tous les 6 articles | Bloc newsletter intégré — cohérent avec nl-dark de articles.html |
| art-related (Continue Reading) | tous les 6 articles | Liens relatifs — country-*.html et articles entre eux |

---

## Règles actives pour ce dossier

- `data-fmt=""` interdit — utiliser `"general"` pour contenu cross-format
- `data-type` obligatoire sur toutes les cartes Latest
- `data-country` obligatoire sur toutes les cartes Featured et Latest
- Tout lien inter-article (même dossier) : chemin relatif sans `../`
- Tout lien vers racine depuis articles/ : préfixe `../` obligatoire
