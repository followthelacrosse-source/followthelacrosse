# REPORT — index.html (Homepage)
**Follow The Lacrosse · État au 2026-04-02 — Pass 6 appliquée**

---

## A. Hiérarchie finale réelle (vérifiée sur le HTML)

| # | Section | Classe HTML réelle | Background |
|---|---------|-------------------|------------|
| — | Hero | `section.hero-home` | `linear-gradient(135deg, var(--nuit) 0%, var(--marine) 100%)` |
| 01 | Top Stories | `section.s` | `var(--bg)` (#F5F3EE) |
| 02 | Explore by Country | `section.ebc-section` | `var(--ivoire)` (#F0EEE8) |
| — | Scene Radar / RTM | `section.rtm-section` | `var(--nuit)` |
| 03 | Latest Articles | `section.s.bg-white.s-accent-top` | `var(--blanc)` + border-top mauve |
| 04 | On the Ground | `section.s` | `var(--bg)` |
| 05 | Explore by Format | `section.s.bg-white` | `var(--blanc)` |
| — | Where Next | `section.cyep-section` | `var(--nuit)` |
| — | Newsletter | `div.nl-dark#newsletter` | `var(--marine)` |
| — | Footer | `footer.site-footer` | `var(--nuit)` |

---

## B. Modifications Pass 6

### 1. Nouveaux systèmes CSS

| Classe | Règle | Usage |
|--------|-------|-------|
| `.sh-dk` | Modifier de `.sh` pour fonds sombres | RTM section header |
| `.sh-dk .sh-label` | `color:rgba(255,255,255,.4)` | Label visible sur fond sombre |
| `.sh-dk .sh-title` | `color:#fff` | Titre blanc sur fond sombre |
| `.sh-dk .sh-title em` | `color:var(--mauve);font-style:normal` | Accent mauve sur fond sombre |
| `.card-stack` | `display:flex;flex-direction:column;gap:18px` | Colonne de cartes secondaires Top Stories |
| `.s-accent-top` | `border-top:3px solid var(--mauve)` | Ponctuation éditoriale Latest Articles |
| `.card-title-sm` | `font-size:17px` | Titre réduit pour cartes secondaires |

### 2. RTM section header — nettoyage structurel principal
**Avant :** `<div style="display:flex;...">` + enfants entièrement inline-stylés (font-family, font-size, letter-spacing, color, etc. — 5 attributs style sur 4 éléments).
**Après :** `<div class="sh sh-dk">` + `.sh-label` + `<h2 class="sh-title">` — structure conforme au système de sections.

### 3. Latest Articles — border-top formalisé
**Avant :** `<section class="s bg-white" style="border-top:3px solid var(--mauve)">` — inline.
**Après :** `<section class="s bg-white s-accent-top">` — classe réutilisable.

### 4. Top Stories — nettoyage side column
**Avant :** `<div style="display:flex;flex-direction:column;gap:18px;">` + `style="width:100%;height:100%;object-fit:cover;"` sur 2 images + `style="font-size:17px;;"` (double-semicolon bug) sur 2 titres + `class="cat "` (espace spurieux).
**Après :** `<div class="card-stack">` + images sans inline + `.card-title.card-title-sm` + `class="cat"`.

### 5. Inline styles redondants supprimés (replace_all)

| Pattern supprimé | Occurrences | Raison |
|-----------------|------------|--------|
| ` style="font-size:28px;margin:0;"` sur `.sh-title` | 5 | Déjà défini dans `.sh-title` CSS |
| ` style="width:100%;height:100%;object-fit:cover;"` sur `<img>` dans `.card-photo` | 12 | Déjà défini dans `.card-photo img` CSS |
| ` style="font-size:21px;"` sur `.card-title` dans s5-grid | 12 | Déjà défini dans `.card-title` CSS |

Total inline styles supprimés : 29. Aucun de ces styles ne faisait du travail utile — tous étaient des redondances exactes avec les classes CSS existantes.

---

## C. Décisions de structure assumées

### CTA doctrine — inchangée depuis Pass 5

| Section | CTA | Type | Justification |
|---------|-----|------|---------------|
| Hero | 2 boutons `.btn` | Logique hero — hors `.sh` | Section standalone |
| Top Stories (01) | Aucun | — | Section lead — Latest Articles couvre déjà `articles.html` |
| Explore by Country (02) | `see-all "All Country Profiles →"` | `.see-all` dans `.sh` | ✓ doctrine standard |
| RTM | `.btn-out-white.btn-sm "Full Radar →"` | Bouton — exception justifiée | Section sombre, `.see-all` illisible |
| Latest Articles (03) | `see-all "View All →"` | `.see-all` dans `.sh` | ✓ doctrine standard |
| On the Ground (04) | `see-all "Full Calendar →"` | `.see-all` dans `.sh` | ✓ doctrine standard |
| Explore by Format (05) | `see-all "All Articles →"` | `.see-all` dans `.sh` | ✓ doctrine standard |
| Where Next | — | Cartes CYEP | Section de sortie — CTA dans les cartes |

### Logique de destination — On the Ground (inchangée depuis Pass 5)

| Carte | Type | Destination | Logique |
|-------|------|-------------|---------|
| ELF Spring Championship | Tournament | `tournaments.html` | Événement multi-équipes → calendrier |
| Thunder LC vs Falcons LC | Club Match | `country-england.html` | Match de ligue → scène nationale |
| Berlin Box Invitational | Tournament | `tournaments.html` | Événement multi-nations → calendrier |
| Berlin LC vs München LC | Club Match | `country-germany.html` | Match de ligue → scène nationale |

Logique transitoire assumée : pas de pages match/ligue disponibles dans le projet actuel. Les pages pays sont la meilleure destination existante pour contextualiser un match de club.

---

## D. Exceptions maintenues volontairement

- **RTM CTA** : `.btn-out-white.btn-sm` au lieu de `.see-all` — section sombre, contraste nécessaire.
- **Top Stories : pas de `see-all`** — section lead, évite le doublon avec Latest Articles (même cible `articles.html`).
- **`style="margin-bottom:10px;"` sur les `.sh-label`** — override du CSS (qui a `margin-bottom:6px`). Non supprimé car c'est une valeur intentionnellement différente du défaut CSS. Suppression nécessiterait un changement CSS global potentiellement impactant d'autres pages.
- **`style="background:#FF6B35;"` et `style="color:#FF6B35;"` sur les dots RTM** — couleurs de signal spécifiques à chaque carte (orange, mauve, vert). Non factorisables sans ajouter des classes au coût disproportionné.

---

## E. Placeholders encore présents

| Élément | Statut |
|---------|--------|
| Top Stories : 3 images Unsplash, `article-detail.html` comme href principal | Placeholder structurel |
| Latest Articles : 4 images Unsplash, 2 cartes pointant vers `article-detail.html` | Placeholder structurel |
| On the Ground : ELF Spring Championship, Berlin Box Invitational | Vraisemblables mais non vérifiés |
| On the Ground : Thunder LC, Falcons LC, Berlin LC, München LC | Semi-fictifs — clubs inventés |
| Explore by Format : 12 articles (images, contenus, 9 liens `article-detail.html`) | Placeholder structurel |
| RTM France : "The win over England in October 2025" | Non audité en session pays dédiée |
| Nav : search bar | Non fonctionnelle |
| Footer : réseaux sociaux | Liens vides (`#`) |
| Footer Leagues (Field / Sixes / Box) | Pointent tous vers `articles.html` — pas de pages ligues |

---

## F. Dettes CSS résiduelles constatées

| Classe | État dans index.html | Note |
|--------|---------------------|------|
| `.hero` (ligne 80) et `.hero-inner` | En CSS, non utilisées dans index.html | Utilisées sur d'autres pages avec la classe `.hero` — partagé |
| `.hero-kicker`, `.hero-title`, `.hero-sub`, `.hero-btns` | Définies deux fois en CSS (lignes 83-88 et 334-339) | Duplication exacte — partagé multi-pages, hors périmètre |
| `.scene-teams` | En CSS, absent du HTML | Remplacé par `.scene-detail` en Pass 4 — orphelin index.html |
| `.cyep-eyebrow` | En CSS, absent du HTML | Retiré du HTML en Pass 4 — orphelin |
| `.card-sm` | En CSS, absent du HTML index.html | Potentiellement utilisé sur d'autres pages |
| `.list-item` / `.li-*` | En CSS, absent du HTML | Potentiellement utilisé sur d'autres pages |
| `.sponsor-bar` | En CSS, absent du HTML | Retiré en Pass 1 — orphelin dans index.html |
| `.radar-mini-*` | En CSS, absent du HTML index.html | Potentiellement utilisé ailleurs |
| `.ph` / `.about-2col` / `.acc-*` / `.srv-*` / `.team-*` / etc. | En CSS, absents du HTML index.html | CSS multi-pages partagé — hors périmètre |

---

## G. Vérifications finales

| Point | Résultat |
|-------|---------|
| DOM vérifié — balises ouvertes/fermées | ✓ |
| RTM header — plus d'inline styles | ✓ — `.sh.sh-dk` + `.sh-label` + `.sh-title` |
| `.sh-title` inline styles supprimés | ✓ — 0 occurrence de `style="font-size:28px;margin:0;"` dans le HTML |
| Images `.card-photo` inline styles supprimés | ✓ — 0 occurrence de `style="width:100%;height:100%;object-fit:cover;"` |
| `.card-title` font-size inline supprimés | ✓ — 0 occurrence de `style="font-size:21px;"` dans le HTML |
| Top Stories side column | ✓ — `.card-stack`, `.card-title-sm`, bug double-semicolon corrigé, espace class supprimé |
| `.s-accent-top` | ✓ — classe en CSS, appliquée sur Latest Articles |
| On the Ground — destinations inchangées | ✓ — matchs → pages pays, tournois → `tournaments.html` |
| CYEP — non touché | ✓ |
| CTA doctrine — non dégradée | ✓ |
| Hiérarchie finale | ✓ — Hero → Stories → Countries → Radar → Latest → Ground → Format → Where Next → Newsletter → Footer |
