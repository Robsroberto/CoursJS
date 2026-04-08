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

#  **JavaScript Asynchrone et AJAX**

---

## **1. Introduction au JavaScript Asynchrone**

###  1.1 Qu'est-ce que l'asynchronicité ?

En JavaScript, par défaut, les opérations s'exécutent de manière **synchrone**, c'est-à-dire ligne par ligne.
Cependant, certaines tâches comme les requêtes réseau, les accès aux fichiers ou aux bases de données peuvent être **longues**. Les exécuter de façon synchrone **bloquerait le reste du code**.

L'asynchronicité permet donc d'**exécuter du code sans attendre** que les opérations lentes soient terminées.

###   1.2 Exemple de code synchrone vs asynchrone

**Code synchrone (bloquant)** :

```js
console.log("Début");
alert("Je bloque tout !");
console.log("Fin");
```

**Explication :**

- `console.log("Début");` : Affiche "Début" dans la console.
- `alert("Je bloque tout !");` : Affiche une boîte de dialogue qui bloque l'exécution du script tant que l'utilisateur ne l'a pas fermée.
- `console.log("Fin");` : Affiche "Fin" dans la console, mais seulement après la fermeture de l'alerte.

**Code asynchrone (non bloquant)** :

```js
console.log("Début");
setTimeout(() => {
    console.log("Opération asynchrone terminée");
}, 2000);
console.log("Fin");
```

**Explication :**

- `console.log("Début");` : Affiche "Début" dans la console.
- `setTimeout(() => { ... }, 2000);` : Lance une fonction qui s'exécutera après 2 secondes (2000 ms).
    - `console.log("Opération asynchrone terminée");` : S'affichera dans la console après 2 secondes.
- `console.log("Fin");` : S'affiche immédiatement après "Début", sans attendre la fin du setTimeout.

---

## **2. Les Mécanismes Asynchrones de JavaScript**

###   2.1 `setTimeout` et `setInterval`

```js
setTimeout(() => {
  console.log("Exécuté après 1 seconde");
}, 1000);

setInterval(() => {
  console.log("Toutes les 2 secondes");
}, 2000);
```

* `setTimeout` : exécute une seule fois après un délai.
* `setInterval` : exécute en boucle à chaque intervalle.

**Explication :**

- `setTimeout(() => { ... }, 1000);` : Exécute la fonction une seule fois après 1 seconde.
    - `console.log("Exécuté après 1 seconde");` : S'affiche dans la console après 1 seconde.
- `setInterval(() => { ... }, 2000);` : Exécute la fonction toutes les 2 secondes, indéfiniment.
    - `console.log("Toutes les 2 secondes");` : S'affiche dans la console toutes les 2 secondes.

---

###   2.2 Les **Callbacks**

Un **callback** est une fonction passée en argument à une autre fonction, à exécuter plus tard.

```js
function chargerFichier(callback) {
  console.log("Chargement en cours...");
  setTimeout(() => {
    console.log("Fichier chargé !");
    callback(); // Appelle la fonction passée
  }, 2000);
}

chargerFichier(() => {
  console.log("Traitement du fichier...");
});
```

**Explication :**

- `function chargerFichier(callback) {...}` : Déclare une fonction qui prend un callback à exécuter après le chargement.
- `console.log("Chargement en cours...");` : Affiche un message indiquant le début du chargement.
- `setTimeout(() => { ... }, 2000);` : Simule un chargement asynchrone de 2 secondes.
    - `console.log("Fichier chargé !");` : Affiche que le fichier est chargé après 2 secondes.
    - `callback();` : Appelle la fonction passée en argument (le callback).
- `chargerFichier(() => {...});` : Appelle la fonction en passant un callback qui affiche "Traitement du fichier..." après le chargement.

#### **Apport des callbacks**

- Les callbacks permettent de gérer des opérations asynchrones : ils sont essentiels pour exécuter du code une fois qu'une tâche longue (comme une requête AJAX, une lecture de fichier, etc.) est terminée, sans bloquer l'exécution du reste du programme.
- Avant l'apparition des Promesses et de `async/await`, les callbacks étaient la principale méthode pour traiter les résultats des opérations asynchrones en JavaScript.
- Ils sont à la base du fonctionnement de nombreuses API JavaScript, notamment pour AJAX (par exemple avec `XMLHttpRequest`), les timers (`setTimeout`, `setInterval`), ou encore la gestion d'événements.

**Exemple d'utilisation d'un callback avec AJAX :**

```js
function chargerDonnees(url, callback) {
  let xhr = new XMLHttpRequest();
  xhr.open("GET", url);
  xhr.onload = function() {
    if (xhr.status === 200) {
      callback(null, xhr.responseText);
    } else {
      callback("Erreur lors du chargement");
    }
  };
  xhr.send();
}

chargerDonnees("data.json", (erreur, donnees) => {
  if (erreur) {
    console.error(erreur);
  } else {
    console.log("Données reçues :", donnees);
  }
});
```

**Explication :**

- `function chargerDonnees(url, callback) {...}` : Déclare une fonction qui prend en paramètre une URL et un callback à exécuter après la récupération des données.
- `let xhr = new XMLHttpRequest();` : Crée un nouvel objet XMLHttpRequest pour effectuer une requête AJAX.
- `xhr.open("GET", url);` : Prépare une requête HTTP GET vers l'URL fournie.
- `xhr.onload = function() {...}` : Définit ce qui doit se passer lorsque la réponse est reçue.
    - Si le statut est 200 (succès), on appelle le callback avec `null` (pas d'erreur) et la réponse reçue.
    - Sinon, on appelle le callback avec un message d'erreur.
- `xhr.send();` : Envoie la requête au serveur.
- `chargerDonnees("data.json", (erreur, donnees) => {...})` : Appelle la fonction en passant une fonction anonyme comme callback.
    - Si une erreur est détectée, elle est affichée dans la console.
    - Sinon, les données reçues sont affichées dans la console.

---

## **3. Promesses (Promises)**

###   3.1 Définition

Une **Promise** est un objet qui représente la **valeur future** d'une opération asynchrone.

```js
let promesse = new Promise((resolve, reject) => {
  let operation = true;

  if (operation) {
    resolve("Succès !");
  } else {
    reject("Échec !");
  }
});

promesse
  .then((resultat) => console.log(resultat))
  .catch((erreur) => console.error(erreur));
```

**Explication :**

- `let promesse = new Promise((resolve, reject) => {...});` : Crée une nouvelle promesse qui prendra fin soit en succès (resolve), soit en échec (reject).
- `let operation = true;` : Variable simulant le succès ou l'échec d'une opération.
- `if (operation) { resolve("Succès !"); } else { reject("Échec !"); }` : Si l'opération réussit, la promesse est résolue, sinon elle est rejetée.
- `promesse.then(...).catch(...);` : Permet de traiter le résultat de la promesse.
    - `.then((resultat) => ...)` : S'exécute si la promesse est résolue (succès).
    - `.catch((erreur) => ...)` : S'exécute si la promesse est rejetée (échec).

---

###   3.2 Utilité dans la pratique

```js
function attendreDeuxSecondes() {
  return new Promise(resolve => {
    setTimeout(() => {
      resolve("Temps écoulé !");
    }, 2000);
  });
}

attendreDeuxSecondes().then(message => console.log(message));
```

**Explication :**

- `function attendreDeuxSecondes() {...}` : Déclare une fonction qui retourne une promesse.
- `return new Promise(resolve => {...});` : Retourne une promesse qui sera résolue après 2 secondes.
- `setTimeout(() => {...}, 2000);` : Lance un timer de 2 secondes.
    - `resolve("Temps écoulé !");` : Résout la promesse avec le message après 2 secondes.
- `attendreDeuxSecondes().then(message => console.log(message));` : Appelle la fonction et affiche le message une fois la promesse résolue.

---

## **4. `async` / `await` : la syntaxe moderne**

Permet d'écrire du code **asynchrone** qui ressemble à du **code synchrone**.

```js
async function lancerTraitement() {
  console.log("Début");
  let resultat = await attendreDeuxSecondes();
  console.log(resultat);
  console.log("Fin");
}

lancerTraitement();
```

**Explication :**

- `async function lancerTraitement() {...}` : Déclare une fonction asynchrone.
- `console.log("Début");` : Affiche "Début" dans la console.
- `let resultat = await attendreDeuxSecondes();` : Attend la résolution de la promesse retournée par attendreDeuxSecondes, puis stocke le résultat.
- `console.log(resultat);` : Affiche le message reçu après l'attente.
- `console.log("Fin");` : Affiche "Fin" à la fin du traitement.
- `lancerTraitement();` : Appelle la fonction pour lancer le traitement asynchrone.

---

## **5. AJAX – Asynchronous JavaScript And XML**

###   5.1 Définition

AJAX est un **ensemble de techniques** permettant de **charger des données dynamiquement sans recharger la page**.

###   5.2 Exemple avec `XMLHttpRequest`

```js
let xhr = new XMLHttpRequest();
xhr.open("GET", "data.json");
xhr.onload = function() {
  if (xhr.status === 200) {
    let data = JSON.parse(xhr.responseText);
    console.log(data);
  }
};
xhr.send();
```

**Explication :**

- `let xhr = new XMLHttpRequest();` : Crée un nouvel objet XMLHttpRequest pour effectuer une requête AJAX.
- `xhr.open("GET", "data.json");` : Prépare une requête HTTP GET vers le fichier data.json.
- `xhr.onload = function() {...}` : Définit la fonction à exécuter lorsque la réponse est reçue.
    - `if (xhr.status === 200) {...}` : Vérifie si la requête a réussi (statut 200).
        - `let data = JSON.parse(xhr.responseText);` : Convertit la réponse JSON en objet JavaScript.
        - `console.log(data);` : Affiche les données dans la console.
- `xhr.send();` : Envoie la requête au serveur.

---

###   5.3 Exemple avec `fetch` (plus moderne)

```js
fetch("data.json")
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(err => console.error("Erreur :", err));
```

**Explication :**

- `fetch("data.json")` : Envoie une requête HTTP GET pour récupérer le fichier data.json.
- `.then(response => response.json())` : Transforme la réponse en objet JavaScript (JSON).
- `.then(data => console.log(data))` : Affiche les données reçues dans la console.
- `.catch(err => console.error("Erreur :", err))` : Affiche une erreur si la requête échoue.

---

###   5.4 Exemple d'utilisation avec une API

```js
async function getUsers() {
  try {
    let response = await fetch("https://jsonplaceholder.typicode.com/users");
    let data = await response.json();
    console.log("Utilisateurs :", data);
  } catch (error) {
    console.error("Erreur API :", error);
  }
}

getUsers();
```

**Explication :**

- `async function getUsers() {...}` : Déclare une fonction asynchrone pour récupérer des utilisateurs.
- `let response = await fetch("https://jsonplaceholder.typicode.com/users");` : Attend la réponse de l'API.
- `let data = await response.json();` : Transforme la réponse en objet JavaScript.
- `console.log("Utilisateurs :", data);` : Affiche la liste des utilisateurs dans la console.
- `catch (error) {...}` : Capture et affiche toute erreur survenue lors de la requête.
- `getUsers();` : Appelle la fonction pour lancer la récupération des utilisateurs.

---

## **6. Cas Pratique : Charger des utilisateurs depuis une API et les afficher**

```js
async function chargerUtilisateurs() {
  let container = document.querySelector("#utilisateurs");
  let response = await fetch("https://jsonplaceholder.typicode.com/users");
  let utilisateurs = await response.json();

  utilisateurs.forEach(user => {
    let p = document.createElement("p");
    p.textContent = `${user.name} (${user.email})`;
    container.appendChild(p);
  });
}
chargerUtilisateurs();
```

**Explication :**

- `async function chargerUtilisateurs() {...}` : Déclare une fonction asynchrone pour charger les utilisateurs.
- `let container = document.querySelector("#utilisateurs");` : Sélectionne l'élément HTML où afficher les utilisateurs.
- `let response = await fetch("https://jsonplaceholder.typicode.com/users");` : Récupère la liste des utilisateurs depuis l'API.
- `let utilisateurs = await response.json();` : Transforme la réponse en tableau d'utilisateurs.
- `utilisateurs.forEach(user => {...});` : Parcourt chaque utilisateur du tableau.
    - `let p = document.createElement("p");` : Crée un nouvel élément paragraphe.
    - `p.textContent = ...` : Définit le texte du paragraphe avec le nom et l'email de l'utilisateur.
    - `container.appendChild(p);` : Ajoute le paragraphe dans la page.
- `chargerUtilisateurs();` : Appelle la fonction pour lancer le chargement.

**Explication HTML :**

- `<div id="utilisateurs"></div>` : Élément qui servira de conteneur pour afficher dynamiquement la liste des utilisateurs récupérés.