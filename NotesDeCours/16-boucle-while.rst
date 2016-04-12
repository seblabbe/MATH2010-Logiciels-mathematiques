
Boucle ``while`` et interruption de boucle
==========================================

La boucle ``while``
-------------------

Parfois, on ne sait pas à l'avance combien de fois on voudra exécuter un bloc
d'instructions. Dans ce cas, il vaut mieux utiliser une boucle ``while`` dont
la syntaxe est::

    while CONDITION:
        INSTRUCTION 1
        INSTRUCTION 2
        ...
        INSTRUCTION n

Le bloc d'instruction est exécuté tant que la condition est satisfaite. Par
exemple, on peut afficher les puissances de 5 inférieures à un million avec une
boucle ``while``::

    >>> a = 1
    >>> while a < 1000000:
    ...     print a
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

Interrompre une boucle avec ``break``
-------------------------------------

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

Continuer une boucle à l'itération suivante avec ``continue``
-------------------------------------------------------------

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

