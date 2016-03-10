
Nombres complexes en ``Python``
-------------------------------

En Python, les nombres complexes s'écrivent avec la lettre ``j`` pour
symboliser la partie imaginaire. Par exemple, le nombre complexe `2+5i` s'écrit
``2+5j`` en Python::

    In [71]: 2 + 5j
    Out[71]: (2+5j)

Attention, écrire simplement ``j`` retourne une erreur ``NameError: name 'j' is
not defined``, car la variable ``j`` n'a pas été définie. Il faut écrire
``1j``. De même, ``5*j`` retourne la même erreur, car il faut écrire ``5j``.

On vérifie que le carré du nombre imaginaire ``1j`` retourne bien ``-1``::

    In [72]: (1j) ** 2
    Out[72]: (-1+0j)

Les opérations de base sont définies sur les nombres complexes comme pour les
nombres entiers et les nombres décimaux::

    In [82]: (13 + 34j) / (3 + 4j)
    Out[82]: (7+2j)

