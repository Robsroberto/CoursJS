---
marp: false
size: 4:3
style: |
  h2, h3, p {
    font-size: 20px;
  }
  li {
    font-size:20px
  }
headingDivider: 1
header: 
paginate: 
footer: Licence 2 Informatique &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ISI (Institut Supérieur D'Informatique) &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; RD
---
<img src="../isi.png" alt="ISI" width="100px">

# JS : Introduction
---
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 

## Par Robert DIASSÉ &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <img src="js.jpeg" alt="ISI" width="50px">


---
### Introduction à JavaScript

#### Historique de sa création :
JavaScript, souvent abrégé en "JS", a été développé par Brendan Eich chez Netscape Communications Corporation en 1995. À l'origine, il était destiné à ajouter des fonctionnalités interactives aux pages web statiques en permettant de manipuler le contenu HTML de manière dynamique du côté client, c'est-à-dire sur le navigateur de l'utilisateur. Depuis sa création, JavaScript a évolué pour devenir un langage de programmation polyvalent utilisé dans de nombreux contextes, y compris le développement web, les applications mobiles, les jeux, les serveurs, etc.

#### Cadre d'utilisation :
JavaScript est principalement utilisé du côté client pour rendre les pages web interactives et dynamiques. Il est largement utilisé pour créer des fonctionnalités telles que des animations, des formulaires interactifs, des jeux, des applications web en temps réel, etc. De plus en plus, JavaScript est également utilisé côté serveur grâce à des plates-formes comme Node.js, qui permettent aux développeurs d'utiliser JavaScript pour développer des applications backend.

#### Manière de l'utiliser :
JavaScript est un langage de programmation léger et interprété, ce qui signifie qu'il est exécuté ligne par ligne par un moteur JavaScript dans l'environnement du navigateur ou du serveur. Pour l'utiliser dans une page web, vous pouvez incorporer du code JavaScript directement dans les balises `<script>` de votre HTML ou lier des fichiers JavaScript externes. Du côté serveur, vous pouvez exécuter du code JavaScript à l'aide de Node.js ou d'autres environnements d'exécution.

#### Outils essentiels pour utiliser JavaScript :
- Éditeurs de code : Des outils comme Visual Studio Code, Sublime Text, ou Atom sont populaires pour écrire du code JavaScript avec des fonctionnalités d'édition avancées.
- Navigateurs web : Les navigateurs modernes comme Google Chrome, Mozilla Firefox, et Safari disposent de puissants outils de développement intégrés qui permettent de déboguer et de profiler du code JavaScript.
- Frameworks et bibliothèques : Des frameworks comme React.js, AngularJS, ou Vue.js facilitent le développement d'applications web complexes en fournissant des structures et des fonctionnalités prêtes à l'emploi.

#### Portée en tant que langage de programmation :
JavaScript est l'un des langages de programmation les plus largement utilisés dans le monde, en grande partie grâce à sa flexibilité et à sa portabilité. Il est devenu un langage incontournable pour le développement web moderne, et son utilisation continue de croître dans de nombreux autres domaines, notamment le développement mobile, l'IoT (Internet des Objets), et les applications serveur.

### Exécution de JavaScript côté Client et Côté Serveur

#### Côté Client (Navigateur Web) :
JavaScript est principalement utilisé côté client pour rendre les pages web interactives. Voici comment incorporer du JavaScript dans une page HTML pour exécution côté client :

```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ma Page Web</title>
</head>
<body>
    <h1>Mon Premier Script JavaScript</h1>
    
    <!-- Balise script pour incorporer du JavaScript -->
    <script>
        // Code JavaScript ici
        alert("Bonjour, monde !");
    </script>
</body>
</html>
```

#### Côté Serveur (Node.js) :
JavaScript peut également être exécuté côté serveur grâce à des environnements comme Node.js. Voici comment créer et exécuter un script JavaScript côté serveur avec Node.js :

1. **Installer Node.js :** Téléchargez et installez Node.js depuis le site officiel (https://nodejs.org/).

2. **Créer un fichier JavaScript :** Créez un fichier `hello.js` avec le code suivant :

```javascript
// hello.js
console.log("Bonjour, monde !");
```

3. **Exécuter le script :** Ouvrez une ligne de commande et exécutez le script avec la commande `node` :

```
node hello.js
```

Vous verrez la sortie "Bonjour, monde !" dans la console.
