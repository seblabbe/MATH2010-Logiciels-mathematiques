Algèbre linéaire
================

Cette section concerne l'algèbre linéaire et les matrices.
On trouvera d'autres exemples dans le tutoriel de Sympy sur le même sujet:
http://docs.sympy.org/latest/tutorial/matrices.html

Définir une matrice
-------------------

En SymPy, on peut créer une matrice avec la fonction ``Matrix``::

    >>> from sympy import Matrix

Il suffit d'écrire les entrées lignes par lignes avec la syntaxe suivante::

    >>> Matrix([[2, 5, 6], [4, 7, 10], [1, 0, 3]])
    [2  5  6 ]
    [        ]
    [4  7  10]
    [        ]
    [1  0  3 ]

Une autre façon équivalente est de spécifier le nombre de lignes, le nombre de
colonnes et puis la liste des entrées::

    >>> Matrix(2, 3, [1, 2, 3, 4, 5, 6])
    [1  2  3]
    [       ]
    [4  5  6]

Par défaut, si on ne spécifie pas les dimensions de la matrice, un vecteur
colonne est retourné::

    >>> Matrix([1,2,3,4])
    [1]
    [ ]
    [2]
    [ ]
    [3]
    [ ]
    [4]

Opérations de base
------------------

Les opérations de l'algèbre des matrices (addition, multiplication,
multiplication par un scalaire) sont définies naturellement::

    >>> M = Matrix([[5, 2], [-1, 7]])
    >>> N = Matrix([[0, 4], [0, 5]])
    >>> M + N
    [5   6 ]
    [      ]
    [-1  12]
    >>> M * N
    [0  30]
    [     ]
    [0  31]
    >>> 4 * M
    [20  8 ]
    [      ]
    [-4  28]
    >>> M ** 5
    [-475   12242]
    [            ]
    [-6121  11767]

De même, on peut calculer l'inverse d'une matrice si elle est inversible::

    >>> M**-1
    [7/37  -2/37]
    [           ]
    [1/37  5/37 ]
    >>> N**-1
    Traceback (most recent call last):
    ...
    ValueError: Matrix det == 0; not invertible.

La transposition d'une matrice se fait avec ``.transpose()``::

    >>> from sympy import I
    >>> M = Matrix(( (1,2+I,5), (3,4,0) ))
    >>> M
    [1  2 + I  5]
    [           ]
    [3    4    0]
    >>> M.transpose()
    [  1    3]
    [        ]
    [2 + I  4]
    [        ]
    [  5    0]

Accéder aux coefficients
------------------------

::

    >>> from sympy import I
    >>> M = Matrix(( (1,2+I,5), (3,4,0) ))
    >>> M
    [1  2 + I  5]
    [           ]
    [3    4    0]

On accède à l'élément en position ``(i,j)`` en écrivant ``M[i,j]``::

    >>> M[0,1]
    2 + I
    >>> M[1,1]
    4

.. Attention::

    Les indices des positions commencent à zéro!!

On accède aux lignes et au colonnes d'une matrices avec les méthodes ``row`` et
``col``::

    >>> M.row(1)
    [3  4  0]
    >>> M.col(0)
    [1]
    [ ]
    [3]


Construction de matrices particulières
--------------------------------------

Les fonctions ``zeros`` et ``ones`` permettent de créer des matrices de zéros
et de uns::

    >>> from sympy import ones,zeros
    >>> ones(2)
    [1, 1]
    [1, 1]
    >>> zeros((2, 4))
    [0, 0, 0, 0]
    [0, 0, 0, 0]

La fonction ``eye`` de sympy permet de créer une matrice identité::

    >>> from sympy import eye
    >>> eye(3)
    [1, 0, 0]
    [0, 1, 0]
    [0, 0, 1]

La fonction ``diag`` permet de créer une matrice diagonale::

    >>> from sympy import diag
    >>> diag(1,2,3)
    [1  0  0]
    [       ]
    [0  2  0]
    [       ]
    [0  0  3]

Les éléments de la diagonales peuvent être eux-mêmes des matrices::

    >>> diag(1, 2, Matrix([[7,8],[2,3]]))
    [1  0  0  0]
    [          ]
    [0  2  0  0]
    [          ]
    [0  0  7  8]
    [          ]
    [0  0  2  3]

Matrice échelonnée réduite
--------------------------

On calcule la forme échelonnée réduite d'une matrice avec la méthode ``rref``
(abbréviation de *reduced row echelon form* en anglais)::

    >>> M = Matrix([[1, 2, 0, 3], [2, 6, 5, 1], [-1, -4, -5, 2]])
    >>> M.rref()
    ([1  0  -5    8  ], [0, 1])
     [               ]
     [0  1  5/2  -5/2]
     [               ]
     [0  0   0    0  ]

Noyau
-----

On calcule le noyau d'une matrice avec ``nullspace``::

    >>> M = Matrix([[1, 2, 0, 3], [2, 6, 5, 1], [-1, -4, -5, 2]])
    >>> M.nullspace()
    [[ 5  ], [-8 ]]
     [    ]  [   ]
     [-5/2]  [5/2]
     [    ]  [   ]
     [ 1  ]  [ 0 ]
     [    ]  [   ]
     [ 0  ]  [ 1 ]

Déterminant
-----------

On calcule le déterminant avec la méthode ``det``::

    >>> M = Matrix([[2, 5, 6], [4, 7, 10], [1, 0, 3]])
    >>> M.det()
    -10

Polynôme caractéristique
------------------------

La méthode ``charpoly`` permet de calculer le polynôme caractéristique d'une
matrice carrée::

    >>> M = Matrix([[3, -2,  4, -2], [5,  3, -3, -2], [5, -2,  2, -2], [5, -2, -3,  3]])
    >>> from sympy.abc import x
    >>> M.charpoly(x)
    PurePoly(x**4 - 11*x**3 + 29*x**2 + 35*x - 150, x, domain='ZZ')

On ajoute ``.as_expr()`` pour obtenir l'expression symbolique du polynôme
caractéristique::

    >>> M.charpoly(x).as_expr()
     4       3       2
    x  - 11*x  + 29*x  + 35*x - 150
    >>> from sympy import factor
    >>> factor(_)
           2
    (x - 5) *(x - 3)*(x + 2)

Valeurs propres et vecteurs propres
-----------------------------------

Continuons avec la même matrice ``M`` définie précédemment::

    >>>  M
    [3  -2  4   -2]
    [             ]
    [5  3   -3  -2]
    [             ]
    [5  -2  2   -2]
    [             ]
    [5  -2  -3  3 ]

Soient les vecteurs colonnes ``w`` et ``v`` suivants::

    >>> w = Matrix((1,2,3,4))
    >>> v = Matrix((1,1,1,0))
    >>> w
    [1]
    [ ]
    [2]
    [ ]
    [3]
    [ ]
    [4]
    >>> v
    [1]
    [ ]
    [1]
    [ ]
    [1]
    [ ]
    [0]

En général, l'image par ``M`` d'un vecteur n'a rien à voir avec ce vecteur.
Par exemple, l'image par ``M`` de ``w`` n'a rien à voir avec ``w``::

    >>> M * w
    [3 ]
    [  ]
    [-6]
    [  ]
    [-1]
    [  ]
    [4 ]

Dans certains cas particuliers, l'image par ``M`` d'un vecteur retourne un
multiple scalaire de ce vecteur. C'est ce qui se produit pour le vecteur
``v``::

    >>> M * v
    [5]
    [ ]
    [5]
    [ ]
    [5]
    [ ]
    [0]

Le résultat précédent est égal à 5 fois le vecteur ``v``::

    >>> 5 * v
    [5]
    [ ]
    [5]
    [ ]
    [5]
    [ ]
    [0]

Un vecteur ``v`` qui satisfait l'équation ``M * v = lamda * v`` pour un certain
nombre réel (ou complexe) ``lamda`` est appelé *vecteur propre*. Le nombre
``lamda`` qui satisfait l'équation est appelé *valeur propre*. Il se trouve que
les valeurs propres d'une matrice sont les racines de son polynôme
caractéristique. Le calcul des valeurs et vecteurs propres d'une matrice est
utile dans presque tous les domaines des mathématiques.

En sympy, on calcule les valeurs propres d'une matrice avec la méthode
``eigenvals``. Le résultat est un dictionnaire qui associe à chaque valeur
propre sa multiplicité algébrique (comme pour le calcul des racines)::

    >>> M.eigenvals()
    {-2: 1, 3: 1, 5: 2}

Et on calcule les vecteurs propres d'une matrice avec la méthode
``eigenvects``::

    >>> M.eigenvects()
    [(-2, 1, [[0]]), (3, 1, [[1]]), (5, 2, [[1], [0 ]])]
              [ ]            [ ]            [ ]  [  ]
              [1]            [1]            [1]  [-1]
              [ ]            [ ]            [ ]  [  ]
              [1]            [1]            [1]  [0 ]
              [ ]            [ ]            [ ]  [  ]
              [1]            [1]            [0]  [1 ]

Le calcul précédent montre bien que le vecteur colonne ``v = [1, 1, 1, 0]^T``
est bien un vecteur propre de la matrice ``M`` associé à la valeur propre ``5``
comme on l'avait vu plus tôt. Il permet aussi de réaliser qu'un autre vecteur
colonne linéairement indépendant de ``v`` est aussi un vecteur propre associé à
la valeur propre ``5``. Finalement, il y a deux autres vecteurs propres
associés aux valeurs propres ``-2`` et ``3``.

