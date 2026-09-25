# Sprites : ce qu'on a et ce qu'il reste à dessiner

Tous les sprites font **32×32 px**, fond transparent, en PNG. Noms de fichiers en minuscules, sans accents ni espaces (`pain-de-mie.png`).

Sources :
- Pack nourriture : `pack pixel art/food icon pack 32x32/` ([Darina Grant](https://darinagrant.itch.io/pixel-art-food-icon-pack-32x32), gratuit, usage libre).
- Pack légumes : `pack pixel art/vegetables/` ([Quipinny](https://quipinny.itch.io/pixelartvegetablespack), licence à confirmer).
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
| Œufs | `oeuf.png` | ✅ pack (œuf au plat, à remplacer par un œuf entier ?) |
| Fromage râpé | `fromage.png` | ✅ pack |
| Parmesan | `fromage.png` | ✅ pack (même sprite pour l'instant) |
| Sel | `sel.png` | ✅ pack |
| Riz | `riz.png` | ✅ pack |
| Pain de mie | `pain-de-mie.png` | ✅ pack |
| Poulet | `poulet.png` | ✅ pack |
| Jambon | `jambon.png` | ✅ pack |
| Beurre | `beurre.png` | ✏️ à dessiner |
| Poivre | `poivre.png` | ✏️ à dessiner (partir de `sel.png` en changeant les couleurs) |
| Huile | `huile.png` | ✏️ à dessiner |
| Ail | `ail.png` | ✅ pack légumes |
| Oignon | `oignon.png` | ✅ pack légumes |
| Carotte | `carotte.png` | ✅ pack légumes |
| Pomme de terre | `pomme-de-terre.png` | ✅ pack légumes |
| Tomate | `tomate.png` | ✅ pack légumes |
| Basilic | `basilic.png` | ✏️ à dessiner |
| Pâtes | `pates.png` | ✏️ à dessiner |
| Petits pois | `petits-pois.png` | ✅ pack légumes |
| Sauce soja | `sauce-soja.png` | ✏️ à dessiner |
| Lardons | `lardons.png` | ✏️ à dessiner |
| Tablette de curry | `curry.png` | ✏️ à dessiner |
| Eau | `eau.png` | ✏️ à dessiner |

## Ustensiles (`CODE/assets/sprites/ustensiles/`)

| Ustensile | Fichier | Statut |
|---|---|---|
| Poêle | `poele.png` | ✏️ à dessiner |
| Casserole | `casserole.png` | ✏️ à dessiner |
| Bol | `bol.png` | ✏️ à dessiner |
| Plaque de four | `plaque.png` | ✏️ à dessiner |

## Plats (`CODE/assets/sprites/plats/`)

| Plat | Fichier | Statut |
|---|---|---|
| Omelette | `omelette.png` | ✏️ à dessiner |
| Pâtes tomate | `pates-tomate.png` | ✏️ à dessiner |
| Croque-monsieur | `croque-monsieur.png` | ✏️ à dessiner (base possible : `Sandwich.png` du pack) |
| Riz sauté | `riz-saute.png` | ✏️ à dessiner (base possible : `Bowl of rice.png` du pack) |
| Carbonara | `carbonara.png` | ✏️ à dessiner |
| Curry japonais | `curry-japonais.png` | ✏️ à dessiner |

En attendant, chaque sprite manquant est remplacé par un sprite temporaire (`.sprite-temp`).
