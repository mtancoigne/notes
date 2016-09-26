# Algo / C

<!-- MarkdownTOC -->

- [Structure de fichier](#structure-de-fichier)
- [Types de variables](#types-de-variables)
  - [Structures](#structures)
- [Opérateurs de comparaisons](#opérateurs-de-comparaisons)
- [Structures conditionnelles](#structures-conditionnelles)
  - [Si](#si)
  - [Cas](#cas)
- [Structures itératives](#structures-itératives)
  - [Pour](#pour)
  - [Tant que... faire](#tant-que-faire)
  - [Faire... tant que](#faire-tant-que)
- [Tableaux](#tableaux)
- [Incrémentation de variables](#incrémentation-de-variables)
- [Entrées/Sorties](#entréessorties)

<!-- /MarkdownTOC -->


<a name="structure-de-fichier"></a>
## Structure de fichier
```c
// Librairies inclues avant compilation
#include <librairie1>
#include <librairie2>

// Début du programme: fonction qui sera lancée lors de l'exécution
int main()
{
    // <code>

    // Code de retours
    return 0
}
```
<a name="types-de-variables"></a>
## Types de variables

  - __Entier__ : integer, _int_
  - Flottants : float, _float_
  - Caractère : character, _char _
  - Tableaux(longueur) en type : <type> <nomVar>[<taille>]. A noter que les tableaux __ne peut pas__ avoir de longueur inconnue.

<a name="structures"></a>
### Structures

<a name="opérateurs-de-comparaisons"></a>
## Opérateurs de comparaisons
Comparatif des opérateurs de comparaison :

| Opérateur         | Algo | C    |
|-------------------|------|------|
| inférieur à       | `<`  | `<`  |
| supérieur         | `>`  | `<`  |
| supérieur ou égal | `≥`  | `>=` |
| inférieur ou égal | `≤`  | `<=` |
| différent         | `≠`  | `!=` |
| égal              | `=`  | `==` |
| affectation       | `←`  | `=`  |
| et                | `ET` | `&&` |
| ou                | `OU` | `||` |

<a name="structures-conditionnelles"></a>
## Structures conditionnelles

<a name="si"></a>
### Si

```c
#include <stdio.h>
#include <stdlib.h>

int main()
{
    int var = 5;

    if(var>0){ // Si
        printf("positif");
    }else if( var < 0 ){ // Sinon si
        printf("positif");
    }else{ // Sinon
        printf("nul");
    } // Finsi

    return 0;
}
```

<a name="cas"></a>
### Cas

```c
#include <stdio.h>
#include <stdlib.h>

int main()
{
    int var = 5;

    switch (var){ // Cas <var>
        case 1: // <val>:
            printf("un"); // <instructions>
            break; // Ne pas oublier le break pour sortir du switch
        case 2:
            printf("deux");
            break;
        default:
            printf("?"); // Pas besoin de break: dernier cas.
    }

    return 0;
}
```

<a name="structures-itératives"></a>
## Structures itératives

<a name="pour"></a>
### Pour

```c
#include <stdio.h>
#include <stdlib.h>

int main()
{
    int i;

    for(i=1; i<6; i++){ // Pour i ← 1 à 6 par 1 Faire
        printf("ligne %d\n", i);
    } // Finpour

    return 0;
}
```

<a name="tant-que-faire"></a>
### Tant que... faire

```c
#include <stdio.h>
#include <stdlib.h>

int main()
{
    int i=0;

    while(i < 3 ){ // Tant que ... Faire...
        i++;
        printf("%d\n"); 
    } //FTantQue
    /*
    Affichera :
    1
    2
    3
    */
    return 0;
}
```

<a name="faire-tant-que"></a>
### Faire... tant que

```c
#include <stdio.h>
#include <stdlib.h>

int main()
{
    int i=3;

    do{ // Faire ...
        i++;
        printf("%d\n"); 
    }while(i < 3 ) // Tant que...
    // Affichera 4

    return 0;
}
```

<a name="tableaux"></a>
## Tableaux
A la différence de l'algo, le premier indice d'un tableau est `0`. De plus, un tableau __ne peut pas__ avoir de longueur inconnue.
```c
#include <stdio.h>
#include <stdlib.h>

int main()
{
    int tab[5], i;

    for(i=0; i<5; i++){
        tab[i]=i+1;
    }
    for(i=0; i<5; i++){
        printf("%d ", tab[i]);
    }
    return 0;
}
```

Un tableau peut être initialisé avec des valeurs: 
```c
int tab[5]={1,2,3,4,5};
```

Pour créer un tableau avec une taille définie par l'utilisateur, on le déclarera une fois qu'on connaît la taille:

```c
#include <stdio.h>
#include <stdlib.h>

int main()
{
    int taille, i;

    // Définition de la taille
    printf("Taille du tableau ?");
    scanf("%d", &taille);

    // Déclaration du tableau
    int tab[taille];

    for(i=0; i<taille; i++){
        tab[i]=i+1;
    }
    for(i=0; i<taille; i++){
        printf("%d ", tab[i]);
    }
    return 0;
}
```

<a name="incrémentation-de-variables"></a>
## Incrémentation de variables

```c
// Addition
i = i + 1;
i++; // l'incrémentation se fait après l'exécution de la ligne
++i; 
i+=1;

// Soustraction:
i = i - 1;
i--; // l'incrémentation se fait après l'exécution de la ligne
--i; 
i+ - =1;
```

<a name="entréessorties"></a>
## Entrées/Sorties

```c
#include <stdio.h>
#include <stdlib.h>

int main()
{
    int var1, var2, resultat;

    // Sortie : printf(sortie, [valeur1, valeur1, valeurN])
    printf("Entrez un nombre :\n");
    // 
    scanf("%d", &var1);
    printf("Entrez un nombre :\n");
    scanf("%d", &var2);

    resultat = var1 + var2;
    printf("\nLa somme de %d et %d est %d", var1, var2, resultat);

    return 0;
}
```

**Note : ** Pour récupérer un caractère en entrée (type _char_), il est pratique d'utiliser `getchar()`.