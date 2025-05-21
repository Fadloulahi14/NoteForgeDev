# Module 4 : Structures de Données – Tableaux et Objets en JavaScript

Maintenant que nous savons utiliser des variables et des fonctions, intéressons-nous aux **structures de données** les plus utilisées en JavaScript : les **tableaux** (arrays) et les **objets**. Ces deux types de structures permettent de regrouper des valeurs, mais de manière différente : un tableau pour une liste ordonnée indexée, un objet pour une collection de propriétés nommées.

## 4.1. Les tableaux (Arrays)

Un **tableau** est une liste ordonnée de valeurs, indexées numériquement à partir de 0. En JavaScript, les tableaux sont très flexibles : on peut changer leur taille, ils peuvent contenir des éléments de différents types (bien que ce soit rarement une bonne idée en pratique de mélanger les types).

### Création de tableau :

On peut créer un tableau avec des littéraux en utilisant des crochets `[]`.
**Exemple** :

```js
let fruits = ["Pomme", "Banane", "Orange"];
console.log(fruits[0]); // "Pomme" (les indices commencent à 0)
console.log(fruits[2]); // "Orange"
```

Ici `fruits` est un tableau de 3 éléments. La propriété `fruits.length` donne la taille (3 dans cet exemple).

Les tableaux peuvent être modifiés : on peut assigner à un index pour changer une valeur, ou utiliser diverses **méthodes** pour manipuler le tableau :

- `push(element)` ajoute un élément à la fin du tableau.
- `pop()` enlève le dernier élément.
- `unshift(element)` ajoute un élément au début du tableau (décale les autres).
- `shift()` enlève le premier élément.

Exemple :

```javascript
fruits.push("Mangue"); // Ajoute "Mangue" à la fin
console.log(fruits.length); // 4
let dernier = fruits.pop(); // retire "Mangue"
let premier = fruits.shift(); // retire "Pomme"
fruits.unshift("Fraise"); // ajoute "Fraise" au début
console.log(fruits); // ["Fraise", "Banane", "Orange"]
```

D’autres méthodes utiles :

- `indexOf(valeur)` pour trouver l’index d’une valeur,
- `includes(valeur)` pour tester la présence,
- `slice(debut, fin)` pour extraire une portion de tableau,
- `splice` pour enlever/insérer en plein milieu
- etc.

Pour parcourir un tableau, utilisez la boucle `for` classique avec index, ou plus simplement la boucle `for...of` :

```javascript
for (const fruit of fruits) {
  console.log(fruit);
}
```

Cela affichera chaque fruit de la liste sans qu’on se soucie des indices.

### Tableaux et méthodes modernes :

Le JavaScript moderne propose des méthodes de haut niveau très pratiques pour travailler avec les tableaux de manière déclarative :

- `forEach` : pour exécuter une fonction sur chaque élément.
- `map` : pour transformer chaque élément et obtenir un nouveau tableau.
- `filter` : pour filtrer les éléments selon un critère.
- `find / findIndex` : pour trouver un élément (ou son index) satisfaisant une condition.
- `reduce` : pour réduire tout le tableau à une seule valeur selon une fonction d’accumulation (somme, produit, agrégation…).

Par exemple, supposons un tableau de nombres et on veut obtenir leur carré :

```javascript
let nums = [1, 2, 3, 4];
let carres = nums.map((n) => n * n);
console.log(carres); // [1, 4, 9, 16]
```

Ou filtrer les nombres pairs :

```javascript
let pairs = nums.filter((n) => n % 2 === 0);
console.log(pairs); // [2, 4]
```

Ces méthodes prennent en argument une fonction (souvent écrite en arrow function pour être concise). Elles évitent d’écrire des boucles manuelles et rendent le code plus lisible de façon fonctionnelle.

**Remarque performance** : Les tableaux JS ne sont pas des tableaux statiques comme en C/Java ; ce sont en réalité des objets spéciaux. Ils sont très optimisés en général, mais certaines opérations (comme insérer en début de grand tableau avec `unshift`) sont moins performantes que d’autres (ajouter en fin avec `push` est très efficace). Pour un usage normal, ne vous souciez pas trop de ces détails, mais sachez que la performance peut varier selon l’opération.

## 4.2. Les objets (Objects)

Un **objet** en JavaScript est une collection de **paires clé-valeur** (on parle aussi de propriétés). C’est un peu comme un “dictionnaire” ou une “table de hachage” : à chaque nom de propriété est associée une valeur. Presque tout en JavaScript est objet (les tableaux eux-mêmes sont des objets particuliers, les fonctions sont des objets appelables, etc.). Mais ici on parle des objets JSON classiques.

### Création d’objets

On peut utiliser des littéraux avec `{}`. Exemple :

```javascript
let personne = {
  nom: "Moustapha",
  age: 30,
  ville: "Paris",
};
```

Cet objet `personne` a trois propriétés. Pour accéder à une propriété, deux notations possibles :

- **La notation point** : `personne.nom` renvoie `"Moustapha"`.
- **La notation avec crochets** : `personne["age"]` renvoie `30`. Celle-ci est utile si le nom de propriété est dans une variable ou contient des caractères spéciaux.

On peut ajouter ou modifier des propriétés :

```javascript
personne.profession = "Dev";
personne["age"] = 29;
```

Pour supprimer une propriété, on utilise l’opérateur `delete : delete personne.ville;`.

Si on accède à une propriété qui n’existe pas, on obtient `undefined` (et non une erreur).

### Itération sur les propriétés

On peut utiliser la boucle `for...in` pour parcourir les clés d’un objet :

```javascript
for (let cle in personne) {
  console.log(cle + " : " + personne[cle]);
}
// Affiche par ex:
// nom : Moustapha
// age : 31
// profession : Dev
```

Note : l’ordre d’énumération n’est pas garanti pour les objets non structurés, mais en pratique la plupart des moteurs énumèrent dans l’ordre d’insertion (pour les clés non numériques).

### Objets imbriqués et tableaux d’objets :

Les valeurs dans un objet peuvent être n’importe quel type, y compris un autre objet ou un tableau. Par exemple :

```javascript
let entreprise = {
  nom: "SuperCorp",
  employes: [
    { nom: "Moustapha", poste: "CEO" },
    { nom: "Bob", poste: "Développeur" },
  ],
};
console.log(entreprise.employes[1].poste); // "Développeur"
```

Ici `entreprise.employes` est un tableau d’objets, on peut enchaîner l’accès : le poste du 2ème employé (index 1) est "Développeur".

C’est courant de manipuler des **données au format JSON** qui sont exactement ces structures objets/tableaux combinées. Savoir naviguer dans ces structures est important. Vous pouvez utiliser `console.table(obj)` pour afficher un objet ou un tableau d’objets en table dans la console, ce qui aide à visualiser.

### Copie et référence

Attention, en JavaScript, les objets (et tableaux) sont manipulés par **référence**. Si vous faites `let perso2 = personne;`, vous ne copiez pas l’objet, vous créez une nouvelle référence pointant vers le même objet.

Modifier `perso2.age` modifiera aussi `personne.age` car c’est le même objet en mémoire.

Pour copier un objet superficiellement, on peut utiliser

- `Object.assign({}, personne)`
- ou l’opérateur de spread : let `persoCopy = {...personne};`.
- Pour les tableaux, `arrCopy = [...arr];`.

Notez que ce sont des copies **superficielles** (shallow copy) : si l’objet a des sous-objets, ils resteront partagés entre copies (il faudrait une copie profonde pour les dupliquer aussi).

## 4.3. Comparaison : Objets vs Tableaux vs Map

Il est important de choisir la bonne structure selon le besoin :

- On utilise un **tableau** quand on a une collection ordonnée d’éléments, généralement du même type logique, par exemple une liste de produits, une liste de noms, etc., et qu’on accède principalement par indice ou qu’on itère sur l’ensemble.
- On utilise un **objet** pour représenter une entité structurée avec des propriétés nommées, par exemple un utilisateur avec nom, email, âge, etc., ou pour représenter une collection associative (clés/valeurs) quand les clés sont des chaînes peu nombreuses.
- Pour des **données associatives dynamiques** où les clés ne sont pas connues à l’avance ou ne sont pas forcément des chaînes, JavaScript propose aussi la structure **Map** (ES6). Une Map est similaire à un objet mais avec des méthodes dédiées (`map.set(cle, valeur)`, `map.get(cle)`) et accepte n’importe quel type de clé (y compris objets). Pour un usage courant, un objet littéral suffit souvent, mais sachez que Map existe et peut être plus appropriée si vous avez beaucoup de paires clé-valeur à gérer et que la clé n’est pas forcément un string.

## 4.4. Exemples concrets et manipulation de JSON

**Exemple 1**: Vous récupérez des données d’un utilisateur en JSON (on verra comment avec fetch plus tard). Par exemple :

```javascript
let user = {
"id": 101,
"name": "John Doe",
"address": {
"city": "Paris",
"zip": 75001
},
"roles": ["admin", "editor"]
};
```

Pour accéder aux informations :

- `user.name` est "John Doe",
- `user.address.city` est "Paris",
- `user.roles[0]` est "admin".
  Si vous voulez lister tous les rôles de l’utilisateur :

```js
for (let role of user.roles) {
console.log(role);
}
```

**Exemple 2** : Vous souhaitez stocker plusieurs utilisateurs :

```js
let users = [
{ id: 1, name: "Moustapha" },
{ id: 2, name: "Bob" },
{ id: 3, name: "Charlie" }
];
```

Ici `users` est un tableau de trois objets utilisateur. Pour trouver l’utilisateur avec id 2 :

```js
let user2 = users.find(u => u.id === 2);
console.log(user2.name); // "Bob"
```

On utilise la méthode `find` avec une fonction fléchée conditionnelle.

## Bonnes pratiques :

- Lorsque vos données deviennent complexes (beaucoup d’objets imbriqués), essayez de structurer de manière logique et cohérente. Par exemple, évitez des tableaux trop hétérogènes ou des objets aux propriétés non uniformes entre eux.
- Exploitez les méthodes natives (**map**, **filter**, **etc**.) au lieu de tout coder à la main : c’est généralement optimisé et plus lisible.
- Faites attention aux **mutations** : beaucoup de méthodes de tableau (push, pop, etc.) modifient le tableau original. Parfois on préfère utiliser des méthodes non mutables (par ex, `concat` pour concaténer sans modifier, ou utiliser **... spread operator**) surtout dans un contexte où on veut éviter les effets de bord (pattern de programmation plus fonctionnelle).
- Apprenez à utiliser la console pour examiner vos objets. Par exemple `console.log(JSON.stringify(obj))` peut aider à imprimer un objet entier en JSON (s’il n’a pas de références circulaires), ou utilisez les devtools pour inspecter l’objet.

## 4.5. Exercices pratiques sur tableaux/objets

1. **Manipulation d’un tableau de nombres** : Écrivez un script qui crée un tableau contenant par exemple `[10, 5, 8, 12, 3]`. Calculez la **somme** de ces nombres (en parcourant le tableau), puis la **moyenne**. Affichez-les. Ensuite, trouvez la **valeur maximale** du tableau (sans utiliser de fonction prête à l’emploi type Math.max, faites-le à la main dans une boucle).
2. **Recherche dans un tableau** : Reprenez le tableau précédent. Demandez-vous comment vérifier la présence d’une valeur, par exemple 8, dans ce tableau. Utilisez soit `includes`, soit parcourez jusqu’à trouver l’élément (et notez l’index trouvé via `indexOf` ou en le stockant).
3. **Objets simples** : Créez un objet `livre` avec des propriétés `titre`, `auteur`, `annee`. Remplissez-le avec un livre de votre choix. Puis, ajoutez dynamiquement une propriété `genre`. Enfin, affichez un petit texte du style : "*Le livre {titre}, écrit par {auteur}, est un {genre} publié en {annee}."*.
4. **Tableau d’objets**: Créez un tableau `bibliotheque` qui contient plusieurs objets livres (2 ou 3). Écrivez une fonction `trouverLivreParAuteur(auteur)` qui renvoie le premier livre de la bibliothèque écrit par l’auteur donné (utilisez `find`). Testez-la.
5. **Transformation de données** : À partir du tableau `bibliotheque`, utilisez `map` pour créer un nouveau tableau contenant uniquement les titres des livres. Puis utilisez `filter` pour ne garder que les livres publiés après l’an 2010 (supposons que l’un de vos livres a une année correspondante).

En pratiquant ces opérations, vous vous familiariserez avec la manipulation des données en JavaScript – une compétence cruciale pour le développement d’applications web qui souvent reçoivent, transforment et affichent des données.

Dans le prochain module, nous allons plonger dans le **DOM et les événements**, ce qui nous permettra d’appliquer ces bases pour réellement **interagir avec la page web**.
