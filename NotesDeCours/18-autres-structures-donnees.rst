
Autres structures de données
============================

::

    >>> from __future__ import division, print_function   # Python 3

Tuples (type ``tuple``)
-----------------------

En Python, les tuples (ou n-uplets) sont créées avec l'utilisation des
parenthèses et on peut mettre n'importe quel objet dans un tuple::

    >>> t = (45, 'bonjour', 6.7, [3])
    >>> t
    (45, 'bonjour', 6.7, [3])

Comme pour les listes et les chaînes de caractères, on peut accéder aux
éléments avec les crochets et zéro dénote la première position::

    >>> t[0]
    45
    >>> t[1]
    'bonjour'

On vérifie le type de cet objet::

    >>> type(t)
    <type 'tuple'>

Un tuple joue le même rôle qu'une liste à la différence principale qu'on ne
peut pas modifier un tuple. On ne peut donc pas ajouter ou supprimer des objets
d'un tuple.

La fonction ``tuple`` permet de transformer un objet en tuple pourvu qu'il soit
itérable::

    >>> tuple('bonjour')
    ('b', 'o', 'n', 'j', 'o', 'u', 'r')
    >>> tuple([1,2,3])
    (1, 2, 3)

Emballage et déballage d'un tuple
---------------------------------

Les tuples peuvent être créés comme emballage de valeurs::

    >>> b = ('Bob', 23, 'math')      # emballage d'un tuple
    >>> b
    (u'Bob', 23, u'math')

Mais, il peuvent aussi être déballés directement en faisant comme suit::

    >>> (nom, age, etude) = b        # déballage d'un tuple
    >>> nom
    u'Bob'
    >>> age
    23
    >>> etude
    u'math'

Dictionnaires (type ``dict``)
-----------------------------

Les listes et tuples ont cela de contraignants que les positions sont des
nombres de 0 à n-1 où n est la longueur de la liste. Parfois, il est pratique
que les positions prennent d'autres valeurs ou d'autres types.

En Python, les dictionnaire sont créées avec l'utilisation des accolades avec
la syntaxe ``{cle1:valeur1, cle2:valeur2, cle3:valeur3}``. Par exemple::

    >>> d = {'namur':813248, 'liege':441432, 'anvers':978756}
    >>> d
    {'liege': 441432, 'namur': 813248, 'anvers': 978756}

est un dictionnaire qui associe des noms de villes avec des nombres qui peuvent
représenter le nombre d'habitants::

    >>> type(d)
    <type 'dict'>

On peut accéder à la valeur associée à une clé en utilisant les crochets::

    >>> d['liege']
    441432

Tenter d'accéder à une clée inexistante retourne une erreur::

    >>> d['bruxelles']
    Traceback (most recent call last):
    ...
    KeyError: 'bruxelles'

Toutefois, on peut ajouter les données pour la ville de Bruxelles en faisant::

    >>> d['bruxelles'] = 5000000
    >>> d
    {'bruxelles': 5000000, 'liege': 441432, 'namur': 813248, 'anvers': 978756}

La fonction ``len`` retourne la taille du dictionnaire::

    >>> len(d)
    4

Les méthodes ``.keys()`` et ``.values()`` retourne respectivement les clés et
les valeurs d'un dictionnaire sous forme de liste::

    >>> d.keys()
    ['bruxelles', 'liege', 'namur', 'anvers']
    >>> d.values()
    [5000000, 441432, 813248, 978756]

Finalement, la méthode ``.items()`` retourne la liste des paires clé-valeur
d'un dictionnaire::

    >>> d.items()
    [('bruxelles', 5000000), ('liege', 441432), ('namur', 813248), ('anvers', 978756)]

En SymPy, on se rappelle que certaines fonctions retournent des dictionnaires
telles que la fonction ``factorint``::

    >>> from sympy import factorint
    >>> factorint(240)
    {2: 4, 3: 1, 5: 1}

Les clés d'un dictionnaire doivent être des objets non modifiables
(techniquement, des objets qui définissent une fonction de hachage ``hash``).
Comme les listes sont modifiables, une liste ne peut pas jouer le rôle d'une
clé d'un dictionnaire. Si on le fait, on obtient l'erreur suivante::

    >>> d = dict()
    >>> cle = [2,3,4]
    >>> d[cle] = 'valeur'
    Traceback (most recent call last):
    ...
    TypeError: unhashable type: 'list'

Comme les listes sont modifiables, elle ne sont pas hachable d'où l'erreur
obtenue. Par contre, on peut utiliser un tuple comme clé d'un dictionnaire::

    >>> cle = (2,3,4)
    >>> d[cle] = 'valeur'
    >>> d
    {(2, 3, 4): 'valeur'}

Ensembles (type ``set``)
------------------------

Les listes peuvent contenir plusieurs fois le même objet::

    >>> [1,2,2,3,3,3,4,4,4,4]
    [1, 2, 2, 3, 3, 3, 4, 4, 4, 4]

En Python, le type ``set`` permet de créer un ensemble au sens mathématique où
chaque élément apparaît au plus une fois::

    >>> set('gauffredeliege')
    set(['a', 'e', 'd', 'g', 'f', 'i', 'l', 'r', 'u'])

::

    >>> set([1,2,2,3,3,3,4,4,4,4])
    set([1, 2, 3, 4])

La méthode ``.add()`` permet d'ajouter un élément à l'ensemble::

    >>> s = set([1,2,3,4])
    >>> s.add('bonjour')
    >>> s
    set([1, 2, 3, 4, 'bonjour'])

Comme pour les clés d'un dictionnaire, les éléments d'un ensemble doivent être
hachables (non modifiables). Par exemple, on ne peut pas ajouter une liste à un
ensemble, mais on peut ajouter un tuple::

    >>> s.add([1,2,3])
    Traceback (most recent call last):
    ...
    TypeError: unhashable type: 'list'
    >>> s.add((1,2,3))
    >>> s
    set([1, 2, 3, 4, (1, 2, 3), u'bonjour'])

