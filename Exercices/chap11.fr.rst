
Types de données de Python
==========================

Exercice 1
----------

Vrai ou faux.
En Python 3, toutes les opérations de base sur les entiers de type
``int`` comme 
``4 + 7``,
``4 * 7``,
``4 - 7``,
``4 / 7``
retournent un objet de type ``int``.

Exercice 2
----------

Quelle est la différence, s'il y en a une, entre les objets de la liste
``[4, 4., '4.0', "4.0", 4.0]``?

Exercice 3
----------

Est-ce que tout objet ``X`` de type ``int`` peut être
transformé en un objet de type ``str`` avec la fonction
``str(X)``?
Est-ce que tout objet ``X`` de type ``str`` peut être
transformé en un objet de type ``int`` avec la fonction
``int(X)``?

Exercice 4
----------

Trouver une opération binaire ``op`` 
telle que ``4 op 7`` retourne un objet de type ``bool``.

Exercice 5
----------

Trouver toutes les solutions de l'équation booléenne suivante où ``X``, ``Y``
valent ``True`` ou ``False``:

    ``not (not X and not Y) and not (X and Y) == True``

Peut-on simplifier cette équation?

Exercice 6
----------

Soit la chaîne de caractères ``w='logiciels mathematiques'``. 
Pour quelles valeurs entières positives et négatives de ``a`` est-ce que
``w[a]=='i'``?
Pour quelles valeurs entières positives de ``a`` et ``b`` est-ce que
``w[a:b]`` vaut ``'ciels math'``?


Exercice 7
----------

Soit la chaîne de caractères

``a = 'lundi mardi mercredi jeudi vendredi samedi dimanche'``.

En utilisant les méthodes des objets de type ``str`` (écrire ``a.`` et
appuyer sur la touche tabulations pour afficher les méthodes), trouver une
façon de créer les chaînes de caractères et listes suivantes:

    ``'LUNDI MARDI MERCREDI JEUDI VENDREDI SAMEDI DIMANCHE'``
    ``'Lundi mardi mercredi jeudi vendredi samedi dimanche'``
    ``'lundx mardx mercredx jeudx vendredx samedx dxmanche'``
    ``['lundi', 'mardi', 'mercredi', 'jeudi', 'vendredi', 'samedi', 'dimanche']``

.. % sage: a = 'lundi mardi mercredi jeudi vendredi samedi dimanche'
.. % sage: a.split()
.. % ['lundi', 'mardi', 'mercredi', 'jeudi', 'vendredi', 'samedi', 'dimanche']
.. % sage: a.upper()
.. % 'LUNDI MARDI MERCREDI JEUDI VENDREDI SAMEDI DIMANCHE'
.. % sage: a.replace(' ', '+')
.. % 'lundi+mardi+mercredi+jeudi+vendredi+samedi+dimanche'
.. % sage: a.capitalize()
.. % 'Lundi mardi mercredi jeudi vendredi samedi dimanche'


