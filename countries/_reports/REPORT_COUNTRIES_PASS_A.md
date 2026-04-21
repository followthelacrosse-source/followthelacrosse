# REPORT — Countries PASS A + LOT A.1bis

**Date** : 2026-04-12  
**Scope** : Unification du système Countries + rangement structurel + sponsor bar removal  
**Statut** : ✅ Complet

---

## 1. Livrables

| Fichier | Emplacement | Action | Statut |
|---------|-------------|--------|--------|
| `countries.css` | `/countries/` | Créé — CSS partagé extrait de 8 pages | ✅ |
| `nations.json` | `/countries/_data/` | Créé — 35 nations, source unique | ✅ |
| `country-template.html` | `/countries/_templates/` | Créé — template canonique pour génération future | ✅ |
| `CLAUDE.md` | `/countries/` | Créé — session guard avec doctrine complète | ✅ |
| `country-england-old.html` | `/countries/_archive/` | Archivé | ✅ |
| `country-france-old.html` | `/countries/_archive/` | Archivé | ✅ |
| `country-germany-old.html` | `/countries/_archive/` | Archivé | ✅ |
| Reports (4 fichiers) | `/countries/_reports/` | Déplacés depuis racine | ✅ |

## 2. LOT A.1bis — Rangement structurel

### Déplacements effectués
- 8 pages `country-*.html` : racine → `/countries/`
- `countries.css` : racine → `/countries/`
- `_archive/` : racine → `/countries/_archive/`
- Reports Countries : racine → `/countries/_reports/`

### Chemins corrigés
- **countries.html** (hub, reste à la racine) : `country-*.html` → `countries/country-*.html` (48 occurrences)
- **8 pages pays** : toutes les refs racine préfixées `../` (nav, footer, assets, country-pictures)
- **Template** : mêmes corrections de chemins que les pages pays
- Les liens inter-pays restent relatifs (même dossier) : `country-yyy.html`

### Sponsor bar
- **Supprimé** du HTML de : 8 pages pays + countries.html + template
- **Supprimé** du CSS inline de : 8 pages pays + template
- Les fichiers `_archive/` conservent l'ancien code (non touchés)

## 3. Pages pays — Migration .cdna → .dna-strip

| Page | CSS link | Nav | .dna-strip | Tier label | CSS dédupliqué | Sponsor bar |
|------|---------|-----|------------|------------|---------------|-------------|
| country-england.html | ✅ | ✅ | ✅ | Tier 1 | ✅ | ✅ Supprimé |
| country-france.html | ✅ | ✅ | ✅ | Tier 1 | ✅ | ✅ Supprimé |
| country-germany.html | ✅ | ✅ | ✅ | Tier 1 | ✅ | ✅ Supprimé |
| country-italy.html | ✅ | ✅ | ✅ (ajouté) | Tier 1 | ✅ | ✅ Supprimé |
| country-czech-republic.html | ✅ | ✅ | ✅ | Tier 1 | ✅ | ✅ Supprimé |
| country-netherlands.html | ✅ | ✅ | ✅ | Tier 2 | ✅ | ✅ Supprimé |
| country-spain.html | ✅ | ✅ | ✅ | Tier 2 | ✅ | ✅ Supprimé |
| country-sweden.html | ✅ | ✅ | ✅ | Tier 1 | ✅ | ✅ Supprimé |

## 4. countries.html hub — Restructuration

### Ajouté (PASS A)
- **Sweden dans Scene Radar** : 8e carte (Founding Depth)
- **European Landscape section** : 35 nations, 3 tiers, format compact
- **"Your Country" CTA** sorti de la grille

### Corrigé (PASS A)
- Double `radar-subtitle`, orphan WHY WE'RE WATCHING, triple `map-section::before`, CSS cassé, `@media` vides, `.dna-strip` CSS inline dupliqué

### Corrigé (LOT A.1bis)
- Tous les liens pays préfixés `countries/`
- Sponsor bar supprimé

## 5. Doctrine Tier

| Tier | Label | Nations | Live |
|------|-------|---------|------|
| Tier 1 | Elite / Founding Nations | 9 | CZ, DE, SE, FR, IT, EN |
| Tier 2 | Growth Nations / Competitive Powers | 13 | NL, ES |
| Tier 3 | Emerging Nations | 13 | 0 |

## 6. Arborescence finale

```
/                           ← racine du site
├── countries.html          ← hub (liens vers countries/country-*.html)
├── country-pictures/       ← images des fédérations
├── assets/                 ← logo, etc.
└── countries/
    ├── CLAUDE.md           ← session guard
    ├── countries.css       ← CSS partagé
    ├── country-england.html
    ├── country-france.html
    ├── country-germany.html
    ├── country-italy.html
    ├── country-czech-republic.html
    ├── country-netherlands.html
    ├── country-spain.html
    ├── country-sweden.html
    ├── _data/
    │   └── nations.json
    ├── _templates/
    │   └── country-template.html
    ├── _reports/
    │   ├── REPORT_COUNTRIES_PASS_A.md
    │   ├── REPORT_COUNTRIES_CURRENT.md
    │   ├── FACT_LEDGER_COUNTRIES_CURRENT.csv
    │   └── PENDING_REVIEW_COUNTRIES_CURRENT.md
    └── _archive/
        ├── country-england-old.html
        ├── country-france-old.html
        └── country-germany-old.html
```

## 7. Dettes restantes

### CSS
- **Pages pays gardent ~380 lignes de CSS inline** (header, layout, responsive) identiques entre pages
- **CZ garde des variantes locales** de composants spécifiques
- **countries.html garde ~600 lignes de CSS inline** (hub-specific)

### Contenu
- **nations.json** : champs `highlights`, `todo`, `note` sont des placeholders éditoriaux non affichés
- **Fed abbreviations** : certaines à vérifier (ex: SBSLF pour Suède)

### Pages
- **27 pages pays à générer** (Tier 1 restant : DK, PL, CH + 13 Tier 2 + 13 Tier 3)
- **country-template.html** : placeholders `{{VARIABLE}}`, pas de génération automatique

### Visuel (LOT A.1bis non terminé)
- Carte interactive non intégrée depuis ftl_apps_coutries_V2.2.html
- European Landscape non filtrable
- Sections 05/06/07 + newsletter non homogénéisées
- Système de couleurs tier non implémenté

## 8. Placeholders structurels assumés

- Statistiques hero countries.html (30+ ELF nations, 150+ years, 3 formats)
- Articles / coverage cards dans les pages pays (liens test)
- Map SVG (`assets/europe_map_ftl.svg`) — asset externe non vérifié

## 9. Données non vérifiées

- SBSLF comme abréviation actuelle de la fédération suédoise
- Nombre exact de clubs pour certains pays dans nations.json
- Certains pourcentages ELF dans nations.json
- Dates de fondation de fédérations Tier 2/3

## 10. Vérifications finales effectuées

- ✅ **Arborescence** : tous les fichiers dans `/countries/` (8 pages, CSS, data, templates, reports, archives)
- ✅ **Chemins hub** : 48 liens `countries/country-*.html` dans countries.html
- ✅ **Chemins pays** : toutes les refs racine préfixées `../` (nav, footer, assets, country-pictures)
- ✅ **Chemins inter-pays** : relatifs (même dossier)
- ✅ **CSS link** : `countries.css` accessible depuis même dossier
- ✅ **Sponsor bar** : supprimé de tous les fichiers actifs (10 fichiers)
- ✅ **Session guard** : `countries/CLAUDE.md` créé avec doctrine complète
- ✅ **DOM vérifié** (PASS A) : sections ouvrent/ferment correctement
- ✅ **`.cdna` grep = 0 code actif** (2 commentaires FR/DE uniquement)
- ✅ **Nav canonique** : 9 fichiers
- ✅ **Tier labels** : 8 pages pays
- ✅ **Scene Radar** : 8 cartes
- ✅ **European Landscape** : 35 nations, 3 tiers, 8 live links
- ✅ **Template** : chemins corrigés, sponsor bar supprimé
- ✅ **Archives** : 3 fichiers dans `/countries/_archive/` (non touchés)
