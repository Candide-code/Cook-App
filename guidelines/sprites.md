# Sprites : ce qu'on a et ce qu'il reste à dessiner

Tous les sprites font **32×32 px** (sauf les légumes et herbes : **16×16**, affichés à la même taille, donc aux pixels deux fois plus gros), fond transparent, en PNG. Noms de fichiers en minuscules, sans accents ni espaces (`pain-de-mie.png`).

Sources :
- Pack nourriture : `pack pixel art/food icon pack 32x32/` ([Darina Grant](https://darinagrant.itch.io/pixel-art-food-icon-pack-32x32), gratuit, usage libre).
- Pack légumes et herbes : `pack pixel art/vegetables/99_vegetables_and_herbs/` ([« 99 vegetables and herbs », keifoopx](https://keifoopx.itch.io/99-vegetables-and-herbs), 16×16, gratuit, usage commercial et non commercial d’après la page ; itch.io bloque la vérification automatique). Adopté le 2026-09-25.
- Pack fruits et fruits à coque : `pack pixel art/fruits/99_fruits_and_nuts/` ([« 99 fruits and nuts », keifoopx](https://keifoopx.itch.io/99fruitsandnuts), 16×16, même auteur et même licence libre que les légumes). Ajouté le 2026-09-25.
- Pack ingrédients variés : `pack pixel art/ingredients random/99_ingredients/` ([« 99 various ingredients », keifoopx](https://keifoopx.itch.io/99-various-ingredients), 16×16 : légumineuses, fromages, œufs, céréales, champignons, algues, épices, eau, lait). Ajouté le 2026-09-25.
- ~~Pack légumes Quipinny~~ : retiré du jeu le 2026-09-25 (licence jamais confirmée). ⚠️ Ses anciennes images restent dans l’historique Git du dépôt public.
- Pack plats : [« Pixel Food », ghostpixxells](https://ghostpixxells.itch.io/pixelfood), `pack pixel art/plats/`, 102 images 32×32, gratuit, usage libre d’après la page.
- Personnage : `pack pixel art/characters/char_a_p1/` ([Mana Seed Character Base, démo gratuite](https://seliel-the-shaper.itch.io/character-base), Seliel the Shaper, usage commercial ou non autorisé). Planches de 512×512 en cases de 64×64 : on n'utilise que la 1re case (pose de face). Exception au format 32×32.

## Personnage (`CODE/assets/sprites/chef/`)

Chaque fichier fait 64×64 (pose de face). Toutes les couches ont le même cadre : on les empile au même endroit, dans cet ordre : **corps → yeux → veste → tablier → cheveux → toque**.

| Couche | Fichiers | Source | Statut |
|---|---|---|---|
| Corps (11 peaux) | `peau-01.png` à `peau-11.png`, de la plus claire à la plus foncée | `char_a_p1_0bas_humn_v00` à `v10` (ordre : v00, v01, v03, v02, v04, v05, v08, v09, v06, v10, v07) | ✅ pack |
| Cheveux : carré (13 couleurs) | `cheveux-carre-01.png` à `-13.png` | `4har/char_a_p1_4har_bob1_v01` à `v13` | ✅ pack (`v00` = modèle gris, pas utilisé) |
| Cheveux : chignon (13 couleurs) | `cheveux-chignon-01.png` à `-13.png` | `4har/char_a_p1_4har_dap1_v01` à `v13` | ✅ pack (`v00` = modèle gris, pas utilisé) |
| Cheveux : courte (13 couleurs) | `cheveux-court-01.png` à `-13.png` | dessinée en gris `v00`, recolorée avec les 13 gammes du pack | 🟡 temporaire, à redessiner dans Piskel |
| Cheveux : afro (13 couleurs) | `cheveux-afro-01.png` à `-13.png` | forme calculée par script : ovale au bord ondulé, moins l'ovale du visage (arc de la ligne des cheveux), ombre claire en haut à gauche ; recolorée avec les 13 gammes du pack | 🟡 temporaire, à redessiner dans Piskel |
| Cheveux : locs (13 couleurs) | `cheveux-locs-01.png` à `-13.png` | dessinée en gris `v00` : chignon rond, crâne serré à rayures, deux locs sur le front (longueurs différentes), une de chaque côté du visage ; recolorée avec les 13 gammes du pack | 🟡 temporaire, à redessiner dans Piskel |
| Yeux (4 couleurs) | `yeux-noir.png`, `-marron`, `-bleu`, `-vert` | 4 pixels (2 par œil, x 30 et 33, y 23-24) : haut = ombre de la paupière, bas = iris | ✅ généré |
| Veste + pantalon | `veste.png` | `1out/char_a_p1_1out_pfpn_v01` (tenue de fermier) recolorée : haut blanc, bas gris foncé | 🟡 temporaire, à redessiner dans Piskel |
| Tablier (5 couleurs) | `tablier-rouge.png`, `-orange`, `-vert`, `-bleu`, `-noir` | dessiné pixel par pixel, 3 teintes Sweetie 16 par couleur | 🟡 temporaire, à redessiner dans Piskel |
| Toque | `toque.png` | dessinée pixel par pixel | 🟡 temporaire, à redessiner dans Piskel |

## Ingrédients (`CODE/assets/sprites/ingredients/`)

| Ingrédient | Fichier | Statut |
|---|---|---|
| Œufs | `oeuf.png` | ✅ pack ingrédients variés (œuf blanc entier, remplace l’œuf au plat de Darina) |
| Fromage râpé | `fromage.png` | ✅ pack |
| Parmesan | `fromage.png` | ✅ pack (même sprite pour l'instant) |
| Sel | `sel.png` | ✅ pack |
| Riz | `riz.png` | ✅ pack |
| Pain de mie | `pain-de-mie.png` | ✅ pack |
| Poulet | `poulet.png` | ✅ pack |
| Jambon | `jambon.png` | ✅ pack |
| Beurre | `beurre.png` | ✏️ à dessiner |
| Huile | `huile.png` | ✏️ à dessiner |
| Légumes (87) : tous ceux du pack « 99 vegetables and herbs » (ail, carotte, oignon, pomme de terre, tomate, courgette, épinards, salade…) | `[identifiant].png` (voir `recettes/ingredients.js`) | ✅ pack légumes 16×16 |
| Herbes (12) : basilic, persil, menthe, ciboulette, aneth, ail des ours, gingembre, shiso… | `[identifiant].png` | ✅ même pack |
| PRC (plat) | `plats/prc.png` | 🟡 pack plats (`86_roastedchicken_dish`, un poulet rôti) en attendant une vraie image de poulet pané + riz + courgettes |
| Chapelure | `chapelure.png` | ✏️ sprite temporaire |
| Cinnamon roll (plat) | `plats/cinnamon-roll.png` | 🟡 pack plats (`12_bun_dish`, une brioche) en attendant une vraie image |
| Levure boulangère, cannelle, cream cheese, crème fraîche, sucre glace | `[identifiant].png` | ✏️ sprite temporaire |
| Pépites de chocolat | `pepites-chocolat.png` | ✅ pack plats (`26_chocolate`, une tablette) |
| Feuilles de gyoza, sauce huître, sauce soja sucrée, huile pimentée, nokoss, graines de sésame (gyozas) | `[identifiant].png` | ✏️ sprite temporaire |
| Farine, sucre, levure chimique | `farine.png`, `sucre.png`, `levure-chimique.png` | ✏️ sprite temporaire (à trouver ou dessiner) |
| Légumes absents des packs : avocat, céleri-rave, jalapeño, oignon nouveau, patate douce, pois gourmands, poivrons jaune et rouge, radis blanc | — | ✏️ sprite temporaire (à trouver ou dessiner) |
| Fruits (51) et fruits à coque (9) | `[identifiant].png` | ✅ pack fruits 16×16 (variantes tranchées / ouvertes non utilisées) |
| Champignons (15), légumineuses (14), céréales, fromages (15), lait et yaourts, épices (cumin, muscade, safran, vanille…), algues, eau | `[identifiant].png` | ✅ pack ingrédients variés 16×16 (œufs de couleur, œufs fêlés et champignons « dessin animé » non utilisés) |
| Petits pois, maïs, poivre, eau | `petits-pois.png`, `mais.png`, `poivre.png`, `eau.png` | ✅ complétés par le pack ingrédients variés |
| Pâtes | `pates.png` | ✏️ à dessiner |
| Sauce soja | `sauce-soja.png` | ✏️ à dessiner |
| Lardons | `lardons.png` | ✏️ à dessiner |
| Tablette de curry | `curry.png` | ✏️ à dessiner |

## Ustensiles (`CODE/assets/sprites/ustensiles/`)

| Ustensile | Fichier | Statut |
|---|---|---|
| Poêle | `poele.png` | ✏️ à dessiner |
| Casserole | `casserole.png` | ✏️ à dessiner |
| Bol | `bol.png` | ✅ pack plats (`04_bowl`) |
| Assiette | `assiette.png` | ✅ pack plats (`01_dish`) |
| Plaque de four | `plaque.png` | ✏️ à dessiner |
| Tous les autres ustensiles du catalogue (53, avec congélateur et réfrigérateur) : poêles et casseroles, plats et moules, bols et mesures, petits outils, électroménager | `[identifiant].png` (voir `ustensiles` dans `recettes/ingredients.js`) | ✏️ à trouver ou dessiner (sprite temporaire en attendant) |

## Plats (`CODE/assets/sprites/plats/`)

| Plat | Fichier | Statut |
|---|---|---|
| Omelette | `omelette.png` | ✅ pack plats (`74_omlet_dish`) |
| Pâtes tomate | `pates-tomate.png` | ✅ pack plats (`94_spaghetti`) |
| Croque-monsieur | `croque-monsieur.png` | ✅ pack plats (`93_sandwich_dish`) |
| Riz sauté | `riz-saute.png` | ✏️ à dessiner (base possible : `Bowl of rice.png` du pack) |
| Carbonara | `carbonara.png` | ✏️ à dessiner |
| Curry japonais | `curry-japonais.png` | ✅ pack plats (`33_curry_dish`), branché quand la recette sera ajoutée |
| Cookies | `cookies.png` | ✅ pack plats (`29_cookies_dish`) |
| Gyozas au poulet | `gyozas-poulet.png` | ✅ pack plats (`37_dumplings_dish`) |

En attendant, chaque sprite manquant est remplacé par un sprite temporaire (`.sprite-temp`).
