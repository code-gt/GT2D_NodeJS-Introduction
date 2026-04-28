# Introduction à Node.js



![NodeJS](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d9/Node.js_logo.svg/330px-Node.js_logo.svg.png "NodeJS").

**Présentation :** [Lien vers la présentation](https://docs.google.com/presentation/d/1jf586G62z-13970_4TmWhnYsR9jZUjg8rGzMNwfTQkg/edit?usp=sharing)

## Crée ton premier code backend


# 01 - Installation et Initialisation

## 🎯 Objectifs de cette étape

À la fin de cette section, tu devras :

- ✅ Avoir installé Node.js et NPM sur ton ordinateur

- ✅ Comprendre ce qu'est Node.js et NPM

- ✅ Créer et configurer ton premier projet Node.js

- ✅ Pouvoir lancer des commandes dans le terminal

- ✅ Avoir un fichier `package.json` configuré et prêt

---

## 📚 Concepts clés

### Qu'est-ce que Node.js ?

**Node.js** est un **environnement d'exécution JavaScript** qui te permet de faire tourner du JavaScript **en dehors du navigateur**, directement sur ton ordinateur.

**Avant Node.js :** JavaScript = seulement dans le navigateur (frontend)
**Après Node.js :** JavaScript = sur ton serveur aussi (backend) ✨

### Qu'est-ce que NPM ?

**NPM** = **Node Package Manager** (Gestionnaire de Paquets Node)

C'est un outil qui te permet de :

- 📦 **Installer des bibliothèques** (du code réutilisable écrit par d'autres)

- 🔄 **Gérer les versions** de tes dépendances

- 📋 **Organiser ton projet** avec un fichier `package.json`

**Exemple :** Au lieu de réécrire un framework web from scratch, tu peux installer Express.js en 1 ligne :

    npm install express

### Qu'est-ce que package.json ?

`package.json` est un fichier de **configuration** qui décrit ton projet. Il contient :

- 📝 Le nom et la version de ton projet

- 📦 La liste des bibliothèques installées (dépendances)

- 🔧 Les scripts pour lancer ton code

- 👤 Auteur, licence, etc.

**Exemple :**

    {
      "name": "mon-projet-nodejs",
      "version": "1.0.0",
      "description": "Mon premier serveur Node.js",
      "main": "index.js",
      "scripts": {
        "start": "node index.js"
      },
      "dependencies": {
        "express": "^4.18.2"
      }
    }

---

## 🚀 Installation de Node.js

### Étape 1.1 : Télécharger Node.js

1. Rendez-vous sur le site officiel : **[nodejs.org](https://nodejs.org/)**
2. Vous verrez deux boutons :
   - **LTS** (Long Term Support) = Version stable, recommandée ✅
   - **Current** = Version la plus récente, mais moins stable
3. Cliquez sur **LTS** et téléchargez la version pour **votre système** (Windows, Mac, Linux)

### Étape 1.2 : Installer Node.js

**Sur Windows :**
1. Lancez le fichier `.msi` téléchargé
2. Suivez l'installateur (cliquez "Next" partout)
3. À la fin, cochez **"Automatically install the necessary tools"** (si disponible)
4. L'installation installe **automatiquement Node.js ET NPM** ensemble

**Sur Mac/Linux :**
Consultez le guide officiel : [Installation Node.js Mac/Linux](https://nodejs.org/en/download/package-manager/)

### Étape 1.3 : Vérifier l'installation

Ouvrez un **terminal** :
- **Windows :** Utilisez `cmd` ou PowerShell (ou le terminal de VSCode)

- **Mac :** Utilisez Terminal.app

- **Linux :** Utilisez votre terminal habituel

Tapez ces deux commandes pour vérifier :

    node -v

Vous devriez voir : `v18.x.x` (ou une version plus récente)

    npm -v

Vous devriez voir : `9.x.x` (ou une version plus récente)

✅ **Si vous voyez des numéros de version, c'est bon !**

---

## ✅ Checklist : Installation réussie ?

- [ ] Node.js téléchargé et installé

- [ ] Terminal ouvert sur votre ordinateur

- [ ] La commande `node -v` affiche une version

- [ ] La commande `npm -v` affiche une version

- [ ] Aucun message d'erreur type "command not found"

**Si vous cochez tout : vous êtes prêt(e) pour la suite ! 🎉**

---

## 🎬 Initialiser ton premier projet

### Étape 2.1 : Créer un dossier de projet

1. Créez un dossier vide sur votre ordinateur, par exemple : `mon-serveur-nodejs`
2. Ouvrez ce dossier avec **VSCode** (File > Open Folder)

### Étape 2.2 : Ouvrir le terminal dans VSCode

Dans VSCode, allez à : **Terminal** → **New Terminal** (ou Ctrl + `)

Vous devriez voir un terminal s'ouvrir en bas de l'écran, et il devrait être positionné dans votre dossier.

**Vérification :** Tapez la commande :

    pwd

(Mac/Linux) ou

    cd

(Windows)

Vous devriez voir le chemin vers votre dossier.

### Étape 2.3 : Initialiser ton projet avec npm

Dans le terminal, tapez :

    npm init

NPM vous posera une série de questions. Voici comment répondre :

| Question | Réponse | Explication |
|----------|---------|-------------|
| `package name` | Appuyez sur **Entrée** | Prendra le nom du dossier |
| `version` | Appuyez sur **Entrée** | `1.0.0` par défaut |
| `description` | Appuyez sur **Entrée** | Vous pouvez le laisser vide |
| `entry point` | Appuyez sur **Entrée** | Garder `index.js` |
| `test command` | Appuyez sur **Entrée** | À ignorer pour maintenant |
| `git repository` | Appuyez sur **Entrée** | À ignorer pour maintenant |
| `keywords` | Appuyez sur **Entrée** | À ignorer pour maintenant |
| `author` | Appuyez sur **Entrée** | Vous pouvez mettre votre nom |
| `license` | Appuyez sur **Entrée** | `ISC` par défaut |
| `Is this OK?` | Tapez **yes** | Valide la configuration |

**💡 Conseil :** Si vous êtes bloqué sur une question, appuyez simplement sur **Entrée** pour accepter la valeur par défaut.

### Étape 2.4 : Vérifier la création du package.json

Après avoir répondu aux questions, un fichier `package.json` devrait apparaître dans votre dossier VSCode.

Cliquez dessus pour l'ouvrir et consultez son contenu. Il devrait ressembler à :

    {
      "name": "mon-serveur-nodejs",
      "version": "1.0.0",
      "description": "",
      "main": "index.js",
      "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1"
      },
      "author": "",
      "license": "ISC"
    }

✅ **C'est parfait ! Ton projet est maintenant initialisé.**

---

## 🎓 Qu'avez-vous appris ?

À cette étape, vous devez comprendre :

- ✅ **Node.js** = JavaScript sur le serveur

- ✅ **NPM** = Gestionnaire de bibliothèques et de dépendances

- ✅ **package.json** = Configuration de ton projet, liste des dépendances

- ✅ Comment ouvrir un terminal et exécuter des commandes

- ✅ Comment initialiser un projet avec `npm init`

---

## 🐛 Ça ne marche pas ?

### ❌ "Erreur : command not found: node"

**Cause :** Node.js n'est pas installé ou le terminal ne le reconnaît pas.

**Solutions :**
1. Vérifiez que vous avez bien lancé l'installateur Node.js
2. Redémarrez votre terminal (fermez et rouvrez)
3. Redémarrez votre ordinateur
4. Réinstallez Node.js en suivant les étapes de [nodejs.org](https://nodejs.org/)

### ❌ "Erreur : EACCES: permission denied"

**Cause :** Problème de permissions sur Mac/Linux.

**Solution :** Demandez à votre formateur ou consultez [cette page NPM](https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally).

### ❌ "npm init" ne pose pas de questions

**Cause :** C'est normal ! NPM utilise un mode rapide.

**Solution :** C'est ok, votre `package.json` a quand même été créé. Passez à l'étape suivante.

### ❌ "Je ne vois pas le fichier package.json"

**Solution :**
1. Dans VSCode, appuyez sur **Ctrl + Shift + P** (Windows) ou **Cmd + Shift + P** (Mac)
2. Tapez "Explorer" et sélectionnez "Focus on File Explorer"
3. Vous devriez voir le fichier `package.json`

---

## 💡 Ressources Utiles

- 📖 [Documentation officielle Node.js](https://nodejs.org/en/docs/)

- 📖 [Documentation officielle NPM](https://docs.npmjs.com/)

- 🎥 [Tutoriel vidéo Node.js (EN)](https://www.youtube.com/watch?v=ENrzD6AvFZE)

---

## 🚀 Prochaine étape

Maintenant que tu as installé Node.js et inicalisé ton projet, tu es prêt pour :

👉 **[02 - Express.js et Routes](./02_Express.js_et_routes.md)**

Là, tu vas installer **Express.js** et créer ton **premier serveur web** ! 🚀
