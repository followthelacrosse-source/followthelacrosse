# REPORT — LOT COHÉRENCE HIÉRARCHIQUE

**Date** : 2026-04-22  
**Scope** : Recalibration tier sur 3 pages pays (NL → Tier 1 full, SE → Tier 2 label, CZ → sortie hybride)  
**Commit** : `438abc3`  
**Statut** : Livré

---

## Fichiers modifiés

| Fichier | Modifications |
|---------|---------------|
| `countries/country-netherlands.html` | DNA label Tier 2 → Tier 1 · Section 01 key facts box → timeline 6 étapes · Section 03 grille 2 → 3 colonnes + carte mauve "Sixes Pioneer" |
| `countries/country-sweden.html` | DNA label Tier 1 → Tier 2 (label uniquement — structure déjà conforme Tier 2) |
| `countries/country-czech-republic.html` | Section 01 : bloc `nl-editorial-note` supprimé · container prose reformaté (max-width:680px) · timeline enrichi 4 → 6 étapes |

---

## A. Netherlands — Tier 1 / PREMIUM (upgrade complet)

### Ce qui a été fait
- **DNA label** : `Tier 2 — Growth Nations / Competitive Powers` → `Tier 1 — Elite / Founding Nations`
- **Section 01 droite** : key facts box inline supprimé → remplacé par `.timeline` 6 étapes (classe countries.css, aucun CSS ajouté)
  - 2003 : NLB Founded
  - 2008 : ELF Championship Silver
  - 2010s : Sixes Infrastructure Built
  - EuroLax Cup : Sixes Cup Won in Overtime
  - 2024 : Olympic Sixes Cycle
  - 2025–26 : NLB Active — Multi-City Scene
- **Section 03** : `repeat(2,1fr)` → `repeat(3,1fr)` · carte mauve "Sixes Pioneer" ajoutée en 3e position
- **Why Follow** : conservé (3 arguments déjà solides — Sixes Cup, reference scene, fédération 20 ans)

### Placeholders structurels assumés
- Étape "2010s" : approximation de période sans date exacte confirmée dans nations.json
- Étape "EuroLax Cup" : sans année (date non confirmée dans nations.json) — **donnée non vérifiée pour l'année**
- Étape "2024" : référence au cycle olympique LA28, pas à un événement spécifique NL

### Données confirmées utilisées
- NLB fondé 2003 ✓
- ELF Silver 2008 ✓
- EuroLax Sixes Cup gagnée (OT) ✓
- Villes actives : Amsterdam, Rotterdam, The Hague, Utrecht ✓

---

## B. Sweden — Tier 2 / STRONG (recalibration label)

### Ce qui a été fait
- **DNA label** : `Tier 1 — Elite / Founding Nations` → `Tier 2 — Growth Nations / Competitive Powers`

### Ce qui a été conservé (conforme Tier 2)
- Section 01 droite : key facts box (correct pour Tier 2)
- Section 03 : `repeat(2,1fr)`, 2 cartes (correct pour Tier 2)
- Pip Stage : `#FFD166` "Consistent" — laissé en l'état (cohérent avec la réalité suédoise)
- Why Follow : 3 arguments (correct)

### Note
Sweden est un ELF founding member 1995. Le label Tier 2 peut sembler en tension avec ce statut historique. Cependant, la scène suédoise n'a pas de résultats de compétition comparables à England, France, Germany, Czech Republic — le Tier 2 est le positionnement produit juste. À signaler si révision de doctrine tier est envisagée.

---

## C. Czech Republic — Tier 1 hybride → pure PREMIUM

### Ce qui a été fait
- **Section 01** : bloc `nl-editorial-note` ("Scene at a glance") entièrement supprimé
- **Grid container** : `grid-template-columns:1fr 1fr` → `max-width:680px` (prose pleine largeur sans colonne fantôme)
- **Timeline** : enrichi de 4 → 6 étapes
  - Conservées : 1986, 1994, 1995·1997, 2004
  - Ajoutées : "2000s–2010s AHM Goes International" (structurel assumé), "2025 AHM 32nd Edition — Record Scale" (confirmé : 24 équipes, 19 pays)
- **Section 03** : conservée (3 cartes, grille `repeat(3,1fr)`, carte mauve "European Box Capital" — déjà en place)

### Données confirmées utilisées
- 1986 introduction ✓
- 1994 premier AHM ✓
- Aleš Hřebeský décédé 30 novembre 1993 ✓
- 1995 ELF founding member + Silver (hôte) ✓
- 1997 Silver ✓
- 2004 CLU fondé 12 mai ✓
- 2025 AHM 32e édition : 24 équipes, 19 pays ✓

### Placeholders structurels assumés
- "2000s–2010s" : période générale sans date précise confirmée — **placeholder structurel**

---

## Doctrine tier — État après ce lot

| Page | Tier actuel | Structure Section 01 | Section 03 grille | DNA label |
|------|-------------|---------------------|-------------------|-----------|
| `country-england.html` | Tier 1 | Timeline | repeat(3,1fr) | Elite / Founding Nations |
| `country-france.html` | Tier 1 | Timeline | repeat(3,1fr) | Elite / Founding Nations |
| `country-germany.html` | Tier 1 | Timeline | repeat(3,1fr) | Elite / Founding Nations |
| `country-italy.html` | Tier 1 | Timeline | repeat(3,1fr) | Elite / Founding Nations |
| `country-czech-republic.html` | Tier 1 | Timeline seul (6 étapes) | repeat(3,1fr) | Elite / Founding Nations |
| `country-netherlands.html` | **Tier 1** | **Timeline (6 étapes)** | **repeat(3,1fr)** | **Elite / Founding Nations** |
| `country-switzerland.html` | Tier 1 | Timeline (6 étapes) | repeat(3,1fr) | Elite / Founding Nations |
| `country-denmark.html` | Tier 1 | Timeline (6 étapes) | repeat(3,1fr) | Elite / Founding Nations |
| `country-poland.html` | Tier 1 | Timeline (6 étapes) | repeat(3,1fr) | Elite / Founding Nations |
| `country-spain.html` | Tier 2 | Key facts box | repeat(2,1fr) | Growth Nations / Competitive Powers |
| `country-sweden.html` | **Tier 2** | Key facts box | repeat(2,1fr) | **Growth Nations / Competitive Powers** |

---

## Dettes restantes

| Dette | Nature | Priorité |
|-------|--------|----------|
| Année exacte EuroLax Sixes Cup (NL) | Donnée non vérifiée | À confirmer dans nations.json si disponible |
| "2010s" NL Sixes investment | Placeholder structurel assumé | Acceptable |
| "2000s–2010s" CZ AHM international | Placeholder structurel assumé | Acceptable |
| Sweden Tier 2 vs founding nation 1995 | Tension potentielle doctrine | À surveiller |
| ~300 lignes CSS inline par page | Dette technique non prioritaire | Hors périmètre |
| 27 pages pays à générer | Hors lot | Hors périmètre |

---

## Vérifications finales effectuées

- [x] DOM vérifié sur les 3 fichiers
- [x] NL Section 01 : grid 2 colonnes (prose + timeline) correctement fermée
- [x] NL Section 03 : grid `repeat(3,1fr)` avec 3 enfants, CTA hors grille
- [x] CZ Section 01 : `nl-editorial-note` retiré, prose pleine largeur, timeline seul
- [x] CZ Section 01 : grid fantôme corrigé (`max-width:680px`)
- [x] SE DNA label : seul changement, aucune section altérée
- [x] Terminologie homogène : "Tier 1 — Elite / Founding Nations" / "Tier 2 — Growth Nations / Competitive Powers"
- [x] Aucun CTA accidentellement imbriqué dans une grille
- [x] Aucun bloc mort, aucun commentaire obsolète
- [x] `.timeline` utilisé sans nouveau CSS inline (classes existantes de countries.css)
- [x] countries.css non modifié
- [x] nations.json non modifié
- [x] Données inventées : zéro — placeholders assumés signalés ci-dessus

---

## Historique des lots antérieurs

| Lot | Commit | Date | Scope |
|-----|--------|------|-------|
| Mini-lot correctif (Carte D3, Landscape, newsletter) | — | 2026-04-13 | countries.html, CSS, 8 pages |
| LOT PREMIUM (CH, DK, PL → Tier 1, NL/CZ light audit) | `7a460e1` | 2026-04-21 | 3 nouvelles PREMIUM pages |
| LOT COHÉRENCE HIÉRARCHIQUE | `438abc3` | 2026-04-22 | NL Tier 1 full, SE Tier 2, CZ hybride fix |
