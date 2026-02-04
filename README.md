# Introduction à Node.js

**Présentation :** [Lien vers la présentation](https://docs.google.com/presentation/d/1jf586G62z-13970_4TmWhnYsR9jZUjg8rGzMNwfTQkg/edit?usp=sharing)

## Crée ton premier code backend

### 1. Installe Node.js et NPM

Pour commencer, rends-toi sur la page officielle de [Node.js](https://nodejs.org/) et télécharge la version LTS (Long Term Support), qui est la version stable recommandée, pour Windows ou ta plateforme.

L'installateur pour Windows installe à la fois Node.js et NPM.

#### Vérification de l'installation

L'installation de Node.js ajoutera la commande `node` dans ton terminal (Windows, VSCode, etc.). Pour vérifier que tout est bien installé, ouvre un terminal et tape les commandes suivantes :

```sh
node -v
npm -v
```

Ces commandes devraient afficher les versions de Node.js et NPM installées.

#### Utilisation du terminal
Nous utiliserons souvent le terminal pour exécuter des programmes Node.js. La commande node te permettra de lancer des programmes Node.js directement depuis le terminal.

NPM (Node Package Manager) te permettra d'ajouter des bibliothèques (ou "paquets") à ton projet. Il installe également la commande npm.

### 2. Initialise ton projet backend
Crée un dossier de projet : Ouvre un nouveau dossier vide dans VSCode.
Ouvre un terminal dans VSCode : Va dans le menu Terminal > Nouveau Terminal.
Dans le terminal qui apparaît, tape la commande suivante :

```sh
npm init
```

Réponds aux questions posées. Cela créera un fichier `package.json` à la racine de ton dossier. Ce fichier de configuration - présent dans tout projet JavaScript utilisant des plugins Node - contiendra entre autres la liste des bibliothèques que tu installeras.

## Exercices 

### Exercice 1 : Afficher une page HTML
Crée une nouvelle route en GET avec l'adresse `/page-html` qui affiche une page HTML contenant un titre `<h1>`, un paragraphe `<p>` avec un texte lambda et une image `<img>`de ton choix.

### Exercice 2 : Afficher une liste de courses
Crée une nouvelle route en GET avec l'adresse `/courses` qui affiche une liste de courses sous forme de texte. Utilise `<ul>` et `<li>` pour afficher tout ceci.

### Exercice 3 : Afficher l'heure actuelle
Crée une nouvelle route en GET avec l'adresse `/heure` qui affiche l'heure actuelle. Utilise la fonction `new Date()` pour obtenir la date et l'heure actuelle.  
Essaye de la formater de la manière suivante : HH:MM:SS.
