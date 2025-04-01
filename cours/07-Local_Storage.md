
# Gestion du Local Storage

## Sauvegarder des données dans le Local Storage

Pour sauvegarder des données dans le Local Storage, procédez comme suit :

### 1. Données à sauvegarder

Par exemple, une liste d'éléments :

```js
const items = ["item 1", "item 2", "item 3"];
```

### 2. Étapes de sauvegarde

#### a. Convertir les données en JSON (sérialisation)

Les données doivent être converties en chaîne de caractères au format JSON pour être stockées dans le Local Storage :

```js
const itemsJSON = JSON.stringify(items);
```

#### b. Enregistrer les données dans le Local Storage

Utilisez la méthode `setItem` pour sauvegarder les données sous une clé :

```js
localStorage.setItem("items", itemsJSON);
```

---

## Récupérer des données depuis le Local Storage

Pour récupérer et utiliser des données stockées :

### 1. Récupérer les données

Récupérez la chaîne JSON associée à la clé spécifiée avec `getItem` :

```js
const itemLocalStorage = localStorage.getItem("items");
```

### 2. Convertir les données en objet ou tableau (désérialisation)

Transformez la chaîne JSON en un objet ou un tableau js exploitable :

```js
const itemsParsed = JSON.parse(itemLocalStorage);
```

### 3. Utiliser les données récupérées

Vous pouvez maintenant manipuler les données comme un tableau normal :

```js
console.log(itemsParsed); // ["item 1", "item 2", "item 3"]
```

---

## Points importants

- **Vérifiez si une donnée existe** avant de la désérialiser, pour éviter des erreurs si elle est `null` :

  ```js
  if (itemLocalStorage) {
      const itemsParsed = JSON.parse(itemLocalStorage);
      console.log(itemsParsed);
  } else {
      console.log("Aucune donnée trouvée dans le Local Storage.");
  }
  ```

- **Limitation du Local Storage** :  
  Sa capacité est généralement de 5 à 10 Mo selon le navigateur. Utilisez-le pour des données légères.

### Résumé des actions

JSON.stringify(data) -> sérialise la data
JSON.parse(data)     -> Désérialise la data

localStorage.setItem("key", value) -> Créer une paire key/value en Localstorage
localStorage.getItem("key")        -> Récupérer la value "key"
localStorage.removeItem("key")     -> Supprimer la donnée avec la "key"
localStorage.clear() -> Supprime toutes données du local storage
