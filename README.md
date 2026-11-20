# Acrylogic

**Acrylogic** est une application web indépendante permettant de recopier, compléter et vérifier des grilles de logique mêlant **nombres et couleurs**. Elle fonctionne sur ordinateur, tablette et téléphone, directement dans le navigateur.

**Version actuelle : V14** — application web installable (PWA), avec prise en charge du fonctionnement hors ligne après un premier chargement.

**Jouer :** https://pixou2000.github.io/Acrylogic/

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

## Installer Acrylogic sur iPhone ou iPad

1. Ouvrir https://pixou2000.github.io/Acrylogic/ dans **Safari**.
2. Toucher le bouton **Partager**.
3. Choisir **Sur l'écran d'accueil**, puis **Ajouter**.
4. Lancer Acrylogic depuis l'icône ajoutée.

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

*Projet personnel indépendant, non affilié au jeu Acrylogic d'origine.*
