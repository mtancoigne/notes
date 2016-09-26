# Algorithmie

<!-- MarkdownTOC -->

- [Introduction](#introduction)
- [Format](#format)
  - [Variables](#variables)
  - [Constantes](#constantes)
  - [Les tableaux](#les-tableaux)
  - [Opérateurs arithmétiques](#opérateurs-arithmétiques)
- [Structures conditionnelles](#structures-conditionnelles)
  - [Si... Sinon...](#si-sinon)
  - [Cas](#cas)
  - [Pour](#pour)
  - [Tant que](#tant-que)
  - [Répéter tant que](#répéter-tant-que)
  - [Exemple de suivi de variables](#exemple-de-suivi-de-variables)
- [Exercices](#exercices)
  - [1 - Calcul de prix TTC](#1---calcul-de-prix-ttc)
  - [2 - Permutation de valeurs](#2---permutation-de-valeurs)
  - [3 - Pizzas](#3---pizzas)
  - [4 - Reçu avec mention](#4---reçu-avec-mention)
  - [5 - M/Mme](#5---mmme)
    - [Avec des _Si_](#avec-des-si)
    - [Avec _Cas_](#avec-cas)
  - [6 - Exercice sur les boucles](#6---exercice-sur-les-boucles)
  - [7 - Secondes en J/H/M/S](#7---secondes-en-jhms)
  - [8 - Tableaux](#8---tableaux)
  - [9 - Valeur max dans un tableau](#9---valeur-max-dans-un-tableau)
  - [10 - Triage - Recherche du minimum](#10---triage---recherche-du-minimum)
  - [11 - Triage - Tri à bulle](#11---triage---tri-à-bulle)
  - [12 - Puissances](#12---puissances)
  - [13 - Chute libre](#13---chute-libre)
  - [14 - Tonte de pelouse](#14---tonte-de-pelouse)
  - [15 - Tri décroissant par recherche du minimum](#15---tri-décroissant-par-recherche-du-minimum)
  - [16 - Moyenne d'un classe](#16---moyenne-dun-classe)

<!-- /MarkdownTOC -->

<a name="introduction"></a>
## Introduction
Un _algorithme_ décrit un programme dans une langue donnée, et pas un langage. De ce fait, il est lisible par tous et peut ensuite être retranscrit dans n'importe quel langage de programmation. 
Il n'y a pas réellement de normes concernant les algorithmes : les structures, même si elles suivent un ordre logique, peuvent être écrites avec une certaine souplesse. Finalement, tout ce qui compteur, c'est que le programme fonctionne et qu'il soit facile à lire.

<a name="format"></a>
## Format

```txt
Algorithme: <nom de l'algo>
{Description}

Constantes: MA_CONSTANTE : <type> ← Valeur

Tableaux:
    monTableau(<taille>) en <type>

Variables: 
    nomVar, autreVar : <type>
    encoreAutreVar : <autre type>

Début:
 |  <contenu>
Fin
```

**Notes**:

  - Ne pas oublier le trait vertical lorsque l'on écrit un algorithme sur papier : cela permet de se situer rapidement dans l'écriture. Pour un algorithme écrit dans un logiciel de traitement de texte, utiliser l'indentation (espaces ou tabulations).
  - Les mots clés **Algorithme**, **Variables**, **Constantes**, ...
  - Les variables sont afféctées suivant cette structure : `<variable> ← <valeur>`

<a name="variables"></a>
### Variables

Les variables utilisées dans le programme sont définies en début de programme, ainsi que leur type. Elles peuvent être des **entiers** (`1`, `2`, `10`, `-20`,...), des **réels** (`1.5`, `-128.1587`, ...), des **chaines** (`"une chaine de caractères"`), des **caractères** (`'a'`, `'$'`,..) ou des **booléens** (`Vrai` ou `Faux`).

Il est de bon usage d'utiliser des noms en camelCase pour les variables (`maVariableEnCamelCase`).

<a name="constantes"></a>
### Constantes

Les constantes doivent être définies et affectées en début de programmes. Pour les noms de constantes, on utilisera des majuscules et underscores (`MA_CONSTANTE`)

<a name="les-tableaux"></a>
### Les tableaux

Les tableaux sont des variables contenant plusieur valeurs d'**un même type**. Ils doivent être déclarés avant les variables. 

**Note :** Les indices des tableaux commencent à 1.

Représentation "graphique" d'un tableau à une dimension:

```
+---+---+---+---+---+
| 1 | 2 | 3 | 4 | 5 |
+---+---+---+---+---+
Tableau: monTableau(5) en entier
```

Représentation "graphique" d'un tableau à deux dimensions:

```
+-----+-----+-----+-----+-----+
| 1,1 | 1,2 | 1,3 | 1,4 | 1,5 |
+-----+-----+-----+-----+-----+
| 2,1 | 2,2 | 2,3 | 2,4 | 2,5 |
+-----+-----+-----+-----+-----+
| 3,1 | 3,2 | 3,3 | 3,4 | 3,5 |
+-----+-----+-----+-----+-----+
Tableau: monTableau(5)(3) en entier
```

Représentation "graphique" d'un tableau à trois dimensions:

```
              +-------+-------+-------+-------+-------+
              | 1,1,3 | 1,2,3 | 1,3,3 | 1,4,3 | 1,5,3 |
              +-------+-------+-------+-------+-------+
       +-------+-------+-------+-------+-------+2,5,3 |
       | 1,1,2 | 1,2,2 | 1,3,2 | 1,4,2 | 1,5,2 |------+
       +-------+-------+-------+-------+-------+2,5,3 |
+-------+-------+-------+-------+-------+2,5,2 |------+
| 1,1,1 | 1,2,1 | 1,3,1 | 1,4,1 | 1,5,1 |------+
+-------+-------+-------+-------+-------+2,5,2 |
| 2,1,1 | 2,2,1 | 2,3,1 | 2,4,1 | 2,5,1 |------+
+-------+-------+-------+-------+-------+
| 3,1,1 | 3,2,1 | 3,3,1 | 3,4,1 | 3,5,1 |
+-------+-------+-------+-------+-------+  <-- indices: y,x,z
Tableau: monTableau(5)(3) en entier
```

Il n'y a aucune limite sur le nombre de dimensions.

Pour accéder à une valeur donnée, il faut utiliser le/les indexes permettant d'y arriver: `monTableau(index1)(index2)...`.

<a name="opérateurs-arithmétiques"></a>
### Opérateurs arithmétiques

Les seuls opérateurs arithmétiques utilisables dans un algorithme sont :
  - **<nombre1> + <nombre2>** : Effectue une addition.
  - **<nombre1> - <nombre2>** : Effectue une soustraction
  - **<nombre1> * <nombre2>** : Effectue une multiplication
  - **<nombre1> / <nombre2>** : Effectue une division
  - **<nombre1> % <nombre2>** : Retourne le _modulo_: le reste de la division euclidienne de _nombre1 / nombre2_

<a name="structures-conditionnelles"></a>
## Structures conditionnelles

<a name="si-sinon"></a>
### Si... Sinon...

```txt
Si <expression>:
Alors: 
    <instructions>
Sinon: 
    <instructions>
Fsi
```

<a name="cas"></a>
### Cas

```txt
Cas <identificateur>
  <val 1>: <insrtuctions>
  <val 2>: <instructions>
  <val x...>: <instructions>
  défault: <instructions>
FinCas
```

<a name="pour"></a>
### Pour

```txt
Pour <compteur> ← <valInit> à <valFin> par <pas> faire:
    <instruction>
FPour
```

**Attention :**
  - la variable de compteur DOIT être définie en début d'algo
  - il ne faut pas écrire dessus.

<a name="tant-que"></a>
### Tant que

```txt
Tant que <expression logique est vraie> faire:
    <instructions>
Ftq
```

<a name="répéter-tant-que"></a>
### Répéter tant que

```txt
Répéter
    <instructions>
Tant que <expression logique est vraie>
```

**Note :** Les instructions de la boucle sont éxécutées au moins une fois.

<a name="exemple-de-suivi-de-variables"></a>
### Exemple de suivi de variables

Soit l'algorithme suivant:

```
Algorithme : exerciceAffectations

Constante : SEUIL : réel ← 13,25

Variables : 
    valA, valB : réels
    compteur : entier
    mot, tom : chaines

Début
    valA ← 0,56
    valB ← valA
    valA ← valA x (10,5 + SEUIL)
    compteur ← 1
    compteur ← compteur + 10
    mot ← « bonjour »
    tom ← « au revoir! »
Fin
```

Le tableau de suivi variables peut être écrit comme suit:

| Ligne | valA | valB | compteur | mot       | tom           |
| ----- | ---- | ---- | -------- | --------- | ------------- |
| 1     | 0.56 | null | null     | null      | null          |
| 2     | 0.56 | 0.56 | null     | null      | null          |
| 3     | 13.3 | 0.56 | null     | null      | null          |
| 4     | 13.3 | 0.56 | 1        | null      | null          |
| 5     | 13.3 | 0.56 | 11       | null      | null          |
| 6     | 13.3 | 0.56 | 11       | "bonjour" | null          |
| 7     | 13.3 | 0.56 | 11       | "bonjour" | "au revoir !" |

<a name="exercices"></a>
## Exercices

<a name="1---calcul-de-prix-ttc"></a>
### 1 - Calcul de prix TTC

```txt
Algorithme: CalculTTC
{Calcule le prix TTC à partir d'un prix HT donné}

Constantes: 
    TAUX_TVA : entier ← 20

Variables: prixHT : réel

Début:
    Ecrire ("Quel est le prix HT ?")
    Lire (prixTH)
    Ecrire ("Le prix TTC est ", prixHT * (1 + TAUX_TVA/100), '€')
Fin
```

<a name="2---permutation-de-valeurs"></a>
### 2 - Permutation de valeurs

```txt
Algorithme: permutationAB
{Permute les valeurs A et B demandées à l'utilisateur}

Variables: valA, valB, pivot : entier

Début:
    Ecrire ("Donnez moi A...")
    Lire (valA)
    Ecrire ("Donnez moi B...")
    Lire (valB)
    pivot ← valA
    valA ←valB
    valB ←pivot
    Ecrire ("Les valeurs permutées sont : A=", valA, "et B=", valB)
Fin
```

| Ligne | valA | valB | pivot |
| ----- | ---- | ---- | ----- |
| 1     | null | null | null  |
| 2     | 10   | null | null  |
| 3     | 10   | null | null  |
| 4     | 10   | 5    | null  |
| 5     | 10   | 5    | 10    |
| 6     | 5    | 5    | 10    |
| 7     | 5    | 10   | 10    |

<a name="3---pizzas"></a>
### 3 - Pizzas

> Pour deux pizzas dont on donne un pris et un diamètre, déterminer quelle pizza est la plus _rentable_.

```txt
Algorithme: meilleurePizza
{Pour deux pizzas données, choisir la meilleure offre}

Constantes: PI : réel ← 3.14

Variables: pizADiam, pizAPx, pizARap, pizBDiam, pizBPrix pizBRap: rééls

Début:
    Ecrire ("Quel est le prix de la pizza A ?")
    Lire (pizAPx)
    Ecrire ("Quel est son diamètre ?")
    Lire (pizADiam)
    Ecrire ("Quel est le prix de la pizza B ?")
    Lire (pizBPx)
    Ecrire ("Quel est son diamètre ?")
    Lire (pizBDiam)
    #Comparaison surfaces/prix
    pizARap ← ((PI * (pizADiam/2) * (pizADiam/2)) / pizAPx)
    pizBRap ← ((PI * (pizBDiam/2) * (pizBDiam/2)) / pizBPx)
    Si ( pizARap > pizBRap ) Alors:
        Ecrire ("La pizza A est la plus intéressante")
    Sinon:
        Si ( pizARap < pizBRap ) Alors:
            Ecrire ("La pizza B est la plus intéressante")
        Sinon:
            Ecrire ("Les deux offres sont valables... Choisissez suivant vos goûts !")
        Finsi
    Finsi
Fin
```

<a name="4---reçu-avec-mention"></a>
### 4 - Reçu avec mention

> Affiche une mention suivant la note donnée :  "Reçu avec mention" si supérieure à 12, "Passable" si supérieure à 10 et "Insuffisant" dans les autres cas.

```txt
Algorithme: recuAvecMention
{Affiche la mention pour une note donnée}

Variables: note: réel

Début:
    Ecrire ("Qelle est la note ?")
    Lire (note)
    Si (note <= 10 ) Alors:
        Ecrire ("Insuffisant")
    Sinon:
        Si (note  < 12 ) Alors:
            Ecrire ("Passable")
        Sinon:
            Ecrire ("Reçu avec mention")
        Finsi
    Finsi
Fin
```

<a name="5---mmme"></a>
### 5 - M/Mme

> Ce programme doit retourner un _titre_ complet suivant le _titre abrégé_ donné :
>   - _Monseur_ pour _M_
>   - _Madame_ pour _Mme_
>   - _Mademoiselle_ pour _Mlle_
>   - _Madame, Monsieur_ pour les autres cas.
> 
> Réaliser des algorithmes utilisant les méthodes _Si_ et _Cas_.

<a name="avec-des-si"></a>
#### Avec des _Si_

```txt
Algorithme: mMme
{Affiche une particule suivant le titre donné}

Variables: titre : chaine

Début:
    Ecrire ("Quel est votre titre ?")
    Lire (titre)
    Si (titre = "M") Alors:
        Ecrire ("Monsieur")
    Sinon:
        Si (titre = "Mme") Alors:
            Ecrire ("Madame")
        Sinon
            Si (titre = "Mlle") Alors:
                Ecrire ("Mademoiselle")
            Sinon:
                Ecrire "Monsieur, Madame"
            Fsi
        Fsi
    Fsi
Fin
```

<a name="avec-cas"></a>
#### Avec _Cas_

```txt
Algorithme: mMme
{Affiche une particule suivant le titre donné}

Variables: titre : chaine

Début:
    Ecrire ("Quel est votre titre ?")
    Lire (titre)
    Cas titre:
        "M":
            Ecrire "Monsieur"
        "Mme":
            Ecrire "Madame"
        "Mlle":
            Ecrire "Mademoiselle"
        défaut:
            Ecrire "Madame, Monsieur"
    Fcas
Fin
```

<a name="6---exercice-sur-les-boucles"></a>
### 6 - Exercice sur les boucles

> Chaque année, une machine perd 10% de sa valeur d'achat. Calculer la valeur de la machine au bout de 5 ans

```txt
Algorithme: perteDeValeur
{Calcule la valeur d'une machine au bout de 5 ans.}

Constantes: NB_ANNEES : entier ← 5

Variables:
    valeur: réel
    compteur: entier

Début
    Ecrire ("Quelle est la valeur de la machine ?")
    Lire (valeur)
    Pour compteur ← 1 à NB_ANNEES par 1 faire:
        valeur ← valeur * 0.9
    FPour
    Ecrire ("Valeur après ", NB_ANNEES, " ans : ", valeur)
Fin
```

**Test pour une machine de valeur 100000**

  - Valeur initiale: 100 000
  - compteur=1: 90000
  - compteur=2: 81000
  - compteur=3: 72900
  - compteur=4: 65610
  - compteur=5: 59049

> Calculer le nombre d'années nécessaires pour que la machine perde la moitié de sa valeur.

```txt
Algorithme: moitieValeur
{Calcule le temps nécéssaire pour qu'une machine perde la moitié de sa valeur.}

Variables:
    valeurInit, valeurActuelle : réels
    compteur: int

Début
    compteur ← 0
    Ecrire ("Quelle est la valeur de la machine ?")
    Lire (valeur)
    valeurActuelle ← valeurInit
    Répéter:
        valeurActuelle ← 0.9 * valeurActuelle
        compteur ← compteur +1
    Tant que (valeurActuelle > (valeurInit/2))
    Ecrire ("Il faut ", compteur, " années pour que la machine perde la moitié de sa valeur")
Fin
```

<a name="7---secondes-en-jhms"></a>
### 7 - Secondes en J/H/M/S

> L'utilisateur entre une durée en secondes. Le programme doit afficher cette durée en jours/heures/minutes/secondes.

```txt
Algorithme: secondesVersJHMS
{Convertit des secondes en Jours/Heures/Minutes/Secondes}

Variables: 
    sInitiales, secondes, minutes, heures, jours, sMod, mMod, hMod, jMod: entier

Constantes:
    MINUTE ← 60
    HEURE ← 60*60
    JOUR ← 60*60*24 

Début
    Ecrire ("Nombre de secondes ?")
    Lire sInitiales
    
    # Calcul des jours
    jMod ← sInitiales % JOUR
    jours ← (sInitiales - jMod) / JOUR

    # Calcul des heures
    hMod ← jMod % HEURE
    heures ← (jMod - hMod) / HEURE

    # Calul des minutes
    mMod ← hMod % MINUTE
    minutes ← (hMod - mMod) / MINUTE

    # Secondes restantes
    secondes ← hMod

    Ecrire (sInitiales, " secondes = ", jours, "J, ", heures, "H ", minutes, "M ", secondes, "S")
Fin
```

<a name="8---tableaux"></a>
### 8 - Tableaux

> Faire un algorithme qui demande à l'utilisateur d'entrer 5 caractères dans un tableau. Le programme devra afficher cette liste en sens inverse.

```txt
Algorithme: inverseTableau

Tableaux:
    liste (5) en caractère

Variables: 
    compteur : entier

Début
    Pour compteur ← 1 à 5 par 1 faire:
        Ecrire("Quel est le caractère ", compteur, " ?")
        Lire( liste(compteur) )
    FPour
    
    # Affiche le contenu du tableau en partant du dernier caractère
    Pour compteur ← 5 à 1 par -1 faire:
        Ecrire ("Le caractère ", compteur, "est : ", liste( compteur ))
    FPour
Fin
```

<a name="9---valeur-max-dans-un-tableau"></a>
### 9 - Valeur max dans un tableau

> L'utilisateur entre 5 entiers dans un tableau, et l'algorithme affichera la valeur max contenue dans le tableau.

```txt
Algorithme: valeurMax

Tableaux:
    liste (5) en entier

Variables: 
    compteur, max: entiers

Début
    Pour compteur ← 1 à 5 par 1 faire:
        Ecrire("Entrez un nombre")
        Lire( liste(compteur) )
    FPour
    
    # Affectation de max à la valeur du premier élément du tableau
    max ← liste(1)
    # Recherche de la valeur max
    Pour compteur ← 2 à 5 par 1 faire:
        Si (liste(compteur) > max) Alors:
            max ← liste(compteur)
        Fsi
    FPour

    Ecrire ("La valeur max du tableau est ", max)
Fin
```

<a name="10---triage---recherche-du-minimum"></a>
### 10 - Triage - Recherche du minimum

> L'utilisateur va entrer 5 entiers dans un tableau et le programme devra les trier par ordre croissant

```txt
Algorithme: valeurMax
{Tri par recherche du minimum}

Tableaux:
    liste (5) en entier

Variables: 
    compteur1, compteur2, min, pivot, index: entiers

Début
    Pour compteur1 ← 1 à 5 par 1 faire:
        Ecrire("Entrez un nombre")
        Lire( liste(compteur1) )
    FPour
    
    # Recherche de la valeur max
    Pour compteur1 ← 1 à 4 par 1 faire:
        min ← liste(compteur1)
        Pour compteur2 ← (compteur1 + 1) à 5 par 1 faire:
            Si (liste(compteur2) < min) Alors:
                min ← liste(compteur2)
                index ← compteur2
            Fsi
        FPour
        # Permutation
        pivot ← liste(compteur1)
        liste(compteur1) ← liste(index)
        liste(index) ← pivot
        # Affichage
        
    FPour

    Pour compteur1 ← 1 à 5 par 1 faire:
        Ecrire (liste(compteur1), ", ")
    FPour
Fin
```

Exemple en JS:

```js
var liste=[3,9,7,12,4,5]

function tri(liste){
  console.log(liste.length)
    var min, i, j, pivot, index;
    for(i=0; i <= liste.lenght-1; i++){
        min=liste[i];
        index=i;
        for(j=i+1; j <= liste.lenght-1; j++){
            if(liste[j] < min){
                min=liste[j];
                index=j
            }
        }
        // Permutation
        pivot = liste[i];
        liste[i] = liste[index];
        liste[index] = pivot;
        console.log(liste[i]);
    }
    console.log(liste);
}

tri(liste);
```

<a name="11---triage---tri-à-bulle"></a>
### 11 - Triage - Tri à bulle

> L'utilisateur va entrer 5 entiers dans un tableau et le programme devra les trier par ordre croissant

```txt
Algorithme: valeurMax
{Tri à bulle}

Tableaux:
    liste (5) en entier

Variables: 
    compteur1, compteur2, pivot: entiers
    permutation: booleen

Début
    Pour compteur1 ← 1 à LG_TABLEAU par 1 faire:
        Ecrire("Entrez un nombre")
        Lire( liste(compteur1) )
    FPour
    
    compteur1 ← 1
    permutation ← Vrai
    Tant que (permutation = Vrai) faire:
        permutation ← Faux
        Pour compteur2 ← 1 à (5 - compteur1) par 1 faire:
            Si (liste(compteur1) > liste(compteur1 + 1)) Alors:
                pivot ← liste(compteur1)
                liste(compteur1) ← liste(compteur2)
                liste(compteur2) ← pivot
                permutation ← Vrai
            Fsi
        FPour
        compteur1 ← compteur1 + 1
    FTantQue

    Pour compteur1 ← 1 à 5 par 1 faire:
        Ecrire (liste(compteur1), ", ")
    FPour
Fin
```

<a name="12---puissances"></a>
### 12 - Puissances

> L'utilisateur entre un entier x et un entier n >= 0. Le programme affiche le résultat de x^n

```txt
Algorithme: Puissance
{Affiche la puissance d'un nombre}

Variables: 
    x, n, r, compteur : entier

Début
    Ecrire("Entrez x")
    Lire( x )

    Répéter:
        Ecrire("Entrez un entier n")
        Lire( n )
    Tant que (n < 0)

    r ← 1

    Pour compteur ← 1 à n par 1:
        r ← r * x
    FPour

    Ecrire (x, "^", n, " = ", r)
Fin
```

<a name="13---chute-libre"></a>
### 13 - Chute libre
> Soit un objet tombant d'une tour de hauteur _h_. On souhaite connaitre, toutes les _x_ secondes, la distance au sol de cet objet.
> La distance parcourue se calcule avec _G=9.80665_ et la formule suivante : d= 1.5 * gt^2

```txt
Algorithme: chute

Constante: GRAVITE : reel ← 9.80665

Variables: 
    h, x, d : réels
    iterations : entier

Début
    Ecrire("Entrez la hauteur de la tour")
    Lire( h )
    Ecrire("Entrez la durée en seconde entre deux calculs")
    Lire( x )

    iterations ← 1
    Répéter
        # Calcul de la chute
        d = 0.5 * GRAVITE * (iterations * x) * (iterations * x)
        Si ( d-h < 0 ) Alors:
            Ecrire ("Hauteur à l'instant ", (iterations * x), " : ", h - d)
        Fsi
        iterations ← iterations + 1
    Tant que d < h
    Ecrire ("Boum")
Fin
```

<a name="14---tonte-de-pelouse"></a>
### 14 - Tonte de pelouse

```txt
Algorithme: tonte

Constantes: PI : reel ← 3.14

Variables : longApp, longMais, largMais, longTer, largTer, rayPisc, totalBat, totalTer, vitesse: reels

Début
    Ecrire ("Quelle est la largeur de l'appenti ?") Lire longApp
    Ecrire ("Quelle est la largeur de la maison ?") Lire largMais
    Ecrire ("Quelle est la longueur de la maison ?") Lire longMais
    Ecrire ("Quelle est la largeur du terrain ?") Lire largTer
    Ecrire ("Quelle est la longueur du terrain ?") Lire longTer
    Ecrire ("Quelle est le rayon de la piscine ?") lire rayPisc
    Ecrire ("Quelle est la vitesse de tonte ?") lire vitesse

    # Calcul du total batiments:
    ## Appenti
    totalBat ← longApp * largMais / 2
    ## Maison
    totalBat ← totalBat + largMais + longMais
    ## Piscine
    totalBat ← totalBat + PI*rayPisc*rayPisc

    # Calcul total terrain
    totalTer ← largTer * longTer - totalBat

    Ecrire ("Il y a un total de ", totalTer, "m2 de gazon.")
    Ecrire ("Il faudra ", totalTer / vitesse, "s  pour tondre le gazon")
Fin
```

<a name="15---tri-décroissant-par-recherche-du-minimum"></a>
### 15 - Tri décroissant par recherche du minimum

> Sur un tableau de 5 cellules, l'algorithme doit faire un tri décroissant par recherche du minimum.

```txt
Algorithme : triDecroissant

Tableau: liste(5) en entier

Variables: compteur1, compteur2, index, pivot, min : entier

Début
  Pour compteur1 de 1 à 5 par 1 Faire:
    Ecrire ("Quel est le nombre ?")
    Lire liste(compteur1)
  FPour

  # Tri
  Pour compteur1 ← 1 à 5 par 1 faire:
      min ← liste(compteur1)
      index ← compteur1
      Pour compteur2 ← (compteur1 + 1) à 5 par 1 faire:
          Si (liste(compteur2) < min) Alors:
              min ← liste(compteur2)
              index ← compteur2
          Fsi
      FPour
      # Permutation
      pivot ← liste(compteur1)
      liste(compteur1) ← liste(index)
      liste(index) ← pivot
  FPour

  # Affichage
  Pour compteur1 ← 1 à 5 par 1 faire:
      Ecrire (liste(compteur1), ", ")
  FPour
Fin
```

<a name="16---moyenne-dun-classe"></a>
### 16 - Moyenne d'un classe

> Ecrire un algorithme qui demande à l'utilisateur de rentrer le nombre d'élèves d'une classe, puis leurs notes, afin d'en faire un moyenne.

```txt
Algorithme : moyenneClasse

Tableau: notes en réel

Variables: 
  nbEleves, compteur : entiers
  moyenne, total : réel

Début
  total ← 0

  Ecrire ("Quel est le nombre d'élèves ?")
  Lire nbEleves

  redim notes (nbEleves)

  Pour compteur ← 1 à nbEleves par 1 Faire:
    Ecrire ("Quel est la note de l'élève ", compteur)
    Lire (liste(compteur))
  FPour

  # Moyenne
  Pour compteur ← 1 à nbEleves par 1 faire:
    total ← total + notes(compteur)
  FPour

  moyenne ← total/nbEleves

  # Affichage
  Ecrire ("La moyenne de la classe est ", moyenne)
Fin
```