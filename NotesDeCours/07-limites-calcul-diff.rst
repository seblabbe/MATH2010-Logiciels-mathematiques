Calcul différentiel et intégral
===============================

.. contents:: **Contenu**
   :local:

.. code:: pycon

    >>> from __future__ import division, print_function   # Python 3
    >>> from sympy import init_printing
    >>> init_printing(use_latex='mathjax',use_unicode=False)  # Affichage des résultats

Cette section concerne le calcul différentiel et intégral. 
On trouvera d'autres exemples dans le tutoriel de Sympy sur le même sujet:
http://docs.sympy.org/latest/tutorial/calculus.html

Limites
-------

Pour calculer la limite d'une ``expression`` lorsqu'une ``variable`` tend vers
une ``valeur``, on utilise la fonction ``limit`` de sympy avec la syntaxe
``limit(expression, variable, valeur)``. :

.. code:: pycon

    >>> from sympy import limit, sin, S
    >>> from sympy.abc import x

Par exemple, pour évaluer la limite lorsque ``x`` tend vers ``0`` de
l'expression `(\sin(x)-x)/x^3`, on écrit:

.. code:: pycon

    >>> limit((sin(x)-x)/x**3, x, 0)
    -1/6

La limite de `f(x)=2x+1` lorsque `x \to 5/2`:

.. code:: pycon

    >>> limit(2*x+1, x, S(5)/2)   # la fonction S permet de créer un nombre rationel
    6

Pour calculer la limite **à gauche** en un point, on doit spécifier l'option
``dir="-"``:

.. code:: pycon

    >>> limit(1/x, x, 0, dir="-")
    -oo

Pour calculer la limite **à droite** en un point, on doit spécifier l'option
``dir="+"``:

.. code:: pycon

    >>> limit(1/x, x, 0, dir="+")
    oo

Lorsque la direction n'est pas spécifiée, c'est la limite à droite
(``dir="+"``) qui est calculée par défaut:

.. code:: pycon

    >>> limit(1/x, x, 0)
    oo

En sympy, tout comme dans SageMath, le symbole ``oo`` représente l'infini
`\infty`. Les deux ``o`` collés resemblent au symbole de l'infini ``8`` à
l'horizontal. Les opérations d'addition, de soustraction, de multiplication,
etc. sont possibles avec l'infini ``oo`` tant qu'elle soient bien définies. On
doit l'importer pour l'utiliser:

.. code:: pycon

    >>> from sympy import oo
    >>> oo
    oo
    >>> 5 - oo
    -oo
    >>> oo - oo           # nan signifie "Not A Number"
    nan

On peut calculer la limite d'une expression lorsque ``x`` tend vers **plus
l'infini**:

.. code:: pycon

    >>> limit(1/x, x, oo)
    0

et aussi lorsque ``x`` tend vers **moins l'infini**:

.. code:: pycon

    >>> limit(4+x*exp(x), x, -oo)
    4

Sympy procède à des simplifications lorsque possible:

.. code:: pycon

    >>> limit((1+1/x)**x, x, oo)
    E

Sommes
------

En Python, il existe une fonction (``sum``) que l'on a pas besoin d'importer et
qui permet de calculer la somme des valeurs d'une liste:

.. code:: pycon

    >>> sum([1,2,3,4,5])
    15

Cette fonction ``sum`` permet aussi de calculer une somme impliquant des
variables et expressions symboliques de SymPy:

.. code:: pycon

    >>> from sympy import tan
    >>> from sympy.abc import x,z
    >>> sum([1,2,3,4,5,x,tan(z)])
    x + tan(z) + 15

Par contre, ``sum`` ne permet pas de calculer des sommes infinies ou encore des
séries données par un terme général. En SymPy, il existe une autre fonction
(``summation``) pour calculer des sommes possiblement infinies d'expressions
symboliques:

.. code:: pycon

    >>> from sympy import summation

Pour calculer la somme d'une série dont le terme général est donné par une
``expression`` qui dépend de ``n`` pour toutes les valeurs entières de ``n``
entre ``debut`` et ``fin`` (``debut`` et ``fin`` inclus), on utilise la syntaxe
``summation(expression (n,debut,fin))``:

.. code:: pycon

    >>> from sympy.abc import n
    >>> summation(n, (n,1,5))
    15

Le début et la fin de l'intervalle des valeurs de ``n`` peut être donné par des
variables symboliques:

.. code:: pycon

    >>> from sympy.abc import a,b
    >>> summation(n, (n,1,b))
     2
    b    b
    -- + -
    2    2
    >>> summation(n, (n,a,b))
       2        2
      a    a   b    b
    - -- + - + -- + -
      2    2   2    2

Pour faire la somme d'une série pour tous les nombres entiers de 1 à l'infini,
on utilise le symbole ``oo``:

.. code:: pycon

    >>> from sympy import oo
    >>> summation(1/n**2, (n, 1, oo))
      2
    pi
    ---
     6

Si la série est divergente, elle sera évaluée à ``oo`` ou encore elle restera
non évaluée:

.. code:: pycon

    >>> summation(n, (n,1,oo))
    oo
    >>> summation((-1)**n, (n,1,oo))
      oo
     ___
     \  `
      \       n
      /   (-1)
     /__,
    n = 1

Sympy peut aussi calculer une double somme. Il suffit de spéficier l'intervalle
des valeurs pour chacune des variables en terminant avec la variable dont la
somme est effectuée en dernier:

.. code:: pycon

    >>> from sympy.abc import m,n
    >>> summation(n*m, (n,1,m), (m,1,10))
    1705

Les doubles sommes fonctionnent aussi avec des intervalles infinis:

.. code:: pycon

    >>> summation(1/(n*m)**2, (n,1,oo), (m,1,oo))
      4
    pi
    ---
     36

Produit
-------

Comme pour la somme, le calcul d'un produit dont le terme général est donné par
une ``expression`` qui dépend de ``n`` pour toutes les valeurs entières de
``n`` entre ``debut`` et ``fin`` (``debut`` et ``fin`` inclus), on utilise la
syntaxe ``product(expression (n,debut,fin))``:

.. code:: pycon

    >>> from sympy import product
    >>> from sympy.abc import n,b
    >>> product(n, (n,1,5))
    120
    >>> product(n, (n,1,b))
    b!

Voici un autre exemple:

.. code:: pycon

    >>> product(n*(n+1), (n, 1, b))
    RisingFactorial(2, b)*b!

Calcul différentiel
-------------------

Pour dériver une ``fonction`` par rapport à une variable ``x``, on utilise la
fonction ``diff`` de sympy avec la syntaxe ``diff(fonction, x)``:

.. code:: pycon

    >>> from sympy import diff

Faisons quelques importations de fonctions et variables pour la suite:

.. code:: pycon

    >>> from sympy import sin,cos,tan,atan,pi
    >>> from sympy.abc import x,y

On calcule la dérivée de `\sin(x)`:

.. code:: pycon

    >>> diff(sin(x), x)
    cos(x)

Voici quelques autres exemples:

.. code:: pycon

    >>> diff(cos(x**3), x)
        2    / 3\
    -3*x *sin\x /
    >>> diff(atan(2*x), x)
       2
    --------
       2
    4*x  + 1
    >>> diff(1/tan(x), x)
         2
    - tan (x) - 1
    -------------
          2
       tan (x)

Pour calculer la i-ème dérivée d'une fonction, on ajoute autant de variables
que nécessaire ou bien on spécifie le nombre de dérivées à faire:

.. code:: pycon

    >>> diff(sin(x), x, x, x)
    -cos(x)
    >>> diff(sin(x), x, 3)
    -cos(x)

Cela fonctionne aussi avec des variables différentes:

.. code:: pycon

    >>> diff(x**2*y**3, x, y, y)
    12*x*y

Calcul intégral
---------------

Le calcul d'une intégrale indéfinie se fait avec la fonction ``integrate`` avec
la syntaxe ``integrate(f, x)``:

.. code:: pycon

    >>> from sympy import integrate

Par exemple:

.. code:: pycon

    >>> integrate(1/x, x)
    log(x)

Le calcul d'une intégrale définie se fait aussi avec la fonction
``integrate`` avec la syntaxe ``integrate(f, (x, a, b))``:

.. code:: pycon

    >>> integrate(1/x, (x, 1, 57))
    log(57)

Voici quelques autres exemples:

.. code:: pycon

    >>> from sympy import exp
    >>> integrate(cos(x)*exp(x), x)
     x           x
    e *sin(x)   e *cos(x)
    --------- + ---------
        2           2

.. code:: pycon

    >>> integrate(x**2, (x,0,1))
    1/3

L'intégrale d'une fonction rationnelle:

.. code:: pycon

    >>> integrate((x+1)/(x**2+4*x+4), x)
                   1
    log(x + 2) + -----
                 x + 2

L'intégrale d'une fonction exponentielle polynomiale:

.. code:: pycon

    >>> integrate(5*x**2 * exp(x) * sin(x), x)
       2  x             2  x                             x             x
    5*x *e *sin(x)   5*x *e *cos(x)        x          5*e *sin(x)   5*e *cos(x)
    -------------- - -------------- + 5*x*e *cos(x) - ----------- - -----------
          2                2                               2             2

Deux intégrales non élémentaires:

.. code:: pycon

    >>> from sympy import erf
    >>> integrate(exp(-x**2)*erf(x), x)
      ____    2
    \/ pi *erf (x)
    --------------
          4

Calculer l'intégrale de `x^2 \cos(x)` par rapport à `x`:

.. code:: pycon

    >>> integrate(x**2 * cos(x), x)
     2
    x *sin(x) + 2*x*cos(x) - 2*sin(x)

Calculer l'intégrale définie de `x^2 \cos(x)` par rapport à `x` sur
l'intervalle de `0` à `\pi/2`:

.. code:: pycon

    >>> integrate(x**2 * cos(x), (x, 0, pi/2))
           2
         pi
    -2 + ---
          4

Sommes, produits, dérivées et intégrales non évaluées
-----------------------------------------------------

Les fonctions ``summation``, ``product``, ``diff`` et ``integrate`` ont tous un
équivalent qui retourne un résultat non évalué. Elles s'utilisent avec la même
syntaxe, mais portent un autre nom et commencent avec une majuscule: ``Sum``,
``Product``, ``Derivative``, ``Integral``.

.. code:: pycon

    >>> from sympy import Sum, Product, Derivative, Integral, sin, oo
    >>> from sympy.abc import n, x
    >>> Sum(1/n**2, (n, 1, oo))
      oo
    ____
    \   `
     \    1
      \   --
      /    2
     /    n
    /___,
    n = 1
    >>> Product(n, (n,1,10))
      10
    _____
    |   | n
    |   |
    n = 1
    >>> Derivative(sin(x**2), x)
    d /   / 2\\
    --\sin\x //
    dx
    >>> Integral(1/x**2, (x,1,oo))
     oo
      /
     |
     |  1
     |  -- dx
     |   2
     |  x
     |
    /
    1

Pour les évaluer, on ajoute ``.doit()``:

.. code:: pycon

    >>> Sum(1/n**2, (n, 1, oo)).doit()
      2
    pi
    ---
     6
    >>> Product(n, (n,1,10)).doit()
    3628800
    >>> Derivative(sin(x**2), x).doit()
           / 2\
    2*x*cos\x /
    >>> Integral(1/x**2, (x,1,oo)).doit()
    1

Cela est utile pour écrire des équations:

.. code:: pycon

    >>> A = Sum(1/n**2, (n, 1, oo))
    >>> B = Product(n, (n,1,10))
    >>> C = Derivative(sin(x**2), x)
    >>> D = Integral(1/x**2, (x,1,oo))
    >>> from sympy import Eq
    >>> Eq(A, A.doit())
      oo
    ____
    \   `        2
     \    1    pi
      \   -- = ---
      /    2    6
     /    n
    /___,
    n = 1
    >>> Eq(B, B.doit())
      10
    _____
    |   | n = 3628800
    |   |
    n = 1
    >>> Eq(C, C.doit())
    d /   / 2\\          / 2\
    --\sin\x // = 2*x*cos\x /
    dx
    >>> Eq(D, D.doit())
     oo
      /
     |
     |  1
     |  -- dx = 1
     |   2
     |  x
     |
    /
    1

Intégrales multiples
--------------------

Pour faire une intégrale double, on peut intégrer le résultat d'une première
intégration comme ceci:

.. code:: pycon

    >>> from sympy.abc import x,y
    >>> integrate(integrate(x**2+y**2, x), y)
     3        3
    x *y   x*y
    ---- + ----
     3      3

Mais, il est plus commode d'utiliser une seule fois la commande ``integrate``
et sympy permet de le faire:

.. code:: pycon

    >>> integrate(x**2+y**2, x, y)
     3        3
    x *y   x*y
    ---- + ----
     3      3

Pour les intégrales définies multiples, on spécifie les intervalles pour chaque
variable entre parenthèses. Ici, on fait l'intégrale sur les valeurs de ``x``
dans l'intervalle ``[0,y]``, puis pour les valeurs de ``y`` dans l'intervalle
``[0,10]``:

.. code:: pycon

    >>> integrate(x**2+y**2, (x,0,y), (y,0,10))
    10000/3

Développement en séries
-----------------------

On calcule la série de Taylor d'une ``expression`` qui dépend de ``x`` au point
``x0`` d'ordre ``n`` avec la syntaxe ``series(expression, x, x0, n)``. Par
exemple, la série de Maclaurin (une série de Maclaurin est une série de Taylor
au point `x_0=0`) de `\cos(x)` d'ordre 14 est:

.. code:: pycon

    >>> from sympy import series, cos
    >>> from sympy.abc import x
    >>> series(cos(x), x, 0, 14)
         2    4     6      8       10         12
        x    x     x      x       x          x         / 14\
    1 - -- + -- - --- + ----- - ------- + --------- + O\x  /
        2    24   720   40320   3628800   479001600

Par défaut, le développement est efféctuée en ``0`` et est d'ordre 6:

.. code:: pycon

    >>> series(cos(x), x)
         2    4
        x    x     / 6\
    1 - -- + -- + O\x /
        2    24

De façon équivalente, on peut aussi utilise la syntaxe ``expression.series(x,
x0, n)``:

.. code:: pycon

    >>> (1/cos(x**2)).series(x, 0, 14)
         4      8       12
        x    5*x    61*x      / 14\
    1 + -- + ---- + ------ + O\x  /
        2     24     720

Le développement de Taylor de `\log` se fait en `x_0=1`:

.. code:: pycon

    >>> from sympy import log
    >>> series(log(x), x, 0)
    log(x)
    >>> series(log(x), x, 1)
                2          3          4          5
         (x - 1)    (x - 1)    (x - 1)    (x - 1)         /       6        \
    -1 - -------- + -------- - -------- + -------- + x + O\(x - 1) ; x -> 1/
            2          3          4          5

Équations différentielles
-------------------------

Une équation différentielle est une relation entre une fonction inconnue et ses
dérivées. Comme la fonction est inconnue, on doit la définir de façon abstraite
comme ceci:

.. code:: pycon

    >>> from sympy import Function
    >>> f = Function("f")

Déjà, cela permet d'écrire ``f`` et ``f(x)``:

.. code:: pycon

    >>> f
    f
    >>> from sympy.abc import x
    >>> f(x)
    f(x)

On peut définir les dérivées de ``f`` à l'aide de la fonction ``Derivative`` de
sympy:

.. code:: pycon

    >>> from sympy import Derivative
    >>> Derivative(f(x), x)             # ordre 1
    d
    --(f(x))
    dx
    >>> Derivative(f(x), x, x)          # ordre 2
      2
     d
    ---(f(x))
      2
    dx

En utilisant, ``Eq`` on peut définir une équation impliquant la fonction f et
ses dérivées, c'est-à-dire une équation différentielle:

.. code:: pycon

    >>> Eq(f(x), Derivative(f(x),x))
           d
    f(x) = --(f(x))
           dx

Puis, on peut la résoudre avec la fonction ``dsolve`` de sympy avec la syntaxe
``dsolve(equation, f(x))`` et trouver quelle fonction ``f(x)`` est égale à sa
propre dérivée:

.. code:: pycon

    >>> from sympy import dsolve
    >>> dsolve(Eq(f(x), Derivative(f(x),x)), f(x))
               x
    f(x) = C1*e

Voici un autre exemple qui trouve une fonction égale à l'opposé de sa dérivée
d'ordre 2:

.. code:: pycon

    >>> Eq(f(x), -Derivative(f(x),x,x))
               2
              d
    f(x) = - ---(f(x))
               2
             dx
    >>> dsolve(Eq(f(x), -Derivative(f(x),x,x)), f(x))
    f(x) = C1*sin(x) + C2*cos(x)

Résoudre une équation différentielle ordinaire comme `f''(x) + 9 f(x) = 1` :

.. code:: pycon

    >>> dsolve(Eq(Derivative(f(x),x,x) + 9*f(x), 1), f(x))
    f(x) = C1*sin(3*x) + C2*cos(3*x) + 1/9

Pour définir la dérivée, on peut aussi utiliser ``.diff()``. L'exemple
précédent s'écrit:

.. code:: pycon

    >>> dsolve(Eq(f(x).diff(x, x) + 9*f(x), 1), f(x))
    f(x) = C1*sin(3*x) + C2*cos(3*x) + 1/9

Finalement, voici un exemple impliquant deux équations:

.. code:: pycon

    >>> from sympy.abc import x,y,t
    >>> eq1 = Eq(Derivative(x(t),t), x(t)*y(t)*sin(t))
    >>> eq2 = Eq(Derivative(y(t),t), y(t)**2*sin(t))
    >>> systeme = [eq1, eq2]
    >>> systeme
     d                            d           2
    [--(x(t)) = x(t)*y(t)*sin(t), --(y(t)) = y (t)*sin(t)]
     dt                           dt
    >>> dsolve(systeme)
                       C1
                     -e                     -1
    set([x(t) = ---------------, y(t) = -----------])
                    C1                  C1 - cos(t)
                C2*e   - cos(t)

