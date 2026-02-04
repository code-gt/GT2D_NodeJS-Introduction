## Exercices 

### Exercice 1 : Afficher une page HTML
Crée une nouvelle route GET avec l'adresse `/page-html` qui affiche une page HTML contenant un titre `<h1>`, un paragraphe `<p>` avec un texte lambda et une image `<img>`de ton choix.

### Exercice 2 : Afficher une liste de courses
Crée une nouvelle route GET avec l'adresse `/courses` qui affiche une liste de courses sous forme de texte. Utilise `<ul>` et `<li>` pour afficher tout ceci.

### Exercice 3 : Faire un lien HTML
Crée une nouvelle route GET avec l'adresse `/lien` qui renvoie à la pase `/courses`grâce à une balise `<a>`.

### Exercice 4 : Afficher l'heure actuelle
Crée une nouvelle route GET avec l'adresse `/heure` qui affiche l'heure actuelle. Utilise la fonction `new Date()` pour obtenir la date et l'heure actuelle.  
Essaye de la formater de la manière suivante : HH:MM:SS.

### Exercice 5 : Quiz et réponse conditionnelle
Créez une route `/quiz` qui récupère le paramètre GET `reponse` depuis l’URL.  

 ```js
   const reponse = req.query.reponse || '';
```

Créez une variable `correct` qui contient la bonne réponse et une variable `message` vide.  
Comparez la valeur à la bonne réponse (`B`) avec une condition `if / else`.  
Affichez du HTML contenant : la question, trois liens `<a>` pour répondre (`A`, `B`, `C`) et un `message` (par exemple dans une balise `<p>`) indiquant si la réponse est correcte ou non.  

```js
  // Exemple de lien à inclure
  <a href="/quiz?reponse=A">A) Réponse A</a>
```

Testez en cliquant sur les liens et observez la réaction dynamique selon la réponse choisie.
