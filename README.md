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


### 5. Aller plus loin en manipulant les fichiers
Nous allons maintenant créer un formulaire HTML sur `/ma-page` et traiter les données soumises pour créer un fichier.

#### Afficher un formulaire HTML
Remplace le contenu de la route `/ma-page` par ceci :

```js
app.get('/ma-page', (req, res) => {
    res.send(`
        <form action="/creer-fichier">
            <input type="text" name="fichier">
            <button type="submit">Envoyer</button>
        </form>
    `);
});
```

#### Créer une route pour traiter le formulaire
Ajoute cette nouvelle route à ton fichier `index.js` :

```js
// Requête GET pour récupérer les données du formulaire
app.get('/creer-fichier', (req, res) => { 
    const fs = require('fs'); // Appel à la bibliothèque file system qui permet de manipuler les fichiers
    const content = req.query.fichier; // req.query permet d'accéder aux paramètres de la requête

    try {
        // Création d'un fichier txt via la la méthode fs.writeFileSync
        // Deux arguments : le nom du fichier et le contenu à écrire
        fs.writeFileSync('test.txt', content);
        // retour de la réponse
        res.send("Fichier créé !");
    }
    // Gestion des erreurs
    catch (err) {
        console.error(err);
        res.send("Échec de création du fichier.");
    }
});
```

Maintenant, envoie une phrase via le formulaire sur `/ma-page` et observe la création d'un fichier `test.txt` contenant le texte saisi.

### Créer un fichier différent à chaque fois
Pour créer un fichier unique à chaque soumission, utilise un nom de fichier dynamique.
Voici un guide détaillé :

1. Importer fs : `const fs = require('fs');`
2. Récupérer le contenu de l'input : `const content = req.query.fichier;`
3. Générer un nom de fichier unique : `const fileName = \file_${Date.now()}.txt`;`
4. Écrire dans le fichier : `fs.writeFileSync(fileName, content);`
5. Envoyer une réponse : `res.send(\Fichier ${fileName} créé !`);`


Maintenant, chaque soumission créera un nouveau fichier avec un nom unique.

Bravo! Passsons à quelques exercices simples.

## Exercices 

### Exercice 1 : Afficher une page HTML
Crée une nouvelle route en GET avec l'adresse `/page-html` qui affiche une page HTML contenant un titre `<h1>`, un paragraphe `<p>` avec un texte lambda et une image `<img>`de ton choix.

### Exercice 2 : Afficher une liste de courses
Crée une nouvelle route en GET avec l'adresse `/courses` qui affiche une liste de courses sous forme de texte. Utilise `<ul>` et `<li>` pour afficher tout ceci.

### Exercice 3 : Afficher l'heure actuelle
Crée une nouvelle route en GET avec l'adresse `/heure` qui affiche l'heure actuelle. Utilise la fonction `new Date()` pour obtenir la date et l'heure actuelle.  
Essaye de la formater de la manière suivante : HH:MM:SS.
