# Countries Subsystem — Session Guard

**Dernière MAJ** : 2026-04-13  
**Version** : PASS A + LOT A.1bis (rangement) + LOT correctif (carte D3, Landscape filtrable, newsletter unifiée)

---

## 1. Inventaire exact des fichiers

### Pages pays (8 live) — `/countries/`
| Fichier | Tier | Fed | Statut |
|---------|------|-----|--------|
| `country-england.html` | Tier 1 | England Lacrosse | ✅ Aligné |
| `country-france.html` | Tier 1 | AFL | ✅ Aligné |
| `country-germany.html` | Tier 1 | DLaxV | ✅ Aligné |
| `country-italy.html` | Tier 1 | FIGL | ✅ Aligné |
| `country-czech-republic.html` | Tier 1 | CLU | ✅ Aligné |
| `country-netherlands.html` | Tier 2 | NLB | ✅ Aligné |
| `country-spain.html` | Tier 2 | AEL | ✅ Aligné |
| `country-sweden.html` | Tier 1 | SBSLF | ✅ Aligné |

### Hub — racine
| Fichier | Statut |
|---------|--------|
| `countries.html` | ✅ Hub live — liens vers `countries/country-*.html` |

### CSS partagé — `/countries/`
| Fichier | Statut |
|---------|--------|
| `countries.css` | ✅ Chargé par les 8 pages + template |

### Data — `/countries/_data/`
| Fichier | Statut |
|---------|--------|
| `nations.json` | ✅ 35 nations, source unique |

### Template — `/countries/_templates/`
| Fichier | Statut |
|---------|--------|
| `country-template.html` | ✅ Placeholders `{{VARIABLE}}`, nav canonique |

### Reports — `/countries/_reports/`
| Fichier | Statut |
|---------|--------|
| `REPORT_COUNTRIES_PASS_A.md` | ✅ Report PASS A |
| `REPORT_COUNTRIES_CURRENT.md` | ✅ Report courant |
| `FACT_LEDGER_COUNTRIES_CURRENT.csv` | ✅ Ledger factuel |
| `PENDING_REVIEW_COUNTRIES_CURRENT.md` | ✅ Révisions en attente |

### Archives — `/countries/_archive/`
| Fichier | Statut |
|---------|--------|
| `country-england-old.html` | Archivé |
| `country-france-old.html` | Archivé |
| `country-germany-old.html` | Archivé |

---

## 2. Doctrine Tier

| Tier | Label affiché | Compte | Live |
|------|--------------|--------|------|
| Tier 1 | Elite / Founding Nations | 9 | CZ, DE, SE, FR, IT, EN |
| Tier 2 | Growth Nations / Competitive Powers | 13 | NL, ES |
| Tier 3 | Emerging Nations | 13 | 0 |

**Format dans le DNA** : `Tier X — Label` (ex: `Tier 1 — Elite / Founding Nations`)

---

## 3. Doctrine visuelle

### Composant DNA
- Classe : `.dna-strip` (fond nuit, grille 5 colonnes)
- `.cdna` est **supprimé** — ne pas recréer
- Champs : Stage, Formats, Identity, Why it matters, Fed (avec tier label)

### CSS Architecture
- `countries.css` = styles partagés (hero, stats, dna-strip, timeline, clubs, coverage, related, community, etc.)
- Pages gardent ~380 lignes de CSS inline (header, layout, responsive) — identiques entre pages
- CZ garde des variantes locales (fed-badge, nl-editorial, coverage-card, etc.)
- `countries.html` garde ~600 lignes de CSS inline (hero, map, radar, cards) — hub-specific

### Sponsor bar
- **Supprimé** de tous les fichiers actifs (PASS A.1bis)

### Tier Color System (countries.css)
- `--tier-elite: #1A3A6B` (bleu nuit foncé)
- `--tier-growth: #7A56C2` (violet)
- `--tier-emerging: #B088E8` (lilas)
- `--tier-undocumented: #E0DACC` (beige)

### Carte interactive (hub)
- D3.js + TopoJSON — carte Europe complète cliquable
- Couleurs par tier, tooltip au hover, clic → page pays si live
- Source : logique adaptée de `ftl_apps_coutries_V2.2.html`
- CDN : d3 7.8.5 + topojson 3.0.2

### European Landscape (hub)
- 35 nations, 3 tiers filtrables via boutons Elite/Growth/Emerging
- Elite actif par défaut, un seul tier visible à la fois
- Nations live = liens cliquables, non-live = "FTL profile planned"

### Newsletter canonique
- Composant `.nl-editorial` dans countries.css (fond nuit gradient, cercle décoratif ::before)
- Classes : `.nl-ed-kicker`, `.nl-ed-title`, `.nl-ed-sub`, `.nl-ed-form`, `.nl-ed-promise`
- Utilisé par les 8 pages pays — plus aucun inline newsletter

### Section headers 05/06/07
- Utilisent `.sh-block` / `.sh-kicker` / `.sh-h2` / `.sh-sub` de countries.css
- Titres canoniques : "Latest {COUNTRY} Coverage", "Explore Related Scenes", "Help FTL Cover {COUNTRY}"

---

## 4. Nav canonique

```
Home | Articles | Tournaments | Interviews | Countries(active) | What's Lacrosse? | About | Follow Us
```

- Appliquée sur les 9 fichiers (8 pages + hub via root)
- Chemins depuis `/countries/` : toujours `../page.html`
- Chemins depuis racine : toujours `page.html`
- Pas de lien "Services" dans la nav

---

## 5. Chemins — Convention post-rangement

### Depuis une page pays (`/countries/country-xxx.html`)
| Cible | Chemin |
|-------|--------|
| Homepage | `../index.html` |
| Countries hub | `../countries.html` |
| Autre page racine | `../page.html` |
| Assets (logo, etc.) | `../assets/xxx` |
| Country pictures | `../country-pictures/xxx` |
| CSS partagé | `countries.css` (même dossier) |
| Autre page pays | `country-yyy.html` (même dossier) |

### Depuis le hub (`/countries.html`)
| Cible | Chemin |
|-------|--------|
| Page pays | `countries/country-xxx.html` |
| Autres pages racine | `page.html` |
| Assets | `assets/xxx` |
| Country pictures | `country-pictures/xxx` |

---

## 6. Règles absolues

1. **Ne jamais recréer `.cdna`** — le composant canonique est `.dna-strip`
2. **Ne jamais ajouter de sponsor-bar** — supprimé définitivement
3. **Tier labels** toujours au format `Tier X — Label`
4. **Nav canonique** identique sur toutes les pages
5. **countries.css** doit être le seul CSS partagé country-specific
6. **nations.json** est la source unique pour les 35 nations
7. **Ne pas modifier les archives** dans `_archive/`
8. **Placeholders `{{VARIABLE}}`** dans le template — pas de génération automatique implémentée
9. **"FTL profile planned"** = texte canonique pour nations non-live dans le Landscape

---

## 7. État réel actuel

### Complet
- [x] 8 pages pays alignées (CSS link, nav, .dna-strip, tier labels, CSS dédupliqué)
- [x] Hub countries.html restructuré (Scene Radar 8 cartes, European Landscape 35 nations, CSS nettoyé)
- [x] Arborescence rangée dans `/countries/`
- [x] Tous les chemins corrigés (hub → pages, pages → racine, pages → assets)
- [x] Sponsor bar supprimé
- [x] Template et data en place
- [x] Carte D3 interactive intégrée dans le hub (adaptée de ftl_apps_coutries_V2.2.html)
- [x] European Landscape filtrable (Elite/Growth/Emerging, Elite par défaut)
- [x] Newsletter unifiée sur les 8 pages (composant .nl-editorial canonique)
- [x] Section headers 05/06/07 unifiés (.sh-block canonical)
- [x] CSS inline dupliqué supprimé des PREMIUM pages (EN, FR, DE)
- [x] Tier color variables dans countries.css

### Dettes restantes
- [ ] ~300 lignes de CSS inline restantes par page (header, layout, responsive — identiques entre pages)
- [ ] CZ variantes locales gardées en inline (intentionnel)
- [ ] ~500 lignes de CSS inline dans countries.html (hub-specific — hero, radar, cards)
- [ ] 27 pages pays à générer (Tier 1 restant + Tier 2 + Tier 3)
- [ ] Tier colors non encore propagées dans DNA badges / metadata (hors newsletter et carte)

---

## 8. Checklist de reprise session

Si tu reprends ce projet dans une nouvelle session :

1. **Lis ce fichier en premier**
2. Vérifie que l'arborescence `/countries/` est intacte
3. Lis `countries.css` pour comprendre les styles partagés
4. Lis `nations.json` pour la doctrine des 35 nations
5. Lis le dernier report dans `_reports/`
6. Ne touche PAS aux fichiers hors périmètre Countries sauf si CLAUDE.md racine l'autorise
7. Respecte la doctrine tier, la nav canonique, et les conventions de chemins ci-dessus
