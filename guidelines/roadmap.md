# Roadmap : jeu de cuisine avec XP et niveaux

Mini-jeu 2D où l'on prépare de vraies recettes faciles en manipulant les ingrédients. Chaque recette réussie rapporte de l'XP, fait monter de niveau et débloque de nouveaux plats.

**Techno :** HTML, CSS, JavaScript (sans framework)
**Méthode :** on code ensemble, étape par étape. Chaque étape se termine par quelque chose qui marche dans le navigateur.

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
- [ ] **1. Structure du projet** : `index.html`, `style.css`, `game.js`, reliés entre eux
  - *Terminé quand :* la page s'ouvre et un `console.log` s'affiche dans la console (F12)
- [ ] **2. Maquette statique** : l'accueil en HTML/CSS (en-tête joueur, cartes de recettes), selon le design de la phase 0

## Phase 2 : Les données
- [ ] **3. Décrire une recette en JS** : nom, emoji, niveau requis, XP, ingrédients, étapes
  - *JS découvert :* variables, objets `{}`, tableaux `[]`
- [ ] **4. Afficher les recettes depuis le JS** : les cartes sont générées depuis la liste
  - *JS découvert :* boucles, `document.querySelector`, `innerHTML`

## Phase 3 : XP et niveaux
- [ ] **5. Le joueur** : un objet `joueur` avec son XP, une fonction qui calcule le niveau
  - *JS découvert :* fonctions, calculs, conditions `if`
- [ ] **6. Barre d'XP dynamique** : l'en-tête affiche le vrai niveau et la progression
- [ ] **7. Recettes verrouillées** : carte grisée avec 🔒 si le niveau est insuffisant

## Phase 4 : L'écran de cuisine
- [ ] **8. Changer d'écran** : clic sur une recette pour aller à la cuisine, bouton ← pour revenir
  - *JS découvert :* événements `click`, afficher/cacher des éléments
- [ ] **9. Afficher l'étape en cours** : « Étape 2/6 : Casse 2 œufs », avec des pastilles de progression
- [ ] **10. L'ustensile et le plateau d'ingrédients** : assiette, bol, poêle ou casserole, plus quelques ingrédients pièges
- [ ] **11. Vérifier le bon ingrédient** : bon ingrédient, on passe à l'étape suivante ; mauvais, il tremble et on compte une erreur
  - *C'est le cœur du jeu.*

**Résultat : le jeu est jouable.**

---

## 🗣️ Point d'étape 1 : on rejoue et on rediscute
- [ ] Le déroulé d'une recette est-il agréable ? Trop simple, trop long ?
- [ ] Le design tient-il la route en vrai ? Qu'est-ce qu'on ajuste ?
- [ ] On détaille les interactions de la phase 6 (glisser-déposer, mini-jeux, animations)

---

## Phase 5 : Récompenses
- [ ] **12. Fin de recette** : écran « Réussi ! », étoiles selon les erreurs, XP gagnée
- [ ] **13. Level up et déblocage** : annonce du nouveau niveau et des plats débloqués
- [ ] **14. La vraie recette** : récapitulatif avec les quantités, pour la cuisiner en vrai

## Phase 6 : Le côté interactif 2D
- [ ] **15. Animation** : l'ingrédient vole du plateau jusque dans l'ustensile et y reste affiché
- [ ] **16. Étapes d'action** : taper l'ustensile pour remuer, griller ou fouetter, avec une jauge et un effet 🔥 💨
- [ ] **17. Glisser-déposer** : à la souris et au doigt

---

## 🗣️ Point d'étape 2 : bilan avant les finitions
- [ ] Qu'est-ce qui manque pour que ce soit fun sur la durée ?
- [ ] Choix des recettes à ajouter et équilibrage de l'XP
- [ ] Tri des bonus : ce qu'on fait maintenant et ce qu'on garde pour plus tard

---

## Phase 7 : Finitions
- [ ] **18. Sauvegarde** : la progression reste après un rechargement (`localStorage`)
- [ ] **19. Contenu** : plus de recettes, équilibrage de l'XP
- [ ] **20. Bonus** choisis au point d'étape 2 : sons, badges, recette du jour, version mobile…
