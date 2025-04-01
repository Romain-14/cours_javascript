# Structures de contrôle

## Instruction IF

```js
let age = 21;

// L'évaluation de la condition doit être vraie (truthy) pour exécuter le bloc de code
// pour "age < 18", on va poser la question :
if (age < 18) {
    // Est-ce que la variable age est inférieure à 18 ?
    console.log("Tu es mineur !"); // <--- Oui c'est vrai
} else if (age < 21) {
    // Sinon, est-ce que age est inférieur à 21 (et donc >= 18) ?
    console.log("Tu peux conduire en France !!");
} else {
    // Si aucune des conditions précédentes n'est vraie (truthy), on exécute ce bloc :
    console.log("Il y un problème avec ton age ... 🤔");
}
```

### Combinaison de conditions

```js
let sayHi = "hello";

if (sayHi === "salut" || (sayHi === "hello" && sayHi === "hi")) {
    console.log(
        "----> COMPARAISON --> sayHi est égale à 'salut ou hello' ou 'hi' !"
    );
}

/*******/
let age = 18;
if (age >= 18 && (sayHi === "hello" || sayHi === "hi")) {
    console.log("Tu dis bonjour et t'es majeur, WOAH 👏👏👏!! ");
}
```

## Instruction SWITCH

```js
let sayHi = "hello";

switch (sayHi) {
    case "salut": // if (sayHi === "salut")
    case "hello": // Possibilité de vérifier une autre valeur pour la même instruction (OU)
    case "hi":
        console.log("sayHi est égale à 'salut ou hello' ou 'hi' !");
        break; // Interrompt le switch ici

    default: // Fonctionnement tel que else
        console.log("no comprendo !!");
        break;
}
```

### Opérateurs

- `=` : opérateur d'affectation
- `==` : opérateur de comparaison (valeur)
- `===` : opérateur de comparaison strict (valeur et type)
- `||` : opérateur de comparaison logique OU/OR
- `&&` : opérateur de comparaison logique ET/AND
- `!==` : opérateur de comparaison strictement différent de (valeur et type)
- `!=` : différent de (valeur uniquement)

## Boucles

### Boucle (for 'let')

```js
for (let i = 0; i < 5; i++) {
    console.log("Itération n°", i);
}

// for (initialisation; condition; incrémentation)
// initialisation -> exécutée une seule fois au début
// condition -> test effectuée avant chaque itération
// incrémentation -> exécutée à la fin de chaque tour
```

### Boucle for

> cette boucle ne fonctionne que sur les objets itérables (comme les tableaux, chaînes, etc.).

```js
const fruits = ["apple", "orange", "strawberry"];

for (const element of fruits) {
    console.log("Fruit : ", element);
}

// for (const itération of Array)
// element -> représente l'élément en cours d'itération
// Array -> un tableau/Array sur lequel boucler
```

## Boucle forEach

```js
const fruits = ["apple", "orange", "strawberry"];

fruits.forEach(fruit => {
    console.log("Fruit : ", fruit);
});

// tableau.forEach(element => { bloc de code });
// forEach est une méthode disponible sur les tableaux (version simple) / (version avancée -> méthode du prototype Array)
// Elle prend une fonction callback en paramètre
// element -> représente l'élément courant du tableau
```

### Boucle WHILE

#### Exemple de base

```js
let count = 0;

while (count < 10) {
    count++; // Incrémentation de la variable count
    console.log("salut", count);
}
```

#### Avec condition de sortie

```js
let count = 0;

while (true) {
    count++;
    console.log("count -> ", count);
    if (count === 10) break; // Sort de la boucle dès que count atteint 10
}
```

### Boucle DO WHILE

```js
let isValid = false;

do {
    console.log("je boucle");
} while (isValid); 
// La boucle s'exécute au moins une fois, même si la condition est fausse au départ grace au "do"
```

## Falsy & Truthy

> En JavaScript, toutes les valeurs peuvent être interprétées comme vraies (truthy) ou fausses (falsy) dans un contexte booléen (par exemple dans un if).

### Valeurs falsy

```js
if (false) {}
if (0) {}
if (-0) {}
if (0n) {}         // BigInt zéro
if ("") {}         // Chaîne vide
if (null) {}
if (undefined) {}
if (NaN) {}
```

> Toutes ces conditions ne seront pas exécutées, car la valeur est falsy.

### Valeurs truthy

> Toutes les autres valeurs sont truthy.

```js
true
1, -42, 3.14        // Nombres différents de 0
"hello"             // Chaîne non vide
[], {}              // Tableau ou objet vide
"false"             // Chaîne de caractères, même si elle contient le mot "false"
```
