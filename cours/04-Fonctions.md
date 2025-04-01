# Fonctions

## Définition

Une fonction est un **bloc de code réutilisable** qui effectue une tâche.

```js
function sayHello() {
    console.log("Bonjour !");
}
```

Pour **exécuter** une fonction, on l'appelle avec des parenthèses :

```js
sayHello(); // Affiche : Bonjour !
```

---

## Fonction avec paramètres

```js
function introduce(firstname) {
    console.log("Salut", firstname);
}

introduce("Alice"); // Salut Alice
introduce("Bob");   // Salut Bob
```

> Les **paramètres** sont les "entrées" de la fonction.  
> On peut en avoir plusieurs.

```js
function add(a, b) {
    return a + b;
}

let result = add(3, 4); // 7
```

---

## Mot-clé `return`

- Permet de **renvoyer une valeur** depuis la fonction.
- Met fin à l'exécution de la fonction.

```js
function square(x) {
    return x * x;
}

console.log(square(5)); // 25
```

---

## Fonctions anonymes et fléchées (ES6)

### Fonction anonyme (stockée dans une variable)

```js
const sayHello = function() {
    console.log("Salut !");
};
```

### Fonction fléchée

> La flèche fait office de return implicite
> Mettre des `{}` casse cet effet le return doit être explicite dans ce cas là

```js
const sayHello = () => {
    console.log("Salut !");
};

const compute = (a, b) => a + b; // ✅ return implicite
const compute = (a, b) => {
    return a + b; // ❌ return explicite, fonctionne mais mauvaise pratique
} 
```

---

## Valeurs par défaut

```js
function introduce(firstname = "visiteur") {
    console.log("Bienvenue", firstname);
}

introduce();         // Bienvenue visiteur
introduce("Marie");  // Bienvenue Marie
```

---

## Fonctions imbriquées (scope)

```js
function outside() {
    const message = "Je suis dehors";

    function inside() {
        console.log(message); // a accès à la variable "message"
    }

    inside();
}
```

---

## Bonnes pratiques

✅ Donné un **nom clair et descriptif** à la fonction :

```js
// Bien :
function computeSum() {} ✅ 

// Moins bien :
function cs() {} ❌
```

✅ Utilise **const** pour stocker une fonction :

```js
const displayMessage = () => {
    console.log("Message");
};
```

✅ Une fonction doit **faire une seule chose** (principe de responsabilité unique)

```js
// Bien :
function getUserFullName(user) { 
    return user.firstName + " " + user.lastName; ✅
}
```

✅ Privilégie **les fonctions pures** quand c’est possible (pas d’effets de bord)

---

## À éviter

❌ Ne pas appeler la fonction sans parenthèses si tu veux qu’elle s’exécute

```js
direBonjour; // ❌ rien ne se passe
direBonjour(); // ✅ la fonction est exécutée
```

❌ Trop de paramètres → utiliser un objet :

```js
// Moins bien
function createProfil(nom, age, pays, email, bio) {} ❌

// Mieux
function createProfil({ nom, age, pays, email, bio }) {} ✅
```

> **on peut utiliser des structures de contrôle, des variables dans les fonctions**
