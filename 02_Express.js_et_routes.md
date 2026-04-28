
# 02 - Express.js et Routes

## 🎯 Objectifs de cette étape

À la fin de cette section, tu devras :

- ✅ Comprendre ce qu'est Express.js et à quoi ça sert

- ✅ Installer Express.js dans ton projet

- ✅ Créer ton premier serveur web

- ✅ Créer et tester des routes GET

- ✅ Comprendre la différence entre GET et POST

---

## 📚 Concepts clés

### Qu'est-ce qu'Express.js ?

**Express.js** est un **framework web** pour Node.js. C'est une bibliothèque qui simplifie la création d'un serveur web.

**Sans Express :** Tu devrais écrire beaucoup de code compliqué pour gérer les routes
**Avec Express :** Tu peux créer des routes en quelques lignes

Express.js est **le framework standard** pour le développement web en Node.js.

### Qu'est-ce qu'une route ?

Une **route** est simplement une **adresse web** (URL) que tu peux visiter.

**Exemples de routes :**

- `http://localhost:3000/` (page d'accueil)

- `http://localhost:3000/ma-page` (une page personnalisée)

- `http://localhost:3000/contact` (page de contact)

- `http://localhost:3000/utilisateurs` (liste d'utilisateurs)

### GET vs POST

Il existe deux façons principales de communiquer avec un serveur web :

**GET :**

- ✅ Récupère des données du serveur

- ✅ Les paramètres sont visibles dans l'URL

- ✅ Pas sécurisé pour les données sensibles

- **Exemple :** `http://localhost:3000/search?q=javascript`

**POST :**

- ✅ Envoie des données au serveur

- ✅ Les paramètres ne sont pas visibles dans l'URL

- ✅ Plus sécurisé pour les données sensibles

- **Exemple :** Soumettre un formulaire de connexion

**Pour maintenant :** On va utiliser **GET** qui est plus simple. On verra POST plus tard.

### req et res

Quand une personne visite une route, Express.js crée deux objets :

**req (request = requête) :**

- Les informations que l'utilisateur envoie au serveur

- Exemple : les paramètres dans l'URL, les données du formulaire, etc.

**res (response = réponse) :**

- Ce que tu envoies au navigateur de l'utilisateur

- Exemple : du HTML, du texte, du JSON, etc.

**Flux :**

    Utilisateur visite URL
         ↓
    Express crée req et res
         ↓
    Tu écris du code dans la route
         ↓
    Tu envoies une réponse avec res.send()
         ↓
    Utilisateur reçoit la réponse dans son navigateur

### Qu'est-ce que localhost:3000 ?

**localhost** = Votre ordinateur (le serveur local)
**3000** = Un numéro de port (une "porte" sur votre ordinateur)

Quand vous tapez `http://localhost:3000`, vous visitez un serveur qui tourne sur **votre propre ordinateur**.

---

## 🚀 Installation d'Express.js

### Étape 3.1 : Installer Express.js

Assurez-vous que vous êtes dans le dossier de votre projet (voir étape 02), puis dans le terminal, tapez :

    npm install express

Cela va **télécharger Express.js** et l'ajouter à votre projet. Vous verrez apparaître un dossier `node_modules` (qui contient Express) et votre `package.json` sera mis à jour.

### Étape 3.2 : Créer un fichier index.js

À la racine de votre dossier de projet, créez un fichier `index.js`. C'est le fichier principal de votre serveur.

Copiez ce code de base (du site officiel Express) :

    const express = require('express');
    const app = express();

    app.get('/', (req, res) => {
      res.send('Hello World!');
    });

    app.listen(3000, () => {
      console.log('Serveur lancé sur http://localhost:3000');
    });

**Explication :**

- `require('express')` = Importe Express

- `const app = express()` = Crée une application Express

- `app.get('/', ...)` = Crée une route GET pour la page d'accueil

- `res.send('Hello World!')` = Envoie du texte au navigateur

- `app.listen(3000, ...)` = Lance le serveur sur le port 3000

### Étape 3.3 : Lancer ton serveur

Dans le terminal, tapez :

    node index.js

Vous devriez voir :

    Serveur lancé sur http://localhost:3000

Ouvrez votre navigateur et allez à l'adresse : **http://localhost:3000**

Vous devriez voir : **Hello World!**

✅ **Bravo ! Votre premier serveur Node.js fonctionne !**

### Pour arrêter le serveur

Dans le terminal, appuyez sur **Ctrl + C**

---

## 🛣️ Créer des routes

### Qu'est-ce qu'une route GET ?

Une route GET permet de **répondre quand quelqu'un visite une adresse web**.

**Syntaxe :**

    app.get('/adresse', (req, res) => {
      res.send('Réponse à envoyer');
    });

### Étape 4.1 : Créer ta première route personnalisée

Dans votre fichier `index.js`, **après** la route `/` et **avant** `app.listen(...)`, ajoutez cette nouvelle route :

    app.get('/ma-page', (req, res) => {
      res.send('Bienvenue sur ma page!');
    });

Votre `index.js` devrait maintenant ressembler à :

    const express = require('express');
    const app = express();

    app.get('/', (req, res) => {
      res.send('Hello World!');
    });

    app.get('/ma-page', (req, res) => {
      res.send('Bienvenue sur ma page!');
    });

    app.listen(3000, () => {
      console.log('Serveur lancé sur http://localhost:3000');
    });

### Étape 4.2 : Redémarrer le serveur et tester

1. Arrêtez le serveur actuel : **Ctrl + C**
2. Relancez-le : `node index.js`
3. Visitez : **http://localhost:3000/ma-page**

Vous devriez voir : **Bienvenue sur ma page!**

✅ **Vous venez de créer votre première route !**

---

## 💡 Conseil pour gagner du temps : Nodemon

Chaque fois que vous modifiez le code, vous devez arrêter et relancer le serveur. C'est pénible !

**Nodemon** redémarre le serveur **automatiquement** quand vous sauvegardez votre fichier.

### Installation de Nodemon

    npm install --save-dev nodemon

### Utiliser Nodemon

Au lieu de taper `node index.js`, tapez :

    npx nodemon index.js

Maintenant, quand vous modifiez votre code et que vous sauvegardez (Ctrl + S), le serveur redémarre automatiquement !

---

## 🎓 Qu'avez-vous appris ?

À cette étape, vous devez comprendre :

- ✅ **Express.js** = Framework pour créer des serveurs web

- ✅ **Route** = Une adresse web que vous pouvez visiter

- ✅ **GET** = Récupérer des données

- ✅ **req et res** = La requête et la réponse

- ✅ **localhost:3000** = Votre serveur local

- ✅ Comment créer et tester une route simple

- ✅ Comment redémarrer le serveur après modifications

---

## 🐛 Ça ne marche pas ?

### ❌ "Cannot find module 'express'"

**Cause :** Express n'est pas installé.

**Solution :**
1. Vérifiez que vous êtes dans le bon dossier (celui avec `package.json`)
2. Lancez `npm install express`
3. Relancez votre serveur

### ❌ "Port 3000 already in use" / "Port déjà utilisé"

**Cause :** Un autre serveur utilise déjà le port 3000.

**Solutions :**
1. Arrêtez le serveur précédent (Ctrl + C)
2. Ou changez le port : `app.listen(3001, ...)` pour utiliser le port 3001

### ❌ "ERR_HTTP_HEADERS_ALREADY_SENT"

**Cause :** Vous avez appelé `res.send()` deux fois dans la même route.

**Solution :** N'appelez `res.send()` qu'une seule fois par route.

### ❌ Les modifications ne s'appliquent pas

**Cause :** Vous n'avez pas redémarré le serveur.

**Solution :** Appuyez sur Ctrl + C pour arrêter, puis relancez `node index.js`

**Astuce :** Utilisez nodemon pour redémarrer automatiquement (voir section ci-dessus)

---

## 🎯 Défi : Créer tes propres routes

Essayez de créer ces routes dans votre `index.js` :

1. Une route `/contact` qui affiche "Page de contact"
2. Une route `/about` qui affiche "À propos de nous"
3. Une route `/utilisateurs` qui affiche une liste de prénoms

Testez chaque route dans votre navigateur !

---

## 💡 Ressources Utiles

- 📖 [Documentation officielle Express.js](https://expressjs.com/fr/)

- 📖 [Guide Express en français](https://expressjs.com/fr/starter/hello-world.html)

- 🎥 [Tutoriel Express.js (EN)](https://www.youtube.com/watch?v=SccSCuHhOw0)

---

## 🚀 Prochaine étape

Maintenant que tu maîtrises les routes simples, tu vas apprendre à :

- Afficher du **vrai HTML** (pas juste du texte)

- Manipuler des **fichiers**

- Traiter des données de **formulaires**

👉 **[03 - Manipuler un fichier](./03_Manipuler_un_fichier.md)**

Tu vas créer des formulaires et sauvegarder les données dans des fichiers ! 🚀
