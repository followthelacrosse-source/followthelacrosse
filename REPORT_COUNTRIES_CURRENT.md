# REPORT — Countries System
**Follow The Lacrosse · État au 2026-04-01 — Micro-passe finale appliquée**

---

## Statut global

| Page | Tier | Statut éditorial | Profil in progress retiré | Fed-badge | Liens officiels |
|------|------|-----------------|--------------------------|-----------|----------------|
| country-germany.html | Premium | Complet | ✓ | ✓ dlaxv.de | ✓ |
| country-italy.html | Premium | Complet + micro-passe | ✓ | ✓ lacrosseitalia.it | ✓ |
| country-netherlands.html | Strong Standard | Complet | ✓ | ✓ | À revalider |
| country-spain.html | Strong Standard | Complet + micro-passe | ✓ | ✓ spainlacrosse.org | À revalider |
| country-sweden.html | Strong Standard | Complet | ✓ | ✓ lacrosse.se | À revalider |
| country-czech-republic.html | Strong Standard | Complet | ✓ | ✓ lacrosse.cz | À revalider |
| countries.html | Hub | Corrigé | N/A | N/A | — |

---

## Ce qui a été fait par page

### country-germany.html
- Hero : sous-titre reformulé avec faits vérifiés (ELF 1995, Gold 2001, Box tradition)
- Fed-badge ajouté : DLaxV logo (germany.png)
- Stats bar : 1995 / 1998 / 2001 / Field·Box
- Timeline : 4 entrées réelles (1993 premier club, 1995 ELF, 1998 DLaxV, 2001 Gold + 1999/2000/2004 Silver)
- CTA : dlaxv.de (remplace about.html#contact)
- Coverage : carte auto-référentielle supprimée → 2 cartes
- CSS premium (`.cdna`) déjà présent, conservé

### country-italy.html
- Transformation complète vers structure premium (`.cdna`)
- Hero : FIGL fed-badge ajouté (italy.png)
- Stats : 40+ clubs / 2007 FIGL / 2025 Silver / Field·Sixes
- Timeline : 2004 (1er ELF) / 2007 (FIGL, Fabio Antonelli) / 2010s (clubs) / 2025 (Silver 9-8 vs Israel)
- National Teams : 2 boîtes blanches → 3 cartes sombres (Men's/Women's/Sixes)
- Correction critique : FIL → FIGL partout
- CTA : lacrosseitalia.it
- CSS complet ajouté (community-grid, coverage-grid, related-grid, wf-card, fed-badge…)

### country-netherlands.html
- "Amsterdam Open" complètement retiré (hero, DNA, stats, overview, clubs, Why Follow, interview title)
- Stage : Emerging → Established
- Identity DNA : "Sixes pioneer · ELF Silver 2008 · NLB 2003"
- Fed-badge : NLB logo (netherlands.png)
- Stats : 2003 NLB / 2008 ELF Silver / Sixes pioneer / Sixes·Field
- National Teams : 2 cartes sombres (Men's EuroLax Sixes Cup + ELF 2008 Silver / Women's)
- CSS complet ajouté
- CTA : lien federation NL (à revalider)

### country-spain.html
- Correction critique : FEL → AEL (Asociación Española de Lacrosse) partout
- Stats : 2001 / 2010 / Barcelona / Sixes·Field
- Overview : origine 2001 Madrid + AEL 2010 documentés
- Fed-badge : AEL logo (spain.jpeg)
- CTA : spainlacrosse.org
- National Teams : 2 cartes sombres
- CSS complet ajouté

### country-sweden.html
- Correction critique : SLF → SBSLF partout + note merger 2021
- Intro 1988 (Jim Johnson) ajoutée dans hero et overview
- Stats : 1988 / 1995 / University / Field·Sixes
- Fed-badge : SBSLF (sweden.png)
- CTA : lacrosse.se
- National Teams : 2 cartes sombres
- CSS complet ajouté

### country-czech-republic.html
- CSS complet ajouté (was: classes utilisées mais non définies)
- Hero : CLU fed-badge (czech-republic.jpeg)
- Stats : 1986 / 1994 (1er AHM) / 2004 (CLU) / Box·Field
- Overview : "Profile in progress" retiré ; faits vérifiés ; timeline 4 entrées
- Timeline : 1986 (intro) / 1994 (1er AHM, Hřebeský †30.11.1993) / 1995+1997 (ELF Silver) / 2004 (CLU)
- Clubs : "CLU National Programme" (faux) retiré
- National Teams : 2 cartes sombres avec ELF Silver 1995/1997
- Coverage : coverage-item → coverage-grid (2 cartes)
- Related (06) ajouté : England / Germany / Sweden
- Community : 06→07, inline → community-grid

### countries.html
- Nav : "Countries" ajouté avec class="active"
- Scene Radar : Germany ajouté ("Champions Pedigree" — Gold 2001, 3 Silvers)
- Scene Radar Italy : "Grassroots Energy" → "ELF Finalist" (Silver 2025)
- Scene Radar Netherlands : Amsterdam Open retiré → EuroLax Sixes Cup + ELF 2008 Silver
- Callout box NL : Amsterdam Open retiré
- Fed chips : LVD→DLaxV / FIL→FIGL / FEL→AEL / SLF→SBSLF
- Country cards : tous "Profile in progress" → "Full profile"
- Germany cc-hook : "ambitions to reach top 10" → "ELF Gold 2001, DLaxV national structure"
- Netherlands cc-hook : Amsterdam Open retiré → EuroLax Sixes Cup + ELF Silver 2008
- Italy cc-hook : ajout ELF Silver 2025 (9-8 vs Israel)

---

## Données retirées (invérifiables ou fausses)

| Donnée retirée | Page | Raison |
|---------------|------|--------|
| Amsterdam Open (toutes occurrences) | country-netherlands.html | Non vérifiable comme "flagship event" |
| Amsterdam Open (radar + callout) | countries.html | Idem |
| "Profile in progress" | Tous | Retiré, profils complétés |
| "long-term ranking goals" | Germany (ancienne version) | Aspirationnel non sourcé |
| "appears regularly at ELF level" | Sweden (ancienne version) | Vague non vérifié |
| "CLU National Programme" (club card) | country-czech-republic.html | N'est pas un club |
| "World-level / International standing" (stat) | country-czech-republic.html | Aspirationnel vague |
| FEL (Federación Española) | country-spain.html + countries.html | Nom incorrect — c'est AEL |
| FIL (Federazione Italiana) | country-italy.html + countries.html | Nom incorrect — c'est FIGL |
| SLF | country-sweden.html + countries.html | Fusionné dans SBSLF en 2021 |
| LVD (Lacrosse Verband Deutschland) | countries.html | Nom incorrect — c'est DLaxV |
| CTA about.html#contact | country-germany.html | Remplacé par dlaxv.de |

---

## Notes de production

- Les logos fédéraux locaux sont utilisés sur toutes les pages pays (germany.png, italy.png, netherlands.png, sweden.png, czech-republic.jpeg, spain.jpeg).
- Les liens officiels (dlaxv.de, lacrosseitalia.it, spainlacrosse.org, lacrosse.se, lacrosse.cz) n'ont pas pu être vérifiés en live — voir PENDING_REVIEW.
- Les noms de clubs sur les pages pays sont des noms de villes, pas de clubs réels nommément vérifiés — choix éditorial assumé.
- Les articles de test (interview-jonas-weber-germany.html, article-elf-spring-2026-preview.html) sont conservés comme placeholders de structure mais ne sont pas des sources factuelles.
