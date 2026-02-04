## Manipulation de fichiers simples

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
