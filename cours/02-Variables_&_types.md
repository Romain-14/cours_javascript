# Variables & Types

## Déclaration de variables

```js
let name = "Alice";
const age = 30;
var country = "France";
```

- **let** : permet de créer une variable modulable (réassignable).
- **const** : permet de créer une variable constante (non réassignable).
- **var** : ancienne façon de déclarer une variable (à éviter aujourd’hui).

> On ne peut pas réassigner une `const`.
> Le hoisting (hissage) concerne les variables déclarées avec var (et les fonctions) : la déclaration est remontée en haut du script, mais pas leur valeur.

Exemple :

```js
console.log(a); // undefined (hoisting de var)
var a = 5;

console.log(b); // ReferenceError
let b = 5;
```

## Types de données

```js
// Primitifs
let firstname = "Jean"; // string (chaîne de caractères)
let age       = 25;     // number (nombre)
let bigNumber = 90071992547409915n; // BigInt (grand nombre) 9007199254740991 est la valeur maximal pour un Number entier fiable, ajout du "n" pour créer un BigInt et conserver la précision du nombre
let isAdult   = true;   // boolean (vrai ou faux)
// Primitif Spéciaux
let car       = null;   // null (absence volontaire de valeur)
let house;              // undefined (non défini)
// Types Objets (références)
const fruits    = ["pomme", "banane"];     // tableau (type Object)
const person    = { nom: "Léo", age: 32 }; // object (type Objet)
// Les fonctions sont aussi des objets de type "function"
const maFonction = function () {}; // ici expression de fonction (voir cours plus tard sur les fonctions)
// Les constructeurs natifs également
const currentDate = new Date();
```

> il y a également le type `Symbol`, qu'on ne verra pas ici, plus complexe et moins utilisé.

## Vérification de type

```js
console.log(typeof firstname); // "string"
console.log(typeof age);       // "number"
console.log(typeof house);     // "undefined"
```

## Conversion de types

```js
let nombre   = "42";
let enNombre = Number(nombre); // Convertit en number
let enTexte  = String(42);     // Convertit en string
let enBool   = Boolean(1);     // true
```

### Subtilités de conversion de nombre

```js
// parseInt() → extrait un entier à partir du début de la chaîne
console.log(parseInt("42px"));   // 42
console.log(parseInt("3.14"));   // 3
console.log(parseInt("abc"));    // NaN (pas de chiffre au début)
console.log(parseInt("10", 2));  // 2 (interprète "10" en binaire si on précise la base)
console.log(parseInt("08"));     // 8 (OK en base 10)
console.log(parseInt("08", 8));  // 0 (car 8 est invalide en base 8)

// parseFloat() → extrait un nombre décimal
console.log(parseFloat("3.14"));    // 3.14
console.log(parseFloat("5.99abc")); // 5.99
console.log(parseFloat("abc"));     // NaN

// Number() → conversion stricte : toute la chaîne doit être un nombre
console.log(Number("42"));       // 42
console.log(Number("3.14"));     // 3.14
console.log(Number("42px"));     // NaN (ne peut pas convertir entièrement)
console.log(Number("   10  "));  // 10 (ignore les espaces autour)
```

> **parseInt**   → Lit les chiffres entiers au début de la chaîne, s’arrête dès que c’est invalide
> **parseFloat** → Lit les nombres à virgule, même s’il y a du texte après
> **Number**     → Essaie de convertir toute la chaîne : retourne `NaN` si un seul caractère est invalide

### Notes sur les bases numériques

Par défaut, JavaScript lit les nombres en base 10 (décimale).
> Cette précision de base (radix) **ne concerne que parseInt()**.  
> parseFloat() et Number() ne permettent pas de changer de base.

```js
console.log(42);        // base 10 → 42
console.log(0b101010);  // base 2  (binaire) → 42
console.log(0o52);      // base 8  (octale) → 42
console.log(0x2A);      // base 16 (hexadécimale) → 42
```

> La base est défini en second paramètre après la virgule.

Il peut y avoir de la confusion sur certaines valeurs :

```js
parseInt("10", 10); // 10 (base 10)
parseInt("10", 2);  // 2  (base 2 → "10" binaire)
```

```js
parseInt("010");    // ⚠️ Peut être mal interprété
```

Récap' :

- **parseInt**   → base modifiable     → Peut deviner base 16 (`0x`)
- **parseFloat** → base non modifiable → Toujours base 10
- **Number**     → base non modifiable → Lit les notations `0x`, `0b`, `0o`

## Bonnes pratiques

> Utilisation de l'anglais pour nommer ses variables, ses fonctions de façon explicite ...

```js
let age = 25; // ✅ Bien
let x   = 25; // ❌ Moins bien à part si on parle de la coordonnée "x" 😏 

// autre exemple :
let userName       = "Jean"; // ✅ Bien
let nomUtilisateur = "Jean"; // ❌ Moins lisible pour un code international
```

### Les différents types de *casse*

- **camelCase**  → userName    → ✅ Variables / Fonctions
- **PascalCase** → UserProfile → ✅ Noms de classes, composants React
- **snake_case** → user_name   → ❌ Possible mais à éviter en JS
- **kebab-case** → user-name   → ❌ Interdit en JS (non valide pour nom de variable) – utilisé dans les noms de fichiers ou en HTML/CSS

```js
let userAge  = 25; // camelCase  ✅
let user_age = 25; // snake_case ❌
let UserAge  = 25; // PascalCase ❌
let user-age = 25; // kebab-case ❌❌❌❌
```
