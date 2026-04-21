# REPORT — Mini-lot correctif Countries

**Date** : 2026-04-13  
**Scope** : Carte D3 interactive, Landscape filtrable, newsletter + sections 05/06/07 unifiées, CSS partagé renforcé  
**Statut** : Livré

---

## Fichiers modifiés

| Fichier | Modifications |
|---------|---------------|
| `countries.html` | Carte D3 interactive (remplace ancienne map SVG+pins), Landscape filtrable, lien CSS corrigé, ancien CSS map nettoyé, JS D3+filter ajouté |
| `countries/countries.css` | Variables tier, newsletter canonique `.nl-editorial`, filtres Landscape, D3 map styles, responsive |
| `countries/country-england.html` | Newsletter et sections 05/06/07 vers composants canoniques, inline CSS dupliqué supprimé |
| `countries/country-france.html` | Idem |
| `countries/country-germany.html` | Idem |
| `countries/country-italy.html` | Newsletter inline vers `.nl-editorial`, sections 05/06/07 vers `.sh-block` |
| `countries/country-netherlands.html` | Idem Italy |
| `countries/country-spain.html` | Idem Italy |
| `countries/country-sweden.html` | Idem Italy |
| `countries/country-czech-republic.html` | Idem Italy + `.nl-editorial` panel renommé `.nl-editorial-note` (collision) |
| `countries/CLAUDE.md` | Mis à jour |

---

## A. Carte interactive

### Repris de `ftl_apps_coutries_V2.2.html`
- D3.js + TopoJSON pour SVG carte Europe
- Couleurs par tier : `{1:'#1A3A6B', 2:'#7A56C2', 3:'#B088E8'}`
- Tooltip hover (nom + tier + statut)
- Clic pays vers page FTL si live
- CDN d3 7.8.5, topojson 3.0.2
- ISO européens, légende tier

### Non repris
- Panel latéral liste nations (pas adapté au layout hub)
- Vue détail (les pages pays existent)
- Vue liste séparée (le Landscape filtre)
- Onglets Map/List/Detail
- Filtres tier sur la carte (la carte affiche tout, le Landscape filtre)

## B. Newsletter + sections 05/06/07

### Newsletter
- 8 pages utilisent `.nl-editorial` de countries.css (fond nuit gradient)
- Zéro inline newsletter restant
- Contraste et rendu identiques sur les 8 pages

### Section headers
- 8 pages x 3 sections = 24 headers convertis en `.sh-block`
- Titre 06 normalisé : "Explore Related Scenes"
- Titre 07 normalisé : "Help FTL Cover {COUNTRY}"

### CSS dupliqué supprimé
- EN, FR, DE : ~25 lignes inline pour `.coverage-grid`, `.related-grid`, `.community-grid` etc.

## C. Tier colors

```css
--tier-elite: #1A3A6B;
--tier-growth: #7A56C2;
--tier-emerging: #B088E8;
--tier-undocumented: #E0DACC;
```

Utilisées dans : carte D3, légende, filtres Landscape, dots tier heads.

---

## Dettes restantes

- ~300 lignes CSS inline identiques par page (header, nav, layout, responsive)
- CZ variantes locales inline (intentionnel)
- ~500 lignes CSS inline dans countries.html (hero, radar, cards)
- 27 pages pays à générer
- Tier colors non dans DNA strip badges

---

## Pages vérifiées visuellement

| Page | Carte | Landscape | Newsletter | Sections 05/06/07 |
|------|-------|-----------|-----------|-------------------|
| `countries.html` | D3 interactive, couleurs tier, tooltip, clic | Filtrable, Elite par défaut | OK | N/A |
| `country-england.html` | N/A | N/A | Canonique dark | sh-block |
| `country-czech-republic.html` | N/A | N/A | Canonique dark | sh-block |
| `country-netherlands.html` | N/A | N/A | Canonique dark | sh-block |
| `country-spain.html` | N/A | N/A | Canonique dark | sh-block |
