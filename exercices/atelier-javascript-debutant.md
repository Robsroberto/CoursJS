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

# Atelier JavaScript — Bases
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 

## Par Robert DIASSÉ &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
<img src="js.jpeg" alt="ISI" width="50px">

Niveau : L1 Web

Duree estimee : 3h

---

## Objectifs

A la fin de cet atelier, vous serez capable de :

- Declarer et manipuler des variables et des constantes
- Utiliser les structures conditionnelles et les boucles
- Creer et appeler des fonctions (nommees, anonymes, flechees)
- Interagir avec l'utilisateur via le DOM
- Produire un mini-projet JavaScript entierement fonctionnel

---

## Prerequis

- Avoir lu les cours : Variables/Types/Operateurs, Tableaux/Objets, Fonctions (fournis)
- Visual Studio Code installe
- Un navigateur moderne (Chrome ou Firefox)

---

## Mise en place

Creez un dossier `atelier-js/` contenant deux fichiers :

```
atelier-js/
├── index.html
└── main.js
```

Contenu de `index.html` :

```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Atelier JavaScript</title>
</head>
<body>
    <h1>Atelier JavaScript</h1>

    <!-- Zone d'affichage reservee aux exercices interactifs -->
    <div id="resultat"></div>

    <script src="main.js"></script>
</body>
</html>
```

Ouvrez `index.html` dans Chrome, puis ouvrez la console du navigateur avec la touche **F12** (onglet "Console"). C'est ici que vous verrez les resultats de vos exercices. Chaque fois que vous modifiez `main.js`, rechargez la page avec **F5**.

---

## Etape 1 — Variables, types et operateurs

### Rappel du cours

| Mot-cle | Portee | Reassignable |
|---|---|---|
| `var` | Fonctionnelle (ancien, deconseille) | Oui |
| `let` | Bloc | Oui |
| `const` | Bloc | Non |

L'operateur `typeof` permet de connaitre le type d'une valeur :

```javascript
typeof 42         // "number"
typeof "Bonjour"  // "string"
typeof true       // "boolean"
typeof undefined  // "undefined"
```

### Exercice 1.1 — Declarer et afficher

Ecrivez dans `main.js` :

```javascript
// Constante : la valeur ne changera jamais
const ANNEE_NAISSANCE = 2003;

// Variable : la valeur peut etre modifiee
let prenom = "Fatou";

// Calcul de l'age a partir de la constante
let age = 2025 - ANNEE_NAISSANCE;

// Affichage dans la console
console.log("Prenom :", prenom);           // Affiche : Prenom : Fatou
console.log("Age :", age);                 // Affiche : Age : 22
console.log("Type de age :", typeof age); // Affiche : Type de age : number
```

### Exercice 1.2 — Operateurs et conversion de type

```javascript
let a = "10"; // a est une chaine de caracteres (string)
let b = 5;    // b est un nombre (number)

// Sans conversion : + concatene les chaines
console.log(a + b);          // Affiche : "105" (concatenation, pas addition !)

// Conversion explicite de a en entier avec parseInt()
a = parseInt(a);

// Maintenant + additionne correctement
console.log(a + b);          // Affiche : 15
console.log(a * b);          // Affiche : 50
console.log(a > b);          // Affiche : true
console.log(typeof a);       // Affiche : number
```

### Exercice 1.3 — Egalite stricte vs egalite simple

```javascript
// == compare les valeurs apres conversion de type
console.log(10 == "10");  // true  : "10" est converti en 10 avant la comparaison

// === compare la valeur ET le type, sans conversion
console.log(10 === "10"); // false : number !== string

// En pratique, utilisez toujours ===
```

**Point de controle** : rechargez la page. La console doit afficher les resultats sans aucune erreur rouge. Si une erreur apparait, lisez son message : il indique la ligne et la nature du probleme.

---

## Etape 2 — Structures conditionnelles

### Rappel du cours

La structure `if...else` execute du code selon une condition. Pour des conditions multiples, on enchaene les blocs `else if`. L'operateur ternaire condense un `if...else` simple sur une ligne.

### Exercice 2.1 — Majeur ou mineur

```javascript
let ageUtilisateur = 16;

// Structure if...else
if (ageUtilisateur >= 18) {
    console.log("Acces autorise.");
} else {
    console.log("Acces refuse. Vous devez avoir au moins 18 ans.");
}

// Equivalent avec l'operateur ternaire
let message = (ageUtilisateur >= 18) ? "Acces autorise." : "Acces refuse.";
console.log(message);
```

### Exercice 2.2 — Convertir une note en appreciation

```javascript
let note = 14;
let appreciation;

if (note >= 16) {
    appreciation = "Tres bien";
} else if (note >= 14) {
    appreciation = "Bien";
} else if (note >= 12) {
    appreciation = "Assez bien";
} else if (note >= 10) {
    appreciation = "Passable";
} else {
    appreciation = "Insuffisant";
}

// Concatenation avec le signe +
console.log("Note : " + note + " — Appreciation : " + appreciation);
// Affiche : Note : 14 — Appreciation : Bien
```

**Point de controle** : modifiez manuellement la valeur de `note` avec les valeurs suivantes et verifiez que l'appreciation est correcte a chaque rechargement : 8, 11, 13, 17, 20.

---

## Etape 3 — Structures repetitives

### Rappel du cours

| Boucle | Usage |
|---|---|
| `for` | Quand on connait le nombre d'iterations a l'avance |
| `while` | Quand on repete jusqu'a ce qu'une condition soit fausse |
| `do...while` | Comme `while`, mais le bloc s'execute au moins une fois |

### Exercice 3.1 — Boucle for : afficher les entiers

```javascript
// Afficher les nombres de 1 a 10
// i = 1 : valeur initiale | i <= 10 : condition d'arret | i++ : incrementation
for (let i = 1; i <= 10; i++) {
    console.log(i);
}
// Affiche : 1, 2, 3, ... 10 (chaque nombre sur une ligne)
```

### Exercice 3.2 — Table de multiplication

```javascript
let nombre = 7;

console.log("--- Table de " + nombre + " ---");

for (let i = 1; i <= 10; i++) {
    // L'expression (nombre * i) est evaluee avant la concatenation
    console.log(nombre + " x " + i + " = " + (nombre * i));
}
// Affiche : 7 x 1 = 7, 7 x 2 = 14, ... 7 x 10 = 70
```

### Exercice 3.3 — Boucle while : compter jusqu'a la condition

```javascript
let compteur = 1;
let limite = 5;

// La boucle continue TANT QUE compteur <= limite
while (compteur <= limite) {
    console.log("Tour numero " + compteur);
    compteur++; // Sans cette ligne, la boucle ne s'arreterait jamais (boucle infinie)
}
console.log("Boucle terminee. compteur vaut : " + compteur); // Affiche : 6
```

### Exercice 3.4 — do...while : au moins une execution

```javascript
// do...while execute le bloc une premiere fois AVANT de verifier la condition
let essai = 1;

do {
    console.log("Essai numero " + essai);
    essai++;
} while (essai <= 3);

// Affiche : Essai numero 1, Essai numero 2, Essai numero 3
```

**Point de controle** : verifiez que :

- La boucle `for` affiche bien les nombres de 1 a 10 (10 lignes en tout)
- La table de 7 est correcte jusqu'a 7 x 10 = 70
- La boucle `while` s'arrete bien et affiche "compteur vaut : 6"
- La boucle `do...while` affiche bien 3 lignes

---

## Etape 4 — Fonctions

### Rappel du cours

Une fonction est un bloc de code nomme et reutilisable. Elle peut recevoir des valeurs en entree (parametres) et en retourner une en sortie (valeur de retour via `return`).

### Exercice 4.1 — Fonction nommee

```javascript
// DEFINITION de la fonction (le code ne s'execute pas encore ici)
function additionner(a, b) {
    return a + b; // renvoie la somme
}

// APPEL de la fonction (le code s'execute maintenant)
let resultat = additionner(8, 5);
console.log("8 + 5 =", resultat); // Affiche : 8 + 5 = 13

// La meme fonction peut etre appelee autant de fois que necessaire
console.log("20 + 3 =", additionner(20, 3)); // Affiche : 20 + 3 = 23
console.log("100 + 1 =", additionner(100, 1)); // Affiche : 100 + 1 = 101
```

### Exercice 4.2 — Fonction anonyme

```javascript
// La fonction est stockee dans une variable : elle n'a pas de nom propre
let multiplier = function(a, b) {
    return a * b;
};

// On appelle la fonction via le nom de la variable
console.log("4 x 6 =", multiplier(4, 6));   // Affiche : 4 x 6 = 24
console.log("3 x 9 =", multiplier(3, 9));   // Affiche : 3 x 9 = 27
```

### Exercice 4.3 — Fonction flechee (arrow function)

```javascript
// Syntaxe condensee : pas besoin du mot-cle "function"
// Pour une expression simple, les accolades et "return" sont optionnels
let soustraire = (a, b) => a - b;

console.log("10 - 3 =", soustraire(10, 3)); // Affiche : 10 - 3 = 7

// Si la fonction contient plusieurs instructions, on remet les accolades et return
let decrire = (a, b) => {
    let somme = a + b;
    let produit = a * b;
    return "Somme : " + somme + ", Produit : " + produit;
};

console.log(decrire(3, 4)); // Affiche : Somme : 7, Produit : 12
```

### Exercice 4.4 — Fonction de rappel (callback)

Un callback est une fonction passee en argument a une autre fonction, qui l'appellera au bon moment.

```javascript
// Cette fonction recoit deux nombres ET une operation (qui est elle-meme une fonction)
function effectuerOperation(a, b, operation) {
    return operation(a, b); // appel de la fonction passee en parametre
}

// On definit les operations comme des fonctions flechees
let addition       = (a, b) => a + b;
let multiplication = (a, b) => a * b;
let soustraction   = (a, b) => a - b;

// On passe l'operation souhaitee comme troisieme argument
console.log(effectuerOperation(5, 3, addition));        // Affiche : 8
console.log(effectuerOperation(5, 3, multiplication));  // Affiche : 15
console.log(effectuerOperation(5, 3, soustraction));    // Affiche : 2
```

**Point de controle** : sans regarder le code, repondez aux questions suivantes :

- Quelle est la difference entre une fonction nommee et une fonction anonyme ?
- Quand le mot-cle `return` est-il obligatoire dans une fonction flechee ?
- Qu'est-ce qu'un callback ? Donnez un exemple en une phrase.

---

## Etape 5 — Mini-projet : Calculatrice interactive

Vous allez assembler tout ce que vous avez appris pour creer une calculatrice qui interagit avec l'utilisateur dans la page.

### Etape 5.1 — Modifier `index.html`

Remplacez le contenu du `<body>` par la structure suivante :

```html
<body>
    <h1>Calculatrice JavaScript</h1>

    <label for="nb1">Nombre 1 :</label>
    <input type="number" id="nb1" value="0">

    <label for="nb2">Nombre 2 :</label>
    <input type="number" id="nb2" value="0">

    <br><br>

    <button id="btnAddition">Addition</button>
    <button id="btnSoustraction">Soustraction</button>
    <button id="btnMultiplication">Multiplication</button>
    <button id="btnDivision">Division</button>

    <p id="resultat">Resultat : ---</p>

    <script src="main.js"></script>
</body>
```

### Etape 5.2 — Ecrire le JavaScript dans `main.js`

```javascript
// --- 1. Recuperer les elements du DOM par leur identifiant ---
let inputNb1  = document.getElementById("nb1");       // champ nombre 1
let inputNb2  = document.getElementById("nb2");       // champ nombre 2
let affichage = document.getElementById("resultat");  // paragraphe d'affichage

let btnAdd    = document.getElementById("btnAddition");
let btnSous   = document.getElementById("btnSoustraction");
let btnMult   = document.getElementById("btnMultiplication");
let btnDiv    = document.getElementById("btnDivision");


// --- 2. Definir les fonctions de calcul (fonctions flechees) ---
let additionner    = (a, b) => a + b;
let soustraire     = (a, b) => a - b;
let multiplier     = (a, b) => a * b;
let diviser        = (a, b) => {
    // Cas particulier : division par zero impossible en mathematiques
    if (b === 0) {
        return "Erreur : division par zero impossible.";
    }
    return a / b;
};


// --- 3. Fonction utilitaire : afficher le resultat dans la page ---
function afficherResultat(valeur) {
    // textContent modifie le texte de l'element sans interpreter le HTML
    affichage.textContent = "Resultat : " + valeur;
}


// --- 4. Attacher un evenement "click" a chaque bouton ---
btnAdd.addEventListener("click", function() {
    // parseFloat() convertit la valeur du champ (toujours une chaine) en nombre decimal
    let a = parseFloat(inputNb1.value);
    let b = parseFloat(inputNb2.value);
    afficherResultat(additionner(a, b));
});

btnSous.addEventListener("click", function() {
    let a = parseFloat(inputNb1.value);
    let b = parseFloat(inputNb2.value);
    afficherResultat(soustraire(a, b));
});

btnMult.addEventListener("click", function() {
    let a = parseFloat(inputNb1.value);
    let b = parseFloat(inputNb2.value);
    afficherResultat(multiplier(a, b));
});

btnDiv.addEventListener("click", function() {
    let a = parseFloat(inputNb1.value);
    let b = parseFloat(inputNb2.value);
    afficherResultat(diviser(a, b));
});
```

**Point de controle** : testez votre calculatrice avec les cas suivants et verifiez chaque resultat :

| Nb 1 | Nb 2 | Bouton | Resultat attendu |
|---|---|---|---|
| 10 | 5 | Addition | 15 |
| 8 | 3 | Soustraction | 5 |
| 4 | 7 | Multiplication | 28 |
| 10 | 2 | Division | 5 |
| 10 | 0 | Division | Erreur : division par zero impossible. |
| 7.5 | 2.5 | Addition | 10 |

---

## Recapitulatif

| Concept | Syntaxe cle |
|---|---|
| Variable | `let x = 10;` |
| Constante | `const PI = 3.14;` |
| Condition | `if (x > 0) { ... } else { ... }` |
| Ternaire | `let msg = (x > 0) ? "positif" : "negatif";` |
| Boucle for | `for (let i = 0; i < n; i++) { ... }` |
| Boucle while | `while (condition) { ... }` |
| Fonction nommee | `function nom(a, b) { return a + b; }` |
| Fonction anonyme | `let nom = function(a, b) { return a + b; };` |
| Fonction flechee | `let nom = (a, b) => a + b;` |
| Callback | `function f(a, b, op) { return op(a, b); }` |
| Acces au DOM | `document.getElementById("monId")` |
| Modification du texte | `element.textContent = "nouveau texte";` |
| Evenement | `element.addEventListener("click", maFonction);` |

---

## Points d'amelioration (a realiser seul apres l'atelier)

1. Ajouter un bouton "Effacer" qui remet les deux champs a 0 et le resultat a "---".

2. Ajouter un historique des calculs : chaque resultat est ajoute a une liste `<ul>` sous la calculatrice, sans effacer les precedents.

3. Empecher les saisies invalides : utiliser `isNaN()` pour detecter si un champ ne contient pas un nombre valide, et afficher un message d'erreur au lieu de calculer.

4. Ajouter le modulo (reste de la division entiere) : `a % b`. Exemple : 10 % 3 = 1.

5. Refactoriser le code en creant une fonction generique `calculer(operateur)` qui lit les champs, appelle la bonne operation selon l'operateur recu en parametre ("+", "-", "*", "/"), et affiche le resultat. Remplacer les 4 blocs `addEventListener` par un seul appel par bouton.
