# ColorDigitLogic

**ColorDigitLogic** est une application web indépendante permettant de recopier, compléter et vérifier des grilles de logique mêlant **nombres et couleurs**. Elle fonctionne sur ordinateur, tablette et téléphone, directement dans le navigateur.

**Version actuelle : V19** — application web installable (PWA), utilisable hors ligne après un premier chargement, avec solveur et contrôle immédiat des erreurs par rapport à la solution unique lorsqu’elle existe.

**Jouer :** https://pixou2000.github.io/ColorDigitLogic/

## Fonctionnalités

- Grilles de plusieurs formats : **2×3, 3×3, 3×4, 4×4, 4×5, 5×5 et 5×6**.
- Démarrage sur une grille vide **2×3**.
- **Mode préparation** : saisie des indices situés entre les cases (sommes numériques ou mélanges de couleurs), y compris les indices négatifs. Les emplacements laissés vides ne comportent pas d'indice.
- **Mode jeu** : saisie des nombres et couleurs dans les cases.
- Palettes adaptées à la taille de la grille, avec les couleurs dans l'ordre **bleu, rouge, jaune, blanc, noir**, suivies des mélanges disponibles.
- Annulation, effacement de la sélection et vérification de la grille.
- Chronomètre avec pause, reprise et remise à zéro ; mémorisation de records par format de grille sur l'appareil.
- Sauvegarde locale et **import/export JSON** pour conserver une grille et son temps écoulé.
- Interface adaptée aux écrans tactiles ; fond gris autour du plateau pour distinguer les cases blanches.

## Utilisation

### 1. Préparer une grille

1. Choisir le format souhaité dans le menu **Format**.
2. Cliquer sur **Nouvelle grille vide** si nécessaire.
3. En mode préparation, sélectionner un emplacement entre deux cases, puis choisir son indice numérique ou coloré.
4. Utiliser l'option d'indice négatif pour indiquer qu'une somme ou un mélange est **interdit**.
5. Laisser vides les emplacements sans indice. Un second clic sur la même valeur permet d'effacer un indice saisi par erreur.

### 2. Résoudre la grille

1. Cliquer sur **Passer en mode jeu**.
2. Sélectionner une case et lui attribuer un nombre et une couleur.
3. Utiliser **Annuler** ou **Effacer la sélection** si nécessaire.
4. Cliquer sur **Vérifier** pour contrôler les contraintes de la grille.

Le chronomètre démarre au passage en mode jeu et peut être mis en pause ou repris.

### 3. Sauvegarder ou transférer une partie

- **Sauvegarder sur cet appareil** : conserve la grille dans le stockage local du navigateur.
- **Recharger la sauvegarde** : récupère cette sauvegarde locale.
- **Exporter en fichier JSON** : télécharge une copie de la grille, incluant le temps écoulé.
- **Importer une grille JSON** : recharge un fichier précédemment exporté, y compris sur un autre appareil.

Les sauvegardes locales et les records **ne se synchronisent pas automatiquement** entre appareils. Pour transférer une partie, utiliser le fichier JSON.

## Installer ColorDigitLogic sur iPhone ou iPad

1. Ouvrir https://pixou2000.github.io/ColorDigitLogic/ dans **Safari**.
2. Toucher le bouton **Partager**.
3. Choisir **Sur l'écran d'accueil**, puis **Ajouter**.
4. Lancer ColorDigitLogic depuis l'icône ajoutée.

L'application est conçue pour fonctionner **hors ligne après un premier chargement en ligne**. Pour vérifier : ouvrir l'application une première fois, fermer l'application, activer le mode Avion et la relancer depuis son icône.

## Installation sur GitHub Pages

Le projet comprend cinq fichiers à placer à la racine du dépôt :

| Fichier | Rôle |
| --- | --- |
| `index.html` | Interface, styles et logique du jeu |
| `manifest.webmanifest` | Informations nécessaires à l'installation de la PWA |
| `sw.js` | Mise en cache pour l'utilisation hors ligne |
| `icon-192.png` | Icône de l'application (192 px) |
| `icon-512.png` | Icône de l'application (512 px) |

Pour publier une nouvelle version, remplacer les fichiers modifiés dans le dépôt GitHub, puis attendre la mise à jour de GitHub Pages. Le cache de la PWA peut nécessiter un rechargement ou une mise à jour pour afficher la dernière version.

## Structure du code

Le fichier `index.html` regroupe trois technologies :

- **HTML** : éléments de l'interface (plateau, boutons et palettes).
- **CSS**, dans la balise `<style>` : apparence et adaptation aux tailles d'écran.
- **JavaScript**, dans la balise `<script>` : construction de la grille, interactions, vérifications, chronomètre et sauvegardes.

Le code peut être consulté et modifié avec **Visual Studio Code**. Pour mettre le fichier en forme : **Shift + Option + F** sur Mac. Pour prévisualiser ce README : **Cmd + Shift + V**.

## Évolutions possibles

- Ajouter un solveur automatique.
- Expliquer les déductions étape par étape.
- Améliorer la validation des grilles et la détection de solutions uniques.

---

*Projet personnel indépendant, non affilié au jeu ColorDigitLogic d'origine.*

## Indépendance du projet

ColorDigitLogic est un projet personnel indépendant, non affilié aux créateurs du jeu Acrylogic. Les grilles d’origine ne sont pas distribuées avec cette application.


## Version 16 — Contrôle des erreurs

En mode jeu, la saisie d'un chiffre ou d'une couleur est comparée aux indices voisins dès que les deux valeurs nécessaires sont renseignées. Toute nouvelle contradiction incrémente le compteur d'erreurs. Le compteur est inclus dans les exports JSON et les sauvegardes locales. Annuler une action ne retire pas les erreurs déjà commises.


## Version 17 — Solveur (étape 1)

Le bouton **Résoudre** cherche une affectation des paires chiffre-couleur respectant tous les indices, les cases déjà saisies et l'unicité de chaque paire. Il recherche jusqu'à deux solutions pour distinguer une solution unique de plusieurs solutions, avec une limite de 7 secondes. Une solution trouvée peut être affichée après confirmation. Le calcul s'effectue localement dans le navigateur.

## Version 18 — Vérification par solution unique

Au passage en **mode jeu**, l'application calcule une solution de référence à partir des **indices seuls**, en ignorant volontairement toutes les valeurs déjà saisies dans les cases. Si une seule solution est trouvée et que la recherche se termine sans dépasser le délai, chaque chiffre et couleur nouvellement saisi est immédiatement comparé à cette solution.

- Une saisie incorrecte augmente le compteur d'erreurs **une seule fois**, même si elle contredit également un indice.
- Cliquer une deuxième fois sur une valeur déjà présente ne compte pas comme une nouvelle saisie.
- Les erreurs sont comptabilisées même si les cases voisines sont encore vides.
- Si plusieurs solutions existent, si aucune solution n'existe ou si le calcul dépasse 7 secondes, seul le contrôle des indices voisins est appliqué.
- Modifier les indices invalide la solution de référence. Elle est recalculée lors du prochain passage en mode jeu.
- Le bouton **Résoudre** continue de tenir compte des valeurs actuellement présentes dans les cases, contrairement au calcul de la solution de référence.
- Les sauvegardes JSON et les records restent compatibles avec les versions précédentes.

**Limite connue :** la recherche s'exécute dans le navigateur ; sur une grille difficile, l'interface peut être momentanément occupée pendant le calcul.


## Version 19 — Générateur de grilles

Le bouton **Générer une grille** crée une répartition aléatoire de toutes les paires chiffre-couleur, calcule un indice par frontière (somme ou mélange), puis utilise le solveur pour rechercher une grille à solution unique. Une fois cette unicité établie, il retire des indices tant que l'unicité reste démontrée.

- Les cases sont **vides** dans la grille créée : il faut passer en mode jeu pour la résoudre.
- Les grilles ne sont annoncées comme **uniques** que lorsque le solveur a terminé la vérification sans dépasser son délai.
- Si la recherche échoue, la grille en cours est conservée.
- Le générateur travaille localement dans le navigateur, sans serveur.
- Le résultat est exportable en JSON comme les autres grilles.
- **Limites :** la génération peut prendre plusieurs secondes, notamment en 5×6 ; la difficulté n'est pas encore calibrée, et la suppression des indices est une heuristique, pas une minimisation garantie.
