# 🚀 Module 2 : Les Bases de la Programmation en JavaScript

Ce module couvre les fondations du langage : comment déclarer des variables, les différents types de données, utiliser les opérateurs et les structures de contrôle (conditions et boucles). Même si vous n’avez jamais programmé, ces concepts de base seront expliqués pas à pas. 🎉

## 2.1. Variables et Types de Données 💡

Une variable est un conteneur qui porte un nom et stocke une valeur (nombre, texte, etc.). En JavaScript moderne, on déclare une variable avec les mots-clés **let** ou **const** (et dans certains cas **var**, plus ancien) :

- **let** sert à déclarer une variable dont la valeur peut changer.  
- **const** sert à déclarer une constante dont la valeur ne sera pas réassignée (constante en écriture, pas immuable pour autant si c’est un objet, mais on y reviendra).  
- **var** est l’ancienne façon de déclarer, qu’on évite généralement en raison de ses particularités de portée (scope) et d’un mécanisme appelé hoisting.  

> **Astuce** : retenez pour l’instant : utilisez `let` pour les variables ordinaires et `const` pour les constantes. 😉

### Exemple :

```js
let age = 25;         // une variable âge qui peut changer
const PI = 3.14159;   // une constante, conventionnellement en majuscules
var nom = "Moustapha Ibrahima Ba";    // ancienne syntaxe var, à éviter
```

JavaScript est faiblement typé : une variable peut contenir différents types de valeurs au cours du programme, mais chaque valeur a un type. Les principaux types primitifs sont :

1. **Number** (nombre)  
2. **String** (chaîne de caractères)  
3. **Boolean** (booléen vrai/faux)  
4. **Undefined** (valeur non définie)  
5. **Null** (absence de valeur)  
6. **BigInt** (grands entiers)  
7. **Symbol** (valeurs uniques)  

Les objets et tableaux sont des types complexes (voir Module 4).  

Exemples de valeurs : 
- **42** est un `Number`, 
- **"Bonjour"** est un `String`, 
- **true** est un `Boolean`, 
- **undefined** est le `type d’une variable déclarée sans valeur.` 

Vous pouvez vérifier le type d’une variable avec l’opérateur `typeof`

```js
let x;
console.log(typeof x);      // "undefined"
x = "Hello";
console.log(typeof x);      // "string"
x = 7;
console.log(typeof x);      // "number"
x = true;
console.log(typeof x);      // "boolean"
```

> **ATTENTION** aux problèmes d’arithmétique en virgule flottante classiques : 
>
> par exemple **0.1 + 0.2** ne donne pas exactement **0.3** pour des raisons de **représentation binaire des nombres**.  
> ```js
> console.log(0.1 + 0.2); // ≠ 0.3 exactement
> ```  

## 2.2. Opérateurs de base 🔧

JavaScript fournit les **opérateurs arithmétiques** usuels :
- **Arithmétiques** : `+`, `-`, `*`, `/` (add, sub, mul, div).  
- **Exponentiation** : `**` (ex : `2 ** 3 === 8`).  
- **Modulo** : `%` (reste de division, ex : `7 % 3 === 1`).  
- **Incrément / décrément** : `++`, `--`. 

Les **opérateurs d’affectation** permettent de modifier une variable 
- `=` affecte une valeur (`x = 5`)
- et on a des **raccourcis**: `+=`, `-=`, `*=`, `/=`, etc. Par exemple **`x += 3` équivaut à `x = x + 3`**.

Pour les **chaînes de caractères (String)**, l’opérateur `+` sert à les **concaténer** (assembler) : `"Hello " + "World" === "Hello World"`.

## 2.3. Comparaisons et Logique en JavaScript 🤔

En programmation, on a souvent besoin de comparer des valeurs :

- **Égalité faible** `==`  
  - Convertit les types au besoin  
  - Exemple : `0 == "0"` est `true` (la chaîne `"0"` est convertie en nombre `0`)
- **Égalité stricte** `===`  
  - Exige la même valeur **et** le même type  
  - Exemple : `0 === "0"` est `false` (types différents)  
- **Différence stricte** `!==` vs différence faible `!=`  

> ✅ **Bonne pratique** :  
> Utilisez toujours `===` et `!==` pour éviter les surprises des conversions implicites.
>
>```js
>console.log(0 == "0");   // true
>console.log(0 === "0");  // false
>```

### 🔢 Opérateurs de comparaison usuels
Les **opérateurs de comparaison** usuels sont :
- `<`  (moins que)  
- `>`  (plus que)  
- `<=` (inférieur ou égal)  
- `>=` (supérieur ou égal)  

Ils fonctionnent pour les nombres et pour les chaînes de caractères (ordre lexicographique).

---

### 🔗 Opérateurs logiques

- `&&` (ET logique)  
- `||` (OU logique)  
- `!`  (NON logique)  

Ces opérateurs permettent de combiner plusieurs conditions.

#### Exemple :

```js
let age = 20;
let citoyen = true;
console.log(age >= 18 && citoyen === true); // true

let a = 5, b = "5";
console.log(a == b);   // true  (comparaison faible, 5 == "5")
console.log(a === b);  // false (comparaison stricte, number vs string)
console.log(a !== b);  // true  (5 n'est pas du même type ou valeur que "5")
console.log(a < 10);   // true
console.log(a > 10 || a == 5); // true (5 > 10 est faux, mais 5 == 5 est vrai, donc OU donne vrai)
```

> 🤓 **Astuce** :  
> Utilisez des parenthèses pour clarifier les expressions complexes, même si elles ne sont pas strictement nécessaires.

> ### ✅ Bonnes pratiques
> 
> - **Évitez l’égalité faible**  
>   Préférez toujours l’égalité stricte `===` (et `!==`) pour éviter les conversions implicites surprenantes.  
>   ```js
>   // Mauvaise pratique (égalité faible)
>   0 == "0"   // true
> 
>   // Bonne pratique (égalité stricte)
>   0 === "0"  // false
>   ```
> 
> **Prudence avec les valeurs *falsy* et *truthy***  
>   En JavaScript, les valeurs suivantes sont *falsy* (considérées comme fausses) :  
>   ```
>   0, "" (chaîne vide), null, undefined, NaN
>   ```  
>   Toute autre valeur non nulle ou non vide est *truthy*.  
>   ```js
>   let variable = 0;
>   if (variable) {
>     // Ne passera pas ici, 0 est falsy
>   }
> 
>   let str = "";
>   if (str) {
>     // Ne passera pas ici, chaîne vide est falsy
>   }
> 
>   let msg = "Bonjour";
>   if (msg) {
>     // Passera ici, "Bonjour" est truthy
>   }
>  ```
>
> - **Utilisez des parenthèses pour la lisibilité**  
>  Même si l’ordre des opérateurs est défini, les parenthèses clarifient les expressions logiques complexes.  
>   ```js
>   if ((x > 0 && x < 10) || conditionAnnexe) {
>     // …
>   }
>   ```

🎉 Voilà, vos règles de comparaison et de logique JavaScript au top de la clarté ! 🚀  

## 2.4. Structures de contrôle : conditions et boucles 🔄

### Conditions `if/else`

La condition `if/else` permet d’exécuter du code seulement si une certaine condition est vraie. La syntaxe est :
```js
if (condition) {
  // bloc si vrai
} else if (autreCondition) {
  // autre bloc
} else {
  // sinon
}
```
Seul le `if(...) {}` de base est obligatoire. Les `else if` et `else` sont optionnels selon les besoins. Par exemple :

```js
let heure = 14;
if (heure < 12) {
  console.log("Bonjour");
} else if (heure < 18) {
  console.log("Bon après-midi");
} else {
  console.log("Bonsoir");
}
```
Ici, le programme affiche un message différent selon l’heure. 

### `switch`

Une autre structure de condition est `switch`, utile quand on compare la même variable à différentes valeurs :

```js
let couleur = "vert";
switch (couleur) {
  case "rouge":
    console.log("STOP");
    break;
  case "orange":
    console.log("ATTENTION");
    break;
  case "vert":
    console.log("ALLEZ-Y");
    break;
  default:
    console.log("Couleur inconnue");
}
```
Le `switch` compare `couleur` aux valeurs indiquées dans les `case`. Le mot-clé `break` empêche d’enchaîner sur les cas suivants une fois un cas trouvé (sinon, l’exécution continue dans le prochain case ce qui est rarement le comportement désiré à part cas spécifiques).

### Boucles

Les **boucles** permettent de répéter un bloc d’instructions tant que certaines conditions sont remplies. JavaScript offre plusieurs types de boucles :

1. **`while`** : répète tant qu’une condition est vraie. Exemple :

   ```js
   let i = 0;
   while (i < 3) {
     console.log("i vaut " + i);
     i++;
   }
   // Affiche : i vaut 0, puis 1, puis 2
   ```

2. **`for`** : boucle avec compteur, très utilisée. Syntaxe : `for(initialisation; condition; incrément) { … }`. Exemple :

   ```js
   for (let j = 0; j < 3; j++) {
     console.log(`j = ${j}`);
   }
   // Affiche j = 0, j = 1, j = 2
   ```
   Ici on initialise `j=0`, la boucle tourne tant que `j < 3`, et on exécute `j++` à chaque fin d’itération.

3. **`do ... while`** : similaire à while, sauf que la condition est évaluée **après** la première itération, ce qui garantit qu’on exécute le bloc au moins une fois. Exemple :

   ```js
   let x = 5;
   do {
     console.log("x vaut " + x);
     x--;
   } while (x > 0);
   ```
4. **Avancées** : JavaScript moderne fournit aussi `for...of` pour itérer sur les éléments d’une collection (tableau, etc.) et `for...in` pour itérer sur les propriétés d’un objet. Nous les verrons quand nous aborderons les tableaux et objets. 
   - `for...of` pour tableaux  
   - `for...in` pour objets  
   
   > **Astuce** : Dans les boucles `for`, vous pouvez utiliser le mot-clé `break` pour sortir prématurément de la boucle, et `continue` pour passer directement à l’itération suivante en sautant le reste du bloc courant.
   >
   > Par exemple, pour ignorer certaines valeurs :
   > ``` javascript
   > for(let n=1; n<=5; n++){
   >  if(n === 3) continue;  // sauter l'affichage pour n = 3
   >  console.log(n);
   >  }
   >  // Ce code affichera 1, 2, 4, 5 (3 est sauté)
    > ```
   > À utiliser avec **parcimonie**, car l’abus de `break`/`continue` peut nuire à la lisibilité. Parfois, re-structurer la condition de la boucle évite d’en avoir besoin.


## 🎯 Exercices pratiques

Pour bien maîtriser ces bases, rien de tel que de pratiquer. Essayez de résoudre ces petits exercices en JavaScript :

1. **Calcul de salaire horaire**  
   Écrivez un script qui déclare une variable `salaireAnnuel` et une variable `heuresParSemaine`. Calculez le salaire horaire en supposant 52 semaines par an, et affichez le résultat dans la console. (Indice : salaire horaire = salaireAnnuel / (heuresParSemaine * 52)).

2. **Parité**  
   Demandez (mentalement) un nombre et stockez-le dans une variable `nombre`. Utilisez une condition pour afficher dans la console "pair" ou "impair" selon la valeur de `nombre`. (Rappel : le test `nombre % 2 === 0` indique la parité).

3. **FizzBuzz basique**  
   Pour les nombres de 1 à 20, affichez "Fizz" s’ils sont multiples de 3, "Buzz" s’ils sont multiples de 5, "FizzBuzz" s’ils sont multiples des deux, ou simplement le nombre sinon. (C’est un classique pour pratiquer les conditions).

4. **Compter les voyelles**  
   Stockez une chaîne de caractères dans une variable (par ex. une phrase) et, à l’aide d’une boucle, comptez le nombre de voyelles (a, e, i, o, u) dans la chaîne. Affichez le résultat.

5. **Deviner un nombre** (exercice libre, nécessitant HTML/interaction donc vous pouvez le garder en tête pour plus tard) – Imaginer un programme qui génère un nombre aléatoire et demande à l’utilisateur de le deviner via une interface, en lui indiquant "plus haut" ou "plus bas". Comment utiliseriez-vous les conditions et boucles pour cela ? 

> Ces exercices peuvent être réalisés dans la console du navigateur ou en créant un petit fichier HTML avec un `<script>` contenant votre code, puis en observant le résultat via `console.log` ou en manipulant le DOM (si vous connaissez déjà un peu, sinon ne vous inquiétez pas, on y vient bientôt). 🏆  
