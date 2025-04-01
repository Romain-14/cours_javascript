# Boîtes de dialogue

Il en existe 3 qui appartiennent directement à l'objet global **window** :

- `alert` : Affiche un message sans possibilité d'interaction autre que sa fermeture.
- `confirm` : Affiche un message avec deux options : Ok (true) ou Annuler (false).
- `prompt`: Affiche un message et permet à l'utilisateur de saisir une réponse.

---

## alert

```js
window.alert("Clique ici pour mettre à jour ton navigateur !!!");
```

## confirm

```js
const response = window.confirm("tu vas bien ?");
if(response){  // ou if(confirm("tu vas bien ?"))
    console.log("Je suis content que t'ailles bien !");
} else {
    console.log("ça ira mieux plus tard !");
}
```

## prompt

```js
const alias = window.prompt("Quel est ton alias ?");
const age   = Number(window.prompt("Quel est ton age ?"));

console.log(`Tu t'appelles ${alias} et tu as ${age} ans !`);
```

---

On peut raccourcir les instructions dont on utilise une propriété sur l'objet window en se passant de l'écriture de ce dernier.

```js
window.alert("Clique ici pour mettre à jour ton navigateur !!!");
// deviendrait
alert("Clique ici pour mettre à jour ton navigateur !!!");
```

### Remarques

> Ces boîtes de dialogue bloquent l'exécution du code tant qu'elles ne sont pas fermées.
Leur usage est limité dans des applications modernes.
> Il conviendra de faire ce qu'on appelle des `modal`, créer un bloc html qui va recevoir/permettre l'interaction avec l'utilisateur.
