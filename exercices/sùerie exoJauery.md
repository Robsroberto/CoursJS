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

## **Série d’exercices – jQuery Cours 1**

<!-- **Thèmes** : Sélecteurs, Manipulation DOM, Événements -->

### **Exercice 1 – Premiers Sélecteurs**

**Objectif** : S’exercer aux sélecteurs jQuery (ID, classes, balises, combinaisons).

**Consignes** :

1. Crée une page HTML avec :

   * Un titre `<h1>`
   * Trois paragraphes, deux avec la classe `.intro`, un avec l’ID `#special`
   * Une liste `<ul>` de trois éléments `<li>`

2. En jQuery :

   * Change la couleur du texte de tous les paragraphes.
   * Change le fond du paragraphe avec l’ID `#special`.
   * Ajoute une bordure aux éléments de classe `.intro`.
   * Cache le premier élément de la liste.

### **Exercice 2 – Manipulation de contenu et d’attributs**

**Objectif** : Modifier dynamiquement les éléments du DOM.

**Consignes** :

1. Crée un formulaire avec un champ `input` de type texte et un bouton.
2. Lorsque l’utilisateur clique sur le bouton :

   * Récupère la valeur du champ.
   * L'affiche dans un `<div>` vide sous forme de phrase : “Bonjour \[nom saisi] !”
   * Vide le champ après soumission.

### **Exercice 3 – Gestion des événements**

**Objectif** : Utiliser `.click()`, `.hover()`, `.keyup()`, etc.

**Consignes** :

1. Crée un bloc `<div>` coloré avec une taille fixe.
2. En jQuery :

   * Lors du survol (hover), change sa couleur.
   * Lors d’un clic, affiche une alerte “Div cliquée !”.
   * Lorsqu’on écrit dans un champ texte, afficher dynamiquement ce texte dans un `<span>`.

### **Recherche guidée pour approfondir** :

* Quelle différence entre `.on('click')` et `.click()` ?
* Comment utiliser `$(this)` pour cibler un élément cliqué ?
* Recherchez comment déclencher des événements personnalisés en jQuery.

---

## **Série d’exercices – jQuery Cours 2**

<!-- **Thèmes** : Effets, Formulaires, AJAX -->

### **Exercice 1 – Effets visuels**

**Objectif** : Maîtriser `.hide()`, `.show()`, `.toggle()`, `.fadeIn()`, `.slideUp()`, etc.

**Consignes** :

1. Crée un bloc d’informations dans un `<div>`.
2. Ajoute deux boutons : “Afficher” et “Cacher”.
3. En jQuery :

   * Le bouton “Afficher” fait apparaître le bloc en `fadeIn`.
   * Le bouton “Cacher” le fait disparaître en `slideUp`.

### **Exercice 2 – Formulaires dynamiques**

**Objectif** : Valider un formulaire avec jQuery et afficher les erreurs.

**Consignes** :

1. Crée un formulaire simple : nom, email, bouton envoyer.
2. En jQuery :

   * Vérifie que les champs ne sont pas vides.
   * Vérifie que l’email contient un `@`.
   * Si erreur : affiche un message sous chaque champ.
   * Sinon : affiche un message de validation dans un `<div>`.

### **Exercice 3 – AJAX simple avec fichier JSON**

**Objectif** : Charger des données sans recharger la page.

**Consignes** :

1. Prépare un fichier `etudiants.json` :

```json
[
  { "nom": "Awa", "filiere": "IAGE" },
  { "nom": "Moussa", "filiere": "SRI" }
]
```

2. Crée un bouton “Charger étudiants”.
3. Lors du clic, avec jQuery AJAX :

   * Récupère les données du fichier.
   * Affiche-les dans une liste HTML (`<ul>`).

### **Exercice 4 – AJAX + Formulaire (Bonus)**

**Objectif** : Envoi de données vers un script PHP via AJAX.

**Consignes** :

1. Crée un formulaire avec `nom` et `email`.
2. Envoie les données vers un fichier `traitement.php` avec `$.post()`.
3. En PHP, renvoie une réponse JSON `{ message: "Bien reçu !" }`.
4. Affiche ce message dans un `div` de confirmation.

### **Recherche guidée pour approfondir** :

* Quelle est la différence entre `$.get()` et `$.post()` ?
* Recherchez comment utiliser `.done()`, `.fail()` et `.always()` avec `$.ajax()`.
* Que fait `dataType: 'json'` dans une requête AJAX ?

