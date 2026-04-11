Follow The Lacrosse — règles projet ## Langue - Tous les prompts et toutes les réponses de cadrage doivent être en français. ## Phase actuelle - Nous sommes en phase PRODUIT / ÉDITORIAL. - Nous ne sommes pas en phase SEO, performance ou optimisation technique générale. ## Périmètre actuel Travailler uniquement sur : - countries.html - country-germany.html - country-italy.html - country-netherlands.html - country-spain.html - country-sweden.html - country-czech-republic.html Références intouchables : - country-england.html - country-france.html ## Interdictions - Ne pas rouvrir la homepage - Ne pas rouvrir articles, interviews, tournaments - Ne pas lancer de recherche web large sans validation - Ne pas utiliser les articles et interviews tests comme sources factuelles - Ne pas inventer de dates, résultats, structures fédérales, classements - Ne pas coder avant validation du plan - Ne pas supprimer Coverage ou Dynamics dans countries.html ## Règle factuelle - Toute donnée sensible doit être vérifiée sur une source officielle ou communautaire crédible. - Si une donnée n’est pas vérifiée, elle doit être retirée ou reformulée honnêtement. - Aucun faux n’est toléré sur les pages pays ou sur countries.html. ## Règle sur les contenus tests - Les articles et interviews de test servent à évaluer la structure, le rebond et la mise en page. - Ils ne doivent jamais être utilisés comme preuves factuelles. ## Logos - Les logos des fédérations sont disponibles localement dans ce dossier. - Ils doivent être utilisés s’ils sont exploitables. - À défaut, utiliser un placeholder qualifié propre, jamais une boîte grise pauvre. ## Objectif produit - Faire monter le système Countries en crédibilité, autorité et cohérence éditoriale. - Germany et Italy doivent être premium. - Netherlands, Spain, Sweden et Czech Republic doivent être strong standard, fortes et distinctes. - countries.html doit être un vrai hub éditorial profond et utile. ## Méthode obligatoire 1. Lire les fichiers locaux 2. Identifier ce qui est structurellement bon 3. Identifier ce qui est faux, flou ou non vérifié 4. Proposer un plan court de vérification factuelle 5. Attendre validation 6. Exécuter ensuite seulement ## Règle d’usage Claude Code - Ne pas lancer d’agent de recherche large au démarrage - Ne pas ouvrir des dizaines d’outils sans validation - Ne pas coder avant d’avoir trié les faits à vérifier - Répondre de façon compacte, critique, précise et exploitable

Quand tu modifies une page structurante comme index.html, tu ne dois pas faire une simple édition visuelle. Tu dois livrer un état final propre, cohérent et auditable.



Règles obligatoires

Toute section supprimée du HTML doit aussi être nettoyée dans le CSS et le JS si elle n’est plus utilisée.

Il est interdit de laisser des blocs morts du type .sponsor-bar, .cyep-\*, .sponsor-row, commentaires de section obsolètes, ou logique JS liée à des intitulés remplacés.

Toute modification de hiérarchie doit être validée au niveau du DOM réel.

Vérifie systématiquement les fermetures de balises, les conteneurs grid/flex, et la position exacte des CTA.

Un bouton de section ne doit jamais devenir accidentellement un item de grille.

Tout renommage éditorial doit être propagé partout.

Si une section passe de “By League” à “Explore by Format”, cette terminologie doit être mise à jour dans :

le titre visible

les CTA associés

les commentaires de code

le JS

le report

Le report ne doit jamais confondre suppression visuelle et nettoyage complet.

Tu dois distinguer explicitement :

retiré du rendu HTML

nettoyé du code

conservé comme dette technique temporaire

Aucune contradiction interne dans le report n’est acceptable.

Les anciennes positions, nouvelles positions, suppressions, déplacements et renommages doivent être cohérents entre toutes les sections du report.

Les placeholders restants doivent être listés avec franchise.

Chaque élément non final doit être classé dans une des trois catégories suivantes :

placeholder structurel assumé

donnée non vérifiée

lien fictif / à remplacer

Pour la homepage FTL, la logique produit prime sur l’empilement de blocs.

Chaque section doit justifier sa place dans la séquence de lecture :

découverte → crédibilité → exploration → actualité → agenda → navigation complémentaire → conversion.

Tu n’as pas le droit de livrer une homepage “presque propre”.

Avant de clôturer :

vérifie la cohérence nav / footer / CTA

vérifie qu’aucun bloc mort majeur ne reste dans le CSS

vérifie qu’aucun commentaire ou libellé ancien ne subsiste

vérifie qu’aucun CTA n’est mal imbriqué dans une grille

vérifie que le report reflète exactement l’état du fichier

Sortie attendue pour tout lot homepage



Tu dois toujours produire :



le fichier modifié

un report clair

une section “dettes restantes”

une section “vérifications finales effectuées”



Les vérifications finales doivent mentionner explicitement :



DOM vérifié

sections supprimées nettoyées ou non

placeholders restants

CTA vérifiés

terminologie homogénéisée

