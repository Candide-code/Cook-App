# Phase 0 : Cadrage du projet

Décisions prises ensemble avant de coder. Ce qui est ici fait foi pour la v1.

**Nom de l'app : Underplate** (choisi le 2026-09-25, clin d'œil à Undertale, la référence pixel). Nom de travail avant : Petit Chef. La clé de sauvegarde garde l'ancien nom (`petit-chef-sauvegarde`) pour ne pas perdre les progressions.

## A. Fonctionnalités

### Public et objectif
- **Pour qui :** projet perso, pour moi et mes potes. Pas de publication prévue.
- **Le but :** cuisiner plus souvent et découvrir de nouvelles recettes, en vrai. L'app rend ça plus fun grâce au côté jeu (XP, niveaux, déblocages).
- **Conséquence :** le jeu est au service de la vraie cuisine. L'XP doit récompenser le fait de cuisiner pour de vrai, pas seulement de jouer.

### Support
- **Ordi et téléphone, mobile d'abord.** Le jeu doit être agréable au doigt sur un téléphone, et marcher aussi sur ordi.

### Multijoueur
- **Chacun de son côté.** Chacun joue sur son téléphone et sa progression reste enregistrée sur son appareil. Pas de serveur.
- Pour partager l'app entre potes, on la mettra en ligne à la fin (GitHub Pages par exemple).

### Recettes
- **5 à 6 recettes dans la v1.**
- **Salé et sucré** (mis à jour le 2026-09-25, avant : uniquement salé). Les 6 plats salés pour le midi ou le soir, et en sucré les **cookies** (recette perso, niveau et difficulté à fixer).
- Les 6 recettes salées de la v1, avec le niveau requis pour les débloquer :

| # | Recette | Niveau | Temps | Technique apprise |
|---|---|---|---|---|
| 1 | 🍳 Omelette au fromage | 1 | 10 min | Cuire des œufs, gérer le feu |
| 2 | 🍝 Pâtes à la sauce tomate | 1 | 20 min | Cuire des pâtes, sauce simple |
| 3 | 🥪 Croque-monsieur | 2 | 15 min | Assembler, utiliser le four |
| 4 | 🍚 Riz sauté | 3 | 20 min | Faire sauter à feu vif |
| 5 | 🍝 Carbonara (sans crème) | 4 | 20 min | Lier une sauce aux œufs |
| 6 | 🍛 Curry japonais au poulet | 5 | 45 min | Mijoter, épaissir avec un roux |
| 7 | 🍪 Cookies (sucré, recette perso, 15 cookies) | 1 | 60 min | Crémer beurre et sucre, repos au congélateur, cuisson au four |
- **Mes propres recettes (CUSTOM)** : avancé dans la v1 le 2026-09-25 (prévu en V2 au départ). Voir « Recettes custom » plus bas.

### Gameplay d'une recette
On cuisine en vrai en même temps : écran pratique avec les mains occupées (gros boutons, peu de texte, une étape à la fois).

1. **Avant de cuisiner :** liste des ingrédients et ustensiles avec les quantités, et des cases à cocher pour vérifier qu'on a tout.
2. **Pendant, une étape par écran :**
   - **Ajouter un ingrédient :** on glisse l'ingrédient dans l'ustensile à l'écran, ce qui valide l'étape.
   - **Action** (remuer, retourner…) : on tape l'ustensile à l'écran.
   - **Cuisson :** minuteur intégré (ex. « Cuire 10 min »), avec un bouton pour lancer le décompte.
3. **À la fin :** bouton « J'ai fini », XP gagnée, level up éventuel.

**Plateau d'ingrédients :** uniquement les ingrédients de la recette, pas de pièges venus d'autres plats (ex. pas de poulet dans l'omelette). Une erreur = prendre un ingrédient de la recette au mauvais moment.

**Erreurs (mauvais ingrédient) :**
- Pas de pénalité (pas de perte d'XP ni d'étoiles).
- L'écran tremble, et le téléphone vibre quand c'est possible.
- À la 3e erreur sur la même étape, un petit message indique le bon ingrédient : « Prends le/la … ».

### Règles d'XP et niveaux (logique RPG)

**Difficulté des recettes (★ à ★★★★★) et XP de base**

| ★ | ★★ | ★★★ | ★★★★ | ★★★★★ |
|---|---|---|---|---|
| 20 XP | 35 XP | 55 XP | 80 XP | 120 XP |

| Recette | Difficulté | Débloquée au niveau |
|---|---|---|
| 🍳 Omelette | ★ | 1 |
| 🍝 Pâtes tomate | ★ | 1 |
| 🥪 Croque-monsieur | ★★ | 2 |
| 🍚 Riz sauté | ★★★ | 3 |
| 🍝 Carbonara | ★★★ | 4 |
| 🍛 Curry japonais | ★★★★ | 5 |
| 🍪 Cookies | ★★ | 1 |

**Multiplicateurs**
- **Découverte ×1,5** : la première fois qu'on fait une recette.
- **Écart de niveau** (niveau du joueur − niveau de déblocage de la recette). Il ne compte **que pendant le déblocage des recettes (niveaux 1 à 5)**. Dès le niveau 6, toutes les recettes sont débloquées et le malus disparaît : refaire une omelette n'est plus puni. Les plats difficiles restent les plus rentables grâce à leur XP de base (curry 80, omelette 20).

| Écart | 0 à 1 | 2 | 3 | 4 et plus |
|---|---|---|---|---|
| XP gagnée | 100 % | 75 % | 50 % | 25 % |

`XP gagnée = arrondi(base × (découverte ? 1,5 : 1) × bonus d'écart)`, avec un bonus d'écart de 100 % dès le niveau 6

**Courbe de niveau** (revue le 2026-09-25) : +25 % par niveau jusqu'au niveau 5, puis +10 XP par niveau, plafonnée à 200 XP.

- Niveaux 1 à 5 : `XP pour passer au niveau suivant = arrondi(70 × 1,25^(niveau − 1))`
- À partir du niveau 6 : `min(171 + 10 × (niveau − 5), 200)`

| Passage | 1→2 | 2→3 | 3→4 | 4→5 | 5→6 | 6→7 | 7→8 | 8→9 et après |
|---|---|---|---|---|---|---|---|---|
| XP à gagner | 70 | 88 | 109 | 137 | 171 | 181 | 191 | 200 |

- Pas de niveau max. Au plafond, un niveau ≈ 3 repas (~61 XP par repas en moyenne) : on continue de monter régulièrement.
- Pourquoi : avec l'ancienne courbe (+25 % sans fin) et le malus d'écart permanent, un repas ne rapportait plus que ~16 XP après quelques mois, et le niveau 15 demandait ~2,5 ans. Une 1re version (plafond 250, malus figé au niveau 6) créait un « mur » vers le niveau 8 : on passait de 2 à 9 repas par niveau d'un coup.
- Objectif choisi : **niveau 100 en ~2 ans** à 3 repas par semaine (surtout pas en 6-8 mois).
- ⚠️ L'XP se gagne **par repas** : à 1 repas par jour tout va ~2,3 fois plus vite (niveau 100 ≈ 10 mois), à 2 repas par jour ~4,7 fois (≈ 5 mois).
- Rythme visé : environ 10 repas pour débloquer les 6 recettes. Chiffres à réajuster au point d'étape 2 si besoin.

**Maîtrise par recette** (plus on refait une recette, plus elle rapporte) :

| Rang | Bronze | Argent | Or | Platine |
|---|---|---|---|---|
| Recette faite | 1 fois | 5 fois | 10 fois | 20 fois |
| Bonus d'XP | +5 % | +10 % | +25 % | +50 % |
| Bordure de la carte | liseré bronze | + 4 coins pixel | + double bordure et 2 petites gemmes | + 2 grandes gemmes et reflets (pas d'animation) |

- Le bonus est celui du rang déjà atteint : il compte à partir de la fois suivante.
- Il se multiplie avec les autres : `XP gagnée = arrondi(base × découverte × bonus d'écart × bonus de rang)`.
- Quand on passe un rang, un message l'annonce en fin de recette. Le rang et la progression vers le suivant sont affichés sur l'écran de préparation.

### Ce qu'on débloque
- **Des recettes**, selon le niveau (voir tableau ci-dessus).
- **Un titre par palier de niveaux** (pas à chaque niveau), accordé selon le genre choisi dans le profil. Les paliers s'espacent : le titre suivant se mérite de plus en plus. Le titre change en fin de recette avec un message.

| Dès le niv. | Masculin | Féminin | Arrive après ~ (3 repas/semaine) |
|---|---|---|---|
| 1 | Commis | Commise | début |
| 5 | Apprenti | Apprentie | 3 semaines |
| 10 | Cuistot | Cuistote | 2 mois |
| 18 | Chef de partie | Cheffe de partie | 5 mois |
| 30 | Sous-chef | Sous-cheffe | 8 mois |
| 50 | Chef | Cheffe | 1,1 an |
| 75 | Chef étoilé | Cheffe étoilée | 1,5 an |
| 100 | Chef 1 étoile | Cheffe 1 étoile | 2 ans |
| 125 | Chef 2 étoiles | Cheffe 2 étoiles | 2,5 ans (proposé) |
| 150 | Chef 3 étoiles | Cheffe 3 étoiles | 3 ans (proposé) |
| ? | _dernière distinction, à trouver_ | | |

### Profil et personnage (« Crée ton chef »)
- **Un seul profil par téléphone**, avec un **pseudo** et un **personnage** personnalisé. Enregistré sur le téléphone avec la progression (pas de compte en ligne, pas de serveur).
- **Genre : masculin ou féminin**, choisi dans le profil. Il change les mots, pas le dessin (le corps Mana Seed est le même, et toutes les coupes, courtes comprises, sont proposées aux deux) :
  - le nom affiché : « Chef [pseudo] » ou « Cheffe [pseudo] » ;
  - les titres de niveau (tableau dans « Ce qu'on débloque ») ;
  - les accords dans les messages du jeu (« Tu te sens plus fort / forte », « Bien joué, chef / cheffe ! »…).
- **Au premier lancement**, l'écran « Crée ton chef » s'ouvre avant l'accueil. On peut le rouvrir plus tard en touchant l'avatar dans l'en-tête.
- **Base des persos : pack Mana Seed Character Base (démo gratuite)**, système « poupée de papier » : des couches superposées (corps, tenue, cheveux, chapeau). Choisi face à Super Retro World : un seul dessin de toque et de tablier marche sur toutes les combinaisons, et la licence est libre (pas de crédit obligatoire).
- **Ce qu'on personnalise :**
  - **Peau** : 11 teintes du pack.
  - **Coupe** : 5 coupes, proposées aux deux genres : **courte**, carré, chignon, **afro**, **locs** (chignon haut attaché, deux locs sur le front, une de chaque côté du visage). L'afro et les locs restent proches de la tête : sous la toque, seuls les côtés dépassent. Le carré et le chignon viennent du pack ; la courte, l'afro et les locs (absentes du pack) sont dessinées par nous, d'abord temporaires puis dans Piskel. Pas que des cheveux lisses.
  - **Couleur des cheveux** : 13 couleurs du pack, pour toutes les coupes. La courte, l'afro et les locs sont dessinées une fois dans les gris du modèle `v00`, puis recolorées avec les gammes du pack (`color ramps and v00.png`) pour avoir exactement les mêmes 13 couleurs.
  - **Couleur des yeux** : noirs, marron, bleus, verts.
  - **Toque** : oui ou non (oui par défaut).
  - La toque doit bien tenir sur l'afro (plus volumineuse) : peut-être une toque adaptée pour cette coupe.
  - **Couleur du tablier** : 5 couleurs de Sweetie 16 (rouge, orange, vert, bleu, noir). La toque et la veste restent blanches (c'est ce qui fait « chef »).
- **Tenue de chef** (toque, veste, tablier) : absente du pack. D'abord une version temporaire générée en pixels et alignée sur le corps Mana Seed, puis redessinée dans Piskel.
- **Pas d'animation pour l'instant** : on affiche seulement la pose de face, immobile.

### Recettes custom (« CUSTOM »)
Décidé le 2026-09-25. Ajouter ses propres recettes, jouables comme celles du jeu.

- **Accès** : un 3e bouton **CUSTOM** sur l'accueil, sous RECETTES et GRIMOIRE. Il ouvre le même sous-menu **SALÉ / SUCRÉ** (boutons jaunes), puis la grille de ses recettes de cette catégorie, avec un bouton **+** en haut.
- **Le + ouvre un assistant en 5 étapes**, une par écran (« Étape 2/5 », ◀ Précédent / Suivant ▶) :
  1. **Infos** : nom, difficulté ★ à ★★★★★, temps. La catégorie (salé/sucré) vient du bouton par lequel on est passé.
  2. **Ingrédients + quantité** : on choisit dans le catalogue du jeu (avec sprites), rangé **par famille** dans un sous-menu : Légumes, Fruits, Viandes, Poissons, Œufs & laitiers, Féculents, Épices & herbes, Épicerie. On touche une famille pour voir ses tuiles, ← revient aux familles ; une famille vide est grisée. La recherche (sans accents) cherche dans toutes les familles. Un ingrédient créé à la main (« Créer … dans : ◀ famille ▶ ») est rangé dans la famille choisie aux flèches (celle ouverte par défaut, sinon Légumes) : pas de famille « Mes ingrédients » à part. La quantité se règle **avec des flèches**, sans rien taper : un nombre (pas qui grandit avec la quantité : 5 g, 10 g… 50 g) et une unité (pièce, g, kg, ml, cl, L, c. à soupe, c. à café, pincée, gousse, tranche, noisette, sachet, boîte, au goût). Un ingrédient absent du jeu peut être ajouté en tapant son nom (sprite temporaire : carré + initiale).
     - **Renommer un ingrédient** : bouton ✏️ sur chaque ingrédient choisi. Le nouveau nom s’applique partout (catalogue, recettes du jeu et perso ; l’identifiant interne ne change pas, les textes des étapes non plus). Ingrédient créé : nom remplacé, vide refusé. Ingrédient du jeu : nom d’origine mémorisé, un champ vide le rétablit. Un nom déjà pris est refusé.
  3. **Ustensiles / électroménager** : même principe que les ingrédients (catalogue du jeu ou nom tapé), avec un **sous-menu par groupe** : Poêles & casseroles, Plats & moules, Bols & mesures, Petits outils, Électroménager (53 ustensiles). Un ustensile créé est rangé dans le groupe choisi aux flèches. Au moins un ustensile pour continuer.
  4. **Étapes**, ajoutées une par une, chacune avec un **type** et l'**ustensile** utilisé (parmi ceux de l'étape 3) :
     - **Ajouter** : un ingrédient choisi parmi ceux de l'étape 2 (plateau d'ingrédients en cuisine) ;
     - **Action** : texte + nombre de taps (jauge) ;
     - **Cuisson / minuteur ⏱** : texte + durée (minutes et secondes). Même minuteur que les recettes du jeu : bouton pour lancer, bip, fiable écran éteint. Sert aussi pour le four, un temps de repos…
     - **Éditeur d’étape** : tout se règle aux flèches (type, ustensile, ingrédient, action parmi 29 — Remuer, Battre, Verser, Couper, Préchauffer, Enfourner, Réchauffer, Faire revenir… —, rangées selon l’ustensile choisi : d’abord celles de l’appareil (four : Préchauffer, Enfourner… ; micro-ondes : Mettre, Réchauffer…), puis de son groupe, puis toutes les autres, nombre de taps 1 à 20, minutes et secondes), sauf la **consigne**, pré-remplie (« Ajoute : Œufs (2). », « Laisse cuire 2 min. ») et modifiable. Les étapes se réordonnent (↑ ↓), se modifient (✏️) et se suppriment (✕). Au moins une étape ; une étape qui utilise un ingrédient ou un ustensile retiré entre-temps bloque SUIVANT.
  5. **Récap** de toute la recette, puis « AJOUTER À MES RECETTES ».
- **Dans le jeu** : une recette custom se joue comme les autres (préparation, cuisine, « J'ai fini »). Toujours débloquée. Elle rapporte l'**XP de la difficulté choisie**, avec découverte et maîtrise (sur l'honneur).
- **Modifier / supprimer** depuis l'écran de préparation de la recette (suppression avec confirmation).
- **Sauvegarde** : dans la sauvegarde du téléphone, avec la progression. `?reset` les efface aussi.
- **Grimoire** : un **filtre à cases à cocher** en haut : « Mes recettes » / « Recettes du jeu ». Rien de coché ou les deux cochés = tout s'affiche ; une seule case = seulement ce groupe. Une recette custom y entre après avoir été cuisinée une 1re fois, comme les autres.

### Téléphone
- La vibration en cas d'erreur marche sur Android. Sur iPhone, l'écran tremble seulement (Safari bloque la vibration).

### Lien avec la vraie cuisine
- **Sur l'honneur.** On suit la recette en vrai en validant chaque étape dans l'app, puis on clique sur « J'ai fini » pour gagner l'XP.

## B. Design

### Ambiance
- **Pixel art 2D obligatoire** (pas de 2D contemporaine / flat design). Undertale et Fear & Hunger servent de références pour le rendu pixel, pas pour les couleurs.
- Palette limitée, police pixel, boîtes de dialogue façon RPG.

### Visuels (ingrédients, ustensiles…)
- **Pixel art**, en mélangeant des packs gratuits et des dessins faits maison.
- **Sprites en 32×32**, affichés agrandis (×2 ou ×3) avec `image-rendering: pixelated`. Exception (2026-09-25) : les **légumes et herbes sont en 16×16** (pack « 99 vegetables and herbs », licence libre), affichés à la même taille : leurs pixels sont deux fois plus gros, accepté pour avoir une licence claire et 99 légumes.
- **Gratuit autant que possible** : pack gratuit + dessins maison pour ce qui manque, plutôt qu'un pack payant.
- Pack de départ : [Pixel Art food icon pack 32x32](https://darinagrant.itch.io/pixel-art-food-icon-pack-32x32) (Darina Grant, gratuit, usage libre).
- En attendant d'avoir tous les sprites : **sprites temporaires** (carré de couleur avec l'initiale), remplacés au fur et à mesure.
- Dessins maison (ustensiles, avatar, logo) : Piskel (gratuit, navigateur) ou Aseprite.

### Police
- Police pixel Google Fonts, à tester : Press Start 2P, VT323, Pixelify Sans.
- Retenues : **Press Start 2P** pour les titres, **Pixelify Sans** pour le texte.
- Exception : le titre des boutons **SALÉ et SUCRÉ** est en **Pixelify Sans gras** (RECETTES et GRIMOIRE restent en Press Start 2P, plus beau sans accent). Press Start 2P écrase les majuscules accentuées (le É de SALÉ sortait plus petit). Attention à ce défaut pour tout futur titre en majuscules avec accent.

### Thème
- **Clair et sombre automatique**, qui suit le réglage du téléphone (variables CSS).
- **Mode clair :** palette pixel dans des tons clairs.
- **Mode sombre :** palette pixel sombre.
- **Palette v1 : Sweetie 16** (lospec.com), la même pour les deux thèmes et pour les sprites. Pourra changer plus tard.

| Rôle | Clair | Sombre |
|---|---|---|
| Fond | `#c5d1b5` (vert sauge) | `#1a1c2c` |
| Cartes / boîtes | `#f2ebd3` (crème) | `#333c57` |
| Texte | `#1a1c2c` | `#f4f4f4` |
| Texte secondaire | `#566c86` | `#94b0c2` |
| Accent (boutons) | `#ef7d57` | `#ef7d57` |
| XP / niveau | `#ffcd75` | `#ffcd75` |
| Réussite | `#38b764` | `#a7f070` |
| Erreur | `#b13e53` | `#b13e53` |

Ajusté à l'étape 4 (comparaison de 5 duos) : en thème clair, fond vert sauge `#c5d1b5` et cartes crème `#f2ebd3` (hors palette tous les deux). Le blanc en fond était trop plat, le sable jurait avec les cartes gris-bleu, le gris-bleu doux a aussi été essayé.

Les 16 couleurs de Sweetie 16 : `#1a1c2c` `#5d275d` `#b13e53` `#ef7d57` `#ffcd75` `#a7f070` `#38b764` `#257179` `#29366f` `#3b5dc9` `#41a6f6` `#73eff7` `#f4f4f4` `#94b0c2` `#566c86` `#333c57`

### Écrans de la v1 (format téléphone)

**1. Accueil** : profil en haut (avatar, niveau, titre, barre d'XP), puis la grille des recettes (sprite, nom, difficulté, nombre de fois faite, badge « NEW! »). Les recettes verrouillées sont masquées (🔒, « ??? », niveau requis).
```
┌──────────────────────────┐
│ [avatar] Niv. 3  Cuistot │
│ XP ▓▓▓▓▓▓▓░░░  78/109    │
├──────────────────────────┤
│ ┌──────────┐┌──────────┐ │
│ │ [omelette││ [pâtes]  │ │
│ │ Omelette ││ Pâtes    │ │
│ │ ★   ✓x2  ││ ★   ✓x1  │ │
│ └──────────┘└──────────┘ │
│ ┌──────────┐┌──────────┐ │
│ │  🔒      ││  🔒      │ │
│ │ ???      ││ ???      │ │
│ │ Niv. 4   ││ Niv. 5   │ │
│ └──────────┘└──────────┘ │
└──────────────────────────┘
```

**2. Préparation** : sprite du plat, temps, XP, liste des ingrédients et ustensiles à cocher, bouton « Commencer ».
```
┌──────────────────────────┐
│ ←        Omelette   ★    │
│        [sprite plat]     │
│   10 min  ·  +30 XP      │
├──────────────────────────┤
│ Ingrédients              │
│ [x] 2 oeufs              │
│ [ ] 1 noisette de beurre │
│ Ustensiles               │
│ [x] poêle  [ ] spatule   │
├──────────────────────────┤
│     [ COMMENCER ▶ ]      │
└──────────────────────────┘
```

**3. Cuisine** : une étape par écran. Progression en haut, ustensile au centre, consigne dans une boîte de dialogue façon Undertale (texte qui s'écrit lettre par lettre). En bas, selon l'étape : plateau d'ingrédients, bouton « tape pour remuer » ou minuteur.
```
┌──────────────────────────┐
│ ✕   Étape 2/6  ■■□□□□    │
├──────────────────────────┤
│     [sprite poêle]       │
├──────────────────────────┤
│ ╔══════════════════════╗ │
│ ║ * Casse 2 oeufs dans ║ │
│ ║   la poêle.          ║ │
│ ╚══════════════════════╝ │
├──────────────────────────┤
│ [oeuf][fromage][beurre]  │
│ [sel] [tomate] [lait]    │
└──────────────────────────┘
```

**4. Fin de recette** : XP gagnée, barre d'XP qui se remplit, level up et recette débloquée annoncés dans une boîte de dialogue, récap de la recette, bouton « Retour ».
```
┌──────────────────────────┐
│    ★ RECETTE TERMINÉE ★  │
│        [sprite plat]     │
│         +30 XP           │
│  XP ▓▓▓▓▓▓▓▓▓▓ → NIV. 4  │
│ ╔══════════════════════╗ │
│ ║ * Tu te sens plus    ║ │
│ ║   fort. Niveau 4 !   ║ │
│ ║ * Nouvelle recette : ║ │
│ ║   Carbonara          ║ │
│ ╚══════════════════════╝ │
│     [ RETOUR ▶ ]         │
└──────────────────────────┘
```

**Mise à jour (2026-09-25) : RECETTES ouvre un menu SALÉ / SUCRÉ** (deux gros boutons comme l'accueil, en jaune doux `#ffcd75` pour les distinguer de l'orange du menu principal), puis la grille de la catégorie choisie. Chaque ← remonte d'un cran (grille → menu salé/sucré → accueil). Une catégorie sans recette affiche « Pas encore de recette ici… bientôt ! ». Badge **NEW!** sur RECETTES (accueil) et sur SALÉ / SUCRÉ tant qu’une recette de cette catégorie est débloquée mais jamais cuisinée (même règle que le NEW! des cartes ; badge orange sur les boutons jaunes).

**Mise à jour pendant la tranche verticale : l'accueil devient un menu.** L'accueil garde le profil en haut, puis deux gros boutons : **RECETTES** (la grille décrite ci-dessus, sur son propre écran avec ←) et **GRIMOIRE**.
```
┌──────────────────────────┐
│ [avatar] Niv. 3  Cuistot │
│ XP ▓▓▓▓▓▓▓░░░  78/109    │
├──────────────────────────┤
│ ┌──────────────────────┐ │
│ │ RECETTES ▶           │ │
│ │ Choisir un plat      │ │
│ └──────────────────────┘ │
│ ┌──────────────────────┐ │
│ │ GRIMOIRE ▶           │ │
│ │ Relire les recettes  │ │
│ └──────────────────────┘ │
└──────────────────────────┘
```

**5. Grimoire** : une simple liste, comme la table des matières d'un livre. Juste le nom des recettes déjà cuisinées, « ??? » pour les autres, et le compteur de découvertes. Pas de rang, de bordure de maîtrise ni de nombre de fois : ça reste sur l'écran Recettes. On touche un nom pour ouvrir la fiche : ★, temps, ingrédients avec quantités, ustensiles, étapes, et un bouton « Cuisiner » qui mène à la préparation. Le récap de fin de recette affiche le même contenu. Quand une recette est cuisinée pour la 1re fois, un badge « NEW! » apparaît sur le bouton GRIMOIRE et sur la ligne de la recette, jusqu'à ce qu'on ouvre sa fiche.
```
┌──────────────────────────┐
│ ←  Grimoire              │
│ 1 / 6 recettes découv.   │
│ ┌──────────────────────┐ │
│ │ Omelette au fromage ▶│ │
│ └──────────────────────┘ │
│ ┌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌┐ │
│ ╎ ???                  ╎ │
│ └╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌┘ │
└──────────────────────────┘
```

**6. Crée ton chef** : le perso en grand au centre (pose de face, agrandi), puis le pseudo et une ligne par réglage avec des flèches ◀ ▶ pour faire défiler les choix. Le perso change en direct. Bouton « C'est parti » (au 1er lancement) qui mène à l'accueil.
```
┌──────────────────────────┐
│     CRÉE TON CHEF        │
├──────────────────────────┤
│                          │
│       [ perso ×4 ]       │
│                          │
├──────────────────────────┤
│ Pseudo  [ Marie_____ ]   │
│ Genre     ◀  Cheffe  ▶   │
│ Peau      ◀   3/11   ▶   │
│ Coupe     ◀  Carré   ▶   │
│ Cheveux   ◀   5/13   ▶   │
│ Yeux      ◀  Marron  ▶   │
│ Tablier   ◀  Rouge   ▶   │
│ Toque     ◀   Oui    ▶   │
├──────────────────────────┤
│     [ C'EST PARTI ▶ ]    │
└──────────────────────────┘
```

_Écrans validés pour démarrer, ajustables au point d'étape 1._

## Plus tard (hors v1)
_Les idées qui arrivent pendant le dev vont ici._
- Photo du plat pour valider une recette (bonus d'XP, galerie de ses plats)
- Classement partagé entre potes (nécessite une base de données en ligne, par exemple Supabase ou Firebase)
- Perso qui évolue avec le niveau (toque plus haute, étoile sur le tablier…)
- Perso animé (le pack Mana Seed a déjà la marche, la course et le saut : par exemple un saut de joie au level up)
- Pack Super Retro World (déjà dans `pack pixel art/characters/`) pour des personnages secondaires. Licence : crédit obligatoire des 3 auteurs et interdiction de redistribuer les fichiers, attention au dépôt GitHub public.
