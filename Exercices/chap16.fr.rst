Boucle ``while``
================

Exercice 1
----------

Écrire une boucle ``while`` qui affiche les nombre de 0 à 20 en ordre croissant
sans utiliser l'instruction ``if``::

    sage:

Même question mais en ordre décroissant::

    sage:

Exercice 2
----------

Que fait le programme suivant?

.. raw::

    a, b, c = 1, 1, 1
    while c < 11 :
        print(c, ": ", b)
        a, b, c = b, a+b, c+1

::

    sage:

Exercice 3
----------

En utilisant une boucle ``while``, écrire une fonction
``orbite\_produit\_des\_chiffres(n)`` qui retourne la liste des itérations
successives de la fonction qui retourne le produit des chiffres:

.. raw::

    [n, produit_des_chiffres(n), produit_des_chiffres(produit_des_chiffres(n)), ..., z]

jusqu'à ce qu'un nombre calculé ``z`` s'écrive avec un seul chiffre::

    sage:

Pouvez-vous trouver un nombre `n` dont la longueur de l'orbite est plus grande
que 5?::

    sage:

plus grande que 10?::

    sage:

..  Conjecture: `f^k(n)` atteint un nombre < 10 en moins de k=11 iterations

Exercice 4
----------

La série de Taylor de `\sin(x)` est

.. MATH::

    \sin x= \lim_{n\to\infty}\sum^{n}_{k=0} \frac{(-1)^k}{(2k+1)!} x^{2k+1} = x -
    \frac{x^3}{3!} + \frac{x^5}{5!} - \cdots

Écrire une fonction ``taylor\_sin(x)`` qui évalue la série de Taylor en
négligeant les termes de la somme qui sont inférieurs à `10^{-5}` en valeur
absolue::

    sage:
