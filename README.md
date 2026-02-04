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
