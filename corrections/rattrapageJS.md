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

# Projet Javascript
---
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 

## Par Robert DIASSÉ &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <img src="js.jpeg" alt="ISI" width="50px">

---

# **Travail Pratique – Rattrapage JavaScript**

## **Énoncé**

Vous devez créer une petite page web permettant de **gérer une liste de produits**.

### **HTML de départ**

```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Rattrapage JS</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <h1>Gestion de Produits</h1>

    <form id="product-form">
        <input type="text" id="product-name" placeholder="Nom du produit" required>
        <input type="number" id="product-price" placeholder="Prix" required>
        <button type="submit">Ajouter</button>
    </form>

    <input type="text" id="search" placeholder="Rechercher un produit...">

    <ul id="product-list"></ul>

    <div id="cart-count">Panier : 0</div>

    <script src="script.js"></script>
</body>
</html>
```

---

### **Tâches à réaliser**

1. **Ajouter un produit**

   * Récupérer les valeurs du formulaire (nom et prix).
   * Ajouter le produit dans un **tableau JavaScript**.
   * Afficher dynamiquement la liste des produits dans `<ul id="product-list">`.

<!-- 2. **Ajouter au panier**   

   * Chaque produit affiché doit avoir un **bouton “Ajouter au panier”**.
   * Quand on clique dessus, le compteur du panier (`#cart-count`) doit augmenter de 1. -->
<!-- 
2. **Recherche dynamique**

   * L’utilisateur peut taper dans le champ `#search` pour filtrer les produits affichés en temps réel par **nom**. -->

2. **Suppression d’un produit**

   * Chaque produit doit également avoir un bouton **“Supprimer”** qui supprime le produit du tableau et de l’affichage.

---

### **Consignes**

* Utiliser uniquement **JavaScript**.
* Manipuler le DOM pour **créer et supprimer** les éléments `<li>`.
* Votre code doit être **lisible**.
* Ajouter un style  CSS pour rendre le tout lisible.

---

### **Barème**

| Critère                                  | Points |
| ---------------------------------------- | ------ |
| Formulaire fonctionnel (ajout produit)   | 5      |
| Affichage dynamique des produits         | 5      |
| Bouton “Supprimer” fonctionnel           | 3      |
| Code lisible                             | 2      |
|  (style/CSS)                        | 2      |
| **Total : 17 points**                    |        |


