# Roadmap : Underplate, jeu de cuisine avec XP et niveaux

App qui gamifie la vraie cuisine : on suit des recettes faciles pas à pas en manipulant les ingrédients dans une interface pixel art 2D. Chaque recette cuisinée rapporte de l'XP, fait monter de niveau (logique RPG) et débloque de nouveaux plats.

**Techno :** HTML, CSS, JavaScript (sans framework)
**Méthode :** on code ensemble, étape par étape. Chaque étape se termine par quelque chose qui marche dans le navigateur.
**Référence :** toutes les décisions sont dans [phase-0-cadrage.md](phase-0-cadrage.md).
**En ligne :** https://candide-code.github.io/Cook-App/ (GitHub Pages, mis à jour à chaque push sur `main`)

---

## Phase 0 : On discute du projet (avant de coder)

### A. Fonctionnalités
- [x] Qui joue ? Sur ordi, sur téléphone, ou les deux ?
- [x] Quelles recettes, combien au départ, quel niveau de difficulté ?
- [x] Comment on joue une recette : clic, glisser-déposer, mini-jeux ?
- [x] Règles d'XP : combien par recette, combien pour passer un niveau, étoiles, bonus ?
- [x] Ce qu'on débloque : recettes seulement, ou aussi ustensiles, titres, badges ?
- [x] Lien avec la vraie cuisine : recette affichée, bonus si on la fait en vrai ?

### B. Design
- [x] Ambiance : mignon et coloré, épuré, rétro pixel art, réaliste ?
- [x] Visuels 2D : emojis, dessins CSS/SVG, ou images ?
- [x] Couleurs et police
- [x] Liste des écrans, avec un croquis rapide de chacun

**Terminé quand :** on a une liste de fonctionnalités validée (v1 et plus tard) et une direction visuelle claire.

---

## Phase 1 : Les fondations
- [x] **1. Structure du projet** : dossier `CODE/` avec `index.html`, `main.js`, un sous-dossier par fonctionnalité (`base/`, `joueur/`, `recettes/`, `accueil/`, `preparation/`, `cuisine/`, `fin-recette/`, `sauvegarde/`) et `assets/sprites/`
  - *Terminé quand :* la page s'ouvre et un `console.log` s'affiche dans la console (F12)
- [x] **2. Le style pixel de base** : police pixel, palette Sweetie 16 en variables CSS, thème clair et sombre automatique, `image-rendering: pixelated`, cadres façon RPG
  - *CSS découvert :* variables CSS, `prefers-color-scheme`
- [x] **3. Les premiers sprites** : trouver un pack « pixel food » 32×32 gratuit sur itch.io (licence vérifiée) et ranger les sprites des ingrédients de la v1
- [x] **4. Maquette statique de l'accueil** : en-tête joueur (avatar, niveau, titre, barre d'XP) et cartes de recettes, en HTML/CSS, pensée mobile d'abord

## 🍳 Tranche verticale : l'omelette jouable de A à Z
Décidé après l'étape 5 : plutôt que de finir chaque phase pour les 6 recettes, on rend **une seule recette** jouable de bout en bout pour tester le process en vrai, puis on ajoute les recettes une par une.

- [x] Omelette décrite en données (10 étapes, ingrédients, ustensiles)
- [x] Accueil généré en JS, en-tête avec niveau / titre / XP réels
- [x] Formules RPG (`joueur/xp.js`)
- [x] Écran de préparation (cases à cocher)
- [x] Écran de cuisine : étapes « ajouter » (plateau avec seulement les ingrédients de la recette), « action » (taps + jauge), « cuisson » (minuteur)
- [x] Erreurs : tremblement, vibration, aide à la 3e erreur
- [x] Fin de recette : « J'ai fini », XP, level up, récap
- [x] Sauvegarde (`localStorage`)
- [x] Maîtrise par recette : rangs Bronze / Argent / Or / Platine, bordure de carte, bonus d'XP, message au passage de rang
- [x] Progression revue (2026-09-25) : titres par paliers (5, 10, 18, 30, 50, 75, 100, 125, 150), courbe d'XP plafonnée à 200 XP par niveau (niveau 100 ≈ 2 ans), malus d'écart supprimé dès le niveau 6
- [x] Recettes rangées en SALÉ / SUCRÉ : menu à 2 boutons avant la grille (champ `categorie` dans chaque recette)
- [x] Accueil en menu (RECETTES / GRIMOIRE) + Grimoire : liste des recettes déjà cuisinées (« ??? » pour les autres) et leur fiche complète
- [x] Avant le test en cuisine :
  - [x] L'écran reste allumé pendant la recette (Wake Lock)
  - [x] Minuteur fiable même écran éteint ou appli changée
  - [x] Bip à la fin du minuteur
  - [x] Confirmation avant de quitter une recette (✕)
  - [x] Bouton « étape précédente »
- [ ] *(Optionnel, plus tard)* Tester l'omelette en vraie cuisine
- [ ] Ajouter les recettes **une par une** (on finit et on teste une recette avant de passer à la suivante), dans l'ordre des déblocages :
  - [x] Pâtes tomate (niv. 1)
  - [ ] Cookies (sucré, niv. 1) — écrite, en attente du test
  - [ ] PRC — poulet riz courgettes (niv. 2) — écrite, en attente du test
  - [ ] Cinnamon roll (sucré, niv. 1, ★★★★) — écrite, en attente du test
  - [ ] Gyozas au poulet maison (niv. 3, ★★) — écrite (recette perso, feuilles achetées), en attente du test
  - [ ] Croque-monsieur (niv. 4) — écrite (mélange fromage + crème fraîche), en attente du test
  - [ ] Carbonara (niv. 5)
  - [ ] Gâteau au chocolat (sucré, niv. 5)
  - [ ] Tarte aux pommes (sucré, niv. 7)
  - [ ] Riz sauté (niv. 8)
  - [ ] Cheesecake (sucré, niv. 9)
  - [ ] Quiche (niv. 10)
  - [ ] Muffins (sucré, niv. 10)
  - [ ] Curry japonais (niv. 12)
  - [x] Déblocages revus (1 par palier, 2 tous les 5 niveaux) + bandeau « À DÉBLOQUER » (3 prochaines) + recettes prévues (`aVenir`)

## 👤 Profil : « Crée ton chef »
Décidé le 2026-09-25 (détails dans le cadrage, « Profil et personnage »). Pack Mana Seed, sans animation pour l'instant.

- [x] **Sprites du perso** : découper la pose de face dans les planches Mana Seed (peaux, coupes, couleurs de cheveux) et ne copier que ces petites images dans `CODE/assets/sprites/chef/`
- [x] **Tenue de chef temporaire** : toque, veste blanche et tablier (une image par couleur), générés en pixels et alignés sur le corps
- [x] **Coupes courte, afro et locs temporaires** : dessinées dans les gris du modèle `v00`, puis recolorées avec les gammes du pack (mêmes 13 couleurs que les autres coupes)
- [x] **Afficher le perso** : empiler les couches (corps → yeux → veste → tablier → cheveux → toque) et le montrer dans l'en-tête de l'accueil
  - *CSS découvert :* `position: absolute` pour superposer des images
- [x] **Écran « Crée ton chef »** : pseudo, genre (Chef / Cheffe), flèches ◀ ▶ pour chaque réglage, perso mis à jour en direct, sauvegarde dans `joueur`
- [x] **Masculin / féminin dans tout le jeu** : « Chef [pseudo] » / « Cheffe [pseudo] » dans l'en-tête, titres de niveau accordés, accords dans les messages (fin de recette…)
- [x] **Au premier lancement** l'écran s'ouvre avant l'accueil ; ensuite on le rouvre en touchant l'avatar
  - *Pour tester comme un nouveau joueur :* ouvrir `index.html?reset` (efface la sauvegarde)
- [ ] **Tenue de chef et coupes maison dans Piskel** : redessiner la toque, la veste, le tablier, la coupe courte, l'afro et les locs (remplace les versions temporaires)

## 🧑‍🍳 CUSTOM : mes propres recettes
Décidé le 2026-09-25 (détails dans le cadrage, « Recettes custom »). Avancé de la V2. Passe avant les cookies.

- [x] **1. Données** : les recettes perso dans la sauvegarde (`joueur`), et un catalogue d'ustensiles plus large (four, plaque, fouet…)
- [x] **2. Bouton CUSTOM** sur l'accueil + sous-menu SALÉ / SUCRÉ + grille de ses recettes avec le bouton **+**
- [x] **3. Assistant, étape 1 : infos** (nom, ★, temps)
- [x] **4. Assistant, étape 2 : ingrédients + quantité** (catalogue du jeu ou nom tapé)
  - [x] Quantités aux flèches (nombre + unité), 24 légumes du pack ajoutés, ingrédients rangés par famille (sous-menu)
- [x] **5. Assistant, étape 3 : ustensiles / électroménager**
- [x] **6. Assistant, étape 4 : étapes typées** (Ajouter / Action / Cuisson-minuteur ⏱, + ustensile)
- [x] **7. Assistant, étape 5 : récap + enregistrement**
- [x] **8. Jouer une recette custom** : préparation, cuisine, minuteur, XP de la difficulté choisie
- [x] **9. Modifier / supprimer** une recette custom (boutons sur l’écran de préparation ; l’assistant s’ouvre pré-rempli)
- [x] **10. Grimoire : filtre** « Mes recettes » / « Recettes du jeu »

## 📲 App installable (PWA)
Décidé le 2026-09-26, à la demande des potes : une version « téléchargeable » dont les recettes se mettent à jour toutes seules. Gratuit, sans store : une PWA sur GitHub Pages. On push, tout le monde reçoit la mise à jour à la prochaine ouverture. La sauvegarde est gardée (même adresse).

- [x] **1. Logo de l'app** : assiette + fourchette et couteau croisés à manches rouges, 32×32, Sweetie 16, fond `#1a1c2c` plein, dessin dans la zone de sécurité centrale 24×24. `CODE/assets/icones/` : `icone-512.png` (×16), `icone-192.png` (×6), source `logo.piskel`
- [x] **2. `manifest.json`** : nom, icônes (dont « maskable » pour Android), plein écran (`standalone`), portrait, couleurs ; liens dans `index.html` (icône iPhone, couleur de la barre qui suit le thème)
- [x] **3. Service worker** (`CODE/service-worker.js`, lancé par `main.js`) : réseau d'abord pour le code et les recettes (copie du téléphone si hors ligne ou réseau > 3 s), copie d'abord pour les images et polices. Pas de numéro de version à changer : un push suffit
  - *JS découvert :* service worker, `caches`, `fetch`, `async` / `await`
  - *À savoir :* un nouveau fichier JS/CSS s'ajoute aussi dans `FICHIERS_DE_BASE` (sinon il n'est hors ligne qu'après un 1er chargement)
- [ ] **4. Message « nouvelle version »** dans le jeu, avec un bouton pour mettre à jour
- [ ] **5. Test sur téléphone** (Android : « Installer l'application » ; iPhone : Safari → Partager → « Sur l'écran d'accueil »), puis envoi du lien aux potes

Les étapes ci-dessous sont la roadmap d'origine. Celles réalisées pendant la tranche verticale ont été cochées le 2026-09-25 (code en place et utilisé). Restent : les 6 recettes de la v1 (en cours, voir plus haut), la phase 6 (interactif et pixel), les tests téléphone et les points d'étape.


## Phase 2 : Les données
- [x] **5. Décrire une recette en JS** : nom, sprite, difficulté (★), niveau requis, temps, ingrédients avec quantités, ustensiles, étapes (types « ajouter », « action », « cuisson »)
  - *JS découvert :* variables, objets `{}`, tableaux `[]`
- [ ] **6. Les 6 recettes de la v1** *(en cours : omelette, pâtes, croque écrites ; carbonara, riz sauté, curry à venir)* : omelette, pâtes tomate, croque-monsieur, riz sauté, carbonara, curry japonais
- [x] **7. Afficher les recettes depuis le JS** : les cartes de l'accueil sont générées à partir de la liste
  - *JS découvert :* boucles, `document.querySelector`, `innerHTML`

## Phase 3 : XP et niveaux (logique RPG)
- [x] **8. Le joueur** : un objet `joueur` avec son XP et le compteur de chaque recette faite
- [x] **9. Les formules RPG** : XP pour passer un niveau (`70 × 1,25^(niveau − 1)`), niveau à partir de l'XP, XP gagnée (base selon la difficulté, découverte ×1,5, bonus d'écart de niveau)
  - *JS découvert :* fonctions, calculs, conditions `if`, `Math.round`, `Math.pow`
- [x] **10. En-tête dynamique** : vrai niveau, titre (Commis → Apprenti → …) et barre d'XP
- [x] **11. Recettes verrouillées** : carte masquée (🔒, « ??? », niveau requis) et badge « NEW! » sur les recettes jamais faites
  - *Test :* on change l'XP à la main pour voir les recettes se débloquer

## Phase 4 : Les écrans de recette
- [x] **12. Naviguer entre les écrans** : accueil → préparation → cuisine → fin, avec les boutons ← et ✕ pour revenir
  - *JS découvert :* événements `click`, afficher/cacher des éléments
- [x] **13. Écran de préparation** : ingrédients et ustensiles à cocher, bouton « Commencer »
- [x] **14. Écran de cuisine** : progression des étapes (« Étape 2/6 »), sprite de l'ustensile, consigne dans une boîte de dialogue façon RPG
- [x] **15. Étape « ajouter »** : plateau avec seulement les ingrédients de la recette ; cliquer sur le bon ingrédient valide l'étape
  - *C'est le cœur du jeu.*
- [x] **16. Les erreurs** : pas de pénalité ; l'écran tremble, le téléphone vibre (Android), et à la 3e erreur un message indique le bon ingrédient
- [x] **17. Étape « action »** : taper l'ustensile plusieurs fois (remuer, retourner…), avec une jauge
- [x] **18. Étape « cuisson »** : minuteur intégré avec un bouton pour lancer le décompte
  - *JS découvert :* `setInterval`, gestion du temps

**Résultat : on peut suivre une recette de bout en bout.**

---

## 🗣️ Point d'étape 1 : on teste en vraie cuisine et on rediscute
- [ ] Cuisiner une vraie recette avec l'app sur le téléphone : c'est pratique avec les mains occupées ?
- [ ] Le déroulé d'une recette est-il agréable ? Trop simple, trop long ?
- [ ] Le design pixel tient-il la route en vrai ? Qu'est-ce qu'on ajuste ?
- [ ] Les chiffres d'XP sont-ils bien réglés ?
- [ ] On détaille les interactions de la phase 6 (glisser-déposer, animations, effets)

---

## Phase 5 : Récompenses et progression
- [x] **19. Fin de recette** : bouton « J'ai fini », XP gagnée, barre d'XP qui se remplit
- [x] **20. Level up** : annonce dans une boîte de dialogue, nouveau titre, recette débloquée
- [x] **21. Récap de la recette** : toutes les étapes avec les quantités, pour la refaire
- [x] **22. Sauvegarde** : la progression reste après un rechargement de la page
  - *JS découvert :* `localStorage`, `JSON.stringify` / `JSON.parse`

## Phase 6 : Le côté interactif 2D et pixel
- [ ] **23. Texte qui s'écrit lettre par lettre** dans la boîte de dialogue, façon Undertale
- [ ] **24. Animation** : l'ingrédient vole du plateau jusque dans l'ustensile et y reste affiché
- [ ] **25. Glisser-déposer** : à la souris et au doigt
- [ ] **26. Effets pixel** : fumée, flammes, bulles pendant les actions et la cuisson
- [ ] **27. Sprites maison** : ustensiles, avatar de chef, logo (Piskel ou Aseprite)

---

## 🗣️ Point d'étape 2 : bilan avant les finitions
- [ ] Qu'est-ce qui manque pour que ce soit fun sur la durée ?
- [ ] Équilibrage de l'XP après quelques semaines d'utilisation
- [ ] Tri de la liste « Plus tard » du cadrage : ce qu'on fait maintenant et ce qu'on garde pour la V2

---

## Phase 7 : Finitions et partage
- [ ] **28. Tests sur téléphone** : Android et iPhone, thème clair et sombre
- [x] **29. Mise en ligne** : GitHub Pages, pour partager le lien avec les potes
- [ ] **30. Bonus** choisis au point d'étape 2 (maîtrise par recette, photo du plat, classement partagé, sons…)

---

## V2 (plus tard)
- ~~Ajout de mes propres recettes~~ → avancé dans la v1 (section CUSTOM)
- Idées de la liste « Plus tard » du cadrage non faites en v1
