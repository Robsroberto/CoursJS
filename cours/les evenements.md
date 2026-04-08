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
paginate: true
# footer: Licence 2 Informatique &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ISI (Institut Supérieur D'Informatique) &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; RD
---
<img src="../isi.png" alt="ISI" width="100px">

---
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 

## Par Robert DIASSÉ &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <img src="js.jpeg" alt="ISI" width="50px">

---
---

# Les Événements en JavaScript

## Introduction
Les événements sont des actions ou des occurrences qui se produisent dans le navigateur et que JavaScript peut détecter et gérer. Les événements peuvent être générés par l'utilisateur (comme cliquer sur un bouton, taper du texte, ou déplacer la souris) ou par le système (comme le chargement de la page).

## Types d'Événements
Il existe de nombreux types d'événements en JavaScript, les plus courants étant :
- **Événements de souris** : `click`, `dblclick`, `mousemove`, `mouseover`, `mouseout`, `mousedown`, `mouseup`
- **Événements de clavier** : `keydown`, `keypress`, `keyup`
- **Événements de document** : `DOMContentLoaded`, `load`, `unload`, `resize`, `scroll`
- **Événements de formulaire** : `submit`, `change`, `focus`, `blur`

## Gestion des Événements
Pour gérer les événements en JavaScript, on utilise des écouteurs d'événements (event listeners). Il y a plusieurs façons d'ajouter un écouteur d'événement à un élément HTML :

### 1. Méthode HTML
Vous pouvez ajouter un gestionnaire d'événements directement dans votre HTML :
```html
<button onclick="alert('Button clicked!')">Click me</button>
```

### 2. Propriétés d'Événement
Vous pouvez assigner une fonction directement à une propriété d'événement d'un élément DOM :
```html
<button id="myButton">Click me</button>
<script>
  const button = document.getElementById('myButton');
  button.onclick = function() {
    alert('Button clicked!');
  };
</script>
```

### 3. Méthode `addEventListener`
C'est la méthode recommandée car elle permet d'ajouter plusieurs écouteurs au même événement et d'enlever des écouteurs si nécessaire :
```html
<button id="myButton">Click me</button>
<script>
  const button = document.getElementById('myButton');
  button.addEventListener('click', function() {
    alert('Button clicked!');
  });
</script>
```

## Exemple Pratique

### Exemple de Gestionnaire d'Événements de Souris
```html
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Événements de Souris</title>
</head>
<body>
  <button id="mouseButton">Hover over me</button>
  <script>
    const button = document.getElementById('mouseButton');
    button.addEventListener('mouseover', function() {
      button.style.backgroundColor = 'yellow';
    });
    button.addEventListener('mouseout', function() {
      button.style.backgroundColor = '';
    });
  </script>
</body>
</html>
```

### Exemple de Gestionnaire d'Événements de Clavier
```html
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Événements de Clavier</title>
</head>
<body>
  <input type="text" id="textInput" placeholder="Tapez quelque chose...">
  <script>
    const input = document.getElementById('textInput');
    input.addEventListener('keydown', function(event) {
      console.log(`Touche pressée: ${event.key}`);
    });
  </script>
</body>
</html>
```

## Événements Personnalisés
Vous pouvez également créer et déclencher des événements personnalisés :
```html
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Événements Personnalisés</title>
</head>
<body>
  <button id="customEventButton">Trigger Custom Event</button>
  <script>
    const button = document.getElementById('customEventButton');

    // Définir l'écouteur pour l'événement personnalisé
    button.addEventListener('myCustomEvent', function(event) {
      alert(`Custom event triggered with data: ${event.detail}`);
    });

    // Déclencher l'événement personnalisé
    button.addEventListener('click', function() {
      const customEvent = new CustomEvent('myCustomEvent', {
        detail: 'Hello, World!'
      });
      button.dispatchEvent(customEvent);
    });
  </script>
</body>
</html>
```

## Conclusion
Les événements sont essentiels pour rendre les pages web interactives. En comprenant comment les gérer efficacement, vous pouvez créer des interfaces utilisateur dynamiques et réactives. Utilisez les différentes méthodes pour ajouter des écouteurs d'événements en fonction de vos besoins spécifiques, et n'hésitez pas à explorer les événements personnalisés pour des interactions plus avancées.

---

N'hésitez pas à pratiquer ces exemples et à les adapter à vos propres projets pour mieux comprendre le fonctionnement des événements en JavaScript.