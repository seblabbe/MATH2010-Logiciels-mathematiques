
Résolution d'équations
======================

Définir une équation
--------------------

La fonction ``Eq`` permet de définir une équation::

    >>> from sympy import Eq
    >>> from sympy.abc import x,y
    >>> Eq(x, 3)
    x == 3
    >>> Eq(x + y, 3)
    x + y == 3

Résoudre une équation
---------------------

La fonction ``solve`` permet de résoudre une équation::

    >>> from sympy import solve
    >>> solve(Eq(x, 3), x)
    [3]
    >>>  solve(Eq(x + y, 3), x)
    [-y + 3]

Dans le premier cas, indiquer la variable ``x`` n'est pas nécessaire::

    >>> solve(Eq(x, 3))
    [3]

Cela fonctionne aussi s'il y a plus d'une solution::

    >>> solve(Eq(x**2, 3))
    [-sqrt(3), sqrt(3)]

Résoudre un système d'équations
-------------------------------

La fonction ``solve`` permet aussi de résoudre un système d'équations. Par
exemple pour trouver deux variables ``x`` et ``y`` telle que leur somme vaut 47
et leur différence vaut 33::

    >>> eq1 = Eq(x + y, 47)
    >>> eq2 = Eq(x - y, 33)
    >>> [eq1, eq2]
    [x + y == 47, x - y == 33]
    >>> solve([eq1, eq2])
    {x: 40, y: 7}

**Attention**: Pour résoudre un système d'équations, il faut absoluement mettre
les équations dans une liste ``[eq1, eq2]`` entre crochets ``[]``. Autrement,
on obtient une erreur::

    In [279]: solve(eq1, eq2)
    Traceback (most recent call last):
    ...
    TypeError: cannot determine truth value of
    x - y == 33

Cela fonctionne aussi pour des systèmes d'équations non linéaires. Par exemple
pour trouver deux nombres dont la somme est 47 et dont le produit est 510::

    >>> eq1 = Eq(x + y, 47)
    >>> eq2 = Eq(x * y, 510)
    >>> [eq1, eq2]
    [x + y == 47, x*y == 510]
    >>> solve([eq1, eq2])
    [{x: 17, y: 30}, {x: 30, y: 17}]

Syntaxe abrégée
---------------

Souvent on désire résoudre des équations dont l'un des termes est zéro:
``solve(Eq(expression,0))``. Pour ce cas, il est équivalent d'écrire
``solve(expression)`` et la fonction ``solve`` trouvera les valeurs des
variables avec lesquelles expression est évaluée à zéro. Les exemples ci-haut
s'écrivent de la façon suivante avec cette syntaxe abrégée::

    >>> solve(x - 3)
    [3]
    >>> solve(x**2 + x - 6)
    [-3, 2]
    >>> solve([x + y - 47, x - y - 33])
    {x: 40, y: 7}
    >>> solve([x + y - 47, x * y - 510])
    [{x: 17, y: 30}, {x: 30, y: 17}]

Un exemple sur un polynôme de degré 3::

    >>> solve(x**3 + 2*x**2 - 1, x)
                 ___      ___     
           1   \/ 5     \/ 5    1 
    [-1, - - + -----, - ----- - -]
           2     2        2     2 

La syntaxe abrégée peut aussi être utilisée pour résoudre un système
d'équations. Dans l'exemple qui suit, on calcule les points d'intersection
d'une ellipse et d'une droite::

    >>> solve( [x**2 + 4*y**2 -2, -10*x + 2*y -15], [x, y])

                ____              ____                ____              ____
        150   \/ 23 *I   15   5*\/ 23 *I      150   \/ 23 *I   15   5*\/ 23 *I
    [(- --- - --------, --- - ----------), (- --- + --------, --- + ----------)]
        101     101     202      101          101     101     202      101

Trouver les racines d'une fonction
----------------------------------

La fonction ``roots`` permet de calculer les racines d'une fonction polynomiale
univariée ::

    >>> from sympy import roots
    >>> roots(x - 7)
    {7: 1}
    >>> roots(x**6)
    {0: 6}

Le résultat est un dictionnaire (``{}``) qui associe à chaque racine sa
multiplicité. La fonction ``roots`` trouve aussi les racines complexes::

    >>> roots(x**5 - 7*x**4 + 2*x**3 - 14*x**2 + x - 7, x)
    {7: 1, -I: 2, I: 2}

Les coefficients des polynômes peuvent être des variables symboliques::

    >>> from sympy.abc import a,b,c
    >>> roots(a*x + b, x)
    {-b/a: 1}

Mais à ce moment-là, il faut absoluement spécifier par rapport à quelle
variable on cherche les racines. Autrement, on obtient une erreur::

    >>> roots(a*x + b)
    Traceback (most recent call last)
    ...
    PolynomialError: multivariate polynomials are not supported

La fonction ``roots`` trouve les formules qui expriment les racines d'un
polynôme quadratique::

    >>> roots(a*x**2 + b*x + c, x)
                _____________                _____________
               /           2                /           2
        b    \/  -4*a*c + b          b    \/  -4*a*c + b
    {- --- - ----------------: 1, - --- + ----------------: 1}
       2*a         2*a              2*a         2*a

On trouvera d'autres exemples (résolution d'équations différentielles) et des
explications plus détaillées dans la section `Solver` du tutoriel de SymPy:
http://docs.sympy.org/latest/tutorial/solvers.html

