
# 03 - Manipuler un Fichier

## 🎯 Objectifs de cette étape

À la fin de cette section, tu devras :

- ✅ Comprendre ce qu'est le module `fs` (File System)

- ✅ Afficher un formulaire HTML dans une route

- ✅ Récupérer les données d'un formulaire

- ✅ Créer des fichiers dynamiquement

- ✅ Gérer les erreurs (try/catch)

- ✅ Créer des fichiers avec des noms uniques

---

## 📚 Concepts clés

### Qu'est-ce que fs (File System) ?

**fs** = **File System** (Système de Fichiers)

C'est un **module Node.js** qui permet de :

- 📁 Créer des fichiers

- 📖 Lire le contenu des fichiers

- ✏️ Modifier des fichiers

- 🗑️ Supprimer des fichiers

**Exemple :** Au lieu de créer manuellement des fichiers dans votre ordinateur, vous pouvez demander à Node.js de les créer automatiquement avec du code.

### Synchrone vs Asynchrone

Il existe deux façons d'utiliser fs :

**Synchrone (Sync) :**

- ⏸️ Le code s'arrête et attend la fin de l'opération

- ✅ Plus facile à comprendre

- ❌ Moins performant

- **Exemple :** `fs.writeFileSync()`

**Asynchrone :**

- ⚡ Le code continue sans attendre

- ✅ Plus performant

- ❌ Plus compliqué

- **Exemple :** `fs.writeFile()`

**Pour maintenant :** On va utiliser **Synchrone** qui est plus facile.

### req.query : Les paramètres GET

Quand vous cliquez sur un lien comme `http://localhost:3000/creer-fichier?fichier=MonTexte`, les données après le `?` s'appellent des **paramètres GET**.

**Comment y accéder :**

    const valeur = req.query.fichier;  // récupère la valeur "MonTexte"

**Format :**

    http://localhost:3000/route?nom=valeur&autre=valeur2
                               └─ paramètre GET

### Try/Catch : Gérer les erreurs

Parfois, une opération peut échouer (fichier non trouvable, permissions insuffisantes, etc.).

**Try/Catch** permet de gérer les erreurs gracieusement :

    try {
      // Code qui peut échouer
      fs.writeFileSync('test.txt', 'contenu');
    } catch (err) {
      // Code exécuté si une erreur survient
      console.error(err);
    }

**Flux :**

- Si tout va bien → exécute le code du `try`

- S'il y a une erreur → exécute le code du `catch`

### Date.now() : Un timestamp unique

`Date.now()` retourne le **nombre de millisecondes écoulées depuis 1970**.

Chaque fois que vous l'appelez, vous obtenez un **nombre différent**.

**Utilité :** Créer des noms de fichiers uniques

    const fileName = 'file_' + Date.now() + '.txt';
    // Résultat : file_1719585342123.txt (chaque fois différent)

---

## 🚀 Créer un formulaire HTML

### Étape 5.1 : Afficher un formulaire

Dans votre fichier `index.js`, **modifiez** la route `/ma-page` pour afficher un formulaire HTML :

    app.get('/ma-page', (req, res) => {
      res.send(`
        <h1>Créer un fichier</h1>
        <form action="/creer-fichier">
          <input type="text" name="fichier" placeholder="Tapez du texte">
          <button type="submit">Envoyer</button>
        </form>
      `);
    });

**Explication :**

- `` ` `` (backticks) = Permet d'écrire du HTML sur plusieurs lignes

- `<form action="/creer-fichier">` = Quand on soumet, ça va à la route `/creer-fichier`

- `name="fichier"` = Le nom du paramètre GET (sera `req.query.fichier`)

### Étape 5.2 : Tester le formulaire

1. Redémarrez votre serveur
2. Allez à `http://localhost:3000/ma-page`
3. Vous devriez voir un formulaire avec un champ texte et un bouton

**Important :** Ne soumettez pas encore ! Vous allez obtenir une erreur car la route `/creer-fichier` n'existe pas.

---

## 📁 Créer un fichier

### Étape 5.3 : Créer la route `/creer-fichier`

Dans votre `index.js`, **après la route `/ma-page`**, ajoutez cette nouvelle route :

    app.get('/creer-fichier', (req, res) => {
      const fs = require('fs');
      const content = req.query.fichier;

      try {
        fs.writeFileSync('test.txt', content);
        res.send('Fichier créé !');
      } catch (err) {
        console.error(err);
        res.send('Erreur lors de la création du fichier.');
      }
    });

**Explication :**

- `const fs = require('fs');` = Importe le module fs

- `req.query.fichier` = Récupère la valeur du formulaire

- `fs.writeFileSync('test.txt', content)` = Crée un fichier `test.txt` avec le contenu

- `try/catch` = Gère les erreurs

### Étape 5.4 : Tester la création de fichier

1. Redémarrez votre serveur
2. Allez à `http://localhost:3000/ma-page`
3. Tapez du texte dans le formulaire
4. Cliquez sur "Envoyer"
5. Vous devriez voir "Fichier créé !"
6. Dans votre dossier projet, vous devriez voir un fichier `test.txt` avec le contenu

✅ **Bravo ! Vous venez de créer votre premier fichier avec Node.js !**

---

## 🔄 Créer des fichiers uniques

### Problème : Fichier écrasé

Actuellement, chaque fois que vous soumettez le formulaire, le fichier `test.txt` est **écrasé** (le contenu ancien est supprimé).

Pour créer un **nouveau fichier à chaque fois**, vous devez utiliser un **nom différent**.

### Étape 5.5 : Utiliser Date.now()

Modifiez la route `/creer-fichier` pour créer des fichiers uniques :

    app.get('/creer-fichier', (req, res) => {
      const fs = require('fs');
      const content = req.query.fichier;
      const fileName = 'file_' + Date.now() + '.txt';

      try {
        fs.writeFileSync(fileName, content);
        res.send(`Fichier ${fileName} créé !`);
      } catch (err) {
        console.error(err);
        res.send('Erreur lors de la création du fichier.');
      }
    });

**Explication :**

- `Date.now()` = Retourne un nombre unique (timestamp)

- `'file_' + Date.now() + '.txt'` = Crée un nom comme `file_1719585342123.txt`

- Chaque fichier a un nom différent, donc rien n'est écrasé

### Étape 5.6 : Tester les fichiers uniques

1. Redémarrez votre serveur
2. Soumettez le formulaire plusieurs fois avec différents textes
3. Observez dans votre dossier projet : Vous devriez voir plusieurs fichiers comme :
   - `file_1719585342123.txt`
   - `file_1719585342456.txt`
   - `file_1719585342789.txt`

✅ **Chaque soumission crée un nouveau fichier !**

---

## 🎓 Qu'avez-vous appris ?

À cette étape, vous devez comprendre :

- ✅ **fs** = Module pour manipuler les fichiers

- ✅ **fs.writeFileSync()** = Créer et écrire dans un fichier

- ✅ **req.query** = Accéder aux paramètres GET du formulaire

- ✅ **try/catch** = Gérer les erreurs

- ✅ **Date.now()** = Créer des noms uniques

- ✅ Comment afficher un formulaire HTML dans une route

- ✅ Comment traiter les données du formulaire

---

## 🐛 Ça ne marche pas ?

### ❌ "Cannot find module 'fs'"

**Cause :** `fs` n'est pas importé correctement.

**Solution :**
Assurez-vous d'avoir cette ligne en haut de votre route :

    const fs = require('fs');

### ❌ "EACCES: permission denied"

**Cause :** Node.js n'a pas la permission de créer des fichiers.

**Solutions :**
1. Vérifiez que votre dossier de projet n'est pas protégé
2. Essayez de lancer VSCode en mode administrateur
3. Changez le dossier du projet

### ❌ "ENOENT: no such file or directory"

**Cause :** Le fichier ou le dossier n'existe pas.

**Solution :**
Assurez-vous que vous écrivez dans le dossier actuel (où est `index.js`), pas dans un sous-dossier.

### ❌ Le fichier ne s'affiche pas dans le dossier

**Causes possibles :**
1. Le fichier a été créé dans le mauvais dossier
2. VSCode ne l'affiche pas (appuyez sur F5 pour rafraîchir)

**Solution :**
1. Dans VSCode, appuyez sur **Ctrl + Shift + E** pour ouvrir l'explorateur
2. Regardez s'il y a des fichiers `file_*.txt`

### ❌ Le formulaire ne soumet rien

**Cause :** Vous avez oublié l'attribut `name` sur l'input.

**Solution :**
Assurez-vous que votre input ressemble à :

    <input type="text" name="fichier">

---

## 🎯 Défi : Améliorer le formulaire

Essayez ces améliorations :

1. **Ajouter un champ pour le nom du fichier :**
   - L'utilisateur choisit le nom du fichier ET le contenu
   - Créez un fichier avec le nom choisi

2. **Ajouter du style CSS :**
   - Rendez le formulaire joli avec du CSS

3. **Afficher un message de succès :**
   - Après création, montrez un lien vers le fichier créé

---

## 📖 Pour aller plus loin

### Lire un fichier

Vous pouvez aussi **lire** le contenu d'un fichier :

    const fs = require('fs');
    const content = fs.readFileSync('test.txt', 'utf8');
    console.log(content);

### Supprimer un fichier

Et **supprimer** des fichiers :

    const fs = require('fs');
    fs.unlinkSync('test.txt');

### Asynchrone (pour plus tard)

Pour des opérations plus performantes, utilisez les versions asynchrones :

    fs.writeFile('test.txt', content, (err) => {
      if (err) console.error(err);
      else console.log('Fichier créé !');
    });

---

## 💡 Ressources Utiles

- 📖 [Documentation fs (Node.js)](https://nodejs.org/api/fs.html)

- 📖 [Guide fs en français](https://www.w3schools.com/nodejs/nodejs_filesystem.asp)

- 🎥 [Tutoriel fs (EN)](https://www.youtube.com/watch?v=ENrzD6AvFZE)

---

## 🚀 Prochaine étape

Maintenant que tu maîtrises la création de fichiers, tu es prêt pour :

👉 **[04 - Exercices](./04_Exercices_simples.md)**

Tu vas mettre en pratique tout ce que tu as appris ! 🚀
