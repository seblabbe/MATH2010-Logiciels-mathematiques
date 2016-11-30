
Exemples (``def`` + ``while`` + ``for`` + ``if``)
=================================================

::

    >>> from __future__ import division, print_function   # Python 3

On a vu dans les chapitres précédents comment définir des fonctions avec
``def``, des boucles avec ``while`` et ``for`` et des tests avec ``if`` ainsi
que quelques exemples sur chaque notion mais indépendants des autres. Très
souvent en programmation, on a besoin d'utiliser plus tous ces outils à la
fois. C'est leur utilisation simultanée qui permet de résoudre des problèmes
très divers et de les exprimer en quelques lignes de code.

Dans ce chapitre, nous allons voir quelques exemples qui utilisent les
fonctions, les boucles et les conditions dans un même programme.

Conjecture de Syracuse
----------------------

La *suite de Syracuse* une suite d'entiers naturels définie de la manière
suivante. On part d'un nombre entier plus grand que zéro ; s’il est pair, on le
divise par 2 ; s’il est impair, on le multiplie par 3 et on ajoute 1. En
répétant l’opération, on obtient une suite d'entiers positifs dont chacun ne
dépend que de son prédécesseur. Par exemple, la suite de Syracuse du nombre 23
est:

    23, 70, 35, 106, 53, 160, 80, 40, 20, 10, 5, 16, 8, 4, 2, 1, 4, 2, 1, ...
    
Après que le nombre 1 a été atteint, la suite des valeurs (1, 4, 2, 1, 4, 2,
...) se répète indéfiniment en un cycle de longueur 3, appelé cycle trivial.

La `conjecture de Syracuse`__ est l'hypothèse selon laquelle la suite de
Syracuse de n'importe quel entier strictement positif atteint 1.  En dépit de
la simplicité de son énoncé, cette conjecture défie depuis de nombreuses années
les mathématiciens. Paul Erdos a dit à propos de la conjecture de Syracuse :
"les mathématiques ne sont pas encore prêtes pour de tels problèmes".

__ https://fr.wikipedia.org/wiki/Conjecture_de_Syracuse

::

    def syracuse(n):
        while n != 1:
            print(n, end=' ')
            if n % 2 == 0:
                n = n//2
            else:
                n = 3*n+1

::

    >>> syracuse(23)
    23 70 35 106 53 160 80 40 20 10 5 16 8 4 2
    >>> syracuse(245)
    245 736 368 184 92 46 23 70 35 106 53 160 80 40 20 10 5 16 8 4 2
    >>> syracuse(245154)
    245154 122577 367732 183866 91933 275800 137900 68950 34475 103426 51713 
    155140 77570 38785 116356 58178 29089 87268 43634 21817 65452 32726 16363
    49090 24545 73636 36818 18409 55228 27614 13807 41422 20711 62134 31067 
    93202 46601 139804 69902 34951 104854 52427 157282 78641 235924 117962 58981 
    176944 88472 44236 22118 11059 33178 16589 49768 24884 12442 6221 18664 9332 
    4666 2333 7000 3500 1750 875 2626 1313 3940 1970 985 2956 1478 739 2218 1109 
    3328 1664 832 416 208 104 52 26 13 40 20 10 5 16 8 4 2

Pouvez-vous trouver un nombre ``n`` tel que la suite de Syracuse n'atteint pas
le cycle 4-2-1?

Énumérer les diviseurs d'un nombre entier
-----------------------------------------

Une fonction qui retourne la liste des diviseurs d'un nombre entiers peut
s'écrire comme ceci en utilisant une boucle ``for`` et un test ``if``::

    def diviseurs(n):
        L = []
        for i in range(1, n+1):
            if n % i == 0:
                L.append(i)
        return L

On vérifie que la fonction marche bien::

    >>> diviseurs(12)
    [1, 2, 3, 4, 6, 12]
    >>> diviseurs(13)
    [1, 13]
    >>> diviseurs(15)
    [1, 3, 5, 15]
    >>> diviseurs(24)
    [1, 2, 3, 4, 6, 8, 12, 24]

Tester si un nombre est premier
-------------------------------

Une fonction peut en utiliser une autre. Par exemple, en utilisant la fonction
``diviseur`` que l'on a définit plus haut, on peut tester si un nombre est
premier::

    def est_premier_1(n):
        L = diviseurs(n)
        return len(L) == 2

::

    >>> est_premier_1(12)
    False
    >>> est_premier_1(13)
    True
    >>> [n for n in range(20) if est_premier_1(n)]
    [2, 3, 5, 7, 11, 13, 17, 19]

On pourrait faire plus efficace, car il suffit de vérifier la non-existence de
diviseurs inférieurs à la racine carrée de ``n``.

::

    from math import sqrt
    def est_premier(n):
        sq = int(sqrt(n))
        for i in range(2, sq):
            if n % i == 0:
                return False
        return True

En utilisant cette fonciton, on trouve que la liste des premiers nombres premiers inférieurs à 20 est::

    >>> [n for n in range(20) if est_premier(n)]
    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 11, 13, 15, 17, 19]

Le résulat est erroné! Pourquoi?

La fonction ``est_premier(8)`` retourne ``True`` en ce moment, car la racine
carrée de 8 vaut ``2.828`` et donc ``sq=int(2.828)`` est égal à ``2`` et la
boucle ne teste pas la valeur ``i=2``, car ``range(2,2)`` retourne une liste
vide. On peut corriger de la façon suivante en ajoutant un ``+1`` au bon
endroit::

    from math import sqrt
    def est_premier(n):
        sq = int(sqrt(n))
        for i in range(2, sq+1):
            if n % i == 0:
                return False
        return True

On vérifie que la fonction retourne bien que 4 et 8 ne sont pas des nombres
premiers::

    >>> [n for n in range(20) if est_premier(n)]
    [0, 1, 2, 3, 5, 7, 11, 13, 17, 19]

Mais il y a encore une erreur, car 0 et 1 ne devraient pas faire partie de la
liste. Une solution est de traiter ces deux cas de base à part::

    from math import sqrt
    def est_premier(n):
        if n == 0 or n == 1:
            return False
        sq = int(sqrt(n))
        for i in range(2, sq+1):
            if n % i == 0:
                return False
        return True

On vérifie que tout marche bien maintenant::

    >>> [n for n in range(50) if est_premier(n)]
    [2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47]

