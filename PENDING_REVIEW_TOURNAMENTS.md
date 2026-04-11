# PENDING REVIEW — tournaments.html
**Follow The Lacrosse · 2026-04-09 · État après 3 lots**

---

## 1. Éditorial à confirmer avant publication

### 1.1 S01 Continental — C2 et C3
"European Sixes Invitational 2026" et "European Box Cup 2026" sont des placeholders structurels marqués "Placeholder · Details to be confirmed". À remplacer dès que le calendrier ELF 2026 est publié.

### 1.2 ELF Spring Championship — "Men & Women"
À vérifier avec la source ELF officielle avant publication.

### 1.3 S03 League Watch — données à injecter
Les noms de ligue (England Box League, Ligue Nationale Field, Bundesliga Field) sont réels. La structure de carte est prête à recevoir des vraies fixtures. Quand les données sont disponibles : injecter clubs, rounds, dates dans `.match-fixture` et `.match-meta`. Ne pas réintroduire de clubs fictifs.

### 1.4 Formats par pays dans S04
Estimés. À vérifier avec les pages `country-*.html` existantes.

---

## 2. Previously in Europe — sources externes à identifier

Les 3 items ont un lien de repli vers leur page pays. Pas de source externe active.

**Pour activer des liens externes :** vérifier d'abord que l'URL pointe vers les résultats spécifiques de l'événement listé. Pas de liens génériques vers homepages de fédération.

**Candidats à évaluer :** Pointbench, sites ELF, FLL, ELA, DLV, FILA, LCZ.

**Format HTML à utiliser :**
```html
<a href="[URL vérifiée]" class="past-link" target="_blank" rel="noopener">Results ↗</a>
```
Remplacer alors "Country scene →" par le lien résultats. Les deux peuvent coexister.

---

## 3. Technique à compléter

### 3.1 tournament-detail.html
Toutes les cartes S01 et S02 y pointent comme placeholder. Lot dédié requis.

### 3.2 Filtrage
Subnav = navigation (ancres). Si filtrage par format/pays/mois est requis à terme, implémenter JS + `data-*` séparément.

### 3.3 Sweden et Spain
Non référencés dans S01/S02/S03 → absents de S04. Réintroduire dès qu'un événement suédois ou espagnol entre dans les sections précédentes. La règle data-driven est la condition d'entrée.

---

## 4. Lot suivant suggéré

| Lot | Périmètre | Prérequis |
|-----|-----------|-----------|
| Sources externes Previously in Europe | URLs Pointbench / fédérations | Vérification URLs événements 2025 |
| tournament-detail.html | Page tournoi réelle | Données événements confirmées |
| League Watch inject | Vraies fixtures S03 | Données ligues disponibles |
| Filtrage calendrier | JS format/pays/mois | Architecture données stables |
