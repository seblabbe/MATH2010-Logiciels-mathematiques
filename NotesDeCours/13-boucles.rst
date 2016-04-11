
Boucle ``for``
==============

Une boucle permet de faire des tâches répétitives sur un ordinateur avec un
moindre effort.

.. image:: images/bart_simpson.jpg
   :width: 7cm

::

    >>> for a in range(9):
    ...     print("I will not do anything bad ever again.")
    I will not do anything bad ever again.
    I will not do anything bad ever again.
    I will not do anything bad ever again.
    I will not do anything bad ever again.
    I will not do anything bad ever again.
    I will not do anything bad ever again.
    I will not do anything bad ever again.
    I will not do anything bad ever again.
    I will not do anything bad ever again.

Une boucle for permet aussi de parcourir les éléments d'une liste, une chaîne
de caractères ou en général de tout objet itérable::

    >>> for a in [1,2,3,4]:
    ...     print(a + 100)
    101
    102
    103
    104
    >>> for a in 'bonjour':
    ...     print('A' + a + 'Z')
    AbZ
    AoZ
    AnZ
    AjZ
    AoZ
    AuZ
    ArZ

En Python, une boucle ``for`` est identifiée par une ligne d'en-tête commançant
par ``for`` se terminant par un deux-points ``:`` et avec la syntaxe ``for TRUC
in MACHIN:``. La convention est de toujours utiliser 4 espaces pour indenter 
les lignes du bloc d'instructions qui appartient à la boucle::

    for i in liste:                       # ligne d'en-tête
        <ligne 1 du bloc d'instruction>
        <ligne 2 du bloc d'instruction>
        ...
        <ligne n du bloc d'instruction>
    <ligne exécutée après la boucle>

Calculer la somme des éléments d'une liste
------------------------------------------

L'exemple suivant illustre comment calculer la somme des éléments d'une liste
en utilisant une variable ``s`` initialisée à zéro avant la boucle::

    >>> L = [134, 13614, 73467, 1451, 134, 88]
    >>> s = 0
    >>> for a in L:
    ...     s = s + a
    >>> s
    88888
    >>> sum(L)
    88888

Un exemple avec Sympy
---------------------

Supposons que l'on désire factoriser le polynôme ``x**k-1`` pour toutes les
valeurs de ``k=1..9``. En SymPy, il est possible d'écrire onze fois le même
calcul où on change la valeur de l'exposant ``k`` à chaque fois::

    >>> from sympy import factor
    >>> from sympy.abc import x
    >>> factor(x**1-1)
    x - 1
    >>> factor(x**2-1)
    (x - 1)*(x + 1)
    >>> factor(x**3-1)
    (x - 1)*(x**2 + x + 1)
    >>> factor(x**4-1)
    (x - 1)*(x + 1)*(x**2 + 1)
    >>> factor(x**5-1)
    (x - 1)*(x**4 + x**3 + x**2 + x + 1)
    >>> factor(x**6-1)
    (x - 1)*(x + 1)*(x**2 - x + 1)*(x**2 + x + 1)
    >>> factor(x**7-1)
    (x - 1)*(x**6 + x**5 + x**4 + x**3 + x**2 + x + 1)
    >>> factor(x**8-1)
    (x - 1)*(x + 1)*(x**2 + 1)*(x**4 + 1)
    >>> factor(x**9-1)
    (x - 1)*(x**2 + x + 1)*(x**6 + x**3 + 1)

La boucle ``for`` permet répéter une action pour toutes les valeurs d'une
liste. En utilisant une boucle ``for``, l'exemple ci-haut peut se réécrire plus
facilement::

    >>> for k in range(1,12):
    ...     print(factor(x**k-1))
    x - 1
    (x - 1)*(x + 1)
    (x - 1)*(x**2 + x + 1)
    (x - 1)*(x + 1)*(x**2 + 1)
    (x - 1)*(x**4 + x**3 + x**2 + x + 1)
    (x - 1)*(x + 1)*(x**2 - x + 1)*(x**2 + x + 1)
    (x - 1)*(x**6 + x**5 + x**4 + x**3 + x**2 + x + 1)
    (x - 1)*(x + 1)*(x**2 + 1)*(x**4 + 1)
    (x - 1)*(x**2 + x + 1)*(x**6 + x**3 + 1)

Pour différencier les lignes, il est possible d'afficher plus d'informations::

    >>> from sympy import Eq
    >>> for k in range(2, 10):
    ...     expr = x**k-1
    ...     eq = Eq(expr, factor(expr))
    ...     print(eq)
    x**2 - 1 == (x - 1)*(x + 1)
    x**3 - 1 == (x - 1)*(x**2 + x + 1)
    x**4 - 1 == (x - 1)*(x + 1)*(x**2 + 1)
    x**5 - 1 == (x - 1)*(x**4 + x**3 + x**2 + x + 1)
    x**6 - 1 == (x - 1)*(x + 1)*(x**2 - x + 1)*(x**2 + x + 1)
    x**7 - 1 == (x - 1)*(x**6 + x**5 + x**4 + x**3 + x**2 + x + 1)
    x**8 - 1 == (x - 1)*(x + 1)*(x**2 + 1)*(x**4 + 1)
    x**9 - 1 == (x - 1)*(x**2 + x + 1)*(x**6 + x**3 + 1)

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

