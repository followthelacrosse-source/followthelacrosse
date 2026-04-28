# REPORT — tournaments.html · État courant

**Date** : 2026-04-27  
**Lots couverts** : LOT 0 (initial) · LOT 1 V1/V2 (restructuration stratifiée) · LOT 2 (classification réelle)  
**Statut** : Livré — 6 sections, données réelles, placeholders signalés

---

## A. Architecture finale — 6 sections stratifiées

```
1. <header>           — nav sombre sticky, logo, liens principaux
2. <section class="hero-page">  — kicker + titre + promesse éditoriale
3. <div class="subnav">         — navigation ancres sticky top:60px
4. S01 #european-competitive-layer  bg-dark  — couche continentale officielle
5. S02 #key-tournaments             bg-white — tournois clés éditoriaux
6. S03 #editorial-watchlist         bg-      — signaux FTL en observation
7. S04 #domestic-league-tracking    bg-ivoire — structures nationales
8. S05 #results-data               bg-white  — appendice externe (s-sm)
9. S06 #country-gateways           bg-ivoire  — navigation pays (s-sm)
10. <div class="nl-dark">           — newsletter
11. <footer>                        — footer complet
```

---

## B. Rôle éditorial par section

| Section | Rôle | Composant cartes | Nb cartes |
|---------|------|-----------------|-----------|
| S01 European Competitive Layer | Sommet hiérarchique : championnats continentaux officiels | `.cont-card` bg-dark | 3 |
| S02 Key Tournaments | Tournois qui révèlent un momentum national ou méritent attention | `.tc-new` bg-white | 7 |
| S03 Editorial Watchlist | Signaux FTL — observation, pas couverture confirmée | `.match-card` | 2 |
| S04 Domestic League Tracking | Structures nationales récurrentes + coupes nationales | `.match-card` | 8 |
| S05 Results & Data Sources | Appendice externe — références passées, non-couverture FTL | `.past-item` | 3 |
| S06 Country Gateways | Navigation vers les scènes nationales | `.gw-card` | 6 |

---

## C. LOT 1 — Restructuration stratifiée (2026-04-[antérieur])

### Ce qui a changé vs l'état initial

| Avant | Après |
|-------|-------|
| 4 sections sans logique de strates | 6 sections stratifiées par niveau hiérarchique |
| Section "League & Match Watch" à plat | Split S03 (watchlist éditoriale) + S04 (structures nationales) |
| Country Gateways en milieu de page | Country Gateways en dernière position (lecture séquentielle) |
| "Season Archives" = faux archives FTL | "Results & Data Sources" = appendice externe honnête |
| Vocabulaire mélangé (watchlist / league / match) | Doctrine lexicale claire par section |

### Doctrine lexicale établie en LOT 1

| Section | `.match-vs` autorisés | `.match-signal` autorisés |
|---------|----------------------|--------------------------|
| S03 Watchlist | "Under Observation" | "FTL Watchlist" |
| S04 Domestic | "National Competition", "National Championship" | "League Structure", "Cup Competition" |

---

## D. LOT 2 — Classification réelle avec données (2026-04-27)

### D1. S01 — European Competitive Layer

**Avant :** ELF Spring 2026 (London, confirmé) + 2 placeholders ("European Sixes Invitational", "European Box Cup").

**Après :**

| Carte | Statut | Source |
|-------|--------|--------|
| ELF Spring Championship 2026 — London, April 5–6 | ✓ Confirmé — **Completed** (marker ajouté) | ELF officiel |
| European Box Lacrosse Championships 2026 — Prague, June 25–Jul 4 | ✓ Confirmé | Source briefe LOT 2 |
| European Sixes Lacrosse Championships 2026 — Salou, Spain, Nov 2–18 | ✓ Confirmé — World Champs 2027 Qualification | Source briefe LOT 2 |

**Placeholders supprimés :** "European Sixes Invitational 2026", "European Box Cup 2026" — entièrement retirés du HTML.

**Note ELF Spring :** événement passé (April 5–6, aujourd'hui April 27). Conservé avec marker "Completed · April 5–6" dans `.cont-row`. Justification : événement réel continental visible cette saison.

### D2. S02 — Key Tournaments

**Avant :** 5 cartes — Amsterdam Sixes Open, French Nationals Div 1, Berlin Box Invitational, Prague Sixes Classic, Italian Cup Round 2.

**Après :** 7 cartes.

| Carte | Action | Données |
|-------|--------|---------|
| Amsterdam Sixes Open | Conservé + marqué "Completed · April 19" | Réel · date initiale confirmée |
| Aleš Hřebeský Memorial | Remplace "Prague Sixes Classic" | Réel · Box · Prague · 2026 Date TBC |
| EuroLax Sixes Cup | Ajouté | Réel · Sixes · Portugal · Date TBC |
| Berlin Open | Remplace "Berlin Box Invitational" | Réel · Box · Berlin · Date TBC |
| Frank Menschner Cup | Ajouté | Réel · Box · Prague · Date TBC |
| G6 Groningen | Ajouté | Réel · Sixes · Groningen · Date TBC |
| Alps Sixes Open | Ajouté | Réel · Sixes · Alps Region · Date TBC |
| French Nationals Div 1 | **Déplacé → S04** | — |
| Italian Cup Round 2 | **Déplacé → S04** | — |

**Placeholders structurels assumés (S02) :** 5 cartes sur 7 affichent "2026 · Date TBC" — dates 2026 non publiées au moment du lot. Les noms d'événements sont réels et annuels.

### D3. S03 — Editorial Watchlist

**Avant :** England Box League (Weekend Watch) + Ligue Nationale Field (Under Observation) — deux structures leagues clairement identifiées, mal placées en "watchlist".

**Après :** 2 signaux réellement éditoriaux.

| Carte | Statut | Nature |
|-------|--------|--------|
| Boxmania 2026 — Belgium · Box | Réel · date non publiée | Placeholder de date assumé |
| Dalmatia Lacrosse Cup — Croatia · Sixes | Réel · édition 2026 non confirmée | Événement non confirmé assumé |

**England Box League + Ligue Nationale Field déplacés → S04** (structures nationales, pas signaux watchlist).

### D4. S04 — Domestic League Tracking

**Avant :** 1 carte (Bundesliga Field).

**Après :** 8 structures, 2 types.

| Carte | Type | Pays | Lien |
|-------|------|------|------|
| England Box League | League Structure | England | country-england.html ✓ |
| Ligue Nationale Field | League Structure | France | country-france.html ✓ |
| Bundesliga Field | League Structure | Germany | country-germany.html ✓ |
| DNLL — Dutch National Lacrosse League | League Structure | Netherlands | country-netherlands.html ✓ |
| Liga Española de Lacrosse | League Structure | Spain | country-spain.html ✓ |
| Campionato Field | League Structure | Italy | country-italy.html ✓ |
| French Nationals Div 1 | Cup Competition | France | country-france.html ✓ |
| Italian Cup Round 2 | Cup Competition | Italy | country-italy.html ✓ |

**Note :** French Nationals (April 26–27) et Italian Cup (May 24) conservent leur date d'origine. Le Nationals est contemporain (April 26–27, aujourd'hui April 27). Aucune date inventée.

### D5. S05 — Results & Data Sources

Aucune modification de fond. Section conservée telle quelle (appendice externe honnête, 3 items 2025, org-cta).

### D6. S06 — Country Gateways

Aucune modification. 6 pays confirmés (England, France, Germany, Netherlands, Italy, Czech Republic).

---

## E. CSS — Ajout minimal LOT 2

| Règle ajoutée | Justification |
|---------------|---------------|
| `.match-badge-si{background:rgba(122,86,194,.15);color:var(--mauve-dk)}` | Sixes badge dans `.match-card` — utilisé en S03 (Dalmatia Lacrosse Cup) |

---

## F. Dettes restantes

| Dette | Nature | Priorité |
|-------|--------|----------|
| `tournament-detail.html` placeholder | Lien fictif — S01, S02 y pointent | Lot pages détail |
| S02 — 5 cartes "2026 · Date TBC" | Placeholder de date structurel assumé | À mettre à jour dès publication des dates |
| S03 — Dalmatia Lacrosse Cup | Événement non confirmé assumé | À vérifier avant couverture |
| S03 — Boxmania 2026 | Date non publiée | À mettre à jour dès annonce |
| ELF Spring "Men & Women" | Non vérifié formellement | Confirmation ELF |
| S05 — "External source TBC" | Sources externes non encore identifiées | Lot sources Pointbench/fédérations |
| S06 — Spain non dans Country Gateways | country-spain.html existe mais non référencé en S06 | Cohérence à évaluer si LEL devient éditoriale |
| England flag 🇬🇧 vs 🏴󠁧󠁢󠁥󠁮󠁧󠁿 | Simplification assumée | Cohérence globale |
| S05 — Paris Sixes Invitational (2025) | Nom non vérifiable formellement | Placeholder assumé |
| S05 — Milan Indoor Classic (2025) | Nom non vérifiable formellement | Placeholder assumé |

---

## G. Vérifications finales

- [x] DOM vérifié — 6 sections dans l'ordre : S01 → S02 → S03 → S04 → S05 → S06
- [x] Subnav : 6 ancres alignées avec les 6 `id` de section
- [x] S01 : 0 placeholder — 3 événements continentaux réels confirmés
- [x] S01 : C2/C3 anciens placeholders entièrement supprimés du HTML
- [x] S01 : ELF Spring marqué "Completed · April 5–6" via `.cont-row`
- [x] S02 : 7 cartes — "French Nationals" et "Italian Cup" supprimés de S02
- [x] S02 : "Berlin Box Invitational" → "Berlin Open", "Prague Sixes Classic" → "Aleš Hřebeský Memorial"
- [x] S02 : Amsterdam Sixes Open marqué "Completed · April 19"
- [x] S03 : England Box League + Ligue Nationale retirés — remplacement par Boxmania + Dalmatia
- [x] S03 : `.match-badge-si` défini en CSS et utilisé (Dalmatia Lacrosse Cup · Sixes)
- [x] S04 : 8 cartes — Bundesliga + 5 nouvelles leagues + 2 coupes nationales
- [x] S04 : intro mise à jour ("league structures, domestic rounds **and national cups**")
- [x] S04 : tous les liens vers country pages vérifiés (`country-*.html` existants)
- [x] S04 : "Cup Competition" / "National Championship" utilisés uniquement pour les cartes cups
- [x] S04 : "League Structure" / "National Competition" utilisés uniquement pour les cartes leagues
- [x] S05 : aucune modification — appendice conservé intact
- [x] S06 : aucune modification — 6 passerelles intactes
- [x] Vocabulaire doctrinal : 0 occurrence "Weekend Watch" / "Matchday Watch" / "Domestic Watch"
- [x] Vocabulaire doctrinal : "FTL Watchlist" uniquement en S03, "League Structure" uniquement en S04
- [x] CSS inline : `.match-badge-si` ajouté, aucun style orphelin créé
- [x] Aucune donnée inventée — dates inconnues → "Date TBC" assumé explicite
- [x] Mobile responsive : grilles existantes couvrent les nouveaux blocs (match-grid, tc-grid déjà responsive)

---

## H. DATA QUALITY corrective pass (2026-04-27)

### Données corrigées

| Événement | Champ | Avant | Après |
|-----------|-------|-------|-------|
| Aleš Hřebeský Memorial | Date | "2026 · Date TBC" | "Completed · April 22–25, 2026" |
| EuroLax Sixes Cup | Date + statut | "2026 · Date TBC" | "Completed · Feb 27 – Mar 1, 2026" |
| Berlin Open | Date | "2026 · Date TBC" | "July 18–19, 2026" |
| G6 Groningen | Date | "2026 · Date TBC" | "August 28–30, 2026" |
| Alps Sixes Open | Lieu | "Alps Region" | "Grenoble, France" |
| Alps Sixes Open | Date | "2026 · Date TBC" | "May 23–24, 2026" |
| Ligue Nationale Field | Nom | "Ligue Nationale Field" | "Championnat AFL Field" |

### Données supprimées (S05)

| Élément supprimé | Raison |
|-----------------|--------|
| Paris Sixes Invitational (Oct 2–4, 2025) | Événement non vérifiable |
| Milan Indoor Classic (Nov 8, 2025) | Événement non vérifiable |
| Toutes les mentions "External source TBC" | Label non informatif et non sourcé |

### Reste non corrigé (donnée inconnue — assumé honnête)

| Événement | Donnée | Statut |
|-----------|--------|--------|
| Frank Menschner Cup | Date 2026 | "Date TBC" — aucune date fournie, conservé |

### Sections touchées

- S02 Key Tournaments — 5 cartes corrigées (AHM, EuroLax, Berlin Open, G6 Groningen, Alps Sixes Open)
- S04 Domestic League Tracking — 1 renommage (D2 : Championnat AFL Field)
- S05 Results & Data Sources — 2 items supprimés, "External source TBC" retiré du dernier item

### CSS

Aucune modification.

---

## I. Historique des lots

| Lot | Date | Scope |
|-----|------|-------|
| LOT 0 — Initial | 2026-04-09 | Structure initiale, watchlist, nav, footer |
| LOT 1 V1 — Restructuration stratifiée | 2026-04-[antérieur] | 6 sections, doctrine lexicale, Country Gateways last |
| LOT 1 V2 — Purification vocabulaire | 2026-04-[antérieur] | Titres, intros, section-note appendice |
| **LOT 2 — Classification réelle** | **2026-04-27** | **S01 : 3 réels · S02 : 7 réels · S03 : 2 signaux · S04 : 8 structures** |
| **DATA QUALITY pass** | **2026-04-27** | **5 dates injectées · 1 lieu corrigé · 1 renommage · 2 faux items S05 supprimés** |
