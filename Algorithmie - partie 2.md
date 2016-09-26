# Algorithmie - Partie 2

<!-- MarkdownTOC -->

- [Structures](#structures)
- [Procédures](#procédures)
  - [Format](#format)
- [Fonctions](#fonctions)
- [Exercices](#exercices)
  - [17 - Meilleur élève](#17---meilleur-élève)
  - [18 - Structure et procédure](#18---structure-et-procédure)
  - [19 - Travaux sur des notes II](#19---travaux-sur-des-notes-ii)
  - [20 - Pizzas II](#20---pizzas-ii)
  - [21 - Suite logique](#21---suite-logique)
  - [22 - Suite logique II](#22---suite-logique-ii)
  - [23 - Sablier](#23---sablier)

<!-- /MarkdownTOC -->


<a name="structures"></a>
## Structures
Les structures servent à créer des _types_ de variable supplémentaires. Elles sont définies dans l'algorithme, dans une rubrique _Types_.
```txt
Algorithme: nom
{Description}

Types:
    Structure Pizza:
       nom, ingredients: chaine,
       diametre: entier
    FStructure

Variables:
    uneVariable: entier
    unePizza: Pizza

Début
    <logique>
Fin

```

On accède aux propriétés d'une structure avec un `.` entre le nom de la variable et la propriété:

```
[...]
Variables:
    unePizza: Pizza
    unTableauDePizzas(10) en Pizza

Début
    unePizza.nom ← "Royale"
    unePizza.diametre ← 40

    Ecrire(unePizza.nom)

    unTableauDePizza(1).nom ← "Quatre fromages"

    Ecrire unTableauDePizza(1).nom
Fin
```

<a name="procédures"></a>
## Procédures

Les procédures sont des suites d'actions _nommées_ pouvant être utilisées dans un algorithme.
Les procédures prennent en compte des arguments.
Les variables définies à l'intérieur sont _locales_ (elles ne sont pas accessibles dans le reste de l'algo).
Elles sont généralement définies dans un _carnet de procédures_. Les procédures ne renvoient pas de valeur et sont donc généralement réservées à l'affichage des données.

<a name="format"></a>
### Format

```txt
Procédure <nom_de_la_procedure> (<param1>: <type>, <paramX>: <type>)

  Constantes:
    <CONST1>: type
  Variables:
    <var1>:type

  Début
    <logique>
  Fin

FinProc
```

<a name="fonctions"></a>
## Fonctions
Tout comme les procédures, les fonctions sont des suites d'actions _nommées_ prenant des arguments. A la différence des procédures, une fonction renvoie une valeur, qui peut être ensuite utilisée dans l'algorithme.

```txt
Fonction <nom_de_la_fonction> (<param1>: <type>, <paramX>: <type>) : <type_retourné>

  Constantes:
    <CONST1>: type
  Variables:
    <var1>:type

  Début
    <logique>
    <nom_de_la_fonction> ← <valeur_a_retourner>
  Fin

FinFonction
```

<a name="exercices"></a>
## Exercices

<a name="17---meilleur-élève"></a>
### 17 - Meilleur élève
>  - Ecrire un algorithme qui demande le nombre d’élève compris dans une classe et qui enregistre les données suivantes pour chaque élèves : nom, prénom, age et moyenne.
>  - Une fois tous les élèves enregistrés, on affiche le meilleur.

```txt
Algorithme : meilleurEleve

Type: Structure Eleve
        nom, prenom: chaine
        age: entier
        moyenne: réel
       FinStruct

Tableau: classe() en Eleve

Variables: compteur, nbEleves, index : entier

Début
  Ecrire ("Quel est le nombre d'élèves ?")
  Lire nbEleves

  redim classe (nbEleves)

  # Remplissage du tableau
  Pour compteur ← 1 à nbEleves par 1 Faire:
    Ecrire ("Quel est le nom de l'élève ", compteur)
    Lire (classe(compteur).nom)
    Ecrire ("Quel est le prénom de l'élève ", compteur)
    Lire (classe(compteur).prenom)
    Ecrire ("Quel est l'age de l'élève ", compteur)
    Lire (classe(compteur).age)
    Ecrire ("Quel est la moyenne de l'élève ", compteur)
    Lire (classe(compteur).moyenne)
  FPour

  # Recherche de la meilleure moyenne
  index ← 1
  Pour compteur ← 2 à nbEleves par 1 faire:
    Si (classe(compteur).moyenne > classe(index).moyenne) Alors:
      index ← compteur
    FSi
  FPour

  # Affichage
  Ecrire (
    "Le meilleur élève est ", classe(index).nom, ' ', classe(index).prenom,
    " (", classe(index).age, " ans), avec une moyenne de ", classe(index).moyenne
  )
Fin
```

Note : Cet algorithme ne tient pas compte d'une éventuelle égalité.

<a name="18---structure-et-procédure"></a>
### 18 - Structure et procédure
>  - Ecrire une structure décrivant les cractéristiques d’une voiture. 
>  - Ecrire une procédure qui affiche les cractéristiques d’une voiture 
>  - Mettre en œuvre la structure et la procédure dans un programme.

```txt
Procédure: afficherVoiture(element : Voiture):
  Variables : -
  Début:
    Ecrire ("Constructeur : ", element.constructeur)
    Ecrire ("Modèle : ", element.modele)
    Ecrire ("Année de construction : " element.annee)
  Fin
FProc
```

```txt
Algorithme: voiture

Types:
  Structure Voiture:
    constructeur, modele: chaines
    annee: entier
  FStruct

Variables: voiture: Voiture

Début
  # Remplissage de voiture
  Ecrire "Constructeur ?" Lire voiture.constructeur
  Ecrire "Modèle ?" Lire voiture.modele
  Ecrire "Année ?" Lire voiture.annee

  afficherVoiture(voiture)
Fin
```


<a name="19---travaux-sur-des-notes-ii"></a>
### 19 - Travaux sur des notes II

> Exercice fonction / procédure:
>  - Écrire un programme qui permet de saisir un tableau de note
>  - Écrire une fonction qui calcule la moyenne.
>  - Écrire une procédure qui affiche les notes au dessus de la moyenne
>  - Mettre en œuvre ces éléments dans un programme.

```txt
Procédure: afficherMeilleuresNotes(notes(): réel, nbElements: entier, moyenne: réel)
  Variables: 
    compteur: entier

  Debut
    Pour compteur ← 1 à nbElements par 1 Faire:
        Si(notes(compteur) > moyenne)
            Ecrire notes(compteur)
        FSi
    FPour
  Fin
FProc

Fonction: calculMoyenne(valeurs(): réel, nbElements: entier) : réel
  Variables: 
    compteur: entier
    total: réel
  
  Début
    total ← 0

    Pour compteur ← 1 à nbElements par 1 Faire
      total ← total + valeurs(compteur)
    FPour

    calculMoyenne ← total / nbElements
  Fin
FFonction
```

```txt
Algorithme: notes

Variables:
  nbNotes, compteur : entier
  moyenne : réel
Tableaux:
  notes(): réel

Début
  Ecrire ("Combien y a-t-il de notes ?") Lire (nbNotes)

  redim note(nbNotes)

  Pour (compteur ← 1 à nbNotes par 1) Faire:
    Ecrire ("Note ?") Lire (note(compteur))
  FPour

  moyenne ← calculMoyenne(notes, nbNotes)

  Ecrire ("Moyenne de classe", moyenne)
  afficherMeilleuresNotes(notes, nbNotes, moyenne)
Fin
```

<a name="20---pizzas-ii"></a>
### 20 - Pizzas II

> L'utilisateur remplit une liste de pizzas (nom, diam, prix). Le programme doit afficher les pizzas triées par leur ratio prix/taille

```txt
Fonction calcRatio(pizza Pizza): réel
    Constantes:
        PI: réel ← 3.14

    Variables:
        aire: réel

    Début
        aire ← PI * (pizza.diam / 2) * (pizza.diam / 2)
        calcRatio ← pizza.prix / aire
    Fin
FFonction

Fonction triPizzas(pizzas(): Pizza, nbE): pizzas()
{Tri à bulles sur un tableau de Pizza}

    Variables: 
        compteur1, compteur2, pivot: entiers
        permutation: booleen

    Début
        compteur1 ← 1
        permutation ← Vrai
        Tant que (permutation = Vrai) faire:
            permutation ← Faux
            Pour compteur2 ← 1 à (nbE - compteur1) par 1 faire:
                Si (calcRatio(pizzas(compteur1)) < calcRatio(pizzas(compteur1 + 1)) Alors:
                    pivot ← pizzas(compteur1)
                    pizza(compteur1) ← pizza(compteur2)
                    pizza(compteur2) ← pivot
                    permutation ← Vrai
                Fsi
            FPour
            compteur1 ← compteur1 + 1
        FTantQue

        triPizzas ← pizzas
        // Pour compteur1 ← 1 à 5 par 1 faire:
        //     afficherPizza(pizzas(compteur1), compteur1);
        // FPour
    Fin
FFonction
```

```txt
Procédure afficherPizza(pizza: Pizza, pos: entier):
    Variables: - 

    Début
        Ecrire ("Position #", pos, ': ', pizza.nom)
        Ecrire ("(diam. : ", pizza.diam, " - prix : ", pizza.prix)
    Fin
FProc
```

```txt
Algorithme: pizza2

Types
    Structure Pizza:
      nom: chaine
      diam: entier
      prix: reel
    FStruct

Constantes: PI: réel ← 3.14

Variables:
    pizzas() Pizza
    nbP, compteur: entier

Début
    # Remplissage du tableau:
    Ecrire ("Combien de pizzas à comparer ?") Lire(nbP)
    redim pizzas(nbP)

    Pour compteur ← 1 à nbP par 1 Faire:
        Ecrire ("Quel est le nom de la pizza #", compteur) Lire pizzas(compteur).nom
        Ecrire ("Quel est le diametre de la pizza #", compteur) Lire pizzas(compteur).diam
        Ecrire ("Quel est le prix de la pizza #", compteur) Lire pizzas(compteur).prix
    FPour

    # Tri
    pizzas ← triPizzas(pizzas, nbP)

    #Affichage
    Pour compteur ← 1 à nbP par 1 Faire
        afficherPizza(pizzas(compteur), nbP)
    FPour
Fin
```

<a name="21---suite-logique"></a>
### 21 - Suite logique
```txt
1
1 2
1 2 3
1 2 3 4
1 2 3 4 5
1 2 3 4 5 6
```

> Soit la suite 1, 1 2, 1 2 3, 1 2 3 4,...
> L'utilisateur doit entrer la taille de la plus grande _suite_ et l'algorithme doit l'afficher.

```txt
Algorithme: suiteLogique

Variables:
    n, ligne, col: entier

Début
    Ecrire ("Largeur de la base") Lire(n)
    
    Pour ligne ← 1 à n par 1 Faire:
        Pour col ← 1 à ligne Faire:
            Ecrire (col, ' ')
        FPour
        Ecrire ("\n")
    FPour
Fin
```

<a name="22---suite-logique-ii"></a>
### 22 - Suite logique II
```txt
1 2 3 4 5 6
  2 3 4 5 6
    3 4 5 6
      4 5 6
        5 6
          6
```

> Soit la suite 1, 1 2, 1 2 3, 1 2 3 4,...
> L'utilisateur doit entrer la taille de la plus grande _suite_ et l'algorithme doit l'afficher.

```txt
Algorithme: suiteLogique

Variables:
    n, ligne, col: entier

Début
    Ecrire ("Largeur de la base") Lire(n)
    
    Pour ligne ← 1 à n par 1 Faire:
        Pour col ← 1 à n par 1 Faire:
            Si ligne > col Faire
              Ecrire("  ")
            Sinon
              Ecrire(col - ligne + 1)
            FSi
        FPour
        Ecrire ("\n")
    FPour
Fin
```

<a name="23---sablier"></a>
### 23 - Sablier
```txt
1 2 3 4 5
  1 2 3
    1
  1 2 3
1 2 3 4 5
```

```txt
Algorithme: Sablier

Variables:
    n, ligne, col, mid: entier

Début
    # Forcer un nombre impaire
    Faire:
      Ecrire ("Largeur de la base") Lire(n)
    Tant que (n%2 = 0)

    mid ← (n - (n%2)/2 +1)

    # Traitement des lignes
    Pour ligne ← 1 à mid par 1 Faire:
      Pour col ← 1 à n par 1 Faire:
        Si (ligne > col OU ligne < (col-1 * 2) Faire
          Ecrire("  ")
        Sinon
          Ecrire(col - ligne + 1)
        FSi
      FPour
      Ecrire ("\n")
    FPour
    Pour ligne ← (mid +1) à n par 1 Faire:
      Pour col ← 1 à n par 1 Faire:
        Si (col OU ligne < (col-1 * 2) Faire
          Ecrire("  ")
        Sinon
          Ecrire(col - ligne + 1)
        FSi
      FPour
      Ecrire ("\n")
    FPour
Fin
```