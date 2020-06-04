***************
Memo Javascript
***************

ECMAScript 6
############

Variable
********

Déclaration de variable
=======================

.. code-block:: javascript
    :linenos:

    let a;   // On déclare une variable modifiable dynamiquement
    const b; // On déclare une variable imuable

Portée de variable (scope)
==========================

let et const: portée de type **bloc**

.. code-block:: javascript
    :linenos:

    let num1 = 0;
    {
        num1 = 1; // OK : num1 est déclarée dans le bloc parent
        const num2 = 0;
    }
    console.log(num1); // 1
    console.log(num2); // Erreur : num2 n'est pas visible ici !

Expression
==========

Evaluation
----------

.. code-block:: javascript
    :linenos:
    
    let e = 3 + 2 * 4; // e contient 11 (3 + 8)
    e = (3 + 2) * 4;   // e contient 20 (5 * 4)

Template literal
----------------

Intégration de variable dans des chaînes de charactère

.. code-block:: javascript
    :linenos:

    const country = "France";
    console.log(`Je vis en ${country}`); // "Je vis en France"
    const x = 3;
    const y = 7;
    console.log(`${x} + ${y} = ${x + y}`); // "3 + 7 = 10"

Type conversion
---------------

Conversion implicite
^^^^^^^^^^^^^^^^^^^^

.. code-block:: javascript
    :linenos:

    const f = 100;
    console.log("f contient " + f); // "f contient 100"

Conversion impossible
^^^^^^^^^^^^^^^^^^^^^

Retourne un type NaN (not a number)

.. code-block:: javascript
    :linenos:

    const g = "cinq" * 2;
    console.log(g); // NaN

Conversion explicite
^^^^^^^^^^^^^^^^^^^^

.. code-block:: javascript
    :linenos:

    const h = "5";
    console.log(h + 1); // Concaténation : affiche "51"
    const i = Number("5");
    console.log(i + 1); // Addition numérique : affiche 6

Condition
*********

Condition if/else
=================

.. code-block:: javascript
    :linenos:

    if (condition) {
      // instructions exécutées quand la condition est vraie
    }
    else {
      // instructions exécutées quand la condition est fausse
    }

.. csv-table:: List Opérator
    :header: "Opérateur", "signification"
    :widths: 15, 25

    "===","Egal à"
    "!==","Différent de"
    "<","Inférieur à"
    "<=",Inférieur ou égal à"
    ">","Supérieur à"
    ">=","Supérieur ou égal à"

Conditions composées
====================

ET
--

.. code-block:: javascript
    :linenos:

    if ((nombre >= 0) && (nombre <= 100)) {
      console.log(nombre + " est compris entre 0 et 100");
    }

OU
--

.. code-block:: javascript
    :linenos:

    if ((nombre < 0) || (nombre > 100)) {
      console.log(nombre + " est en dehors de l'intervalle [0, 100]");
    }

NON
---

.. code-block:: javascript
    :linenos:

    if (!(nombre > 100)) {
      console.log(nombre + " est inférieur ou égal à 100");
    }

Exemple avec else/if
--------------------

.. code-block:: javascript
    :linenos:

    const meteo = prompt("Quel temps fait-il dehors ?");
    if (meteo === "soleil") {
      console.log("Sortez en t-shirt.");
    } else if (meteo === "vent") {
      console.log("Sortez en pull.");
    } else if (meteo === "pluie") {
      console.log("Sortez en blouson.");
    } else if (meteo === "neige") {
      console.log("Restez au chaud à la maison.");
    } else {
      console.log("Je n'ai pas compris !");
    }

Exemple avec switch
-------------------

.. code-block:: javascript
    :linenos:

    const meteo = prompt("Quel temps fait-il dehors ?");
    switch (meteo) {
      case "soleil":
        console.log("Sortez en t-shirt.");
        break;
      case "vent":
        console.log("Sortez en pull.");
        break;
      case "pluie":
        console.log("Sortez en blouson.");
        break;
      case "neige":
        console.log("Restez au chaud à la maison.");
        break;
      default:
        console.log("Je n'ai pas compris !");
    }

Remarque: Les instructions break; dans les blocscase sont indispensables pour sortir du switch et 
éviter de passer d'un bloc à un autre.


Répétition d'instruction
************************

Boucle While
============

.. code-block:: javascript
    :linenos:

    console.log("Début du programme");
    let nombre = 1;
    while (nombre <= 5) {
      console.log(nombre);
      nombre++;
    }
    console.log("Fin du programme");

Boucle for
==========

La syntaxe d'une boucle for se présente sous la forme : for (initialisation; condition; étape) {

.. code-block:: javascript
    :linenos:

    let compteur;
    for (compteur = 1; compteur <= 5; compteur++) {
      console.log(compteur);
    }

Fonction
********

Passage de paramètre
====================

.. code-block:: javascript
    :linenos:

    function direBonjour(prenom) {
      const message = `Bonjour, ${prenom} !`;
      return message;
    }
    console.log(direBonjour("Baptiste")); // "Bonjour, Baptiste !"
    console.log(direBonjour("Sophie")); // "Bonjour, Sophie !"

.. code-block:: javascript
    :linenos:

    function presentation(prenom, age) {
      console.log(`Tu t'appelles ${prenom} et tu as ${age} ans`);
    }
    presentation("Garance", 10); // "Tu t'appelles Garance et tu as 10 ans"
    presentation(6, "Prosper"); // "Tu t'appelles 6 et tu as Prosper ans"

Fonction anonyme
================

.. code-block:: javascript
    :linenos:

    const bonjour = function(prenom) {
      const message = `Bonjour, ${prenom} !`;
      return message;
    }
    console.log(bonjour("Thomas")); // "Bonjour, Thomas !"

Fonction fléchée
================

.. code-block:: javascript
    :linenos:

    const bonjour = (prenom) => {
      const message = `Bonjour, ${prenom} !`;
      return message;
    }
    console.log(bonjour("Thomas")); // "Bonjour, Thomas !"

.. code-block:: javascript
    :linenos:

    // Dificile de faire plus concis !
    const bonjour = prenom => `Bonjour, ${prenom} !`;
    console.log(bonjour("Thomas")); // "Bonjour, Thomas !"

Les objets
**********

Syntaxe littérale
=================

.. code-block:: javascript
    :linenos:

    const stylo = {
      type: "bille",
      couleur: "bleu",
      marque: "Bic"
    };
    console.log(stylo.type); // "bille"
    console.log(stylo.couleur); // "bleu"
    console.log(stylo.marque); // "Bic"
    stylo.couleur = "rouge";
    console.log(`J'écris avec un stylo ${stylo.type} ${stylo.couleur} de marque ${stylo.marque}`);
    // Ajout de la propriété "prix"
    stylo.prix = "2.5";
    // "Mon stylo coûte 2.5 euros"
    console.log(`Mon stylo coûte ${stylo.prix} euros`);

Ajout de méthode à un objet
===========================

.. code-block:: javascript
    :linenos:

    const aurora = {
      nom: "Aurora",
      sante: 150,
      force: 25,
      // Renvoie la description du personnage
      decrire() {
        return `${this.nom} a ${this.sante} points de vie et ${this.force} en force`;
      }
    };
    // "Aurora a 150 points de vie et 25 en force"
    console.log(aurora.decrire());

Les tableaux
************

Déclarer et accéder à un tableau
================================

Les tableaux javascript peuvent contenir des types de données différentes. L'exemple si dessous
ne contient que des chaînes de caractère.

.. code-block:: javascript
    :linenos:

    const films = ["Le loup de Wall Street", "Vice-Versa", "Babysitting"];
    console.log(films.length); // 3
    console.log(films[0]); // "Le loup de Wall Street"
    console.log(films[1]); // "Vice-Versa"
    console.log(films[2]); // "Babysitting"

.. warning:: Les éléments d'un tableau sont passés par référence.

Itération d'un tableau
======================

Avec for
--------

.. code-block:: javascript
    :linenos:

    const films = ["Le loup de Wall Street", "Vice-Versa", "Babysitting"];
    for (let i = 0; i < films.length; i++) {
      console.log(films[i]);
    }

Avec forEach
------------

.. code-block:: javascript
    :linenos:

    const films = ["Le loup de Wall Street", "Vice-Versa", "Babysitting"];
    films.forEach(film => {
      console.log(film);
    });

Avec for-of
-----------

.. code-block:: javascript
    :linenos:

    const films = ["Le loup de Wall Street", "Vice-Versa", "Babysitting"];
    for (const film of films) {
      console.log(film);
    }

Ajouter un élément à un tableau
===============================

En fin de liste(push)
---------------------

.. code-block:: javascript
    :linenos:

    const films = ["Le loup de Wall Street", "Vice-Versa", "Babysitting"];
    films.push("Les Bronzés"); // Ajoute le film à la fin du tableau
    console.log(films[3]); // "Les Bronzés"

En début de liste(unshift)
--------------------------

.. code-block:: javascript
    :linenos:

    const films = ["Le loup de Wall Street", "Vice-Versa", "Babysitting"];
    films.unshift("Les Bronzés"); // Ajoute le film au début du tableau
    console.log(films[0]); // "Les Bronzés"

Supprimer un élément d'un tableau
=================================

Avec pop()
----------

.. code-block:: javascript
    :linenos:

    const films = ["Le loup de Wall Street", "Vice-Versa", "Babysitting"];
    films.pop(); // Supprime le dernier élément
    console.log(films.length); // 2
    console.log(films[2]); // undefined

Avec splice()
-------------

.. code-block:: javascript
    :linenos:

    const films = ["Le loup de Wall Street", "Vice-Versa", "Babysitting"];
    films.splice(0, 1); // Supprime 1 element à partir de l'indice 0
    console.log(films.length); // 2
    console.log(films[0]); // "Vice-Versa"
    console.log(films[1]); // "Babysitting"

Manipulation de chaîne de caractère
===================================

.. code-block:: javascript
    :linenos:

    console.log("Je suis une chaîne".length); // 18
    const motInitial = "Bora-Bora";
    console.log(motInitial.toLowerCase());  // "bora-bora"
    console.log(motInitial.toUpperCase());  // "BORA-BORA"
    console.log(motInitial);  // "Bora-Bora"

Transformer une chaîne en tableau
=================================

.. code-block:: javascript
    :linenos:

    const prenom = "Odile";
    const tabPrenom = Array.from(prenom);
    tabPrenom.forEach(lettre => {
      console.log(lettre);
    });

Rechercher dans une chaîne
==========================

Avec indexOf
------------

indexOf() renvoie l'indice de la première occurence ou -1

.. code-block:: javascript
    :linenos:

    const chanson = "Honky Tonk Women";
    console.log(chanson.indexOf("onk")); // 1
    console.log(chanson.indexOf("Onk")); // -1 (à cause du O)

Avec startsWith ou endsWith
---------------------------

.. code-block:: javascript
    :linenos:

    const chanson = "Honky Tonk Women";
    console.log(chanson.startsWith("Honk")); // true
    console.log(chanson.startsWith("honk")); // false
    console.log(chanson.startsWith("Tonk")); // false
    console.log(chanson.endsWith("men")); // true
    console.log(chanson.endsWith("Men")); // false
    console.log(chanson.endsWith("Tonk")); // false

Découper une chaîne
===================

.. code-block:: javascript
    :linenos:

    const listeMois = "Jan,Fev,Mar,Avr,Mai,Jun,Jul,Aou,Sep,Oct,Nov,Dec";
    const mois = listeMois.split(",");
    console.log(mois[0]); // "Jan"
    console.log(mois[11]); // "Dec"

Les classes
***********

Déclaration d'une classe
========================

* Une classe est créée avec le mot-clé  class   suivi du nom de la classe, qui commence le plus 
  souvent par une majuscule.
* Contrairement aux objets littéraux, on ne sépare pas les éléments définis dans une classe par 
  des virgules.
* Une classe ne contient que des définitions de méthodes.
* Comme pour les objets littéraux, le mot-clé  this  représente à l'intérieur d'une méthode 
  l'objet sur lequel la méthode a été appelée.
* Une méthode spéciale nommée  constructor()  peut être ajoutée à la définition de la classe. 
  Cette méthode est exécutée pendant la création d'un objet et permet d'ajouter des données à 
  l'objet, sous la forme de propriétés.

.. code-block:: javascript
    :linenos:

    class Personnage {
      constructor(nom, sante, force) {
        this.nom = nom;
        this.sante = sante;
        this.force = force;
        this.xp = 0; // Toujours 0 au début
      }
      // Renvoie la description du personnage
      decrire() {
        return `${this.nom} a ${this.sante} points de vie, ${
          this.force
        } en force et ${this.xp} points d'expérience`;
      }
    }

Instantation d'une classe
=========================

.. code-block:: javascript
    :linenos:

    const aurora = new Personnage("Aurora", 150, 25);
    const glacius = new Personnage("Glacius", 130, 30);
    // "Aurora a 150 points de vie, 25 en force et 0 points d'expérience"
    console.log(aurora.decrire());
    // "Glacius a 130 points de vie, 30 en force et 0 points d'expérience"
    console.log(glacius.decrire());

Délégation et prototype
=======================

Le modèle objet de JavaScript est basé sur les prototypes et non sur les classes. Une classe JavaScript est elle-même un objet, pas un modèle statique. "Instancier" une classe crée un nouvel objet lié à un objet prototype.

Les ensembles/set
*****************

`https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Objets_globaux/Set`_

.. code-block:: javascript
    :linenos:

    const set1 = new Set([1, 2, 3, 4, 5]);
    console.log(set1.has(1));
    // expected output: true
    console.log(set1.has(5));
    // expected output: true
    console.log(set1.has(6));
    // expected output: false

Les listes ordonnées/maps
*************************

`https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Objets_globaux/Map`_

.. code-block:: javascript
    :linenos:

    var maMap = new Map();
    var objetClé = {},
        fonctionClé = function () {},
        chaineClé = "une chaîne";
    // définir les valeurs
    maMap.set(chaineClé, "valeur associée à 'une chaîne'");
    maMap.set(objetClé, "valeur associée à objetClé");
    maMap.set(fonctionClé, "valeur associée à fonctionClé");
    maMap.size; // 3
    // récupérer les valeurs
    maMap.get(chaineClé);     // "valeur associée à 'une chaîne'"
    maMap.get(objetClé);      // "valeur associée à objetClé"
    maMap.get(fonctionClé);   // "valeur associée à fonctionClé"
    maMap.get("une chaîne");  // "valeur associée à 'une chaîne'"
                              // car chaineClé === 'une chaîne'
    maMap.get({});            // indéfini car objetClé !== {}
    maMap.get(function() {}); // indéfini car fonctionClé !== function () {}

Gérer les erreurs d'exécution
*****************************

.. code-block:: javascript
    :linenos:

    try {
        // code susceptible à l'erreur ici
    } catch (error) {
        // réaction aux erreurs ici
    }


