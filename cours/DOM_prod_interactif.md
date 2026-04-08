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

# TP 2 – Mini Catalogue Interactif (Épicerie ou Boutique Cosmétiques)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 

## Par Robert DIASSÉ &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <img src="js.jpeg" alt="ISI" width="50px">

Mettre en place **la structure HTML** de notre mini catalogue interactif.

---

###   Ce qui est attendu :

* Un **header complet** avec une barre de contact et un menu de navigation.
* Une **section de filtres** : recherche + tri.
* Une **section de produits** vide pour l'instant (elle sera remplie dynamiquement).
* Un élément de retour visuel pour le panier (`#panier-message`).
 ```html
 <!-- Atelier TP2 - Catalogue Interactif - Etape 1 -->
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Catalogue Interactif</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <div class="top-bar">
            <p>Contact : contact@moncatalogue.com | Tel : +221 77 123 45 67</p>
        </div>
        <nav>
            <ul class="menu">
                <li><a href="#">Accueil</a></li>
                <li><a href="#">Produits</a></li>
                <li><a href="#">Contact</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <section class="filtres">
            <input type="text" id="search" placeholder="Rechercher un produit...">
            <select id="sort">
                <option value="">Trier par...</option>
                <option value="asc">Prix croissant</option>
                <option value="desc">Prix décroissant</option>
            </select>
        </section>

        <section id="product-list" class="produits">
            <!-- Les cartes produits seront injectées ici -->
        </section>

        <div id="panier-message"></div>
    </main>

    <script src="script.js"></script>
</body>
</html>

 ```
---

###   Explication des parties :

#### 1. Barre de contact :

```html
<div class="top-bar">
    <p>Contact : contact@moncatalogue.com | Tel : +221 77 123 45 67</p>
</div>
```

➡ Affiche les infos utiles tout en haut.

#### 2. Menu de navigation :

```html
<nav>
    <ul class="menu">
        <li><a href="#">Accueil</a></li>
        <li><a href="#">Produits</a></li>
        <li><a href="#">Contact</a></li>
    </ul>
</nav>
```

➡ Barre de menu horizontale avec 3 liens.

#### 3. Filtres :

```html
<input type="text" id="search" placeholder="Rechercher un produit...">
<select id="sort">
    <option value="">Trier par...</option>
    <option value="asc">Prix croissant</option>
    <option value="desc">Prix décroissant</option>
</select>
```

➡ Champ de recherche + menu déroulant pour trier les produits.

#### 4. Zone d'affichage des produits :

```html
<section id="product-list" class="produits">
    <!-- À remplir dynamiquement avec JS -->
</section>
```

#### 5. Message de retour du panier :

```html
<div id="panier-message"></div>
```

➡ Pour afficher les messages de confirmation lors de l'ajout au panier.

---
Parfait ! Passons à **l’étape 2 : le CSS de base** pour styliser notre mini-catalogue de produits.
L’objectif ici est de **structurer et rendre agréable l’affichage** à l’aide de `Flexbox`, `Grid`, `variables`, et **animations légères**.

---

##   Étape 2 : CSS de Base pour Mise en Page

###   Objectif :

* Structurer l’interface avec des containers clairs.
* Appliquer des styles cohérents (couleurs, marges, espacements, police).
* Préparer le design pour qu’il soit **simplement responsive**.

---

##   Code CSS à intégrer (`style.css`)

```css
/* === Variables CSS : Palette personnalisable === */
:root {
  --color-primary: #4CAF50;
  --color-light: #f9f9f9;
  --color-dark: #333;
  --color-accent: #ffc107;
  --max-width: 1200px;
  --gap: 1rem;
}

/* === Reset + base === */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Segoe UI', sans-serif;
  background-color: var(--color-light);
  color: var(--color-dark);
  line-height: 1.6;
  padding: 1rem;
}

/* === Top Bar === */
.top-bar {
  background: var(--color-primary);
  color: white;
  text-align: center;
  padding: 0.5rem;
  font-size: 0.9rem;
}

/* === Menu de navigation === */
nav {
  background: white;
  border-bottom: 1px solid #ccc;
  margin-bottom: var(--gap);
}

.menu {
  display: flex;
  justify-content: center;
  gap: var(--gap);
  list-style: none;
  padding: 1rem 0;
}

.menu li a {
  text-decoration: none;
  color: var(--color-dark);
  padding: 0.5rem 1rem;
  transition: all 0.3s ease;
}

.menu li a:hover {
  background: var(--color-primary);
  color: white;
  border-radius: 5px;
}

/* === Filtres === */
#search, #sort {
  padding: 0.5rem;
  margin: 0.5rem 0;
  width: 100%;
  max-width: 400px;
  display: block;
}

/* === Section produits === */
.produits {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: var(--gap);
  margin-top: 2rem;
}

.produit {
  background: white;
  border-radius: 8px;
  padding: 1rem;
  box-shadow: 0 4px 8px rgba(0,0,0,0.05);
  transition: transform 0.3s ease;
}

.produit:hover {
  transform: scale(1.03);
}

.produit img {
  max-width: 100%;
  border-radius: 5px;
}

.produit h3 {
  margin: 0.5rem 0;
  font-size: 1.1rem;
}

.produit p {
  font-size: 0.95rem;
  margin-bottom: 0.5rem;
}

.produit button {
  padding: 0.5rem 1rem;
  background: var(--color-accent);
  border: none;
  color: white;
  cursor: pointer;
  border-radius: 4px;
}

.produit button:hover {
  background: #e0a800;
}

/* === Message panier === */
#panier-message {
  margin-top: 1rem;
  font-weight: bold;
  color: var(--color-primary);
}

/* === Responsive ajusté === */
@media (max-width: 600px) {
  .menu {
    flex-direction: column;
  }

  .menu li {
    text-align: center;
  }
}
```

---

##   Ce qui est attendu à cette étape :

* Un **catalogue clair, agréable à l’œil**, avec une grille fluide (responsive).
* Une interface de navigation bien visible.
* Un **style moderne** avec ombrage, couleurs harmonieuses, et interactions (hover).
* **Les éléments comme `search`, `sort` sont visibles** et accessibles.


---

## Étape 3 : Script JS d’Affichage Dynamique avec Recherche et Tri

###   Objectifs :

* Injecter dynamiquement les produits dans `#product-list`.
* Mettre en place la **fonction de recherche en temps réel**.
* Mettre en place la **fonction de tri par prix**.

---

###   Structure HTML concernée :

```html
<section class="filtres">
  <input type="text" id="search" placeholder="Rechercher un produit...">
  <select id="sort">
    <option value="">Trier par...</option>
    <option value="asc">Prix croissant</option>
    <option value="desc">Prix décroissant</option>
  </select>
</section>

<section id="product-list" class="produits">
  <!-- JS injecte les produits ici -->
</section>

<div id="panier-message"></div>
```

---

##   Code JavaScript : `script.js`

```js
// Liste de produits
const produits = [
    {
        nom: "Huile de Coco Bio",
        description: "100% naturelle, nourrit les cheveux et la peau.",
        prix: 2500,
        image: "https://picsum.photos/350"
    },
    {
        nom: "Masque Hydratant",
        description: "Hydrate les cheveux secs en profondeur.",
        prix: 3000,
        image: "https://picsum.photos/350"
    },
    {
        nom: "Savon Noir",
        description: "Nettoie naturellement la peau.",
        prix: 1500,
        image: "https://picsum.photos/350"
    }
];

// Références aux éléments DOM
const listeProduits = document.getElementById("product-list");
const barreRecherche = document.getElementById("search");
const triSelect = document.getElementById("sort");

// Affichage dynamique des produits
function afficherProduits(liste) {
    listeProduits.innerHTML = "";

    liste.forEach(produit => {
        const div = document.createElement("div");
        div.className = "carte-produit";
        div.innerHTML = `
            <img src="${produit.image}" alt="${produit.nom}">
            <h3>${produit.nom}</h3>
            <p>${produit.description}</p>
            <p><strong>${produit.prix} FCFA</strong></p>
            <button onclick="ajouterAuPanier('${produit.nom}')">Ajouter au panier</button>
        `;
        listeProduits.appendChild(div);
    });
}

// Filtrage
function filtrerEtTrierProduits() {
    let recherche = barreRecherche.value.toLowerCase();
    let tri = triSelect.value;

    let listeFiltree = produits.filter(p =>
        p.nom.toLowerCase().includes(recherche)
    );

    if (tri === "asc") {
        listeFiltree.sort((a, b) => a.prix - b.prix);
    } else if (tri === "desc") {
        listeFiltree.sort((a, b) => b.prix - a.prix);
    }

    afficherProduits(listeFiltree);
}

// Simuler l’ajout au panier
function ajouterAuPanier(nom) {
    const msg = document.getElementById("panier-message");
    msg.textContent = `${nom} ajouté au panier  `;
    msg.style.display = "block";
    setTimeout(() => {
        msg.style.display = "none";
    }, 2000);
}

// Événements
barreRecherche.addEventListener("input", filtrerEtTrierProduits);
triSelect.addEventListener("change", filtrerEtTrierProduits);

// Initialisation
afficherProduits(produits);
```

---

##   Résultat attendu à cette étape :

  Tous les produits s’affichent dès le chargement de la page
  En tapant dans la barre de recherche, les résultats s’actualisent automatiquement
  Le menu déroulant trie les produits par prix croissant/décroissant
  Un message apparaît lors du clic sur “Ajouter au panier”

---
Parfait, passons donc à l’**étape finale** de notre atelier : **l'ajout d’animations avancées** pour rendre l’interface plus fluide, dynamique et agréable à utiliser.

---

##  **Étape 4 – Ajout d’Animations Avancées**

###  Objectifs :

* Animer l’apparition des produits (effet **fade-in / slide-in**).
* Ajouter un **hover interactif** sur les cartes produits.
* Animer le **message panier**.
* Utiliser des **animations CSS modernes** (avec `@keyframes`, `:has()`, `:is()`, `clamp()`, etc.).

---

##   Partie 1 : **Effet de slide/fade à l’apparition**

**Ajoute ce code CSS dans `style.css` :**

```css
/* Animation d’apparition */
@keyframes slideFadeIn {
    from {
        opacity: 0;
        transform: translateY(30px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

.carte-produit {
    opacity: 0;
    animation: slideFadeIn 0.5s ease forwards;
    animation-delay: calc(var(--i, 0) * 0.1s);
}
```

**Modifie la fonction `afficherProduits()` dans `script.js` pour ajouter l’index de chaque carte** :

```js
function afficherProduits(liste) {
    listeProduits.innerHTML = "";

    liste.forEach((produit, index) => {
        const div = document.createElement("div");
        div.className = "carte-produit";
        div.style.setProperty('--i', index); // pour animation décalée
        div.innerHTML = `
            <img src="${produit.image}" alt="${produit.nom}">
            <h3>${produit.nom}</h3>
            <p>${produit.description}</p>
            <p><strong>${produit.prix} FCFA</strong></p>
            <button onclick="ajouterAuPanier('${produit.nom}')">Ajouter au panier</button>
        `;
        listeProduits.appendChild(div);
    });
}
```

---

##   Partie 2 : **Hover dynamique sur les cartes**

```css
.carte-produit {
    transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.carte-produit:hover {
    transform: translateY(-6px) scale(1.02);
    box-shadow: 0 15px 25px rgba(0, 0, 0, 0.1);
}
```

---

##   Partie 3 : **Animation sur le message panier**

```css
#panier-message {
    position: fixed;
    bottom: 20px;
    right: 20px;
    background: #222;
    color: #fff;
    padding: 10px 20px;
    border-radius: 6px;
    box-shadow: 0 2px 10px rgba(0,0,0,0.2);
    opacity: 0;
    transform: translateY(20px);
    transition: all 0.3s ease;
    z-index: 999;
}

#panier-message.active {
    opacity: 1;
    transform: translateY(0);
}
```

**Puis dans `script.js`, modifie la fonction `ajouterAuPanier()` :**

```js
function ajouterAuPanier(nom) {
    const msg = document.getElementById("panier-message");
    msg.textContent = `${nom} ajouté au panier 🛒`;
    msg.classList.add("active");

    setTimeout(() => {
        msg.classList.remove("active");
    }, 2000);
}
```

---

##  BONUS : Responsive progressif avec `clamp()` sur la taille des titres

```css
.carte-produit h3 {
    font-size: clamp(1rem, 2vw, 1.5rem);
}
```

---

##   Résultat attendu :

* Les produits **apparaissent avec animation fluide** au chargement ou au tri.
* Chaque carte a un **hover doux** avec effet de zoom léger.
* Le message panier **glisse et disparaît**.
* Le texte s’adapte à l’écran grâce à `clamp()`.

---

##   **Fonctionnalités élémentaires à ajouter (niveau débutant/intermédiaire)**

###   1. **Compteur de produits ajoutés au panier**

* Afficher dynamiquement le nombre de produits dans un coin du site ou sur un icône panier.
* Exemple : `Panier (3)`

  *Apprentissage DOM + mise à jour de contenu en temps réel*

---

###   2. **Filtrage par catégorie (via un menu déroulant ou des boutons)**

* Ajouter un champ `<select>` ou des boutons : `Tous`, `Légumes`, `Fruits`, `Cosmétiques`, etc.
* Afficher uniquement les produits correspondants.

  *Apprentissage du `filter()` en JS + DOM*

---

###   3. **Affichage du prix total du panier (simulation)**

* À chaque ajout, additionner le prix du produit et afficher un total.
* Possibilité d'un bouton “Voir le total”.

  *Manipulation de tableaux et calculs en JS*

---

###   4. **Ajout en favoris (wishlist)**

* Ajouter un bouton "💖" sur chaque carte produit.
* Marquer en favori (changement de style ou icône).
* Afficher une section “Produits favoris”.

  *Travail sur les classes CSS dynamiques + tableaux JS*

---

###   5. **Confirmation visuelle plus poussée**

* Ajouter une petite animation visuelle sur le bouton au clic (`scale`, `color change`, `disabled`, etc.).
* Exemple :

  ```css
  button:active {
    transform: scale(0.95);
    background: #0f0;
  }
  ```

  *Utilisation des pseudo-classes comme `:active`, `:focus`*

---

###   6. **Stock limité (simulation)**

* Chaque produit a un nombre en stock (ex. 5).
* À chaque ajout, le stock diminue. Quand stock = 0, désactiver le bouton.

  *Exercice de logique + DOM dynamique*

---

###   7. **Zoom sur l’image au survol**

* Ajouter un effet d’agrandissement ou zoom avec `scale()` sur `:hover`.

  *Apprentissage du `transform` avancé*

---

###   8. **Bouton “Vider le panier”**

* Réinitialise le compteur, le message et les styles actifs.
* Affiché en bas ou dans une barre flottante.

  *Travail sur les événements JS et remise à zéro de données*

---

###   9. **Thème clair/sombre**

* Ajouter un bouton toggle pour passer entre un style clair et sombre.
* Utiliser `classList.toggle()`.

  *Excellente initiation à la gestion des classes et au CSS conditionnel*

---
