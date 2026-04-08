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

# **Introduction à jQuery**
---
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 

## Par Robert DIASSÉ &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <img src="js.jpeg" alt="ISI" width="50px">

---

# **Introduction à jQuery, Sélecteurs, Manipulation du DOM, et Événements**

## **1. Introduction à jQuery**

### Qu'est-ce que jQuery ?

jQuery est une bibliothèque JavaScript rapide, légère et concise, créée pour faciliter :

* La manipulation du DOM (ajout/suppression/modification des éléments HTML),
* La gestion des événements (clics, survols, saisie clavier, etc.),
* Les animations,
* Les appels Ajax.

### Pourquoi utiliser jQuery ?

* Écrit moins, fais plus : jQuery simplifie les actions complexes en JavaScript pur.
* Large compatibilité entre navigateurs.
* Excellente documentation et communauté.

### Intégration de jQuery

**Méthode 1 : CDN (recommandée pour les débuts)**

```html
<script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
```

**Méthode 2 : Fichier local**

```html
<script src="js/jquery.min.js"></script>
```

---

## **2. Structure de base et syntaxe de jQuery**

### Syntaxe générale :

```javascript
$(selector).action();
```

* `$` : appel de jQuery
* `selector` : cible un ou plusieurs éléments HTML
* `action()` : action à exécuter (masquer, changer du texte, ajouter une classe, etc.)

### Exemple simple :

```javascript
$(document).ready(function(){
    $("p").hide();
});
```

**Explication:**

* `$(document).ready(...)` : attend que le DOM soit entièrement chargé.
* `$("p")` : sélectionne tous les éléments `<p>` de la page.
* `.hide()` : les masque (display: none).

---

## **3. Les Sélecteurs jQuery**

### Quelques sélecteurs utiles :

| Sélecteur jQuery          | Cible                                       |
| ------------------------- | ------------------------------------------- |
| `$("div")`                | Tous les `<div>`                            |
| `$(".maClasse")`          | Tous les éléments avec la classe `maClasse` |
| `$("#monId")`             | L’élément avec l’ID `monId`                 |
| `$("p:first")`            | Le premier paragraphe                       |
| `$("input[type='text']")` | Tous les champs de texte                    |

**Exemple :**

```javascript
$(".important").css("color", "red");
```

* Sélectionne tous les éléments ayant la classe `important` et leur applique un style rouge.

---

## **4. Manipulation du DOM**

### Modifier le texte et le HTML :

```javascript
$("#titre").text("Bonjour !");
$("#contenu").html("<strong>Texte important</strong>");
```

### Ajouter ou supprimer un élément :

```javascript
$("#maListe").append("<li>Nouvel élément</li>");
$("#maListe").prepend("<li>Premier élément</li>");
$("#aSupprimer").remove();
```

### Modifier des attributs :

```javascript
$("img").attr("src", "nouvelle-image.jpg");
```

### Ajouter/Retirer une classe :

```javascript
$("#carte").addClass("active");
$("#carte").removeClass("active");
```

---

## **5. Gestion des événements**

### Syntaxe de base :

```javascript
$(selector).on("event", function(){
   // code à exécuter
});
```

### Principaux événements :

| Événement                | Déclenché lorsque…                |
| ------------------------ | --------------------------------- |
| `click`                  | Un clic de souris                 |
| `dblclick`               | Double clic                       |
| `mouseover` / `mouseout` | Survol ou sortie de la souris     |
| `keydown` / `keyup`      | Appui ou relâchement d'une touche |
| `change`                 | Modification d’un champ           |
| `submit`                 | Envoi d’un formulaire             |

### Exemple complet :

```javascript
$("#btn").on("click", function(){
    $("#message").text("Vous avez cliqué !");
});
```

**Explication:**

* `$("#btn")` sélectionne le bouton avec l’ID `btn`.
* `.on("click", ...)` attache une fonction au clic.
* `$("#message").text(...)` remplace le texte de l’élément ayant l’ID `message`.

<!-- ---

## **6. Cas pratique à préparer**

Dans le prochain fichier HTML d’exemple, nous créerons :

* Un titre dynamique,
* Une liste interactive,
* Un bouton qui affiche un message,
* Une animation simple avec un effet de fade ou slide. -->


<!-- 
    Commentaires pédagogiques sur les blocs à compléter ou adapter
$("#maListe").append(...) : tu peux inviter les étudiants à ajouter dynamiquement des éléments en utilisant des boucles ou des boutons.

$("#zone").addClass(...) : remplace ou enlève la classe pour illustrer les effets de styles.

Sur les événements (mouseover, click, etc.), propose d’ajouter un champ de saisie pour réagir au keyup, ou un formulaire pour gérer submit.
 -->