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

## Effets, Manipulation de Formulaires et AJAX avec jQuery**

### **1. Introduction aux effets jQuery**

jQuery propose plusieurs méthodes pour ajouter des effets visuels à vos pages web :

#### a. **Effets de base**

* `hide()`, `show()`, `toggle()`
* `fadeIn()`, `fadeOut()`, `fadeToggle()`, `fadeTo()`
* `slideDown()`, `slideUp()`, `slideToggle()`

```javascript
// Cacher un élément
$('#monParagraphe').hide();

// Afficher un élément
$('#monParagraphe').show();

// Alterner entre cacher et afficher
$('#monParagraphe').toggle();

// Fondu entrant
$('#monParagraphe').fadeIn();

// Glissement vers le bas
$('#monParagraphe').slideDown();
```

> **Explication :**

* `$('#monParagraphe')` : sélectionne l’élément avec l’id `monParagraphe`.
* `.hide()` : applique un style `display: none`.
* `.fadeIn()` : fait apparaître l’élément avec un effet de fondu.
* `.slideDown()` : fait glisser l’élément vers le bas jusqu’à ce qu’il soit visible.

---

### \*\*2. Enchaîner des animations personnalisées avec `.animate()`

`animate()` permet de modifier une ou plusieurs propriétés CSS de façon animée.

```javascript
$('#boite').animate({
  width: '300px',
  height: '200px',
  opacity: 0.7
}, 1000); // durée en ms
```

> **Explication :**

* `animate({ ... }, durée)` : modifie les propriétés sur une durée donnée (ici 1 seconde).
* `width`, `height`, `opacity` : sont modifiés progressivement.

---

### **3. Manipulation de formulaires**

jQuery facilite l’interaction avec les champs de formulaire.

#### a. **Lire et modifier la valeur d’un champ**

```javascript
// Lire la valeur
let nom = $('#nom').val();

// Modifier la valeur
$('#nom').val('Jean Dupont');
```

#### b. **Gérer les événements de formulaire**

```javascript
$('#monFormulaire').submit(function(e) {
  e.preventDefault(); // empêche l'envoi
  let nom = $('#nom').val();
  alert("Nom soumis : " + nom);
});
```

> **Explication :**

* `.submit(...)` : déclenche lors de la soumission.
* `e.preventDefault()` : empêche le rechargement de la page.
* `$('#nom').val()` : lit la valeur saisie dans le champ avec id `nom`.

---

### **4. AJAX avec jQuery**

jQuery simplifie les requêtes asynchrones vers le serveur.

#### a. **Méthode `$.ajax()`**

```javascript
$.ajax({
  url: 'etudiants.json',
  method: 'GET',
  dataType: 'json',
  success: function(donnees) {
    console.log(donnees);
  },
  error: function(xhr, status, error) {
    console.log("Erreur AJAX :", error);
  }
});
```

> **Explication :**

* `url` : chemin du fichier/serveur.
* `method` : méthode HTTP (`GET`, `POST`…).
* `dataType` : format attendu (`json`, `html`, `text`…).
* `success()` : fonction appelée en cas de réussite.
* `error()` : fonction en cas d’échec.

---

#### b. **Simplification avec `$.get()`**

```javascript
$.get('etudiants.json', function(data) {
  console.log(data);
});
```

---

### **5. Exemple complet intégré (formulaire + AJAX)**

```javascript
$('#btnCharger').click(function() {
  $.getJSON('etudiants.json', function(etudiants) {
    etudiants.forEach(function(etudiant) {
      $('#resultat').append('<li>' + etudiant.nom + '</li>');
    });
  });
});
```

> **Explication :**

* `.click(...)` : quand on clique sur le bouton.
* `$.getJSON(...)` : récupère les données JSON du fichier.
* `.forEach(...)` : boucle sur le tableau.
* `.append(...)` : insère chaque nom dans la liste HTML.
