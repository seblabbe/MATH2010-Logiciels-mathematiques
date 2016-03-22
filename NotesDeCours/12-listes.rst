Listes
======

En Python, les listes sont beaucoup utilisées. Il est donc important de
connaîtres les différentes façons de créer, modifier et utiliser les listes.
Dans ce chapitre, nous allons voir les différentes opérations sur les listes.

Les listes sont créées avec l'utilisation des crochets et on peut mettre
n'importe quel objet dans une liste::

    >>> [2, 3, 4, 'bateau', 3.24]
    [2, 3, 4, 'bateau', 3.24]

On accède aux éléments de la liste de la même façon qu'avec les chaînes de
caractères, c'est-à-dire en utilisant les crochets et le premier élément est à
la position zéro::

    >>> L = [2, 3, 4, 'bateau', 3.24]
    >>> L[0]
    2
    >>> L[3]
    'bateau'

On peut modifier la liste en lui ajoutant des objets avec la méthode ``append``
de la façon suivante::

    >>> L.append(789)
    >>> L
    [2, 3, 4, 'bateau', 3.24, 789]

On vérifie que le dernier élément de la liste est bien le nombre entier
``789``::

    >>> L[-1]
    789

La fonction ``list`` permet de transformer un objet en liste pourvu qu'il soit
itérable::

    >>> list(w)
    ['b', 'o', 'n', 'j', 'o', 'u', 'r']

Plusieurs autres opérations sont possibles sur les listes. On peut consulter
l'aide ou la documentation pour en savoir plus::

    >>> L.<TAB>
    >>> help(list)

Opérations sur les listes
-------------------------

D'abord, créons une liste::

    >>> L = [1, 8, -4, 38, 8, 8, 4, 18]

Pour créer une sous-liste commençant à l'indice 2 jusqu'à l'indice 5-1=4::

    >>> L[2:5]
    [-4, 38, 8]

On peut créer une nouvelle liste avec
l'opération d'addition (``+``) qui concatène deux listes. Ceci ne change pas
les listes utilisées. Par exemple::

    >>> L + [1,2,3]
    [1, 8, -4, 38, 8, 8, 4, 18, 1, 2, 3]
    >>> L
    [1, 8, -4, 38, 8, 8, 4, 18]

La fonction ``len`` retourne la longueur d'une liste::

    >>> len(L)
    9

Les fonctions ``min`` et ``max`` retournent la valeur minimum et maximum d'une
liste::

    >>> min(L)
    -4
    >>> max(L)
    38

Pour savoir si une ``valeur`` est dans une ``liste``, on utilise ``valeur in
liste``. Cela retourne un booléen. Par exemple::

    >>> 77 in L
    False
    >>> 38 in L
    True

La méthode ``.count()`` permet de compter le nombre d'objets de la liste ayant
une certaine valeur::

    >>> L.count(38)
    1
    >>> L.count(8)
    3
    >>> L.count(77)
    0

La méthode ``.index()`` retourne la position (ou indice) où un élément se
retrouve dans la liste::

    >>> L
    [1, 8, -4, 38, 8, 8, 4, 18]
    >>> L.index(38)
    3

Modification de listes
----------------------

Pour ajouter un élément à la liste, on utilise la méthode ``.append()`` qui
ajoute un élément à la fin de la liste::

    >>> L
    [1, 8, -4, 38, 8, 8, 4, 18]
    >>> L.append(15)
    >>> L
    [1, 8, -4, 38, 8, 8, 4, 18, 15]

La méthode ``.remove()`` permet d'enlever un élément de la liste::

    >>> L.remove(4)
    >>> L
    [1, 8, -4, 38, 8, 8, 18, 15]

Si l'élément est là plus d'une fois, seule la première occurence de celle-ci
est retirée::

    >>> L.remove(8)
    >>> L
    [1, -4, 38, 8, 8, 18, 15]

La méthode ``.reverse()`` permet d'inverser l'ordre d'une liste::

    >>> L.reverse()
    >>> L
    [15, 18, 8, 8, 38, -4, 1]

La méthode ``.sort()`` permet de trier les éléments d'une liste en ordre croissant::

    >>> L.sort()
    >>> L
    [-4, 1, 8, 8, 15, 18, 38]

La fonction ``range``
---------------------

La fonction ``range(n)`` permet de créer la liste des entiers de ``0`` à
``n-1``::

    >>> range(15)
    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14]

Avec deux arguments, la fonction ``range(a, b)`` crée la liste des entiers de
``a`` à ``b-1``::

    >>> range(3, 15)
    [3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14]

Avec trois arguments, la fonction ``range(a, b, saut)`` crée la liste des
entiers de ``a`` à ``b-1`` par saut de ``saut``::

    >>> range(3,40,4)
    [3, 7, 11, 15, 19, 23, 27, 31, 35, 39]

Compréhension de listes
-----------------------

Soit la liste des entiers de zéro à neuf::

    >>> L = range(10)
    >>> L
    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

Les compréhensions de listes permettent de créer des listes facilement en une
ligne. La syntaxe ressemble à la syntaxe qui permet de décrire un ensemble
mathématique: ``[expression_de_i for i in liste]``.  Par exemple, l'ensemble des
cubes des valeurs de la liste ``L`` s'écrit::

    >>> [i**3 for i in L]
    [0, 1, 8, 27, 64, 125, 216, 343, 512, 729]

L'ensemble des cubes des valeurs impaires de la liste ``L`` se fait en ajoutant
une condition à la fin de l'expression::

    >>> [i**3 for i in L if i%2 == 1]
    [1, 27, 125, 343, 729]

