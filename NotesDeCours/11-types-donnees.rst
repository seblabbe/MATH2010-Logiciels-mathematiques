
Types de données de Python
==========================

Nous avons vu dans les chapitres précédents quelques types de données comme les
entiers et les nombres flottants de Python ainsi que quelques structures de
données (listes, tuples, dictionnaires) utilisées comme argument ou comme
valeur de retour de certaines fonctions de SymPy. Dans ce chapitre, nous allons
présenter avec plus de détails les types de données qui sont les plus souvent
utilisées en programmation.

Le type d'un objet
------------------

Construisons le nombre entier 4 de deux façons différentes, avec Python puis
avec SymPy::

    >>> a = 4
    >>> from sympy import S
    >>> b = S(4)

Le nombre 4 est stocké dans la variable ``a`` et dans la variable ``b``::

    >>> a
    4
    >>> b
    4

Bien qu'ils représentent tous deux le nombre 4 et qu'ils s'affichent de la même
façon à l'écran, ils ne se comportent pas de la même façon::

    >>> a/5
    0.8
    >>> b/5
    4/5

C'est que les *objets* stockés dans les variables ``a`` et ``b`` ne sont pas du
même *type*. La fonction ``type`` permet de connaître le type d'un ``objet``
avec la syntaxe ``type(objet)``::

    >>> type(a)
    <type 'int'>
    >>> type(b)
    <class 'sympy.core.numbers.Integer'>

Cela explique le comportement différent de ``a/5`` qui retourne un nombre
décimal et ``b/5`` qui retourne un nombre rationel de SymPy::

    >>> type(a/5)
    <type 'float'>
    >>> type(b/5)
    <class 'sympy.core.numbers.Rational'>

Comme le comportement d'un objet dépend de son type, il est souvent pertinent
de vérifier le type d'un objet avant de l'utiliser. Les autres types très
communs que nous allons voir dans les sections suivantes sont ci-dessous::

    >>> type(4)
    <type 'int'>
    >>> type(4.0)
    <type 'float'>
    >>> type(True)
    <type 'bool'>
    >>> type('bonjour')
    <type 'str'>
    >>> type([3,4,5])
    <type 'list'>
    >>> type((3,4,5))
    <type 'tuple'>
    >>> type({2:3, 4:5})
    <type 'dict'>

Nombres entiers (type ``int``)
------------------------------

Les nombres entiers sont créés simplement en Python::

    >>> 4
    4

Ils sont aussi obtenus par le résultat d'opérations sur les nombres entiers
comme l'addition, la multiplication, la soustraction, le modulo et le
quotient::

    >>> 4 + 6
    10
    >>> 7 * 9
    63
    >>> 4 - 6
    -2
    >>> 27 % 10
    7
    >>> 27 // 10
    2

On peut vérifier que le résultat des opérations ci-haut est bel et bien un
entier Python de type ``int``::

    >>> type(27 // 10)
    <type 'int'>

En Python, la fonction ``int`` permet de créer un entier de type ``int``::

    >>> int()
    0
    >>> int(4)
    4

Cette fonction permet aussi de traduire un objet d'un autre type en un nombre
entier de Python de type ``int``::

    >>> int(4.02)
    4
    >>> int('41234')
    41234

Pour stocker des nombres entiers un peu plus grand, Python utilise une autre
structure de données appelé entier ``long``. On peut tester à partir d'où cela
se produit::

    >>> type(2 ** 61)
    <type 'int'>
    >>> type(2 ** 62)
    <type 'int'>
    >>> type(2 ** 63)
    <type 'long'>
    >>> type(2 ** 64)
    <type 'long'>

Nombres flottants (type ``float``)
----------------------------------

Les nombres décimaux aussi appelé nombre flottants ou nombre à virgule
flottante sont créés simplement en Python::

    >>> 4.
    4.0

Ils sont aussi obtenus par le résultat d'opérations sur les nombres flottants
comme l'addition, la multiplication, la soustraction, le modulo et le
quotient::

    >>> 4. * 3.41
    13.64

On vérifie que le type du résultat précédent est bel et bien un nombre flottant
de type ``float``::

    >>> type(_)
    <type 'float'>

Les nombres flottants peuvent aussi être obtenus comme résultats d'opérations
impliquant des nombres d'autres types comme la multiplication par un nombre
entier ou la division de deux nombres entiers::

    >>> 4. * 3
    12.0
    >>> 4 / 5
    0.8

Finalement, les nombres flottants peuvent être créés avec la fonction ``float``
qui permet aussi de transformer un objet d'un autre type en nombre flottant::

    >>> float()
    0.0
    >>> float(34)
    34.0
    >>> float('1234')
    1234.0
    >>> float('1234.56')
    1234.56

Booléens (type ``bool``)
------------------------

Les booléens permettent de représenter les valeurs *vrai* et *faux*. On les
écrit en anglais avec un majuscule::

    >>> True
    True
    >>> False
    False

Les valeurs ``True`` et ``False`` sont des objets de type ``bool``::

    >>> type(False)
    <type 'bool'>
    >>> type(True)
    <type 'bool'>

Les opérations de base sur les booléens retournent aussi des booléens::

    >>> True or False
    True
    >>> False and True
    False

Si cela est nécessaire, voici toutes les possibilités de valeurs d'entrées pour
le ET logique ``and`` qui retourne *vrai* lorsque les deux valeurs d'entrées
sont vraies::

    >>> True and True
    True
    >>> True and False
    False
    >>> False and True
    False
    >>> False and False
    False

Pareillement le OU logique (``or``) retourne ``True`` dès qu'une des deux valeurs est vraie::

    >>> True or True
    True
    >>> True or False
    True
    >>> False or True
    True
    >>> False or False
    False

La négation (``not``) retourne l'opposé d'une valeur booléenne::

    >>> not True
    False
    >>> not False
    True

Un booléen peut être retourné par des fonctions ou des tests de comparaison::

    >>> 13 == 5 + 8
    True
    >>> 20 > 34
    False

La fonction ``bool`` permet de transformer un objet en un booléen. En général,
les valeurs zéro ou les listes vides sont transformées en ``False`` et les
valeurs non nulles ou les listes non vides sont transformées en ``True``::

    >>> bool(113)
    True
    >>> bool(0)
    False
    >>> bool(1)
    True

Chaînes de caractères (type ``str``)
------------------------------------

En Python, les chaînes de caractères sont définies par l'utilisation des simple
guillemets (``'``) ou des doubles guillemets (``"``)::

    >>> 'bonjour'
    'bonjour'
    >>> "bonjour"
    'bonjour'

Si on veut utiliser les simples guillemets à l'intérieur de la chaînes de
caractères, on doit utiliser les doubles pour l'entourer et vice versa::

    >>> "aujourd'hui"
    "aujourd'hui"
    >>> 'Je suis "ici"'
    'Je suis "ici"'

Pour utiliser à la fois des simples et des doubles guillemets dans la chaîne de
caractères, on utilise des triple double guillemets pour entourer la chaîne de
caractères::

    >>> """Je suis "ici" aujourd'hui"""
    'Je suis "ici" aujourd\'hui'

On peut créer des chaînes de caractères à partir d'autres objets en utilisant
la fonction ``str``::

    >>> str(12345)
    '12345'
    >>> str(12345.789)
    '12345.789'

Pour accéder aux lettres d'une chaîne de caractères, on utilise les crochets
après la variable de la façon suivante::

    >>> w = 'bonjour'
    >>> w[0]
    'b'
    >>> w[1]
    'o'

Comme vous remarquez, l'indexation commence à zéro et non pas à un. C'est comme
ça en Python. Ainsi la septième et dernière lettre du mot bonjour est à la
position 6::

    >>> w[6]
    'r'

On peut aussi compter à partir de la fin avec des indices négatifs. La position
``-1`` retourne la dernière lettre::

    >>> w[-1]
    'r'

On peut accéder aux sous-chaînes de la position ``i`` à la position ``j-1``
avec la syntaxe ``w[i:j]`` de la façon suivante::

    >>> w[2:5]
    'njo'

Si on ne spécifie pas le début ou la fin, alors le comportement par défaut est
d'aller jusqu'au bout::

    >>> w[:4]
    'bonj'

