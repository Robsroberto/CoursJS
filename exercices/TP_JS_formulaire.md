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



# Atelier : Manipulation d'un Formulaire en JavaScript

## Objectifs

- Comprendre comment accéder aux éléments d'un formulaire en JavaScript.
- Valider les entrées utilisateur avant la soumission du formulaire.
- Manipuler dynamiquement le DOM pour fournir un retour visuel en fonction des entrées utilisateur.
- Gérer les événements liés aux formulaires.

## Prérequis

- Connaissance de base du HTML, CSS et JavaScript.
- Connaissance des concepts du DOM.

## Plan de l'Atelier

1. Création du formulaire HTML de base.
2. Accès aux éléments du formulaire en JavaScript.
3. Validation des entrées utilisateur.
4. Manipulation du DOM pour fournir un retour visuel.
5. Gestion des événements de soumission du formulaire.

## Partie 1 : Création du Formulaire HTML de Base

Créez un fichier HTML avec le contenu suivant :

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Atelier Formulaire</title>
    <style>
        .error {
            color: red;
            font-size: 0.9em;
        }
        .success {
            color: green;
            font-size: 1.1em;
        }
    </style>
</head>
<body>
    <h1>Formulaire d'Inscription</h1>
    <form id="inscriptionForm">
        <label for="nom">Nom :</label>
        <input type="text" id="nom" name="nom" required>
        <span class="error" id="nomError"></span><br><br>

        <label for="email">Email :</label>
        <input type="email" id="email" name="email" required>
        <span class="error" id="emailError"></span><br><br>

        <label for="password">Mot de passe :</label>
        <input type="password" id="password" name="password" required>
        <span class="error" id="passwordError"></span><br><br>

        <button type="submit">S'inscrire</button>
    </form>

    <div id="message" class="success"></div>

    <script src="script.js"></script>
</body>
</html>
```

## Partie 2 : Accès aux Éléments du Formulaire en JavaScript

Créez un fichier `script.js` avec le contenu suivant pour accéder aux éléments du formulaire :

```javascript
document.addEventListener("DOMContentLoaded", function() {
    const form = document.getElementById('inscriptionForm');
    const nom = document.getElementById('nom');
    const email = document.getElementById('email');
    const password = document.getElementById('password');

    console.log(nom, email, password); // Pour vérifier que les éléments sont bien sélectionnés
});
```

## Partie 3 : Validation des Entrées Utilisateur

Ajoutez le code suivant dans `script.js` pour valider les entrées utilisateur :

```javascript
document.addEventListener("DOMContentLoaded", function() {
    const form = document.getElementById('inscriptionForm');
    const nom = document.getElementById('nom');
    const email = document.getElementById('email');
    const password = document.getElementById('password');

    form.addEventListener('submit', function(event) {
        let valid = true;

        // Réinitialiser les messages d'erreur
        document.getElementById('nomError').textContent = '';
        document.getElementById('emailError').textContent = '';
        document.getElementById('passwordError').textContent = '';

        // Validation du nom
        if (nom.value.trim() === '') {
            document.getElementById('nomError').textContent = 'Le nom est requis.';
            valid = false;
        }

        // Validation de l'email
        if (!email.value.includes('@')) {
            document.getElementById('emailError').textContent = 'Email invalide.';
            valid = false;
        }

        // Validation du mot de passe
        if (password.value.length < 6) {
            document.getElementById('passwordError').textContent = 'Le mot de passe doit contenir au moins 6 caractères.';
            valid = false;
        }

        if (!valid) {
            event.preventDefault(); // Empêche la soumission du formulaire
        }
    });
});
```

## Partie 4 : Manipulation du DOM pour Fournir un Retour Visuel

Ajoutez le code suivant dans `script.js` pour fournir un retour visuel sur la validation :

```javascript
document.addEventListener("DOMContentLoaded", function() {
    const form = document.getElementById('inscriptionForm');
    const nom = document.getElementById('nom');
    const email = document.getElementById('email');
    const password = document.getElementById('password');
    const message = document.getElementById('message');

    form.addEventListener('submit', function(event) {
        let valid = true;

        // Réinitialiser les messages d'erreur
        document.getElementById('nomError').textContent = '';
        document.getElementById('emailError').textContent = '';
        document.getElementById('passwordError').textContent = '';

        // Validation du nom
        if (nom.value.trim() === '') {
            document.getElementById('nomError').textContent = 'Le nom est requis.';
            valid = false;
        }

        // Validation de l'email
        if (!email.value.includes('@')) {
            document.getElementById('emailError').textContent = 'Email invalide.';
            valid = false;
        }

        // Validation du mot de passe
        if (password.value.length < 6) {
            document.getElementById('passwordError').textContent = 'Le mot de passe doit contenir au moins 6 caractères.';
            valid = false;
        }

        if (!valid) {
            event.preventDefault(); // Empêche la soumission du formulaire
        } else {
            // Afficher un message de succès
            message.textContent = 'Inscription réussie !';
        }
    });
});
```

## Partie 5 : Gestion des Événements de Soumission du Formulaire

Ajoutez le code suivant dans `script.js` pour empêcher la soumission du formulaire si les entrées ne sont pas valides et afficher un message de succès si elles le sont :

```javascript
document.addEventListener("DOMContentLoaded", function() {
    const form = document.getElementById('inscriptionForm');
    const nom = document.getElementById('nom');
    const email = document.getElementById('email');
    const password = document.getElementById('password');
    const message = document.getElementById('message');

    form.addEventListener('submit', function(event) {
        let valid = true;

        // Réinitialiser les messages d'erreur
        document.getElementById('nomError').textContent = '';
        document.getElementById('emailError').textContent = '';
        document.getElementById('passwordError').textContent = '';

        // Validation du nom
        if (nom.value.trim() === '') {
            document.getElementById('nomError').textContent = 'Le nom est requis.';
            valid = false;
        }

        // Validation de l'email
        if (!email.value.includes('@')) {
            document.getElementById('emailError').textContent = 'Email invalide.';
            valid = false;
        }

        // Validation du mot de passe
        if (password.value.length < 6) {
            document.getElementById('passwordError').textContent = 'Le mot de passe doit contenir au moins 6 caractères.';
            valid = false;
        }

        if (!valid) {
            event.preventDefault(); // Empêche la soumission du formulaire
        } else {
            // Afficher un message de succès
            message.textContent = 'Inscription réussie !';
        }
    });
});
```

## Résumé de l'Atelier

1. **Création du Formulaire HTML de Base** : Nous avons créé un formulaire HTML simple avec des champs pour le nom, l'email et le mot de passe, ainsi que des éléments pour afficher les messages d'erreur et de succès.
2. **Accès aux Éléments du Formulaire en JavaScript** : Nous avons appris à accéder aux éléments du formulaire en utilisant JavaScript.
3. **Validation des Entrées Utilisateur** : Nous avons mis en place des validations pour les entrées utilisateur et affiché des messages d'erreur si les validations échouaient.
4. **Manipulation du DOM pour Fournir un Retour Visuel** : Nous avons manipulé le DOM pour fournir un retour visuel en cas de succès ou d'erreur de la soumission du formulaire.
5. **Gestion des Événements de Soumission du Formulaire** : Nous avons géré l'événement de soumission du formulaire pour empêcher sa soumission en cas d'entrées invalides et afficher un message de succès si tout est correct.

## Conclusion

Cet atelier vous a montré comment manipuler un formulaire en JavaScript, depuis l'accès aux éléments jusqu'à la validation des entrées utilisateur et la gestion des événements. En pratiquant ces concepts, vous serez capable de créer des formulaires interactifs et dynamiques pour vos applications web.