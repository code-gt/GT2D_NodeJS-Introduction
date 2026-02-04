
## Express.js

### 3. Installe le paquet Express.js
Express.js est un framework pour construire des applications web basées sur NodeJS. C'est le framework standard pour le développement de serveur en NodeJS.

#### Installe Express.js : 
Dans le terminal, tape la commande suivante :

```sh
npm install express
```

#### Crée un fichier index.js : 
À la racine de ton dossier, crée un fichier `index.js` et copie-colle le code suivant depuis le site officiel : [Express Hello World](https://expressjs.com/fr/starter/hello-world.html).

#### Lance ton programme Node.js : 
Dans le terminal, tape :

```sh
node index.js
```

Si tout fonctionne, tu devrais pouvoir accéder à l'adresse `http://localhost:3000`.

### 4. Fais ta première route GET /ma-page
En backend, une "route" est simplement une adresse web. On peut interroger une adresse web de deux façons : `GET` ou `POST`.

#### Création d'une nouvelle route GET
Le but de cet exercice est de créer une nouvelle route en `GET` avec l'adresse `/ma-page`, ce qui donnera l'URL `http://localhost:3000/ma-page`. Ajoute ce code dans ton fichier `index.js` :

```js
app.get('/ma-page', (req, res) => {
    res.send('Bienvenue sur ma page!');
});
```

Pour tester ta nouvelle route, relance le serveur en arrêtant le précédent (Ctrl+C dans le terminal) et en relançant la commande :

```sh
node index.js
```

Puis, visite http://localhost:3000/ma-page.
