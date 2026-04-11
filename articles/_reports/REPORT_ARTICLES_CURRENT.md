# REPORT — articles.html · Couche 2 (état final consolidé)
**Follow The Lacrosse · 2026-04-07**

---

## A. Hiérarchie finale réelle de articles.html

```
1. <header> — nav sombre, logo, liens, newsletter CTA
2. <section class="hero-page"> — promesse éditoriale, pas de filtre
3. <section class="s bg-white"> — Featured (fixe, non filtrable)
4. <section class="s" id="latest"> — Latest Articles (filtrable)
   ├── .sh — titre "Latest Articles" + see-all
   ├── .fbar-inner — contrôles : search · country · format
   ├── .pills — filtre type éditorial
   └── .grid-3 — 6 cartes filtrables
5. <div class="nl-dark"> — newsletter
6. <footer> — footer standard
```

---

## B. Rôle de chaque bloc

| Bloc | Rôle |
|------|------|
| hero-page | Promesse éditoriale de la newsroom. Pas de contrôle. |
| Featured (section.s.bg-white) | Sélection éditoriale fixe. Non pilotée par les filtres. |
| Latest (section.s#latest) | Flux exploratoire. 100% filtrable. |
| .fbar-inner dans Latest | Contrôles search/country/format — scope Latest uniquement |
| .pills dans Latest | Filtre par type éditorial — scope Latest uniquement |
| .nl-dark | Newsletter "The European Lacrosse Briefing" |

---

## C. Ce qui est éditorial fixe

- **Featured section** : 3 cartes (F1 card-feat + F2/F3 dans .card-stack)
- F1/F2/F3 ont des `data-*` pour cohérence DOM mais sont **hors scope JS** grâce au sélecteur `#latest .card[data-country]`
- Aucun filtre — search, country, format, type — ne les touche

---

## D. Ce qui est exploratoire filtrable

- **Latest grid** : 6 cartes (G1–G6) dans `section#latest .grid-3`
- 4 dimensions de filtrage :
  1. **Country** — `data-country` vs select `#art-country`
  2. **Format** — `data-fmt` vs select `#art-league` (label "All Formats")
  3. **Search** — texte libre sur `.textContent` de chaque carte
  4. **Type éditorial** — `data-type` vs pills `.pill[data-filter-type]`
- Règle spéciale : `data-fmt="general"` → visible quel que soit le filtre format actif

---

## E. Décisions fermes prises sur les filtres

| Décision | État |
|----------|------|
| Select genre supprimé | ✓ HTML et JS nettoyés |
| "All Leagues" → "All Formats" | ✓ `<option value="">All Formats</option>` |
| `.fbar` externe supprimé | ✓ plus entre hero et Featured |
| Filtres déplacés dans `#latest` | ✓ fbar-inner après .sh, avant pills |
| Ordre dans Latest : sh → filtres → pills → grid | ✓ |
| CSS `.fbar` orphelin supprimé | ✓ (`.fbar-inner` conservé) |

---

## F. Corrections JS exactes

**Avant :**
```js
var cards = document.querySelectorAll('.card[data-country]'); // toute la page
var genderEl = document.getElementById('art-gender');
var gender = genderEl ? genderEl.value.toLowerCase() : '';
var cardGender = (card.dataset.gender || '').toLowerCase();
var matchGender = !gender || cardGender === gender;
if (matchCountry && matchLeague && matchGender && matchSearch && matchType)
if (genderEl) genderEl.addEventListener('change', filterCards);
```

**Après :**
```js
var cards = document.querySelectorAll('#latest .card[data-country]'); // Latest uniquement
// genderEl, gender, cardGender, matchGender : supprimés
if (matchCountry && matchLeague && matchSearch && matchType)
// listener genderEl : supprimé
```

**Logique finale — 4 dimensions AND :**
```
matchCountry = !country || cardCountry === country
matchLeague  = !league  || cardFmt === league || cardFmt === 'general'
matchSearch  = !search  || cardText.indexOf(search) !== -1
matchType    = activeType === 'all' || cardType === activeType
```

---

## G. Exceptions maintenues volontairement

- `data-gender` sur les cartes F1/F2/F3 et G1–G6 : conservé comme métadonnée éditoriale, non filtré en surface
- `article-detail.html` dans `articles/` : placeholder structurel conservé
- `interview-sophie-laurent-france.html` (lien G6) : fichier fictif, assumé comme dette

---

## H. Harmonisation des articles — état cumulé

### H1. fts-block (lot précédent)

**Avant :**
- `article-detail.html` avait un bloc `fts-block` — 7 étapes
- Les 5 autres articles avaient le CSS fts-block mais aucun HTML

**Après :**
- Les 6 articles ont maintenant un bloc `fts-block` actif
- article-detail.html : 7 étapes (You are here / France / England / Field guide / Interview / Tournament / Countries)
- 4 autres articles (england-box, sixes-rome, berlin, elf) : 4 étapes (You are here / Country / Format guide / Countries)
- article-olympic : 3 étapes (You are here / Sixes guide / Countries) — pas de pays unique

**Écart résiduel assumé :**
- article-detail.html a des liens vers interview-detail.html et tournament-detail.html (placeholders)
- Les autres articles n'ont pas de step "Interview" ni "Tournament" (pages inexistantes)

### H2. Harmonisation head + art-context-box (lot couche 2 — 2026-04-07)

**Avant :**
- 5 articles avaient un `<br>` invalide dans leur `<title>`
- 5 articles n'avaient pas de `<meta name="description">`
- 5 articles avaient le CSS `art-context-box` mais aucun HTML

**Après :**
- `<br>` supprimé des 5 titres — titre propre sur une ligne
- `<meta name="description">` ajouté aux 5 articles — contenu dérivé du art-hero-deck
- `art-context-box` HTML ajouté aux 5 articles — positionné avant `<div class="art-quote">`

| Article | Context box — thème |
|---------|---------------------|
| england-box | England's National Box League |
| sixes-rome | Italy and the Sixes format |
| berlin-clubs | Germany's club scene: building depth |
| elf-spring | The ELF Spring Championship |
| olympic-2028 | Sixes lacrosse at Los Angeles 2028 |

**Contenu art-context-box :** éditorial, sans statistiques inventées, cohérent avec le corps de l'article.

---

## I. Placeholders encore présents

| Élément | Fichier | Type |
|---------|---------|------|
| href="articles/article-detail.html" | articles.html (F1, see-all) | Placeholder fictif |
| href="interview-sophie-laurent-france.html" (G6) | articles.html | Lien fictif |
| href="../interview-detail.html" (fts step 5) | article-detail.html | Lien fictif |
| href="../tournament-detail.html" (fts step 6) | article-detail.html | Lien fictif |
| Images Unsplash — toutes | tous articles | Placeholders visuels |
| Auteurs fictifs (Alex Dupont, Giulia Rossi, etc.) | tous articles | Données non vérifiées |

---

## J. Dettes résiduelles

| Dette | Fichiers concernés | Priorité |
|-------|-------------------|----------|
| country-*.html ont encore `href="article-*.html"` racine | country-*.html | Lot countries |
| tournament-detail.html a encore `href="article-*.html"` racine | tournament-detail.html | Lot tournaments |
| interview-detail.html n'existe pas | article-detail.html (fts) | Lot interviews |
| tournament-detail.html placeholder | article-detail.html (fts) | Lot tournaments |
| article-detail.html contenu générique | articles.html (F1) | Éditorial Couche 3 |

---

## K. Vérifications finales

- [x] Featured non impacté par les filtres — sélecteur JS `#latest .card[data-country]`
- [x] Latest seul impacté — scope vérifié dans le JS final
- [x] Select genre disparu — 0 occurrence `art-gender`, `genderEl`, `All Genders`
- [x] "All Leagues" n'existe plus — 0 occurrence dans articles.html
- [x] "All Formats" en place — `<option value="">All Formats</option>` à la ligne 409
- [x] Recherche scope Latest uniquement — `searchEl` lié à `filterCards()` sur `#latest`
- [x] `.fbar` externe supprimé — hero → Featured sans intermédiaire
- [x] Filtres visuellement dans Latest — `.fbar-inner` après `.sh`, avant `.pills`
- [x] `fts-block` présent dans les 6 articles — vérifié grep
- [x] 0 badge `<span class="tf">` vide
- [x] 0 `nl-strip` résiduel
- [x] 0 `sponsor-bar` résiduel
- [x] Aucun faux compteur, aucun badge social inventé
- [x] CSS `.fbar` orphelin supprimé
- [x] `<br>` supprimé des 5 titres article — 0 occurrence `<title>` avec `<br>`
- [x] `<meta name="description">` présent dans les 6 articles — vérifié grep
- [x] `art-context-box` HTML présent dans les 6 articles — 42 occurrences, 7 par fichier
- [x] Contenu art-context-box : éditorial, aucune statistique inventée
- [x] report cohérent avec le code

---

## L. Hiérarchie éditoriale assumée

| Niveau | Fichier | Sidebar | fts-steps | Justification |
|--------|---------|---------|-----------|---------------|
| **PREMIUM** | `article-detail.html` | 4 blocs (Article Info, Scene Context, Upcoming, Newsletter sidebar) | 4 (avec liens France + England) | Page de référence, match report bilatéral, plus dense intentionnellement |
| **STRONG** | `article-england-box-goalie-duel.html` | 2 blocs (Article Info, Browse More) | 4 (Box/England) | Match report scène nationale |
| **STRONG** | `article-elf-spring-2026-preview.html` | 2 blocs | 4 (Field/England) | Preview compétition |
| **STRONG** | `article-berlin-clubs-transition.html` | 2 blocs | 4 (Field/Germany) | Feature scène nationale |
| **STRONG** | `article-sixes-rome-italy.html` | 2 blocs | 4 (Sixes/Italy) | Scene report national |
| **PAN-EUROPE** | `article-olympic-lacrosse-2028-europe.html` | 2 blocs (Article Info, Browse More) | 3 (sans référence pays) | Analyse transversale continentale |

**Doctrine** : moins dense que PREMIUM = choix éditorial assumé. Moins pertinent = non acceptable.
Les 4 STRONG ont chacun une sidebar cohérente avec leur sujet (pays, format, catégorie).
L'article PAN-EUROPE ne référence aucun pays spécifique dans ses métadonnées ni dans ses steps.

---

## M. Corrections sémantiques et techniques (mini-lot verrouillage 2026-04-08)

### M1. Corrections sémantiques — article-olympic-lacrosse-2028-europe.html

**Problème :** Europe (continent) était présenté avec la logique d'un country profile.

| Emplacement | Avant | Après |
|-------------|-------|-------|
| Sidebar Article Info — label | `Country` | `Coverage` |
| Sidebar Browse More — description | `Country profile →` | `European Scene →` |

**Périmètre audité entièrement :** hero tag, byline, Article Info, Browse More, fts-block (3 steps), art-related cards, art-community. Résultat : seules ces 2 formulations étaient impropres. Les related cards vers Netherlands et Spain sont éditorialement justifiées (mentionnées dans l'article comme nations les mieux positionnées). Les fts-steps ne contenaient pas de référence pays.

**Vérification finale :**
- 0 occurrence `Country profile` dans article-olympic → confirmé grep
- 0 occurrence `art-meta-label.*Country` dans article-olympic → confirmé grep
- Label `Coverage` en place ligne 686 → confirmé grep

### M2. Déduplication JS — progress bar

**Problème :** Le handler `window.addEventListener('scroll', ...)` de la progress bar était défini deux fois consécutivement dans 5 des 6 articles.

| Fichier | Avant | Après |
|---------|-------|-------|
| `article-england-box-goalie-duel.html` | 2× bloc progressBar | 1× bloc progressBar |
| `article-elf-spring-2026-preview.html` | 2× bloc progressBar | 1× bloc progressBar |
| `article-berlin-clubs-transition.html` | 2× bloc progressBar | 1× bloc progressBar |
| `article-sixes-rome-italy.html` | 2× bloc progressBar | 1× bloc progressBar |
| `article-olympic-lacrosse-2028-europe.html` | 2× bloc progressBar | 1× bloc progressBar |
| `article-detail.html` | 1× bloc progressBar | inchangé (déjà propre) |

**Vérification finale :** grep `progressBar` → 3 occurrences par fichier dans les 6 articles = exactement 1 bloc fonctionnel (`getElementById` + `addEventListener` + `.style.width`). Confirmé.

### M3. Inline styles — décision assumée

Audit complet effectué sur les 6 fichiers. Les inline styles présents sont conservés car :
- `border:1px solid var(--border)` sur `.art-share-btn` = surcharge contextuelle intentionnelle (dark bg hero vs light bg body — différent du CSS)
- Layouts flex inline dans la sidebar = répétitifs mais supprimer nécessiterait de nouvelles classes CSS (hors périmètre)
- Font-size exceptions = overrides intentionnels

**Décision : pas de purge dogmatique.** Aucun inline style supprimé dans ce lot.

---

## N. Vérifications finales du mini-lot verrouillage

- [x] Europe n'est plus labelisé "Country" dans article-olympic — 0 occurrence `art-meta-label.*Country`
- [x] "Country profile" disparu de article-olympic — 0 occurrence grep confirmée
- [x] Progress bar JS : exactement 3 occurrences `progressBar` par fichier × 6 fichiers = 18 total
- [x] article-detail.html reste PREMIUM — aucune modification de structure
- [x] Les 4 STRONG restent STRONG — aucune modification de structure
- [x] article-olympic PAN-EUROPE : aucune ambiguïté pays/continent restante dans le body visible
- [x] Inline styles : conservés intentionnellement, pas de chantier CSS ouvert
- [x] Aucun lien existant cassé
- [x] Périmètre strict respecté — articles.html et index.html non touchés
