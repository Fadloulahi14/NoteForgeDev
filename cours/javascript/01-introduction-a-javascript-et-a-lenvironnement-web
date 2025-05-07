# Module 1 : Introduction à JavaScript et à l’Environnement Web

Dans ce premier module, nous allons répondre aux questions de base :

✅ **Qu’est-ce que JavaScript ?**  
✅ **À quoi sert-il et comment l’exécuter ?**

JavaScript est un **langage de programmation** qui permet d’ajouter de l’**interactivité aux pages web** au-delà du **HTML/CSS statique**.

Par exemple, JavaScript est utilisé pour :
- 🔄 **des mises à jour de contenu en temps réel**,
- 📝 **des formulaires interactifs**,
- 🎞️ **des animations**,
- 🕹️ **des jeux**, etc.

> Dès qu’une page web réagit aux actions de l’utilisateur ou affiche du contenu dynamique, il y a de fortes chances que **JavaScript soit impliqué** ([developer.mozilla.org](https://developer.mozilla.org/fr/docs/Web/JavaScript)).

## 1. JavaScript, HTML et CSS

JavaScript est l’un des **trois langages fondamentaux du web**, aux côtés de :
- **HTML** (structure du contenu)
- **CSS** (mise en style)

👉 **HTML** crée la structure de la page  
👉 **CSS** la présente visuellement  
👉 **JavaScript** rend la page **vivante** en manipulant cette structure et en réagissant aux actions

Il est donc **fortement conseillé d’avoir des bases en HTML/CSS**.  
Mais pas d’inquiétude : nous introduirons progressivement le HTML/CSS nécessaire dans nos projets.

Vous pouvez aussi en parallèle suivre des tutoriels HTML/CSS de base, comme le cours MDN “[Introduction au HTML/CSS](https://developer.mozilla.org/fr/docs/Learn/Getting_started_with_the_web/HTML_basics)”.

## 2. Où s’exécute JavaScript ?

- JavaScript s’exécute **principalement côté navigateur web** (Firefox, Chrome, etc.) pour le **développement front-end**.

- Chaque navigateur intègre un **moteur JavaScript** qui exécute le code **sur la machine de l’utilisateur**.

- ⚠️ JavaScript peut également s’exécuter **côté serveur (avec Node.js)**, mais **ce cours se concentrera sur le front-end** (interaction avec la page web dans le navigateur).


## 3. Préparer son environnement

Pour coder en JavaScript, vous aurez besoin :

- d’un **navigateur moderne**
- d’un **éditeur de code**

Nous vous conseillons un éditeur moderne comme :
- **Visual Studio Code**
- **Atom**
- **WebStorm**

Ces éditeurs offrent :
- ✅ coloration syntaxique  
- ✅ auto-complétion  
- ✅ débogage intégré

Vous écrirez le code JavaScript :
- dans des fichiers texte avec l’extension **.js**
- ou directement dans des pages HTML via la balise `<script>`

Vous utiliserez aussi la **console de développement du navigateur** (accessible via `F12` ou `Ctrl+Shift+I`) pour tester rapidement du code et voir les messages d’erreur ou les résultats de `console.log`.

> 💡 **Astuce** : dans la console de Chrome/Firefox, l’onglet **Console** permet d’exécuter des instructions JavaScript **à la volée** et d’inspecter les éléments de la page.

## 4. Premier script

Créons un premier fichier **HTML minimal** et un **script JavaScript** pour vérifier que tout fonctionne.

- Créez un fichier **index.html** avec le contenu suivant :  :

```html
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Hello JS</title>
</head>
<body>
  <h1>Bienvenue</h1>
  <p id="demo"></p>

  <script src="script.js"></script>
</body>
</html>
```

Ce fichier HTML charge un script externe `script.js` (grâce à la balise `<script src="...">` placée juste avant la fin de `<body>`).  

- Créons maintenant `script.js` dans le même dossier :

```javascript
// script.js
console.log("Hello, JavaScript !");
document.getElementById("demo").textContent = "Hello depuis JS !";
```

Ici, `console.log` affiche un message dans la **console du navigateur**, et la deuxième ligne utilise `document.getElementById` pour sélectionner l’élément `<p id="demo">` dans la page et **changer son texte**.

Ouvrez **index.html** dans votre navigateur :  
✅ Vous devriez voir le message apparaître sur la page  
✅ et dans la **console de développement** le log correspondant.

🎉 **Félicitations, vous avez exécuté votre premier code JavaScript dans une page web !**

> 💡 **Astuce** :  
> Si le texte n’apparaît pas ou que vous voyez une erreur, assurez-vous que votre fichier `script.js` est bien référencé et que la balise `<script>` est placée **en bas du `<body>`**.  
> Placer le script à la fin du body garantit que le **HTML est chargé avant que JS ne s’exécute**.  
> **Alternativement**, vous pouvez inclure la balise `<script>` dans le `<head>` en ajoutant l’attribut `defer` (ce qui reporte l’exécution du script après le chargement du HTML).

## 5. Structure d’un programme JavaScript

JavaScript est un **langage interprété**, à **syntaxe libre inspirée du C et de Java**.

- ✅ **Chaque instruction se termine par un point-virgule** (facultatif mais **recommandé** pour éviter les ambiguïtés).

### ✍️ **Commentaires en JavaScript**

Vous pouvez écrire des **commentaires** de deux façons :

```javascript
// commentaire sur une ligne

/* commentaire
   sur plusieurs lignes */
```
La majorité du code consistera à :

- 📝 **manipuler des variables**
- 🔄 **utiliser des contrôles conditionnels** (if, else, switch…)
- 🏗️ **définir des fonctions**
- 🌐 **interagir avec le DOM** (*Document Object Model*, c’est-à-dire **la représentation de la page web dans le navigateur**)

👉 **Nous verrons tout cela en détail dans les modules suivants.**

## 6. Bonnes pratiques dès le départ

Il est fortement conseillé d’**activer le mode strict de JavaScript** en ajoutant :

```javascript
"use strict";
```
📌 **Placez cette directive en haut de vos fichiers JavaScript ou à l’intérieur de vos fonctions.**

Le **"strict mode"** rend le comportement de JavaScript **plus sûr** car il :

- ❌ **empêche l’utilisation de variables non déclarées**
- ⚠️ **détecte plus d’erreurs au moment de l’exécution**
- 🐛 **facilite le débogage**

👉 **Nous reviendrons plus en détail sur ce mode et ses effets dans les modules suivants.**

> ### ✅ Bonnes pratiques
>
> Dès vos premiers scripts, **habituez-vous à :**
> 
> 🗂️ **Organiser votre code**  
> - Indentez correctement
> - Séparez les sections logiques par des **lignes vides**
> - **Commentez** les parties complexes
> 
> 🏷️ **Nommer clairement vos variables et fonctions**  
> Par exemple:
> 
> ```js
> let nombreArticles = 5; // ✅ clair
> let x = 5;              // ❌ peu explicite
> ```
> Un nom explicite rend le code plus lisible.
> 
> 🧪 **Tester régulièrement dans la console ou le navigateur**
> 
> - Ne **n’attendez pas d’écrire 200 lignes** avant de vérifier > que ça fonctionne.
> 
> 
> ✅ **Construisez et testez par petites étapes** pour identifier > les erreurs plus facilement.
> 
> - 🐞 **Utiliser la console pour déboguer**
> 
> La commande suivante est votre **meilleure alliée** :
> 
> ```javascript
> console.log(votreVariable);
> ```
> Elle vous permet :
> - d’afficher la valeur d’une variable
> - de comprendre ce qui se passe dans votre code