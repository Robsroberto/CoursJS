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

# TP 1 – Mini Réservation (Cosmétiques)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 

## Par Robert DIASSÉ &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <img src="js.jpeg" alt="ISI" width="50px">
---

###  **Objectif général du TP**

Créer une page de réservation pour un salon de beauté/cosmétique, avec formulaire interactif, gestion dynamique via le DOM, et amélioration progressive du design de base (fourni).

---

##  **Phase 1 – Mise en place de la base HTML/CSS (ou Bootstrap)**

###  Étape 1 – Structure HTML  :

Fichier `index.html` minimal contenant :

```html
<header>
  <nav>
    <h1>CosmétiPlus</h1>
    <ul>
      <li><a href="#">Accueil</a></li>
      <li><a href="#">Nos services</a></li>
      <li><a href="#">Réservation</a></li>
    </ul>
  </nav>
</header>

<main>
  <section id="intro">
    <h2>Réservez votre moment beauté</h2>
    <p>Choisissez votre service préféré et un créneau disponible</p>
  </section>

  <section id="reservation-form">
    <form id="formulaire">
      <label>Nom :
        <input type="text" id="nom">
      </label>
      <label>Prénom :
        <input type="text" id="prenom">
      </label>
      <label>Service :
        <select id="service">
          <option>Manucure</option>
          <option>Maquillage</option>
          <option>Massage</option>
        </select>
      </label>
      <label>Date :
        <input type="date" id="date">
      </label>
      <button type="submit">Réserver</button>
    </form>
  </section>

  <section id="confirmation"></section>
</main>
```

---

###  Étape 2 – Feuille CSS de base :

```css
body {
  font-family: Arial, sans-serif;
  background-color: #fce4ec;
  color: #333;
  margin: 0;
  padding: 0;
}

header {
  background: rgba(255, 255, 255, 0.3);
  backdrop-filter: blur(10px);
  padding: 1rem;
}

nav ul {
  display: flex;
  gap: 1rem;
  list-style: none;
}

section {
  padding: 2rem;
}
```

---

##  **Phase 2 – Intégration DOM et interactions JS**

###  Étape 3 – Script de base :

Fichier `script.js` :

```javascript
const formulaire = document.getElementById("formulaire");
const confirmation = document.getElementById("confirmation");

formulaire.addEventListener("submit", function(e) {
  e.preventDefault();

  const nom = document.getElementById("nom").value;
  const prenom = document.getElementById("prenom").value;
  const service = document.getElementById("service").value;
  const date = document.getElementById("date").value;

  confirmation.innerHTML = `
    <h3>Confirmation</h3>
    <p>Merci ${prenom} ${nom} pour votre réservation du service <strong>${service}</strong> le <strong>${date}</strong>.</p>
  `;
});
```

---

##  **Phase 3 – Améliorations progressives attendues**

* Ajouter un effet de slide à la section confirmation.
* Cacher la section confirmation avant soumission, puis l’afficher dynamiquement.
* Vérifier les champs (pas vides, nom/prénom avec au moins 3 lettres…).
* Ajouter un système de compteur de réservations (stockées dans un tableau).
* Afficher la liste des réservations (DOM + tableau).
* Trier ou filtrer les réservations par date ou service.
* Ajouter une zone "supprimer une réservation".
* Adapter le design avec des composants Bootstrap (cards, boutons, etc).
* Ajouter un effet `hover` ou une animation au formulaire.

---

<!-- 
Voici les scripts JavaScript correspondant à chaque amélioration du TP1 **(site de réservation de services cosmétiques)**. Tous ces scripts sont conçus pour fonctionner ensemble et s’intégrer progressivement dans un seul projet HTML/CSS + JS basé sur le DOM pur (sans framework).

---

### ✅ 1. **Afficher automatiquement la date et l'heure actuelle dans un champ de formulaire**

```js
const now = new Date();
const dateField = document.getElementById("date-reservation");
if (dateField) {
  dateField.value = now.toISOString().slice(0, 16); // format 'YYYY-MM-DDTHH:mm'
}
```

Assure-toi que le champ a bien un ID `date-reservation` et est de type `datetime-local`.

---

### ✅ 2. **Mettre en évidence les champs obligatoires si le formulaire est soumis vide**

```js
const form = document.getElementById("reservation-form");
form.addEventListener("submit", function (e) {
  const requiredFields = form.querySelectorAll("[required]");
  let isValid = true;

  requiredFields.forEach(field => {
    if (!field.value.trim()) {
      isValid = false;
      field.style.border = "2px solid red";
    } else {
      field.style.border = "1px solid #ccc";
    }
  });

  if (!isValid) {
    e.preventDefault();
    alert("Veuillez remplir tous les champs obligatoires.");
  }
});
```

---

### ✅ 3. **Afficher un résumé en direct des informations sélectionnées**

```js
const nameInput = document.getElementById("nom-client");
const serviceInput = document.getElementById("service");
const dateInput = document.getElementById("date-reservation");
const recap = document.getElementById("recapitulatif");

function updateRecap() {
  recap.innerHTML = `
    <strong>Nom :</strong> ${nameInput.value}<br>
    <strong>Service :</strong> ${serviceInput.value}<br>
    <strong>Date :</strong> ${dateInput.value}
  `;
}

[nameInput, serviceInput, dateInput].forEach(input => {
  input.addEventListener("input", updateRecap);
});
```

Ajoute un `<div id="recapitulatif"></div>` à l’endroit voulu dans ton HTML.

---

### ✅ 4. **Filtrer dynamiquement les prestations selon la catégorie choisie**

```js
const categorieSelect = document.getElementById("categorie");
const serviceSelect = document.getElementById("service");

const servicesParCategorie = {
  "Coiffure": ["Brushing", "Tresses", "Coloration"],
  "Esthétique": ["Soin du visage", "Massage", "Épilation"],
  "Onglerie": ["Pose gel", "Manucure", "Vernis semi-permanent"]
};

categorieSelect.addEventListener("change", function () {
  const services = servicesParCategorie[categorieSelect.value] || [];
  serviceSelect.innerHTML = "";
  services.forEach(service => {
    const opt = document.createElement("option");
    opt.value = service;
    opt.textContent = service;
    serviceSelect.appendChild(opt);
  });
});
```

---

### ✅ 5. **Afficher une alerte personnalisée de confirmation après soumission**

```js
form.addEventListener("submit", function (e) {
  e.preventDefault();
  alert(`Merci ${nameInput.value}, votre rendez-vous est confirmé pour le service "${serviceInput.value}" le ${dateInput.value}.`);
  form.reset();
  recap.innerHTML = "";
});
```

---

### ✅ 6. **Afficher ou masquer un message "réduction disponible" selon le service choisi**

```js
const messagePromo = document.getElementById("promo-message");

serviceInput.addEventListener("change", function () {
  if (serviceInput.value === "Massage" || serviceInput.value === "Coloration") {
    messagePromo.style.display = "block";
  } else {
    messagePromo.style.display = "none";
  }
});
```

Ajoute un élément dans ton HTML :

```html
<p id="promo-message" style="display:none; color: green;">🎁 Une réduction de 10% est appliquée sur ce service !</p>
```

---

Souhaites-tu que je t’intègre tout ce code dans un fichier HTML complet avec le formulaire de base + style CSS simple ou Bootstrap pour que tu puisses leur fournir un point de départ propre ?

 -->
