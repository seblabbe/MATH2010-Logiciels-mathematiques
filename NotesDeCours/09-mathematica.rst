Mathematica
===========

.. contents:: **Contenu**
   :local:

Les thèmes des chapitres 1 à 8 représentent la base des fonctionalités offertes
par les logiciels de calcul formel dont SymPy, Sage, Mathematica, Maple, Magma
et d'autres font partie. Dans ces notes de cours, nous avons utilisé SymPy dans
les 8 premiers chapitres, mais nous aurions pu utiliser un autre logiciel.

Entre deux logiciels qui font la même chose, on retrouve de nombreuses
ressemblances, mais aussi des différences. Dans ce cours, nous n'aurons pas le
temps d'apprendre à utiliser tous les logiciels de calcul formel ni d'étudier
toutes les différences entre les uns et les autres. Toutefois, il est pertinent
d'avoir une idée de ce que peuvent être ces ressemblances et ces différences
afin d'être prêt à utiliser dans le futur un logiciel différent de celui que
l'on connaît. Pour ce faire, il faut apprendre à utiliser au moins un deuxième
logiciel de calcul formel. 

Dans ce chapitre, nous présentons le logiciel commercial Mathematica. Nous
présentons les différences et ressemblances principales avec SymPy. Puis, le
chapitre se termine avec des tables qui traduisent en Mathematica l'ensemble
des fonctions de SymPy que nous avons présentées dans les chapitre 1 à 8. La
plupart du temps, les fonctions s'utilisent avec les mêmes arguments et dans le
même ordre. Pour voir des exemples ou pour avoir plus de détails, le lecteur
sera invité à consulter la documentation de Mathematica ou internet.

Résumé des différences entre SymPy et Mathematica
-------------------------------------------------

En Python, on doit importer les fonctions que l'on utilise. Une par une en
écrivant ``from sympy import factor,pi,sin`` ou toutes à la fois avec ``from
sympy import *``. En Mathematica, on n'a **pas besoin d'importer les
fonctions** avant de les utiliser.

Tout d'abord, la règle générale en Mathematica est que les fonctions commencent
avec une **lettre majuscule** plutôt qu'avec des minuscules. On écrit donc
``Sin``, ``Pi``, ``Factor`` en Mathematica plutôt que ``sin``, ``pi`` et
``factor`` en SymPy.

Les **noms des fonctions sont le plus souvent les mêmes qu'en SymPy**, mais on
note quelques différences comme ``FactorInteger``, ``ArcSin`` et
``ParametricPlot`` en Mathematica versus ``factorint``, ``asin`` et
``plot_parametric`` en SymPy.  On trouve quelques autres fonctions qui portent
des noms différents dans les tables à la fin de ce chapitre.

Pour évaluer une fonction, on utilise les parenthèses en SymPy ``sin(pi)`` et
les **crochets** ``[]`` en Mathematica ``Sin[Pi]``.

Pour évaluer une cellule dans Mathematica comme dans Jupyter, c'est la même
chose, on appuie sur les touches ``MAJUSCULE + ENTRÉE``.

En SymPy comme en Python, la **multiplication implite** ``3x`` n'est pas
possible et il faut toujours écrire ``3*x`` en spécifiant l'opération de
multiplication (``*``). En Mathematica, les espaces vides sont interprétés
comme des multiplications et ``3x`` sans espace est interprété comme le produit
du nombre ``3`` par la variable ``x``.

En Mathematica, l'**exponentiation** s'écrit avec le symbole chapeau ``^``
plutôt qu'avec ``**`` et la division de nombres entiers retourne bien un nombre
rationnel.

Les listes comme ``[x, 0, 2*pi]`` et les tuples comme ``(x, 0, 2*pi)`` en
Python et SymPy sont souvent utilisés comme arguments de fonctions. De la même
façon en Mathematica, les listes sont beaucoup utilisées. Toutefois, en
Mathematica, on utilise les **accolades** ``{`` **et** ``}`` **pour définir une
liste**. On écrit alors ``{x, 0, 2*Pi}``. Par exemple, l'intégrale de sin(x)
s'écrit en SymPy:

.. code:: pycon

   >>> integrate(sin(x), (x, 0, 2*Pi))

En Mathematica, cela devient::

   >>> Integrate[Sin[x], {x, 0, 2*Pi}]

En SymPy, on doit définir les symboles avec la fonction ``Symbol`` ou bien on
peut les importer du sous-module ``sympy.abc``. En Mathematica, **toute
variable non définie est par défaut un symbole** et prend la couleur bleue
(Mathematica v.10.0) pour les identifier.

En Mathematica, contrairement à SymPy, il n'y a pas de distinction entre la
variable ``x`` et le symbole ``x``. On peut remarquer cette différence en
testant le code suivant qui ne retourne pas la même chose en Mathematica et en
SymPy:

.. code:: pycon

   >>> Clear[x]                         # Mathematica
   >>> from sympy.abc import x          # SymPy
   >>> expr = x + 1
   >>> x = 100
   >>> expr

En Mathematica, la ligne ``x = 100`` change la valeur de la variable ``x`` et
``x`` n'est plus un symbole (sa couleur change et devient noir). Cela a un
effet de bord sur l'expression ``expr`` qui retourne la valeur ``101``. En
SymPy, ``expr`` contient le symbole ``x`` plus ``1``. La ligne ``x = 100``
change la valeur de la variable ``x`` mais n'a pas d'effet sur les expressions
qui contiennent le symbole ``x``. Donc, ``expr`` retourne bien ``x + 1``.

La **complétion automatique** par la touche tabulation en Jupyter a son
équivalent en Mathematica. Des suggestions de noms de fonctions apparraissent à
l'écran en Mathematica pour compléter les premières lettres que l'on écrit.

Pour **accéder à la documentation d'une fonction** en Mathematica, il suffit
d'ajouter un point d'interrogation *avant* le nom de la fonction et d'évaluer
la cellule. En Jupyter, le point d'interrogation peut être placé avant ou après
le nom de la fonction pour accéder à sa documentation.

Python et SymPy sont basés sur la programmation orientée objet ce qui explique
que l'on peut écrire la fonction *après* l'objet comme par exemple ``pi.n()``
pour calculer les décimales de pi et ``M.det()`` pour calculer le déterminant
d'une matrice. En Mathematica, cela ne se produit jamais. Les **fonctions
s'écrivent toujours avant les objets** comme ``N[Pi]`` et ``Det[M]``.

La plupart du temps, la **syntaxe** est exactement la même en SymPy et en
Mathematica, mais il y a quelques exceptions. Par exemple, le calcul d'une
limite en SymPy s'écrit:

.. code:: pycon

   >>> limit(sin(x)/x, x, 0)

alors, qu'en Mathematica, on utilise la flèche ``->`` pour indiquer qu'une
variable tend vers une valeur::

   >>> Limit[Sin[x]/x, x->0]

On trouvera une liste des particularités du langage SymPy ici:
http://docs.sympy.org/dev/tutorial/gotchas.html. On trouvera le manuel de
référence de Mathematica en ligne à l'adresse
http://reference.wolfram.com/language/ et des vidéos d'introduction à l'adresse
https://www.wolfram.com/broadcast/screencasts/handsonstart/.

Tables de traduction entre SymPy et Mathematica
-----------------------------------------------

Les tables ci-bas donnent les équivalents en Mathematica pour chacune des
fonctionnalités de SymPy que l'on a vu dans les chapitres 1 à 8. La plupart du
temps, la syntaxe est essentiellement la même. On doit simplement ajouter des
majuscules et remplacer les parenthèses par des crochets ``[]`` ou des
accolades ``{}`` selon que l'on évalue une fonction ou que l'on définit une
liste.

En cas de problème, il ne faut pas hésiter à consulter la documentation de
Mathematica en ajoutant un point d'interrogation avant le nom de la fonction,
comme ``?Factor`` ou sinon chercher des exemples sur internet.

.. list-table:: Chapitre 1: Interface
   :header-rows: 1
   :widths: 8 9 10

   * - Thème
     - Jupyter, IPython, SymPy
     - Mathematica
   * - Évaluer une cellule
     - MAJUSCULE + ENTRÉE
     - MAJUSCULE + ENTRÉE
   * - Ne pas afficher le résultat
     - Ajouter un ``";"``
     - Ajouter un ``";"``
   * - Règle générale
     - minuscules : ``factor``
     - une majuscule: ``Factor``
   * - Aide
     - ``?factor`` ou ``factor?`` 
     - ``?Factor``
   * - Évaluer une fonction
     - ``factor(x)``
     - ``Factor[x]``
   * - Liste
     - ``[x,0,2*pi]``
     - ``{x,0,2*pi}``
   * - n-uplet
     - ``(x,0,2*pi)``
     - ``{x,0,2*pi}``
   * - Symboles
     - ``x = Symbol('x')``
     - ``x``, symbole par défaut (en bleu)
   * - Variables et affectation
     - ``k = 4``
     - ``k = 4``
   * - Les résultats précédents
     - ``_, __, ___``
     - ``%, %%, %%%``
   * - Le 12e résultat
     - ``Out[12]``
     - ``Out[12]``
   * - Temps de calcul
     - ``%time factorint(100)``
     - ``Timing[FactorInteger[100]]``
   * - Approximation numérique
     - ``pi.n()`` ou ``pi.evalf()`` ou ``N(pi)``
     - ``N[Pi]``
   * - Réinitialiser les variables
     - ``%reset``
     - ?

.. list-table:: Chapitre 2 et 3: Calculatrice et arithmétique
   :header-rows: 1
   :widths: 10 10

   * - SymPy
     - Mathematica
   * - ``2 + 3, 10 - 5``
     - ``2 + 3, 10 - 5``
   * - ``2 * 3``
     - ``2 * 3`` ou ``2 3``
   * - ``3 ** 10``
     - ``3 ^ 10``
   * - ``1 / (1 + 4*5)**2``
     - ``1 / (1 + 4*5)^2``
   * - ``Rational(3,4), S(3)/4``
     - ``3/4``
   * - ``sin, cos, tan``
     - ``Sin, Cos, Tan``
   * - ``asin, acos, atan``
     - ``ArcSin, ArcCos, ArcTan``
   * - ``exp(2), log(2)``
     - ``Exp[2], Log[2]``
   * - ``sqrt(2)``
     - ``Sqrt[2]``
   * - ``E, I, pi, oo``
     - ``E, I, Pi, Infinity``
   * - ``re, im, arg, conjugate``
     - ``Re, Im, Arg, Conjugate``
   * - ``factorial(100)``
     - ``Factorial[100]``
   * - ``factorint(100)``
     - ``FactorInteger[100]``

.. list-table:: Chapitre 4: Calcul symbolique
   :header-rows: 1
   :widths: 10 10

   * - SymPy
     - Mathematica
   * - ``Symbol, symbols, sympy.abc``
     - les symboles sont définis automatiquement
   * - ``srepr``
     - ``FullForm, TreeForm``
   * - ``3*x``
     - ``3*x`` ou ``3x``
   * - ``(x+1).subs(x,0)``
     - ?
   * - ``apart, together, cancel, collect``
     - ``Apart, Together, Cancel, Collect``
   * - ``factor, expand``
     - ``Factor, Expand``
   * - ``simplify``
     - ``Simplify, FullSimplify``
   * - ``radsimp``, ``ratsimp``
     - ?

.. list-table:: Chapitre 5: Résolution d'équations
   :header-rows: 1
   :widths: 10 10

   * - SymPy
     - Mathematica
   * - ``Eq(x + y, 4)``
     - ``x + y == 4``
   * - ``solve(x**2 - 3, x)``
     - ``Solve[x^2-3 == 0, x]``
   * - ``roots, root, real_root, RootOf``
     - ``Root``
   * - ``nsolve(x**2 - 3, x, 2)``
     - ``NSolve[x^2-3 == 0, x]``

.. list-table:: Chapitre 6: Tracer une fonction
   :header-rows: 1
   :widths: 10 10

   * - SymPy
     - Mathematica
   * - ``plot(sin(x), (x,0,2*pi))``
     - ``Plot[Sin[x], {x,0,2 Pi}]``
   * - ``plot3d``
     - ``Plot3D``
   * - ``plot_parametric``
     - ``ParametricPlot``
   * - ``plot3d_parametric_line``
     - ``ParametricPlot3D``
   * - ``plot3d_parametric_surface``
     - ``ParametricPlot3D``
   * - ``plot_implicit``
     - ``RegionPlot[ImplicitRegion[...]]``
   * - ``mpmath.cplot``
     - ?

.. list-table:: Chapitre 7: Calcul différentiel et intégral
   :header-rows: 1
   :widths: 10 10

   * - SymPy
     - Mathematica
   * - ``limit, diff, integrate, series``
     - ``Limit, D, Integrate, Series``
   * - ``dsolve``
     - ``DSolve``
   * - ``summation, product``
     - ``Sum, Product``
   * - ``Function``
     - les symboles sont définis automatiquement
   * - ``Derivative, Integral, Sum, Product``
     - ?

.. list-table:: Chapitre 8: Algèbre linéaire
   :header-rows: 1
   :widths: 10 10

   * - SymPy
     - Mathematica
   * - ``M = Matrix([[1,2],[3,4]])``
     - ``M = {{1,2},{3,4}}``
   * - ``diag(2,3,4)``
     - ``DiagonalMatrix[{2,3,4}]``
   * - ``eye(5)``
     - ``IdentityMatrix[5]``
   * - ``zeros(3,5)``
     - ``Table[0, {i,1,3}, {j,1,5}]``
   * - ``ones(3,5)``
     - ``Table[1, {i,1,3}, {j,1,5}]``
   * - ``M + N``
     - ``M + N``
   * - ``3 * M``
     - ``3 * M``
   * - ``M * N``
     - ``M . N``
   * - ``M ** 4``
     - ``MatrixPower[M, 4]``
   * - ``M.transpose()``
     - ``Transpose[M]``
   * - ``M.det(), M.rank(), M.nullspace()``
     - ``Det[M], Rank[M], NullSpace[M]``
   * - ``M ** -1`` ou ``M.inverse()``
     - ``Inverse[M]``
   * - ``M.rref()``
     - ``RowReduce[M]``
   * - ``M.charpoly()``
     - ``CharacteristicPolynomial[M]``
   * - ``M.eigenvals(), M.eigenvects()``
     - ``Eigenvalues[M], Eigenvectors[M]``
