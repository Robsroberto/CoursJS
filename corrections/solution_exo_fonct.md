<!-- Voici la **solution complète de l'exercice sur les fonctions en JavaScript**, **étape par étape**, avec des explications pédagogiques pour chacune. Cela permettra à tes étudiants de comprendre comment progresser progressivement de la fonction la plus basique à des usages avancés.

--- -->

### ✅ **Étape 1 – Fonction simple**

```javascript
function saluer() {
  console.log("Bienvenue dans le système de gestion des notes");
}
saluer();
```

> 👉 Objectif : introduire la déclaration et l'appel d'une fonction.

---

### ✅ **Étape 2 – Fonction avec paramètre**

```javascript
function afficherNom(nom) {
  console.log("Nom de l'étudiant : " + nom);
}

let etudiants = [
  { nom: "Awa", notes: [12, 15, 14] },
  { nom: "Cheikh", notes: [8, 10, 9] },
  { nom: "Fatou", notes: [17, 18, 16] },
  { nom: "Moussa", notes: [13, 11, 10] }
];

for (let etu of etudiants) {
  afficherNom(etu.nom);
}
```

> 👉 Objectif : montrer comment passer un paramètre à une fonction et l'utiliser.

---

### ✅ **Étape 3 – Fonction avec retour de valeur**

```javascript
function calculerMoyenne(notes) {
  let somme = 0;
  for (let note of notes) {
    somme += note;
  }
  return (somme / notes.length).toFixed(2); // arrondi à 2 décimales
}

// Version avec reduce
function calculerMoyenneReduce(notes) {
  return (notes.reduce((acc, note) => acc + note, 0) / notes.length).toFixed(2);
}

for (let etu of etudiants) {
  console.log("Moyenne de " + etu.nom + " : " + calculerMoyenne(etu.notes));
}
```

> 👉 Objectif : utiliser `return`, faire des calculs, et apprendre la portée locale de variables.

---

### ✅ **Étape 4 – Fonction conditionnelle avec retour**

```javascript
function obtenirMention(moyenne) {
  moyenne = parseFloat(moyenne); // convertit en nombre
  if (moyenne >= 16) {
    return "Très bien";
  } else if (moyenne >= 14 && moyenne < 16) {
    return "Bien";
  } else if (moyenne >= 12 && moyenne < 14) {
    return "Assez bien";
  } else if (moyenne >= 10 && moyenne < 12) {
    return "Passable";
  } else {
    return "Insuffisant";
  }
}

for (let etu of etudiants) {
  let moy = calculerMoyenne(etu.notes);
  console.log(`${etu.nom} : ${moy} - ${obtenirMention(moy)}`);
}
```

> 👉 Objectif : manipuler des conditions et les lier à des fonctions de calcul.

---

### ✅ **Étape 5 – Fonctions imbriquées**

```javascript
function afficherBulletin(etudiant) {
  let moyenne = calculerMoyenne(etudiant.notes);
  let mention = obtenirMention(moyenne);

  console.log("---------------");
  console.log("Nom : " + etudiant.nom);
  console.log("Moyenne : " + moyenne);
  console.log("Mention : " + mention);
}

for (let etu of etudiants) {
  afficherBulletin(etu);
}
```

> 👉 Objectif : combiner plusieurs fonctions pour encapsuler une logique complète.

---

### ✅ **Étape 6 – Fonction fléchée**

```javascript
let calculerMoyenneArrow = (notes) => {
  let somme = 0;
  for (let note of notes) {
    somme += note;
  }
  return (somme / notes.length).toFixed(2);
};
```

> 👉 Objectif : introduire la syntaxe ES6 moderne avec les **arrow functions**.

---

### ✅ **Étape 7 – Fonction anonyme (expression)**

```javascript
let estAdmis = function(moyenne) {
  return moyenne >= 10;
};

for (let etu of etudiants) {
  let moyenne = calculerMoyenne(etu.notes);
  console.log(`${etu.nom} est ${estAdmis(moyenne) ? "admis" : "recalé"}`);
}
```

> 👉 Objectif : découvrir les fonctions anonymes stockées dans des variables.

---

### ✅ **Étape 8 – Callback**

```javascript
function traiterEtudiants(callback) {
  for (let etu of etudiants) {
    callback(etu);
  }
}

traiterEtudiants(afficherBulletin);
```

> 👉 Objectif : utiliser les fonctions comme **arguments** pour automatiser des actions.

---

### ✅ **Étape 9 – Fonction qui retourne un objet**

```javascript
function analyserEtudiant(etudiant) {
  let moyenne = calculerMoyenne(etudiant.notes);
  return {
    nom: etudiant.nom,
    moyenne: moyenne,
    mention: obtenirMention(moyenne),
    admis: estAdmis(moyenne)
  };
}

let resultats = [];
for (let etu of etudiants) {
  resultats.push(analyserEtudiant(etu));
}
```

> 👉 Objectif : faire **retourner des objets** depuis une fonction.

---

### ✅ **Étape 10 – Affichage final structuré**

```javascript
// Affichage avec console.table() qui gère automatiquement le formatage
console.table(resultats, ['nom', 'moyenne', 'mention', 'admis']);
```

> 👉 Objectif : utiliser `console.table()` pour un affichage tabulaire automatique et propre des données.
