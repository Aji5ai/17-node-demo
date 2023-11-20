# Node.js - Node Package Manager

Explorez l'utilisation de npm pour gérer les dépendances et les scripts dans un projet JavaScript.

## Ressources

- [npm - Chalk](https://www.npmjs.com/package/chalk)
- [npm - validator.js](https://github.com/validatorjs/validator.js)

## Contexte du projet

Avec Node.js installé, vous êtes prêt à créer des projets en utilisant le gestionnaire de paquets **npm**.

### Gestionnaire de paquets

Un gestionnaire de paquets facilite l'installation, la mise à jour et la gestion de modules (aussi appelés bibliothèques ou *packages*) dans vos projets, économisant du temps et réduisant les erreurs.

### Node Package Manager

Node Package Manager (**npm**) est le gestionnaire de paquets officiel de Node.js.

Voici ses fonctionnalités :
- Installer et gérer les modules.
- Gérer les versions des modules.
- Publier vos propres modules.
- Automatiser des tâches avec des scripts dans `package.json`.

Vérifiez si **npm** est installé en exécutant `npm -v` dans le terminal.

### Initialisation d'un Projet avec npm

Commençons par créer un dossier avec un script très simple :

```bash
mkdir node-demo
cd node-demo

echo "console.log('Hello, World!');" > main.js
```

Pour initialiser un projet avec **npm**, il faut ouvrir un terminal dans le répertoire de ton projet et taper la commande suivante :

```bash
npm init
```

> Si tu ne souhaites pas répondre à ces questions, tu peux utiliser la commande `npm init -y` pour renseigner toutes les réponses par défaut

### Le fichier package.json

La commande `npm init` crée un fichier `package.json` dans ton projet : tu peux y ajouter des scripts personnalisés qui pourront être exécutés avec **npm**.

Par exemple, pour exécuter ton fichier principal `main.js` avec **Node.js**, tu peux ajouter un script "start" en modifiant le bloc suivant :

```json
"scripts": {
  "test": "echo \"Error: no test specified\" && exit 1"
},
```

Tu vas ajouter une nouvelle entrée pour le script "start" :

```json
"scripts": {
  "start": "node main.js",
  "test": "echo \"Error: no test specified\" && exit 1"
},
```

Exécutez votre application avec `npm start`.

Cela exécutera la commande `node main.js` qui est définie dans ton script "start". C'est un moyen standard de démarrer des applications Node.js.

### Installation d'un module npm

Pour installer un module avec **npm**, tu peux utiliser la commande `npm install`.

Par exemple, pour installer le module **Chalk**, utilisez `npm install chalk`.

```bash
# npm i : raccourci de la commande "npm install"
npm i chalk
```

Importez ensuite le module dans votre script :

```js
// on importe le module en haut du fichier main.js
import chalk from 'chalk';
```

Tu peux maintenant utiliser le module en te référant à sa documentation : [npm - Chalk](https://www.npmjs.com/package/chalk).

```js
// en dessous de l'import
console.log(chalk.blue('Hello world!'));
```

### Type: module

Essaie maintenant d'exécuter le programme :

```bash
npm start
# Warning: To load an ES module, set "type": "module" in the package.json or use the .mjs extension.
```

Zut, un message d'erreur !

Pour te résumer le problème, il s'agit d'une configuration manquante dans ton `package.json` !

En effet, les modules récents sont basés sur le standart **ECMAScript module** (*ES modules*).

Pour que Node.js sache que ton projet peut utiliser la syntaxe **ES6** (et les *ES modules*), il faudra que tu ajoutes la propriété `"type": "module"` à ton fichier `package.json` :

```json
{
  "type": "module",
  // ...
}
```

### Le fichier package-lock.json

Quand tu as installé le module **Chalk**, cela a créé un fichier `package-lock.json` : il contient toutes les versions des modules installés dans ton projet.

Si tu partages ton code, les autres développeur·euse·s pourront installer le projet avec les mêmes modules et versions que toi, en utilisant la commande :

```bash
# npm ci : raccourci de la commande "npm clean-install"
npm ci
```

### Le dossier node_modules

Quand tu as installé le module **Chalk**, cela a aussi créé un dossier `node_modules` : c'est à cet endroit que **npm** installe toutes les bibliothèques nécessaires au fonctionnement de ton projet.

Lorsque tu installes des packages Node.js, npm télécharge les fichiers et les met dans le dossier `node_modules` : ce dossier contient les codes sources des modules, y compris toutes leurs dépendances.

### Ignorer le dossier node_modules

C'est une bonne pratique d'ignorer le dossier `node_modules` dans un projet **git** : ça se fait avec un fichier `.gitignore`.

#### 1. Comment ignorer node_modules

Pour ignorer le dossier `node_modules`, tu dois donc créer un fichier `.gitignore` (pense à bien mettre le point au début du fichier) dans le répertoire racine de ton projet avec le contenu suivant :

```yaml
node_modules
```

Ce fichier doit être commité dans ton dépôt. Il indiquera à **git** d'ignorer les fichiers et dossiers listés à l'intérieur, y compris le dossier `node_modules`, ce qui signifie que ce dossier ne sera pas suivi ni inclus dans tes commits ou pushs.

#### 2. Pourquoi ignorer node_modules ?

Parce que ce dossier peut devenir très gros, contenant potentiellement des centaines de modules. L'ajouter à ton dépôt git consommerait beaucoup de données et rendrait les opérations, comme le clonage et la récupération, bien plus lentes.

#### 3. Comment installer un projet

Quiconque clone le dépôt peut lancer la commande `npm ci` pour installer les dépendances nécessaires spécifiées dans le fichier `package.json`. Cela assure que tout le monde utilise les mêmes versions des dépendances, comme défini dans `package-lock.json`.

### Modalités pédagogiques

Tu vas mettre en pratique tes connaissances nouvellement acquises en créant un nouveau projet, qui permet de valider des adresses emails.

Tu utiliseras le module suivant : [npm - validator.js](https://github.com/validatorjs/validator.js).

- Crée un projet JavaScript avec `npm`
- Installe le module "validator.js"
- Crée un script JavaScript contenant la validation d'un tableau d'adresses email
- Il s'agira d'afficher chaque adresse email du tableau, et d'afficher un booléen pour préciser si l'adresse est valide ou non
- Il doit être possible d'exécuter le projet avec la commande `npm start`
- Versionne ton projet et envoie-le sur GitLab (n'oublie pas d'ignorer le dossier `node_modules`)

## Modalités d'évaluation

- Projet hébergé sur GitLab.
- Dossier `node_modules` non versionné.
- `npm ci` installe les modules nécessaires.
- `npm start` lance `main.js`.
- Le script affiche la validation des emails.
- Utilisation du module "validator.js".

## Livrables

Un lien vers un dépôt GitLab.

## Critères de performance

- Le code source est documenté
- Utiliser les normes de codage du langage
- La documentation technique de l’environnement de travail est comprise
- Utiliser un outil de gestion de versions