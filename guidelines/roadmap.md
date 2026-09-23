# Roadmap : jeu de cuisine avec XP et niveaux

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
- [ ] Tester l'omelette en vraie cuisine
- [ ] Ajouter les recettes une par une : pâtes tomate, croque-monsieur, riz sauté, carbonara, curry japonais

Les étapes ci-dessous restent la référence ; celles couvertes par la tranche verticale seront cochées une fois validées en vrai.

## Phase 2 : Les données
- [ ] **5. Décrire une recette en JS** : nom, sprite, difficulté (★), niveau requis, temps, ingrédients avec quantités, ustensiles, étapes (types « ajouter », « action », « cuisson »)
  - *JS découvert :* variables, objets `{}`, tableaux `[]`
- [ ] **6. Les 6 recettes de la v1** : omelette, pâtes tomate, croque-monsieur, riz sauté, carbonara, curry japonais
- [ ] **7. Afficher les recettes depuis le JS** : les cartes de l'accueil sont générées à partir de la liste
  - *JS découvert :* boucles, `document.querySelector`, `innerHTML`

## Phase 3 : XP et niveaux (logique RPG)
- [ ] **8. Le joueur** : un objet `joueur` avec son XP et le compteur de chaque recette faite
- [ ] **9. Les formules RPG** : XP pour passer un niveau (`70 × 1,25^(niveau − 1)`), niveau à partir de l'XP, XP gagnée (base selon la difficulté, découverte ×1,5, bonus d'écart de niveau)
  - *JS découvert :* fonctions, calculs, conditions `if`, `Math.round`, `Math.pow`
- [ ] **10. En-tête dynamique** : vrai niveau, titre (Commis → Apprenti → …) et barre d'XP
- [ ] **11. Recettes verrouillées** : carte masquée (🔒, « ??? », niveau requis) et badge « NEW! » sur les recettes jamais faites
  - *Test :* on change l'XP à la main pour voir les recettes se débloquer

## Phase 4 : Les écrans de recette
- [ ] **12. Naviguer entre les écrans** : accueil → préparation → cuisine → fin, avec les boutons ← et ✕ pour revenir
  - *JS découvert :* événements `click`, afficher/cacher des éléments
- [ ] **13. Écran de préparation** : ingrédients et ustensiles à cocher, bouton « Commencer »
- [ ] **14. Écran de cuisine** : progression des étapes (« Étape 2/6 »), sprite de l'ustensile, consigne dans une boîte de dialogue façon RPG
- [ ] **15. Étape « ajouter »** : plateau avec seulement les ingrédients de la recette ; cliquer sur le bon ingrédient valide l'étape
  - *C'est le cœur du jeu.*
- [ ] **16. Les erreurs** : pas de pénalité ; l'écran tremble, le téléphone vibre (Android), et à la 3e erreur un message indique le bon ingrédient
- [ ] **17. Étape « action »** : taper l'ustensile plusieurs fois (remuer, retourner…), avec une jauge
- [ ] **18. Étape « cuisson »** : minuteur intégré avec un bouton pour lancer le décompte
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
- [ ] **19. Fin de recette** : bouton « J'ai fini », XP gagnée, barre d'XP qui se remplit
- [ ] **20. Level up** : annonce dans une boîte de dialogue, nouveau titre, recette débloquée
- [ ] **21. Récap de la recette** : toutes les étapes avec les quantités, pour la refaire
- [ ] **22. Sauvegarde** : la progression reste après un rechargement de la page
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
- Ajout de mes propres recettes
- Idées de la liste « Plus tard » du cadrage non faites en v1
