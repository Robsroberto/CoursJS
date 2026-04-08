Voici la **correction complète, commentée ligne par ligne** de l'exercice de gestion de commandes en JavaScript (sans utiliser de fonctions) :

---

### **Correction**

```javascript
// Déclaration initiale du tableau de commandes
let commandes = [
  {
    client: "Alioune",
    plats: ["Burger", "Frites", "Coca"],
    statut: "en attente",
    montant: 5500
  },
  {
    client: "Fatou",
    plats: ["Pizza", "Jus"],
    statut: "en cours",
    montant: 7200
  },
  {
    client: "Cheikh",
    plats: ["Tacos", "Frites"],
    statut: "terminée",
    montant: 6000
  },
  {
    client: "Aminata",
    plats: ["Salade", "Eau", "Yaourt"],
    statut: "en attente",
    montant: 4800
  }
];

// 1. Affichage de toutes les commandes de manière lisible
for (let commande of commandes) {
  console.log(
    "Client :", commande.client,
    "- Plats :", commande.plats.join(", "),
    "- Statut :", commande.statut,
    "- Montant :", commande.montant + " FCFA"
  );
}

// 2. Modification des statuts "en attente" vers "en cours"
for (let commande of commandes) {
  if (commande.statut === "en attente") {
    commande.statut = "en cours";
  }
}

// 3. Affichage des clients dont la commande est terminée
console.log("\nClients avec commande terminée :");
for (let commande of commandes) {
  if (commande.statut === "terminée") {
    console.log(commande.client);
  }
}

// 4. Création du tableau clientsFideles
let clientsFideles = [];
for (let commande of commandes) {
  if (commande.montant >= 6000) {
    clientsFideles.push(commande.client);
  }
}
console.log("\nClients fidèles (montant >= 6000 FCFA) :", clientsFideles);

// 5. Ajout d'une nouvelle commande
let nouvelleCommande = {
  client: "Moussa",
  plats: ["Shawarma", "Soda"],
  statut: "en attente",
  montant: 6300
};
commandes.push(nouvelleCommande);

// 6. Tri du tableau de commandes par montant croissant
commandes.sort(function (a, b) {
  return a.montant - b.montant;
});

// 7. Calcul de la somme des commandes en cours
let totalEnCours = 0;
for (let commande of commandes) {
  if (commande.statut === "en cours") {
    totalEnCours += commande.montant;
  }
}
console.log("\nTotal des montants des commandes en cours :", totalEnCours + " FCFA");

// 8. Réaffichage des commandes triées pour vérification
console.log("\nCommandes après tri par montant :");
for (let commande of commandes) {
  console.log(
    "Client :", commande.client,
    "- Montant :", commande.montant,
    "- Statut :", commande.statut
  );
}
```

---

### **Explications complémentaires pour les étudiants :**

- **`.join(", ")`** : permet de transformer un tableau en une chaîne avec virgules entre les éléments.
- **`.push()`** : ajoute un élément à la fin du tableau.
- **`.sort()`** : trie un tableau. Ici on compare les montants pour un tri croissant.
- **`for...of`** : simplifie la lecture d’un tableau, plus clair que `for(i = 0; i < ...)`.

Souhaites-tu maintenant que je propose une **version avancée avec export en JSON ou CSV**, ou bien un **deuxième exercice de consolidation** dans le même style ?