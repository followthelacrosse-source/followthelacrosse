# REPORT — tournaments.html · État final consolidé
**Follow The Lacrosse · 2026-04-09**
**Lots : initial · verrouillage éditorial · correctif CTA/layout/archives**

---

## A. Hiérarchie finale réelle de tournaments.html

```
1. <header> — nav sombre, logo, Countries, newsletter CTA
2. <section class="hero-page"> — promesse calendrier européen curé
3. <div class="subnav"> — navigation sections (ancres), sticky top:60px
4. <section id="continental" class="s bg-dark"> — calendrier continental (3 cartes)
5. <section id="national" class="s bg-white"> — événements nationaux (5 cartes + bouton bas)
6. <section id="league-watch" class="s"> — watchlist éditoriale (3 cartes + bouton bas)
7. <section id="country-gateways" class="s-sm bg-ivoire"> — passerelles pays (6 cartes + bouton bas)
8. <section id="archives" class="s-sm bg-white"> — Previously in Europe + org-cta
9. <div class="nl-dark"> — newsletter
10. <footer> — footer avec Countries
```

---

## B. Rôle de chaque section

| Section | Rôle éditorial | Identité visuelle |
|---------|---------------|-------------------|
| S01 Continental | Sommet hiérarchique — ELF + continental | Fond nuit, cartes semi-transparentes |
| S02 National Events | Championnats et coupes nationaux | Fond blanc, tc-new, bouton bas de fermeture |
| S03 League Watch | Watchlist éditoriale — scènes domestiques | Fond bg, match-card accent gauche, bouton bas |
| S04 Country Gateways | Passerelle vers les 6 scènes concernées | Fond ivoire, grille 3 col, bouton bas |
| Previously in Europe | Ressources externes saison 2025 + contexte pays | Fond blanc, liste compacte, lien pays repli |

---

## C. Décisions structurelles — lot initial

| Élément | Décision |
|---------|----------|
| `.sponsor-bar` | Supprimé HTML + CSS |
| Subnav filtres → ancres | Convertis — JS filter était factice |
| Selects redondants | Supprimés |
| nl-strip → nl-dark | Harmonisation |
| CSS orphelins (~120 lignes) | Supprimés |
| Countries dans nav + footer | Ajouté |

---

## D. Décisions — lot verrouillage éditorial

### D1. S03 League Watch — requalification watchlist

**Avant :** fixtures inventées avec clubs fictifs, rounds précis, dates fixes.
**Après :** watchlist éditoriale — nom de ligue réel, label éditorial (Weekend Watch / Domestic Watch / Matchday Watch), pas de clubs ni de dates fictives.

**Logique :** S03 signale ce que FTL surveille dans les scènes domestiques, pas ce qu'il certifie comme calendrier officiel. La différence est éditoriale et fondamentale pour la crédibilité du hub.

### D2. Country Gateways — règle data-driven

**Règle appliquée :** seuls les pays référencés dans S01/S02/S03 sont affichés.

| Pays | Présent dans |
|------|-------------|
| England | S01 (London), S03 (Box League) |
| France | S02 (French Nationals), S03 (Ligue Nationale) |
| Germany | S02 (Berlin Box), S03 (Bundesliga) |
| Netherlands | S02 (Amsterdam Sixes) |
| Italy | S02 (Italian Cup) |
| Czech Republic | S02 (Prague Sixes) |
| Sweden | ✗ absent — retiré |
| Spain | ✗ absent — retiré |

### D3. Previously in Europe — ressources externes

**Avant :** "Season Archives" + lien "Browse coverage →" vers `articles.html`.
**Problème :** impliquait une archive FTL interne inexistante.
**Après :** "Previously in Europe" + microcopie explicite ("Not internal FTL coverage") + liens supprimés.

---

## E. Décisions — mini-lot correctif CTA/layout/archives

### E1. CTA — correction de la logique de fermeture de section

**Mauvaise interprétation dans le lot précédent :** les boutons de fin de section de S02 et S03 avaient été supprimés au motif de "doublon". C'était incorrect.

**La logique correcte :**
- Les cartes individuelles servent de liens *spécifiques* (événement précis, ligue précise, pays précis).
- Le bouton bas de section sert de *sortie générique* — fermeture de section et navigation large.
- Ce ne sont pas deux commandes identiques : elles opèrent à des niveaux différents.

**État final :**

| Section | CTA header | Bouton bas | Justification |
|---------|-----------|-----------|---------------|
| S02 National Events | ~~"Explore by country →"~~ — **supprimé** | "Explore by country →" → countries.html — **ajouté** | Un seul point de commande, placé en fermeture naturelle de section |
| S03 League Watch | Aucun (jamais eu) | "Explore all scenes →" → countries.html — **ajouté** | Fermeture + sortie générique |
| S04 Country Gateways | Aucun | "All countries & scenes →" — **conservé** | Déjà présent et juste |

**Note :** le CTA header de S02 ("Explore by country →") a été retiré car sa position à droite du titre créait une ambiguïté : est-ce la commande principale de la section ou un raccourci optionnel ? Le bouton bas est plus lisible comme fermeture de section.

### E2. Country Gateways — correction layout

**Problème :** `grid-template-columns: repeat(4, 1fr)` avec 6 items = 4 cartes ligne 1 + 2 cartes ligne 2 (trou de 2 colonnes). Rendu visuellement déséquilibré.

**Correction :** `repeat(3, 1fr)` → 2 rangées de 3 cartes, grille propre, aucun trou.

| Breakpoint | Avant | Après |
|-----------|-------|-------|
| Desktop (>900px) | 4 colonnes — trou | 3 colonnes — 2 rangées pleines |
| Tablet (≤900px) | 2 colonnes | 2 colonnes — inchangé |
| Mobile (≤600px) | 2 colonnes | 2 colonnes — inchangé |

La logique data-driven (6 pays réels) est conservée. Seul le layout est corrigé.

### E3. Previously in Europe — lien de repli vers les pages pays

**Problème :** la section était sémantiquement honnête mais passive — aucun lien actif, donc aucune navigation possible depuis ces items.

**Logique de repli :**
- Aucune source externe vérifiée disponible → pas de lien externe inventé.
- Mais les pays de chaque événement ont une page pays existante.
- Ces pages offrent du *contexte de scène*, pas des résultats — c'est honnête et utile.

**État final par item :**

| Item | Lien ajouté | Destination | Wording |
|------|------------|-------------|---------|
| European Championship Qualifiers | ✓ | `country-czech-republic.html` | "Country scene →" |
| Paris Sixes Invitational | ✓ | `country-france.html` | "Country scene →" |
| Milan Indoor Classic | ✓ | `country-italy.html` | "Country scene →" |

**Ce qui n'a PAS été fait :** lien vers articles.html, lien fictif Pointbench, texte "Browse coverage", toute formulation suggérant que FTL héberge des résultats.

---

## F. Vérifications finales

- [x] S02 : CTA header supprimé — 0 occurrence `see-all` dans S02
- [x] S02 : bouton bas "Explore by country →" présent en `.section-cta`
- [x] S03 : bouton bas "Explore all scenes →" présent en `.section-cta`
- [x] S04 : bouton bas "All countries & scenes →" conservé
- [x] `gw-grid` = `repeat(3,1fr)` — 2 rangées de 3, aucun trou
- [x] Responsive gw-grid : 2 col ≤900px, 2 col ≤600px — inchangé
- [x] 6 pays dans S04 : England, France, Germany, Netherlands, Italy, Czech Republic
- [x] Sweden et Spain absents — non référencés dans S01/S02/S03
- [x] Previously in Europe : 3 liens "Country scene →" vers les pages pays correspondantes
- [x] 0 lien vers articles.html dans Previously in Europe
- [x] 0 lien Pointbench inventé
- [x] "External source TBC" maintenu sur les 3 items
- [x] S03 watchlist : 0 club fictif, 0 round fictif, 0 date fictive
- [x] DOM vérifié — fermetures balises correctes sur S02, S03, S04, archives
- [x] Aucun lien cassé vers des pages existantes

---

## G. Dettes résiduelles

| Dette | Type | Priorité |
|-------|------|----------|
| `tournament-detail.html` placeholder — S01 et S02 y pointent | Lien fictif | Lot tournaments détail |
| C2 / C3 (Sixes Invitational, Box Cup) — noms non vérifiés | Placeholder structurel visible | Lot calendrier ELF |
| ELF Spring Championship "Men & Women" — non vérifié | Donnée à confirmer | Vérification ELF |
| Previously in Europe — sources externes non injectées | TBC | Lot sources (Pointbench, fédérations) |
| Formats par pays dans S04 — estimés | Non vérifiés | Lot pays |
| England flag = UK (🇬🇧) et non England (🏴󠁧󠁢󠁥󠁮󠁧󠁿) | Simplification assumée | Cohérence globale |
