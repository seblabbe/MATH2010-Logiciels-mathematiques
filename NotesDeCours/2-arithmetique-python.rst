
Calculatrice et arithmétique avec Python
========================================

Dans cette section, nous assumons que la version de Python est la version 3.

Opérations de base en Python
----------------------------

Les opérations de base (addition, soustraction, multiplication, division) sur
les nombres se font avec les opérateurs ``+``, ``-``, ``*`` et ``/``::

    >>> 13.14 + 1.2
    14.34
    >>> 14.34 - 1.2
    13.14
    >>> 6 * 9
    54
    >>> 54 / 9
    6.0

La division d'un nombre par zéro retourne une erreur::

    >>> 53 / 0
    Traceback (most recent call last):
    ...
    ZeroDivisionError: division by zero

Exposant
--------

Le calcul d'une puissance se fait avec la double astérisque ``**``::

    >>> 2 ** 8
    256

.. ATTENTION:: 

    En Python, l'opérateur ``^`` ne calcule pas l'exposant, mais fait plutôt
    une opération sur la représentation binaire des nombres entiers (ou
    exclusif bit à bit)::

        >>> 5 ^ 3
        6

Racine n-ième
-------------

Le calcul d'une puissance permet aussi de calculer la racine n-ième d'un
nombre::

    >>> 256 ** (1 / 8)
    2.0

Reste et quotient de la division
--------------------------------

Le *reste* de la division d'un nombre entier par un autre se fait avec le
symbole ``%``. Par exemple, on calcule le reste de la division du nombre 94 par
10::

    >>> 94 % 10
    4

L'opération ``a//b`` lorsque ``a`` et ``b`` sont des nombres entiers retourne
le *quotient* de la divsion ``a`` par ``b``::

    >>> 94 // 10
    9

Fonctions et constantes mathématiques en Python
-----------------------------------------------

Le module ``math`` de Python contient un certain nombre de fonctions et
constantes mathématiques que l'on retrouve sur une calculatrice::

    acos       atanh      e          factorial  hypot      log10      sin
    acosh      ceil       erf        floor      isinf      log1p      sinh
    asin       copysign   erfc       fmod       isnan      modf       sqrt
    asinh      cos        exp        frexp      ldexp      pi         tan
    atan       cosh       expm1      fsum       lgamma     pow        tanh
    atan2      degrees    fabs       gamma      log        radians    trunc

On trouvera leur documentation sur
https://docs.python.org/library/math.html

Pour importer ``quelquechose`` de ce module, il faut d'abord l'importer avec la
syntaxe ``from math import quelquechose``. Par exemple, pour importer la
fonction ``factorial``, on procède de la façon suivante::

    >>> from math import factorial
    >>> factorial(4)
    24

Alternativement, on peut aussi importer le module ``math`` et procéder ainsi::

    >>> import math
    >>> math.factorial(4)
    24

De même pour les fonctions trigonométriques, on les importe de la façon
suivante::

    >>> from math import sin, cos, tan, pi

Pour importer toutes les fonctions d'un ``module``, il suffit d'écire ``from
module import *``. Par exemple, pour importer toutes les fonctions du module
``math``, on écrit::

    >>> from math import *

On vérifie que le sinus d'un angle de 90 degrés est bien égal à 1::

    >>> sin(90)
    0.8939966636005579

Oups, l'argument doit être écrit est en radians (90 degrés est égal à `\pi/2`
radians) et on obtient bien 1::

    >>> sin(pi/2)
    1.0

La constante `\pi` du module ``math`` retourne une valeur
approchée à une quinzaine de décimales::

    >>> pi
    3.141592653589793

Les fonctions ``degrees`` et ``radians`` permettent de passer d'une unité
d'angle à l'autre::

    >>> from math import degrees, radians
    >>> degrees(pi)
    180.0
    >>> radians(180)
    3.141592653589793

Extraction de la racine carrée avec la fonction ``sqrt``::

    >>> from math import sqrt
    >>> sqrt(100)
    10.0

Calcul des racines du polynôme ``3x**2 + 7x + 2``::

    >>> from math import sqrt
    >>> (- 7 + sqrt(7**2 - 4 * 3 * 2) ) / (2 * 3)
    -0.3333333333333333
    >>> (- 7 - sqrt(7**2 - 4 * 3 * 2) ) / (2 * 3)
    -2.0

Accéder à la documentation d'une fonction
-----------------------------------------

En Python, pour obtenir de l'information sur une ``fonction``, on peut écrire
``help(fonction)``. Par exemple, si on ne sait pas à quoi peut bien servir la
fonction ``hypot``::

    >>> from math import hypot
    >>> help(hypot)
    Help on built-in function hypot in module math:
    hypot(...)
        hypot(x, y)
        Return the Euclidean distance, sqrt(x*x + y*y).

En IPython, on peut consulter la documentation d'une fonction en ajoutant un
point d'interrogation avant ou après le nom de la fonction. Cela fonctionne
aussi dans l'interface Jupiter, ce qui ouvre une fenêtre au bas de la page::

    >>> ?hypot
    Docstring:
    hypot(x, y)
    Return the Euclidean distance, sqrt(x*x + y*y).
    Type:      builtin_function_or_method

    >>> hypot?
    Docstring:
    hypot(x, y)
    Return the Euclidean distance, sqrt(x*x + y*y).
    Type:      builtin_function_or_method

Parenthèses et priorité des opérations
--------------------------------------

Les parenthèses permettent d'indiquer dans quelle ordre faire les opérations
dans un calcul::

    >>> 3 * (5 + 2)        # l'addition est calculée en premier
    21
    >>> (3 * 5) + 2        # la multiplication est calculée en premier
    17

Sans les parenthèses, l'expression est évaluée selon l'ordre de priorité des
opérations. En particulier, le comportement par défaut est que la
multiplication est évaluée avant l'addition::

    >>> 3 * 5 + 2          # la multiplication est calculée en premier
    17

En général, les expressions non parenthésées utilisant les opérations de base
sont évaluées en tenant compte de l'ordre décrit dans la table ci-bas. 

.. csv-table:: Ordre de priorité des opérations de base (de la plus grande à la plus petite)
   :header: Opération, Description
   :widths: 4,10

   ``**``,                         "Élévation à la puissance"
   ``~ + -``,                      "Complément, le plus et le moins unaire"
   ``* / % //``,                   "Multiplication, division, modulo et la division entière"
   ``+ -``,                        "Addition et soustraction"

.. ``>> <<``,                      "Right and left bitwise shift"
   ``&``,                          "Le ET bit à bit"
   ``^ |``,                        "Le OU exclusif bit à bit et le OU régulier"
   ``<= < > >=``,                  "Opérations de comparaison"
   ``<> == !=``,                   "Opérations d'égalité"
   ``= %= /= //= -= += *= **=``,   "Opérations d'assignation"
   ``is is not``,                  "Opérations d'identité"
   ``in not in``,                  "Opérations d'appartenance"
   ``not or and``,                 "Opérations logiques"

Variables et affectation
------------------------

Supposons que l'on veut évaluer le polynôme
``3*x**4 + 7*x**3 - 3*x**2 + x - 5`` lorsque ``x=1234567``. On peut
procéder de la façon suivante::

    >>> 3 * 1234567**4 + 7 * 1234567**3 - 3 * 123467**2 + 1234567 - 5
    6969164759371928046905499

Cela nous oblige à écrire quatre fois le nombre ``1234567`` et on peut éviter cela au moyen d'une variable.

Une variable permet de mémoriser un nombre pour le réutiliser
plus tard. Par exemple, on peut mémoriser le nombre ``1234567``
dans la variable ``x``::

    >>> x = 1234567

Le symbole ``=`` ne doit pas être vu comme une équation à
résoudre, mais plutôt comme une *affectation* de la valeur
``1234567`` dans la variable ``x``. On peut demander la valeur
de ``x``::

    >>> x
    1234567

Cela nous permet de faire des calculs avec ``x``::

    >>> x + 1
    1234568

Finalement, on peut utiliser la variable ``x`` pour évaluer le
polynôme au point ``x=1234567``::

    >>> 3*x**4 + 7*x**3 - 3*x**2 + x - 5
    6969164759367401312173299

C'est curieux. On remarque que le résultat n'est pas le même que celui que l'on
avait calculé plus haut. Pourquoi? En effet, on s'était trompé en écrivant
``123467`` plutôt que ``1234567``. C'est aussi l'autre avantage d'utiliser une
variable: ça permet d'éviter de se tromper lorsqu'on doit utiliser la même
valeur plusieurs fois dans un calcul.

Ensuite, on peut changer la valeur de la variable ``x`` et
évaluer le même polynôme lorsque ``x`` prend une autre valeur::

    >>> x = 10
    >>> 3*x**4 + 7*x**3 - 3*x**2 + x - 5
    36705

Opérateurs de comparaison et d'égalités
---------------------------------------

Comme on l'a vu dans une section précédente, l'opérateur ``=`` est utilisé pour
l'affectation de variable. Pour tester l'égalité de deux expressions, on
utilise alors le l'opérateur ``==`` s'écrivant avec deux signes d'égalité::

    >>> 5 * 9 == 40 + 5
    True

La valeur retournée est un booléen: ``True`` pour vrai et ``False`` pour faux.
Si l'égalité n'est pas vérifiée, alors c'est la valeur ``False`` qui est
retournée::

    >>> 5 * 9 == 40 + 6
    False

Il existe d'autres opérateurs de comparaison dont la description se trouve dans
la table ci-bas.

.. csv-table:: Opérateurs de comparaison et d'égalité
   :header: Opérateur, Description
   :widths: 4,10

   ``<``, strictement inférieur
   ``>``, strictement supérieur
   ``<=``, inférieur ou égal
   ``>=``, supérieur ou égal
   ``==``, égal
   ``!=``, différent

Par exemple::

    >>> 5 * 9 < 1000
    True
    >>> 1 + 2 + 3 + 4 + 5 >= 15
    True
    >>> 2016 != 2016
    False
