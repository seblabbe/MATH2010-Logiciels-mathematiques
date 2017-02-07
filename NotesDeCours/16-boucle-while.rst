
Boucle ``while``
================

.. contents:: **Contenu**
   :local:

::

    >>> from __future__ import division, print_function   # Python 3

Parfois, on ne sait pas à l'avance combien de fois on voudra exécuter un bloc
d'instructions. Dans ce cas, il vaut mieux utiliser une boucle ``while`` dont
la syntaxe est::

    while CONDITION:
        INSTRUCTION 1
        INSTRUCTION 2
        ...
        INSTRUCTION n

Le bloc d'instruction est exécuté (au complet) tant que la condition est
satisfaite. La condition est testée avant l'exécution du bloc, mais pas
pendant. C'est donc toutes les instructions du bloc qui sont exécutées si la
condition est vraie.  Par exemple, on peut afficher les puissances de 5
inférieures à un million avec une boucle ``while``::

    >>> a = 1
    >>> while a < 1000000:
    ...     print(a)
    ...     a = a * 5
    ... 
    1
    5
    25
    125
    625
    3125
    15625
    78125
    390625

L'exemple suivant est un autre exemple typique de la boucle tant que. Il
consiste à rechercher, pour un nombre `x\geq1`, l'unique valeur entière `n`
vérifiant `2^{n−1}< x < 2^n`, c’est-à-dire le plus petit entier vérifiant
`x < 2^n`.

::

    >>> x = 10**4
    >>> u = 1
    >>> n = 0
    >>> while u <= x:
    ...     n = n + 1
    ...     u = 2 * u
    >>> n
    14

On vérifie bien que `2^13 < 10^4 < 2^14`::

    >>> 2 ** 13
    8192
    >>> 2 ** 14
    16384
    >>> 2**13 < 10**4 < 2**14
    True

Interruptions de boucles avec ``break`` et ``continue`` 
-------------------------------------------------------

La commande ``break`` permet d'interrompre une boucle ``for`` ou ``while`` en
cours::

    >>> for i in range(10):
    ...     if i == 5:
    ...         break
    ...     print(i)
    ...
    0
    1
    2
    3
    4

On remarque que les valeurs plus grandes que 4 n'ont pas été imprimées par la
fonction ``print``.

La commande ``continue`` permet de continuer le parcours d'une boucle à la
valeur suivante::

    >>> for i in range(10):
    ...     if i == 5:
    ...         continue
    ...     print(i)
    ...
    0
    1
    2
    3
    4
    6
    7
    8
    9

On remarque que la valeur 5 n'a pas été imprimée par la fonction ``print``.

**NOTE**: Certains auteurs recommandent d'éviter l'utilisation des intructions
``continue`` et des ``break``, car elles sont évitables et leur utilisation
produit des programmes moins bien structurés.

