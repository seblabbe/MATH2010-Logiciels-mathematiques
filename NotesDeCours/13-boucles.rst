
Boucle ``for``
==============

Une boucle permet de faire des tâches répétitives sur un ordinateur avec un
moindre effort. Supposons que l'on désire factoriser le polynôme ``x**k-1``
pour toutes les valeurs de ``k=1..11``. En SymPy, il est possible d'écrire onze
fois le même calcul où on change la valeur de l'exposant ``k`` à chaque fois::

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
    >>> factor(x**10-1)
    (x - 1)*(x + 1)*(x**4 - x**3 + x**2 - x + 1)*(x**4 + x**3 + x**2 + x + 1)
    >>> factor(x**11-1)
    (x - 1)*(x**10 + x**9 + x**8 + x**7 + x**6 + x**5 + x**4 + x**3 + x**2 + x + 1)

La boucle ``for`` permet répéter une action pour toutes les valeurs d'une
liste. En utilisant une boucle ``for``, l'exemple ci-haut peut se réécrire plus
facilement::

    >>> for k in range(1,12):
    ...     factor(x**k-1)
    x - 1
    (x - 1)*(x + 1)
    (x - 1)*(x**2 + x + 1)
    (x - 1)*(x + 1)*(x**2 + 1)
    (x - 1)*(x**4 + x**3 + x**2 + x + 1)
    (x - 1)*(x + 1)*(x**2 - x + 1)*(x**2 + x + 1)
    (x - 1)*(x**6 + x**5 + x**4 + x**3 + x**2 + x + 1)
    (x - 1)*(x + 1)*(x**2 + 1)*(x**4 + 1)
    (x - 1)*(x**2 + x + 1)*(x**6 + x**3 + 1)
    (x - 1)*(x + 1)*(x**4 - x**3 + x**2 - x + 1)*(x**4 + x**3 + x**2 + x + 1)
    (x - 1)*(x**10 + x**9 + x**8 + x**7 + x**6 + x**5 + x**4 + x**3 + x**2 + x + 1)

Pour différencier les lignes, il est possible d'afficher plus d'informations::

    >>> from sympy import Eq
    >>> for k in range(2, 12):
    ...     expr = x**k-1
    ...     Eq(expr, factor(expr))
    x**2 - 1 == (x - 1)*(x + 1)
    x**3 - 1 == (x - 1)*(x**2 + x + 1)
    x**4 - 1 == (x - 1)*(x + 1)*(x**2 + 1)
    x**5 - 1 == (x - 1)*(x**4 + x**3 + x**2 + x + 1)
    x**6 - 1 == (x - 1)*(x + 1)*(x**2 - x + 1)*(x**2 + x + 1)
    x**7 - 1 == (x - 1)*(x**6 + x**5 + x**4 + x**3 + x**2 + x + 1)
    x**8 - 1 == (x - 1)*(x + 1)*(x**2 + 1)*(x**4 + 1)
    x**9 - 1 == (x - 1)*(x**2 + x + 1)*(x**6 + x**3 + 1)
    x**10 - 1 == (x - 1)*(x + 1)*(x**4 - x**3 + x**2 - x + 1)*(x**4 + x**3 + x**2 + x + 1)
    x**11 - 1 == (x - 1)*(x**10 + x**9 + x**8 + x**7 + x**6 + x**5 + x**4 + x**3 + x**2 + x + 1)

En Python, la convention est de toujours utiliser 4 espaces pour indenter et
identifier les lignes qui appartiennent à la boucle::

    for i in liste:
        <ligne 1 de la boucle>
        <ligne 2 de la boucle>
        <ligne ...>
        <ligne n de la boucle>
    <ligne exécutée après la boucle>

L'exemple suivant illustre comment calculer la somme des éléments d'une liste
en utilisant une variable ``s`` initialisée à zéro avant la boucle::

    >>> L = range(10)
    >>> s = 0
    >>> for a in L:
    ...     s += a
    >>> s
    45

TODO: Bart Simpson Copy
