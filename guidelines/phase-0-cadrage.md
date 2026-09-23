# Phase 0 : Cadrage du projet

Décisions prises ensemble avant de coder. Ce qui est ici fait foi pour la v1.

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
- **Uniquement salé**, des plats pour le midi ou le soir.
- Les 6 recettes de la v1, avec le niveau requis pour les débloquer :

| # | Recette | Niveau | Temps | Technique apprise |
|---|---|---|---|---|
| 1 | 🍳 Omelette au fromage | 1 | 10 min | Cuire des œufs, gérer le feu |
| 2 | 🍝 Pâtes à la sauce tomate | 1 | 15 min | Cuire des pâtes, sauce simple |
| 3 | 🥪 Croque-monsieur | 2 | 15 min | Assembler, utiliser le four |
| 4 | 🍚 Riz sauté | 3 | 20 min | Faire sauter à feu vif |
| 5 | 🍝 Carbonara (sans crème) | 4 | 20 min | Lier une sauce aux œufs |
| 6 | 🍛 Curry japonais au poulet | 5 | 45 min | Mijoter, épaissir avec un roux |
- En V2 : ajout de mes propres recettes.

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

**Multiplicateurs**
- **Découverte ×1,5** : la première fois qu'on fait une recette.
- **Écart de niveau** (niveau du joueur − niveau de déblocage de la recette) :

| Écart | 0 à 1 | 2 | 3 | 4 et plus |
|---|---|---|---|---|
| XP gagnée | 100 % | 75 % | 50 % | 25 % |

`XP gagnée = arrondi(base × (découverte ? 1,5 : 1) × bonus d'écart)`

**Courbe de niveau** : +25 % d'XP par niveau, départ à 70 XP.

`XP pour passer au niveau suivant = arrondi(70 × 1,25^(niveau − 1))`

| Passage | 1→2 | 2→3 | 3→4 | 4→5 | 5→6 | 6→7 |
|---|---|---|---|---|---|---|
| XP à gagner | 70 | 88 | 109 | 137 | 171 | 214 |
| XP totale | 70 | 158 | 267 | 404 | 575 | 789 |

- Les niveaux continuent après le 5 (pas de niveau max).
- Rythme visé : environ 10 repas pour débloquer les 6 recettes, en mélangeant découvertes et recettes refaites.
- Chiffres à réajuster au point d'étape 1 si besoin.

### Ce qu'on débloque
- **Des recettes**, selon le niveau (voir tableau ci-dessus).
- **Un titre par niveau** : Commis → Apprenti → Cuistot → Chef de partie → Sous-chef → Chef → Chef étoilé → …

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
- **Sprites en 32×32**, affichés agrandis (×2 ou ×3) avec `image-rendering: pixelated`.
- **Gratuit autant que possible** : pack gratuit + dessins maison pour ce qui manque, plutôt qu'un pack payant.
- Pack de départ : [Pixel Art food icon pack 32x32](https://darinagrant.itch.io/pixel-art-food-icon-pack-32x32) (Darina Grant, gratuit, usage libre).
- En attendant d'avoir tous les sprites : **sprites temporaires** (carré de couleur avec l'initiale), remplacés au fur et à mesure.
- Dessins maison (ustensiles, avatar, logo) : Piskel (gratuit, navigateur) ou Aseprite.

### Police
- Police pixel Google Fonts, à tester : Press Start 2P, VT323, Pixelify Sans.

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

_Écrans validés pour démarrer, ajustables au point d'étape 1._

## Plus tard (hors v1)
_Les idées qui arrivent pendant le dev vont ici._
- Photo du plat pour valider une recette (bonus d'XP, galerie de ses plats)
- Maîtrise par recette : Bronze (1 fois), Argent (3 fois), Or (5 fois)
- Classement partagé entre potes (nécessite une base de données en ligne, par exemple Supabase ou Firebase)
