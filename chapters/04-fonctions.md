# Les Fonctions


## Les Fonctions en JavaScript

Les fonctions sont des blocs de code réutilisables qui permettent d'organiser et de structurer votre code. Elles prennent des entrées (appelées paramètres), effectuent des opérations et retournent une valeur.

## Déclaration de Fonction


### Fonction Nommée


```javascript Une fonction nommée est définie avec le mot-clé function suivi d'un nom, de paramètres entre parenthèses
```

et d'un bloc de code entre accolades.

```javascript function saluer(nom) { return "Bonjour " + nom + "!"; console.log(saluer("Alice")); // Affiche "Bonjour Alice!"
```


### Fonction Anonyme

Une fonction anonyme est une fonction sans nom, souvent utilisée comme valeur de retour ou argument pour une autre fonction.

```javascript let afficherMessage = function(message) { console.log(message); afficherMessage("Salut!"); // Affiche "Salut!"
```


### Fonction Fléchée (Arrow Function)


```javascript Les fonctions fléchées offrent une syntaxe plus concise et ne lient pas leur propre this. let addition = (a, b) => a + b; console.log(addition(2, 3)); // Affiche 5
```


### Fonctions Imbriquées

Les fonctions peuvent être définies à l'intérieur d'autres fonctions.

```javascript function exterieur(a) { function interieur(b) { return a + b; return interieur; let additionDeCinq = exterieur(5); console.log(additionDeCinq(3)); // Affiche 8
```


## Fonctions Prédéfinies (Built-in Functions)

JavaScript inclut de nombreuses fonctions prédéfinies qui peuvent être utilisées immédiatement.

```code parseInt()
```

Convertit une chaîne en entier.

```javascript let entier = "123"; console.log(typeof entier);// Affiche string entier = parseInt("123"); console.log(entier); // Affiche 123 console.log(typeof entier); // Affiche number parseFloat()
```

Convertit une chaîne en nombre à virgule flottante.

```javascript let flottant = parseFloat("123.45"); console.log(flottant); // Affiche 123.45 isNaN()
```

Vérifie si une valeur est NaN (Not-a-Number).

```javascript let resultat = isNaN("123"); console.log(resultat); // Affiche false setTimeout()
```

Exécute une fonction après un certain délai.

```javascript setTimeout(function() { console.log("Exécuté après 2 secondes"); }, 2000); setInterval()
```

Exécute une fonction à intervalles réguliers.

```javascript let compteur = 0; let intervalId = setInterval(function() { compteur++; console.log("Compteur : " + compteur); if (compteur === 5) { clearInterval(intervalId); }, 1000);
```


## Fonctions Avancées


### Fonctions de Rappel (Callback Functions)

Les fonctions de rappel sont des fonctions passées en argument à une autre fonction, qui les appelle après avoir terminé son travail.

```javascript function demanderNom(callback) { let nom = prompt("Quel est votre nom?"); callback(nom); demanderNom(function(nom) { console.log("Bonjour " + nom + "!"); });
```


### Fonctions Immédiatement Invocables (IIFE)

Les fonctions immédiatement invoquées sont définies et exécutées immédiatement.

```javascript (function() { console.log("Cette fonction est immédiatement invoquée."); })();
```


### Fonctions Asynchrones


```code Les fonctions asynchrones utilisent async et await pour gérer les opérations asynchrones de manière plus
```

lisible.

```javascript async function fetchData() { let response = await fetch('https://api.example.com/data'); let data = await response.json(); console.log(data); fetchData();
```


### Portée des Variables

Les variables en JavaScript peuvent avoir une portée globale ou locale. Globale : Déclarée en dehors de toute fonction. Locale : Déclarée à l'intérieur d'une fonction.

```javascript let globalVar = "Je suis globale"; function afficherGlobale() { console.log(globalVar); afficherGlobale(); // Affiche "Je suis globale"
```


### Récursivité

Une fonction récursive est une fonction qui s'appelle elle-même.

```javascript function factorielle(n) { if (n <= 1) { return 1; } else { return n * factorielle(n - 1); console.log(factorielle(5)); // Affiche 120
```


## Exercices


### Exercice 1 : Création de Fonction


```code 1. Créez une fonction multiplier qui prend deux nombres en paramètres et retourne leur produit.
```


### Exercice 2 : Fonction de Rappel


```code 1. Créez une fonction effectuerOperation qui prend deux nombres et une fonction de rappel pour
```

effectuer une opération (addition, multiplication, etc.).

### Exercice 3 : Fonction Fléchée


```code 1. Convertissez la fonction multiplier en fonction fléchée.
```


### Exercice 4 : Récursivité


```code 1. Créez une fonction récursive compter qui affiche les nombres de 1 à 5.
```


### Spread Operator


```code Le spread operator (...) permet d'étaler les éléments d'un tableau ou les propriétés d'un objet. Il est
```

particulièrement utile dans les fonctions pour accepter un nombre variable d'arguments ou pour étendre des objets. Utilisation avec les Tableaux

```javascript let nombres = [1, 2, 3]; let plusDeNombres = [...nombres, 4, 5, 6]; console.log(plusDeNombres); // Affiche [1, 2, 3, 4, 5, 6]
```

Utilisation avec les Objets

```javascript let personne = { nom: "Alice", age: 25 }; let personneAvecVille = { ...personne, ville: "Paris" }; console.log(personneAvecVille); // Affiche { nom: "Alice", age: 25, ville: "Paris"
```

Utilisation dans les Fonctions Le spread operator peut être utilisé pour passer un nombre variable d'arguments à une fonction.

```javascript function addition(...nombres) { return nombres.reduce((acc, curr) => acc + curr, 0); console.log(addition(1, 2, 3, 4)); // Affiche 10
```


### Exercice 5 : Utilisation du Spread Operator


```code 1. Créez une fonction concatenerTableaux qui utilise le spread operator pour fusionner deux tableaux. 2. Créez une fonction fusionnerObjets qui utilise le spread operator pour fusionner deux objets.
```

Ce cours couvre les bases des fonctions en JavaScript, ainsi que des concepts plus avancés, incluant la documentation pour les types de retour, le spread operator, et des exemples concrets pour une meilleure compréhension. Les exercices fournis permettent de mettre en pratique les concepts appris et de consolider les connaissances.

## Exercices pratiques

> Mets en pratique ce que tu viens d'apprendre avant de passer au chapitre suivant.

### Exercice 1 — Application directe

Applique les notions vues dans ce chapitre sur un exemple concret de ton choix.

**Consigne :** Réalise l'exercice correspondant à ce chapitre et valide ta compréhension avant de continuer.

### Exercice 2 — Questions de compréhension

- Quel est le concept principal de ce chapitre ?
- Donne un exemple d'utilisation concrète en contexte professionnel.
- Quelle notion t'a semblé la plus difficile ? Comment l'as-tu abordée ?

### Checklist avant de continuer

- J'ai lu et compris le contenu du chapitre
- J'ai réalisé au moins un exercice pratique
- Je peux expliquer le sujet à quelqu'un d'autre
