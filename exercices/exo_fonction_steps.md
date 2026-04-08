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

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 

## Par Robert DIASSÉ &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <img src="js.jpeg" alt="ISI" width="50px">
## **Exercice : Gestion d’un mini-système de notes en utilisant des Fonctions**

**Objectif général :**  
Consolider l’apprentissage des **fonctions en JavaScript** à travers un exercice structuré en étapes progressives. Chaque étape introduit une notion clé.

---

### **Données de départ** :

```javascript
let etudiants = [
  { nom: "Awa", notes: [12, 15, 14] },
  { nom: "Cheikh", notes: [8, 10, 9] },
  { nom: "Fatou", notes: [17, 18, 16] },
  { nom: "Moussa", notes: [13, 11, 10] }
];
```

---


### **Étape 1 – Déclaration et appel d’une fonction simple**

**Consigne** :  
Déclarez une fonction nommée `saluer` qui affiche “Bienvenue dans le système de gestion des notes”. Appelez cette fonction.

---

### **Étape 2 – Fonction avec paramètre**

**Consigne** :  
Créez une fonction `afficherNom(nom)` qui reçoit un nom en paramètre et affiche `Nom de l'étudiant : nom`. Appelez cette fonction pour chaque étudiant du tableau `etudiants`.

---

### **Étape 3 – Fonction avec retour de valeur**

**Consigne** :  
Créez une fonction `calculerMoyenne(notes)` qui reçoit un tableau de notes et retourne la moyenne.  
Utilisez cette fonction pour afficher la moyenne de chaque étudiant.

---

### **Étape 4 – Fonction avec condition (et retour)**

**Consigne** :  
Créez une fonction `obtenirMention(moyenne)` qui retourne une mention selon la moyenne :  
- >= 16 : Très bien  
- 14-15 : Bien  
- 12-13 : Assez bien  
- 10-11 : Passable  
- < 10 : Insuffisant

Affichez pour chaque étudiant son nom, sa moyenne, et sa mention.

---

### **Étape 5 – Fonctions imbriquées (composition)**

**Consigne** :  
Créez une fonction `afficherBulletin(etudiant)` qui utilise `calculerMoyenne` et `obtenirMention` pour afficher :

```
Nom : Awa
Moyenne : 13.67
Mention : Assez bien
```

Faites cela pour tous les étudiants.

---

### **Étape 6 – Fonction fléchée (arrow function)**

**Consigne** :  
Réécrivez `calculerMoyenne` avec la syntaxe de fonction fléchée.

---

### **Étape 7 – Fonction anonyme et expression de fonction**

**Consigne** :  
Créez une fonction anonyme stockée dans une variable `estAdmis` qui retourne `true` si la moyenne est >= 10, `false` sinon.  
Utilisez-la pour afficher si chaque étudiant est admis.

---

### **Étape 8 – Callback : fonction passée en paramètre**

**Consigne** :  
Créez une fonction `traiterEtudiants(callback)` qui prend une fonction en paramètre et l’applique à chaque étudiant.  
Passez-lui `afficherBulletin` en paramètre pour afficher tous les bulletins.

---

### **Étape 9 – Bonus : Retour d’un objet depuis une fonction**

**Consigne** :  
Créez une fonction `analyserEtudiant(etudiant)` qui retourne un **objet** contenant :  
- son nom,  
- sa moyenne,  
- sa mention,  
- un booléen `admis`.

Stockez ces objets dans un nouveau tableau `resultats`.

---

### **Étape 10 – Synthèse (tableau final)**

**Consigne** :  
Affichez dans la console un tableau final sous forme de résumé :

```
Nom     | Moyenne | Mention      | Admis
--------|---------|--------------|--------
Awa     | 13.67   | Assez bien   | Oui
Cheikh  | 9       | Insuffisant  | Non
...
```

---

<!-- ### **Objectifs pédagogiques atteints :**

- Comprendre les fonctions simples et avec paramètres
- Maîtriser les fonctions avec `return`
- Utiliser des fonctions imbriquées
- Introduire les fonctions fléchées, anonymes et callbacks
- Manipuler les objets en retour de fonctions

--- -->
