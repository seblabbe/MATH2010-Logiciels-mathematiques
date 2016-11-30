
Calculatrice et arithmétique avec SymPy
=======================================

SymPy__ est une librairie Python de mathématiques symboliques et un outil de
calcul formel. SymPy offre un ensemble riche de fonctions documentées qui
facilite la modélisation de problèmes mathématiques (arithmétique, calcul
symbolique, résolution d'équations, recherche de racines, dessin de fonctions,
limites et séries, calcul différentiel et intégral, algèbre linéaire). La
librairie offre aussi des fonctionalités de mathématiques plus avancées
(géométrie différentielle et algébrique, intégration numérique, théorie des
catégories) et pour la physique (optique, mécanique classique, mécanique et
informatique quantique).

Le projet contient deux applications Web, `SymPy Gamma`__ et `SymPy Live`__,
permettant aux étudiants, enseignants et chercheurs d’effectuer des expériences
mathématiques en ligne. SymPy Gamma est une interface d’apprentissage pour le
calcul et la visualisation basée sur des exemples : algébrique, géométrique,
trigonométrique et combinatoire. SymPy Live offre un terminal en ligne avec des
fonctionnalités telle que l’écriture des équations en LaTeX, la manipulation
symbolique avec le langage Python.

__ http://www.sympy.org/ 
__ http://gamma.sympy.org/
__ http://live.sympy.org/ 

Pour plus d'informations sur SymPy:

 - Tutoriel sur SymPy en français:
   http://docs.sympy.org/dev-py3k/tutorial/tutorial.fr.html
 - Aperçu de fonctionalités de SymPy (anglais):
   http://www.sympy.org/en/features.html
 - Documentation complète sur SymPy (anglais):
   http://docs.sympy.org/

Les exemples dans les sections qui suivent sont parfois nouveaux sinon inspirés
de la documentation en ligne de SymPy.

Nombres rationels
-----------------

Les nombres rationnels en SymPy doivent être construits à l'aide de la
fonction ``Rational``::

    >>> from sympy import Rational
    >>> Rational(53, 9)
    53/9
    >>> Rational(1,4) + Rational(1,3)
    7/12

Une autre façon plus courte de construire un nombre rationnel en SymPy est
d'utiliser la fonction raccourcie ``S`` qui traduit des types de Python comme
une chaîne de caractères ou un entier en des nombres entiers ou rationnels de
SymPy::

    >>> from sympy import S
    >>> S("5/2")    # traduction d'une chaîne de caractères en un rationel
    5/2

La division d'un nombre entier de sympy par un nombre entier retourne un nombre
rationnel plutôt qu'un nombre à virgule flottante::

    >>> S(5)/2      # S(5) transforme 5 (type int) en un nombre entier de sympy
    5/2

Nombres complexes
-----------------

En SymPy, les nombres complexes s'écrivent avec la lettre majuscule ``I`` pour
symboliser la partie imaginaire. Il faut d'abord l'importer::

    >>> from sympy import I

Par exemple, le nombre complexe `2+5i` s'écrit ``2+5*I``::

    >>> 2 + 5*I
    2 + 5*I

On vérifie que le carré du nombre imaginaire ``I`` retourne bien ``-1``::

    >>> I ** 2
    -1

Les opérations de base sont définies sur les nombres complexes comme pour les
nombres entiers et les nombres décimaux::

    >>> (13 + 34*I) + (3 + 4*I)
    16 + 38*I

**NOTE**: Le résultat n'est pas toujours simplifié. Pour ce faire, on peut
utiliser la fonction ``simplify`` de SymPy::

    >>> (13 + 34*I) / (3 + 4*I)
    (13 + 34*I)/(3 + 4*I)
    >>> from sympy import simplify
    >>> simplify( (13 + 34*I) / (3 + 4*I) )
    7 + 2*I

La division de nombre complexes entiers de partie imaginaire nulle retourne
bien un nombre rationnel::

    >>> (3+0*I) / (2+0*I)
    3/2

Pour obtenir les parties réelles et imaginaires d'un nombre complexe, on peut
utiliser les fonctions ``re`` et ``im`` de SymPy::

    >>> from sympy import re,im
    >>> re(3 + 7*I)
    3
    >>> im(3 + 7*I)
    7

Pour obtenir le module et l'argument d'un nombre complexe, on utilse les
fonctions ``arg`` et ``abs`` de SymPy. Notez qu'il n'est pas nécessaire
d'importer ``abs``, car cette fonction qui retourne la valeur absolue d'un
nombre réel est déjà dans Python et fonctionne pour les nombres complexes::

    >>> from sympy import arg
    >>> arg(3 + 7*I)
    atan(7/3)
    >>> abs(3 + 7*I)
    sqrt(58)

Quand c'est possible, SymPy procède à des simplifications::

    >>> arg(1 + I)
    pi/4
    >>> abs(3 + 4*I)
    5

Le conjugué d'un nombre complexe s'obtient avec la fonction ``conjugate``::

    >>> from sympy import conjugate
    >>> conjugate(3 + 7*I)
    3 - 7*I

On peut aussi obtenir le conjugué d'un nombre complexe en utilisant la méthode
``conjugate`` de la façon suivante (une *méthode* est une fonction définie dans
la classe d'un objet, ici dans la classe des nombres complexes)::

    >>> a = 3 + 7*I
    >>> a.conjugate()
    3 - 7*I

Utiliser la deuxième façon (méthode ``conjugate``) plutôt que la première
(fonction globale ``conjugate``) permet d'éviter d'importer la fonction et
aussi permet d'utiliser la touche ``TAB`` (dans IPython ou Jupyter) pour
choisir ou compléter l'écriture du nom de la méthode.

Calculer une valeur numérique
-----------------------------

Calculer la valeur numérique d'un ``nombre`` se fait avec la méthode ``evalf``
ou de façon équivalente ``n`` avec la syntaxe ``nombre.n(prec)`` où ``prec``
est le nombre de chiffres à afficher::

    >>> from sympy import pi
    >>> pi.evalf(60)
    3.1415926535897932384626433832795028841971693993751
    >>> pi.n(60)
    3.1415926535897932384626433832795028841971693993751

Le nombre de chiffres inclut les chiffres à gauche et à droite de la virgule::

    >>> from sympy import exp, pi, sqrt
    >>> exp(pi * sqrt(163)).evalf(50)
    262537412640768743.99999999999925007259719818568888

Factoriser un nombre entier
---------------------------

Pour factoriser un nombre entier, il suffit d'utiliser la fonction
``factorint``. La valeur retournée est un dictionnaire qui associe à chaque
diviseur une valeur qui représente la multiplicité du diviseur::

    >>> from sympy import factorint
    >>> factorint(240)
    {2: 4, 3: 1, 5: 1}

Il est possible d'afficher un résultat plus visuel de la factorisation au moyen
de la fonction ``pprint`` et de l'option ``visual=True``::

    >>> from sympy import pprint
    >>> pprint(factorint(240, visual=True))
     4  1  1
    2 ⋅3 ⋅5 

Accéder à la documentation et au code source d'une fonction
-----------------------------------------------------------

Comme on l'a déjà vu, pour obtenir de l'aide sur une fonction ``f``, il suffit
d'écrire ``?f`` ou ``f?``. Par exemple::

    >>> from sympy import Rational
    >>> Rational?

Comme SymPy est un logiciel libre, on peut aussi accéder au **code source** en
ajoutant un deuxième point d'interrogation::

    >>> Rational??

