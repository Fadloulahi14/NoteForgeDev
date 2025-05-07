# Module 3 : Les Fonctions en JavaScript et la Portée des Variables

Dans ce module, nous allons introduire les fonctions, un concept fondamental en programmation permettant de regrouper des instructions, de les réutiliser et de structurer votre code de manière modulaire. Nous aborderons également la notion de portée (scope) des variables, c’est-à-dire les règles qui déterminent où une variable est accessible.

## 3.1. Définir et utiliser des fonctions

Une fonction est comme une "boîte" de code nommée, qui peut prendre des paramètres en entrée et renvoyer une valeur en sortie. Cela permet de réutiliser ce code facilement. En JavaScript, il existe plusieurs façons de définir une fonction :

### **Fonction déclarée (function declaration)** :

```javascript
function saluer(nom) {
  console.log("Bonjour " + nom + "!");

  saluer("Fatou"); // Affiche "Bonjour Fatou!"
}
```
✨ Ici, nous **déclarons une fonction** nommée `saluer` qui prend un **paramètre `nom`**.  
✅ En appelant `saluer("Fatou")`, la console affichera **"Bonjour Fatou!"**.

> 💡 **Remarque importante** : <br>
>
>Les fonctions déclarées de cette manière sont **hoistées** 👉 cela signifie que vous pouvez les **appeler même avant leur définition** dans le code. <br>
>
> ➡️ JavaScript **charge leurs définitions dès l’interprétation initiale**, ce qui les rend accessibles partout dans leur portée.

### **Fonction exprimée (function expression)** : 

📝 On peut aussi **assigner une fonction anonyme à une variable**.  
Dans ce cas, la fonction n’a pas de nom propre, mais est stockée dans une variable (ici une constante) :

```js
const saluer2 = function(nom) {
  console.log(`Salut ${nom} !`);
};

saluer2("Paul");  // Appel de la fonction via la variable
```
✨ Ici, `saluer2` est une **constante** qui **référence une fonction anonyme**.

>💡 **Différence principale** : <br>
>
>- Les **function expressions ne sont pas hoistées**. <br>
>
>- Cela signifie que **vous devez définir la fonction avant de l’appeler**. <br>
> - ⚠️ Tenter de l’appeler avant sa définition générera une erreur.

### **Fonction fléchée (arrow function)**

📝 La **fonction fléchée** est une **syntaxe plus concise** introduite par **ES6**.  
Elle permet de déclarer des fonctions de manière plus rapide :

```js
const saluer3 = (nom) => {
  console.log(`Hello ${nom} !`);
};
```

- ✨ Ici, `saluer3` est une `constante` qui stocke une `arrow function`.

- 💡 Les `arrow functions` ont des `particularités` (notamment concernant `this`, nous y reviendrons plus tard).

- Elles sont **souvent utilisées pour les callbacks ou les fonctions courtes**.

Si l’arrow function se limite à **une seule expression retournée**, on peut encore simplifier la syntaxe :

``` javascript
const carre = x => x * x;
```
✨ Ici, `carre` est une fonction qui **renvoie `x²`**.

 ✅ Quelle que soit la méthode, **on appelle une fonction en écrivant son nom suivi de parenthèses** et des arguments éventuels.

📝 On peut définir une fonction **sans paramètre** (avec des parenthèses vides) ou **choisir de renvoyer une valeur** grâce au mot-clé `return` :

 ```js
 function addition(a, b) {
  return a + b;
 }

 let resultat = addition(2, 3);
 console.log(resultat); // 5
 ```

 - ✨ Ici, la fonction `addition` **prend deux nombres et renvoie leur somme**.

 - 💡 **Le `return` termine la fonction** :  
 - ✅ **toute instruction après un `return` ne sera pas exécutée.**

 - ⚠️ **Sans `return` explicite, une fonction renvoie `undefined` par défaut.**

### Portée locale des fonctions

📝 Les **variables déclarées à l’intérieur d’une fonction** (avec `let` ou `const`) sont **locales à cette fonction** :  
✅ elles **n’existent qu’à l’intérieur** et ne sont **pas accessibles de l’extérieur**.

Exemple :

```js
function demo() {
  let x = 42;
}
console.log(x); // Erreur : x is not defined (car x est local à la fonction demo)
```
👉 En revanche, une fonction a **accès aux variables définies dans son contexte englobant (extérieur).**  
C’est ce qu’on appelle la **portée lexicale**.

```javascript
let message = "Coucou";

function direMessage() {
  console.log(message);
}

direMessage(); // affichera "Coucou"
```

- ✨ Ici, `message` est une **variable globale** (déclarée en dehors de toute fonction).

- 👉 La fonction `direMessage` **peut voir la variable `message`** car **`message` est globale dans ce contexte.**

- ⚠️ **Les variables globales sont accessibles partout**, ce qui peut être pratique mais **peut poser des problèmes de chevauchement de noms ou d’effets indésirables à grande échelle.**

- 💡 **Il est recommandé de limiter l’usage des variables globales pour éviter ces problèmes.**

> ## 💡 Bonnes pratiques :
> 
> ✅ **Limitez les variables globales.**  
> Dans la mesure du possible, **utilisez des fonctions pour encapsuler votre logique** et ne laissez en global **que ce qui est intentionnellement partagé**.  
> Trop de variables globales créent un code **moins maintenable**.
> 
> ✅ **Une fonction = une action.**  
> Donnez aux fonctions **une responsabilité claire et un nom explicite**.  
> 👉 Si vous constatez qu’une fonction fait **deux choses sans rapport**, envisagez de **la scinder**.
> 
> ✅ **N’hésitez pas à utiliser des fonctions pour éviter la répétition.**  
> Si vous vous surprenez à **copier-coller du code**, mettez-le **dans une fonction et appelez-la à la place**.
> 
> ✅ **Paramètres par défaut :**  
> Vous pouvez **assigner des valeurs par défaut à vos paramètres**  
> *(exemple : `function f(x = 1) { ... }`)*, ce qui **évite des erreurs si la fonction est appelée sans ce paramètre ou avec `undefined`**.

## 3.2. Portée (scope) et variables locales/globales

👉 Comme introduit, **la portée d’une variable est la zone du code où elle est accessible**.

En **JavaScript (ES6)**, on a une **portée de bloc** avec `let` et `const` :  
✅ **toute paire d’accolades `{ ... }` délimite une portée pour ces variables**.

```javascript
if (true) {
  let temp = 123;
  console.log(temp); // 123, accessible à l’intérieur du bloc
}
console.log(temp); // Erreur, temp n'existe plus en dehors des accolades
```

👉 Avec `var` (ancienne manière), **la portée est fonctionnelle (ou globale si déclarée hors fonction) et non par bloc**.

✅ Cela signifie qu’un `var` déclaré **dans un bloc `if` sera quand même accessible en dehors du `if`**, ce qui est **contre-intuitif**.

💡 **C’est l’une des raisons principales pour lesquelles on évite d’utiliser `var`.**

### Hoisting (élévation)

📝 **JavaScript possède un mécanisme appelé "hoisting" (élévation)**, où **les déclarations de fonctions et de variables `var` sont traitées en amont**.

👉 Concrètement :

✅ Une **fonction déclarée est utilisable même si elle apparaît plus bas dans le code source**.  
✅ De même, une **variable `var` est techniquement créée en haut de sa portée**, mais **initialisée à `undefined` jusqu’à l’affectation réelle**.

⚠️ Ce comportement peut **surprendre** et **entraîner des erreurs si mal compris**.

Exemple :

```js
console.log(a); // undefined (la variable existe mais pas encore assignée)
var a = 5;

saluer("Bob"); // fonctionne, même si la fonction est déclarée plus bas

function saluer(nom) {
  console.log("Bonjour " + nom);
}
```
- 👉 Avec `let` et `const`, **le hoisting existe aussi**, mais d’une manière différente :

- ⚠️ **L’accès à la variable avant sa déclaration entraîne une erreur** → c’est ce qu’on appelle la **Temporal Dead Zone (TDZ)**.

- ✅ **En pratique, il ne faut pas compter sur le hoisting.**  
💡 **Déclarez toujours vos variables avant de les utiliser** pour obtenir un **code clair, lisible et sans surprise.**

## 3.3. Différents types de fonctions et comparaisons méthodologiques

### Fonctions classiques vs fléchées

📝 Les **arrow functions** `() => { }` ont une **différence majeure** par rapport aux fonctions classiques :

✅ **Elles ne possèdent pas leur propre `this`** (et **pas d’objet `arguments` implicite**).

👉 Cela signifie que **le `this` à l’intérieur d’une fonction fléchée est celui de son contexte englobant**.

En revanche, une **fonction classique** définie avec `function` aura **son propre `this` selon la façon dont elle est appelée**  
*(nous approfondirons `this` dans le module POO).*

---

> 🎯 **En résumé** :
>
>✅ Pour **des petites fonctions utilitaires ou des callbacks** où l’on **ne veut pas manipuler `this`**, **les arrow functions sont concises et pratiques**.
>
>✅ Pour **des méthodes d’objets** ou **quand on a besoin de `this`**, **les fonctions classiques sont mieux adaptées**.

### Paramètres vs variables globales

📝 Comparons **deux façons d’utiliser des valeurs dans une fonction** :

✅ Soit on utilise **une variable globale**  
✅ Soit on **passe la valeur en paramètre**

Exemple :

```javascript
// Méthode 1 : variable globale
let tauxTVA = 0.20;
function calculPrixTTC(prixHT) {
  return prixHT * (1 + tauxTVA);
}

// Méthode 2 : passer en paramètre
function calculPrixTTCv2(prixHT, taux) {
  return prixHT * (1 + taux);
}
```

✅ **La première méthode** a l’avantage de la **simplicité** (moins de paramètres à fournir),  
mais elle **rend la fonction dépendante d’une variable externe `tauxTVA`**.

👉 **La seconde méthode** rend la fonction **complètement générique et autonome**,  
car elle **ne dépend d’aucune variable globale** et **prend tout en paramètre**.

> ✅ **Bonne pratique** :  
>
>👉 **Privilégiez le passage de paramètres pour rendre les fonctions indépendantes**,  
sauf si la valeur en question est **vraiment globale et constante** dans votre application.
>
>💡 Ainsi, `calculPrixTTCv2` pourra être **réutilisée avec n’importe quel taux**,  
par exemple :
>
> ```js
> calculPrixTTCv2(100, 0.055); // calcul avec un taux réduit
>```

## 3.4. Closures (fermetures) – Notion avancée

📝 Un concept avancé lié aux **fonctions** et à la **portée** est celui de **closure** (*fermeture* en français).

👉 Une **fermeture** se produit lorsqu’une fonction **“embarque” avec elle des références vers son environnement lexical**,  
c’est-à-dire **des variables qui étaient en scope au moment de sa création** ([source : MDN](https://developer.mozilla.org)).

✅ Dit simplement, **une fonction interne peut continuer à accéder aux variables de la fonction englobante, même après que cette dernière ait terminé son exécution**.

Exemple classique :

```javascript
function creerCompteur() {
  let count = 0;
  return function() {
    count++;
    console.log(`Compteur : ${count}`);
  };
}

const compteur1 = creerCompteur();
compteur1(); // Compteur : 1
compteur1(); // Compteur : 2

const compteur2 = creerCompteur();
compteur2(); // Compteur : 1  (un nouveau compteur indépendant)
``` 

- ✨ Ici, `creerCompteur` est une fonction qui **crée une variable locale `count`** et **renvoie une fonction anonyme**.

- ✅ Cette fonction retournée **ferme sur (capture) la variable `count` de son parent**.

- 💡 Même **après que `creerCompteur` se soit terminée**, la variable `count` **reste accessible à travers la fonction retournée `compteur1`**.

- ➡️ **Chaque appel à `compteur1()` incrémente le `count` qui lui est propre.**

- ✅ On peut **créer plusieurs compteurs indépendants**, car **chaque invocation de `creerCompteur()` crée sa propre variable `count` capturée dans une closure séparée.**

✅ **Les closures sont très puissantes** :  
👉 Elles permettent par exemple **d’émuler des variables privées en programmation**  
(une **variable interne à une fonction accessible uniquement via des fonctions internes**).

💡 **C’est un concept qui peut paraître déroutant au début**,  
mais retenez que **chaque fonction “se souvient” des variables autour d’elle au moment de sa création**.

🔍 MDN définit une **fermeture** comme :  
> *“la paire formée d’une fonction et des références à son état environnant (les variables locales en mémoire)”* ([source : MDN](https://developer.mozilla.org))

<br>

> ## Pour aller plus loin :
>
> 🚩 **Les closures sont omniprésentes en JavaScript**  
> (par exemple **les gestionnaires d’événements** ou **les callbacks asynchrones** utilisent ce mécanisme).
>
> 💬 **Si ce concept n’est pas clair immédiatement**,  
> je vous recommande **la lecture de l’article MDN sur les Fermetures (Closures)**  
> 👉 [MDN - Closures](https://developer.mozilla.org)  
> ou **des tutoriels vidéos sur le sujet**.
>
> 🎯 **Comprendre les closures vous fera passer un cap en JavaScript.**

## Exercices pratiques :

1. Écrivez une fonction `min(a, b)` qui retourne le plus petit des deux nombres `a` et `b`. Testez-la avec différentes valeurs.

2. Écrivez une fonction `factorielle(n)` qui retourne la factorielle de `n` (`n! = 1 * 2 * ... * n`). Faites-le d’abord avec une boucle, puis (pour challenge) en récursif (une fonction qui s’appelle elle-même).

3. Modifiez la fonction `saluer(nom)` vue plus haut pour qu’elle retourne le message au lieu de le `console.log`. Ainsi, on pourra faire `let msg = saluer("Alice"); console.log(msg);`.

4. Écrivez une fonction `compterVoyelles(phrase)` qui retourne le nombre de voyelles dans la chaîne `phrase`. Réutilisez l’exercice du module 2 mais cette fois en encapsulant la logique dans une fonction réutilisable.

5. **Challenge closures :** Écrivez une fonction `createMultiplier(facteur)` qui retourne une nouvelle fonction. Cette nouvelle fonction prend un nombre en argument et renvoie ce nombre multiplié par `facteur`. Par exemple `const doubler = createMultiplier(2);` puis `doubler(5)` devrait donner `10`. Ici, `createMultiplier` utilise une closure pour “se souvenir” du `facteur`.

> Ce module vous a **introduit aux fonctions**, un **outil essentiel pour structurer le code et éviter les répétitions**.
> 
> 👉 Dans les prochains chapitres, nous allons **approfondir avec les structures de données** (tableaux, objets),  
puis **revenir sur des aspects avancés des fonctions** (contexte, méthodes) dans la partie **POO**.
