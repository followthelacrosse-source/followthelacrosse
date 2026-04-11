# Follow The Lacrosse — règles projet

## Langue
- Tous les prompts, plans, reports et réponses de cadrage doivent être en français.
- Les contenus du site peuvent rester en anglais si le fichier travaillé est déjà rédigé en anglais.

## Phase actuelle
- Nous sommes en phase **PRODUIT / ÉDITORIAL / UX MÉDIA**.
- Nous ne sommes pas en phase SEO, performance, accessibilité avancée, optimisation technique générale ou refactor global multi-pages.
- La priorité est la **justesse produit**, la **hiérarchie éditoriale**, la **crédibilité média** et la **cohérence de navigation**.

## Périmètre actuel
Travailler uniquement sur :
- `index.html`
- `REPORT_INDEX_HOME.md`

## Références de contexte à respecter
- `countries.html` et les pages pays déjà retravaillées constituent désormais un socle éditorial existant.
- Elles peuvent inspirer des hooks, des logiques de scènes et des exemples de pays, mais ne doivent pas être dégradées ni rouvertes dans ce lot.
- Le lot actuel concerne uniquement la **homepage**.

## Interdictions
- Ne pas rouvrir `countries.html` ni les pages `country-*`.
- Ne pas rouvrir `articles.html`, `interviews.html`, `tournaments.html`, `about.html`, `follow.html`, `whats-lacrosse.html` sauf contrainte technique absolument indispensable et explicitement signalée.
- Ne pas lancer de recherche web large sans nécessité claire.
- Ne pas utiliser les articles et interviews tests comme sources factuelles.
- Ne pas inventer de dates, résultats, clubs, structures fédérales, matchs, joueurs, compétitions ou classements.
- Ne pas refondre la homepage depuis zéro.
- Ne pas empiler de nouveaux blocs sans justification produit claire.
- Ne pas coder avant d’avoir identifié précisément :
  1. ce qui est conservé,
  2. ce qui est remplacé,
  3. ce qui est déplacé,
  4. ce qui est nettoyé.

## Principe directeur
**Follow The Lacrosse n’est pas un blog classique.**

C’est un **hub média européen**.
La homepage doit donc exprimer clairement que FTL suit :
- les pays,
- les scènes nationales,
- les clubs,
- les joueurs,
- les matchs,
- les tournois,
- les dynamiques de développement.

Toute décision de structure doit renforcer cette idée.

## Objectif produit du lot homepage
Faire monter `index.html` en niveau sur 5 axes :
1. **Rythme éditorial** : moins de pile verticale, plus de respiration et de tension visuelle.
2. **Identité hub européen** : ne pas donner l’impression que FTL suit uniquement des tournois.
3. **Navigation utile** : chaque section doit servir l’exploration du média.
4. **Crédibilité premium** : éviter tout rendu blog amateur, générique ou placeholder mal assumé.
5. **État final auditable** : HTML, CSS, JS et report doivent raconter la même vérité.

## Hiérarchie cible à respecter
La homepage doit rester dans cette logique générale :

**découverte → crédibilité → exploration → actualité → agenda/scène → navigation complémentaire → conversion**

Hiérarchie actuelle de référence :
- Hero
- Top Stories
- Explore by Country
- Scene Radar
- Latest Articles
- Section agenda / terrain / calendrier
- Explore by Format
- Where Next
- Newsletter
- Footer

Cette séquence peut être améliorée localement, mais ne doit pas être cassée sans justification forte.

## Attentes structurantes pour cette passe
### 1. Latest Articles
- La section ne doit plus fonctionner comme une simple pile verticale lourde.
- Priorité à une logique **plus horizontale**, plus média, plus respirante.
- Le scroll global de page ne doit pas devenir inutilement long.

### 2. Section agenda / terrain
- FTL ne suit pas seulement les tournois.
- La homepage doit commencer à montrer aussi des **matchs**, des **clubs** et la **vie réelle de la scène**.
- Une section mélangeant intelligemment tournois et matchs est préférable à une simple grille “Upcoming Tournaments”.
- Le CTA de section (ex. calendrier complet) doit rester **hors de la grille**.

### 3. Where Next / CYEP final
- Le placement en fin de page est pertinent.
- Le bloc doit être traité comme une **conclusion de homepage**, pas comme un menu générique.
- La microcopie doit être plus éditoriale, moins plate, moins administrative.

### 4. Newsletter
- La newsletter doit être présentée comme un **produit éditorial**, pas comme un simple formulaire standard.
- Le ton doit exprimer la promesse FTL : mieux suivre le lacrosse européen.

### 5. Fin de page
- L’enchaînement **Where Next → Newsletter → Footer** doit être fluide.
- Aucun grand vide artificiel ne doit subsister avant le footer.

## Règle factuelle
- Toute donnée sensible affichée sur la homepage doit être soit :
  - déjà validée dans le projet,
  - clairement placeholder structurel,
  - ou reformulée prudemment.
- Aucun faux dur n’est toléré.
- Si une donnée n’est pas certaine, elle doit être classée honnêtement dans le report.

## Règle sur les contenus tests
- Les articles, interviews, matchs ou cartes de démonstration servent à évaluer la structure, le rythme et la navigation.
- Ils ne doivent jamais être présentés comme des preuves factuelles implicites sans signalement dans le report.

## Règles obligatoires de modification
### Nettoyage complet
Toute section supprimée du HTML doit aussi être traitée côté CSS et JS.

Il est interdit de laisser :
- blocs morts majeurs,
- commentaires de section obsolètes,
- intitulés remplacés encore présents,
- JS lié à une section supprimée,
- styles résiduels massifs non assumés.

### Cohérence de terminologie
Tout renommage éditorial doit être propagé partout :
- titre visible,
- CTA,
- commentaires de code,
- éventuel JS,
- report.

### Cohérence DOM
Toute modification de hiérarchie doit être validée dans le DOM réel.
Vérifier systématiquement :
- fermetures de balises,
- conteneurs grid/flex,
- position exacte des CTA,
- absence de CTA accidentellement imbriqué comme item de grille.

### Cohérence produit
Chaque section doit justifier sa place.
Aucun bloc ne doit rester juste “parce qu’il existait déjà”.

### Cohérence visuelle
- Ne pas créer une homepage surchargée.
- Ne pas empiler des cartes sans hiérarchie.
- Ne pas produire un rendu “blog à l’ancienne”.
- Chercher de la tension, du rythme, de la respiration et une vraie logique média.

## Distinction obligatoire dans le report
Le report doit distinguer clairement :
- **retiré du rendu HTML**,
- **nettoyé du code**,
- **conservé comme dette technique temporaire**.

Il doit aussi classer chaque élément non final dans une des catégories suivantes :
- **placeholder structurel assumé**,
- **donnée non vérifiée**,
- **lien fictif / à remplacer**.

Aucune contradiction interne dans le report n’est acceptable.

## Méthode obligatoire
1. Lire le fichier réel.
2. Identifier ce qui est structurellement bon.
3. Identifier ce qui est faible, générique, trop long, mal hiérarchisé ou mal positionné.
4. Identifier ce qui doit être remplacé, déplacé, nettoyé.
5. Exécuter les modifications de manière ciblée.
6. Vérifier le DOM réel.
7. Mettre à jour le report de façon exacte et auditable.

## Règle d’usage Claude Code
- Répondre de façon compacte, critique, précise et exploitable.
- Ne pas lancer d’agent de recherche large au démarrage.
- Ne pas ouvrir des dizaines d’outils sans nécessité.
- Ne pas faire semblant d’avoir “presque fini” si le report n’est pas propre.
- Ne pas confondre amélioration visuelle locale et résolution produit.
- Ne pas s’auto-féliciter trop tôt : vérifier réellement le fichier final.

## Sortie attendue pour tout lot homepage
Tu dois toujours produire :
1. le fichier modifié,
2. un report clair,
3. une section **Dettes restantes**,
4. une section **Vérifications finales effectuées**.

## Vérifications finales obligatoires
Les vérifications finales doivent mentionner explicitement :
- DOM vérifié,
- sections supprimées nettoyées ou non,
- placeholders restants,
- CTA vérifiés,
- terminologie homogénéisée,
- cohérence nav / footer / newsletter,
- absence de CTA imbriqué par erreur dans une grille,
- prise en compte mobile au minimum sur les blocs modifiés.

## Standard de qualité attendu
Tu ne dois pas livrer une homepage “presque propre”.

Tu dois livrer un état :
- lisible,
- cohérent,
- critique,
- défendable,
- auditable,
- et clairement supérieur à une simple accumulation de blocs.

Le niveau attendu est celui d’un **média européen de référence**, pas d’un prototype étudiant.
