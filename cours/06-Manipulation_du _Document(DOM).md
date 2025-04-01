# 06 - Manipulation du DOM

## Qu'est-ce que le DOM ?

DOM = **Document Object Model**. C'est une **représentation en mémoire** de la page HTML par le navigateur.

> Le DOM permet à JavaScript de lire, modifier, ajouter ou supprimer des éléments HTML dynamiquement.
> La représentation du document forme un "arbre".
> Les éléments sont structurés sous forme de noeud.

Exemple :

```html
<p id="text">Bonjour</p>
```

```js
const element = document.getElementById("text"); // récupération du noeud html avec l'id "text"
element.textContent = "Bonsoir"; // Modification du contenu du noeud
```

---

## Sélection d'éléments

### Par ID

```js
const title = document.getElementById("title");
```

### Par classe

```js
const containers = document.getElementsByClassName("container");
```

### Par balise

```js
const texts = document.getElementsByTagName("p");
```

### Avec querySelector (plus moderne)

```js
const description = document.querySelector("p"); // sélecteur CSS
const button = document.querySelector(".btn"); // classe
const mainTitle = document.querySelector("#main-title"); // id
```

### querySelectorAll

```js
const texts = document.querySelectorAll("p"); // NodeList
```

---

## Modifier le contenu

```js
const title = document.getElementById("title");
title.textContent = "Nouveau titre"; // modifie le texte

title.innerHTML = "<span style='color:red'>Titre</span>"; // interprète le HTML
```

> ✅ `textContent` = plus sûr, évite l'exécution de code
> ⚠️ `innerHTML` = puissant mais à utiliser avec prudence (risque XSS)

---

## Modifier les attributs

```js
const image = document.querySelector("img"); // récupération de l'image
image.setAttribute("alt", "Chat trop mignon"); // créer l'attribut "alt" avec comme valeur "Chat trop mignon"
image.src = "chat-kawai.webp"; // Injection de l'image "chat-kawai.webp" au noeud image
```

---

## Modifier le style CSS

```js
const bouton = document.querySelector("button");
bouton.style.color = "white";
bouton.style.backgroundColor = "blue";
```

> **Les noms de propriété CSS deviennent camelCase en JS** :
> `background-color` → `backgroundColor`

---

## Ajouter / supprimer des classes

```js
const box = document.querySelector(".box");
box.classList.add("active");     // ajoute une classe
box.classList.remove("hidden");  // supprime une classe
box.classList.toggle("dark");    // ajoute si absente, retire si présente
```

---

## Gérer les événements

```js
const btn = document.querySelector("button");

btn.addEventListener("click", () => {
    alert("Bouton cliqué !");
});
```

> D'autres événements sont disponibles : `mouseover`, `keydown`, `submit`, etc.

---

## Créer un élément

```js
const newText = document.createElement("p");
newText.textContent = "Paragraphe ajouté dynamiquement";
```

---

## Ajouter dans la page

```js
const section = document.querySelector("section");
section.appendChild(newText); // ajoute à la fin
```

Tu peux aussi utiliser :

```js
section.prepend(newText);    // ajoute au début
section.append(newText);     // ajoute aussi à la fin (plus souple)
```

### Note sur les différences entre append VS appendChild

#### appendChild()

- ✅ Ajoute un **seul nœud** (élément HTML) à la fin d’un parent.
- ❌ Ne peut **pas ajouter du texte** directement.
- ❌ Ne peut pas ajouter plusieurs éléments en une seule fois.
- ✅ **Retourne** l’élément inséré → **on peut enchaîner dessus**.

```js
const div = document.createElement("div");
div.textContent = "Salut !";

const result = document.body.appendChild(div); // ✅ Retourne le div ajouté
console.log(result.classList); // On peut enchaîner !
```

```js
document.body.appendChild("Coucou"); // ❌ Erreur : doit être un noeud
```

#### append()

- ✅ Plus **souple** : accepte **du texte, des éléments, ou plusieurs éléments**.
- ✅ Peut ajouter plusieurs éléments en même temps.
- ❌ Ne retourne rien → on ne peut **pas chaîner** directement.

```js
const p = document.createElement("p");
p.textContent = "Hello";

document.body.append("Coucou");         // ✅ Ajoute du texte
document.body.append(p);                // ✅ Ajoute un élément
document.body.append("Hey", p);         // ✅ Ajoute du texte ET un élément
```

---

## Supprimer un élément

```js
const cta = document.querySelector("cta");
cta.remove();
```

---

## Bonnes pratiques

✅ Attendre que le DOM soit chargé (si script placé dans le `<head>`)

```js
document.addEventListener("DOMContentLoaded", () => {
    // tout le code ici
});
```

Sinon, placer l'appel du fichier de script avant la fermeture du `<body>`

✅ Ne pas abuser de `innerHTML`  
✅ Regrouper la logique dans des fonctions  
✅ Utiliser `const` ou `let`, pas `var`  
✅ Donner des noms descriptifs aux éléments JS (`mainTitle`, `submitButton`, etc.)
