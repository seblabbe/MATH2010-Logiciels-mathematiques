Conditions ``if``
=================

.. contents:: **Contenu**
   :local:

::

    >>> from __future__ import division, print_function   # Python 3

Les conditions sont, avec les boucles, les éléments les plus importants de la
programmation. Elles permettent de formaliser la prise de décisions selon
l'information disposée. Faisons un exemple, supposons que nous sommes sur
l'autoroute en voiture et que l'on peut faire le plein à la prochaine sortie.
Est-ce qu'on prend la sortie ou est-ce qu'on reste sur l'autoroute? Supposons
que la variable ``reservoir`` prend une valeur entre 0 et 1 et indique le
pourcentage d'espace occupé par l'essence dans le réservoir. Une première façon
de prendre la décision pourrait s'écrire en Python::

    if reservoir < 0.15:
        print('Prendre la sortie')
    else:
        print('Rester sur l'autoroute')

Bien sûr, on pourrait aussi améliorer la prise de décision en considérant la
distance de la prochaine station d'essense et comparer avec la distance pouvant
être parcourue avec ce qui reste d'essence, etc. Mais, pour le moment,
l'important est de comprendre comment on écrit une condition simple en Python.

La forme ``if - else``
----------------------

La forme générale est la suivante::

    if <condition>:
        <code exécuté si la condition est satisfaite, i.e., True>
    else:
        <code exécuté si la condition n'est pas satisfaite, i.e., False>

La ``<condition>`` est une expression qui retourne une valeur booléenne
``True`` ou ``False``. Elle s'écrit avec un ``if`` et la ligne doit se terminer
avec les deux points ``:``. Si la condition est vérifiée, c'est-à-dire si la
condition est évaluée à ``True``, alors le code indenté de 4 espaces sous la
ligne ``if`` est exécuté. Sinon, c'est-à-dire si la condition est évaluée à
``False``, alors c'est le code indenté de 4 espaces sous la ligne ``else:`` qui
est exécuté.

La forme ``if - elif - else``
-----------------------------

Parfois, il y a plusieurs cas à tester. Il est possible d'emboîter les
conditions::

    if reservoir == 0:
        print("Panne d'essence")
    else:
        if 0 < reservoir < 0.15:
            print('Prendre la sortie')
        else:
            print('Rester sur l'autoroute')

Mais en Python, ce qui n'est pas le cas dans tous les langages de
programmation, le ``else if`` s'écrit de façon abrégée ``elif`` ce qui permet
de limiter l'indentation du code. On préférera donc écrire en Python le code
ci-haut de la façon suivante::

    if reservoir == 0:
        print("Panne d'essence")
    elif 0 < reservoir < 0.15:
        print('Prendre la sortie')
    else:
        print('Rester sur l'autoroute')

La forme ``if`` seul
--------------------

La ligne ``elif`` ou la ligne ``else`` n'est pas obligatoire car parfois on ne
veut rien faire si la condition n'est pas satisfaite. Dans ce cas, on écrit
simplement::

    if reservoir == 0:
        print("Panne d'essence")

La forme ``if - elif - ... - elif - else``
------------------------------------------

Il peut y avoir plusieurs lignes de ``elif``::

    if temperature < 0:
        print("L'eau est solide")
    elif temperature == 0:
        print("L'eau est en transition de phase solide-liquide")
    elif temperature < 100:
        print("L'eau est liquide")
    elif temperature == 100:
        print("L'eau est en transition de phase liquide-gaz")
    else:
        print("L'eau est un gaz")

Ci-haut, une seule des lignes ``print`` sera exécutée: celle qui est sous la
première condition est qui satisfaite. Attention, ici comme les conditions ne
sont pas mutuellement exclusives, l'ordre des conditions est important.

Syntaxe compacte d'une assignation conditionnelle
-------------------------------------------------

Parfois, on veut assigner à une variable une valeur qui dépend d'une condition.
Par exemple, on veut calculer le minimum de deux valeurs. On peut utiliser une
condition pour faire cette assignation::

    >>> x,y = 10, 6
    >>> if x < y:
    ...     minimum = x
    ... else:
    ...     minimum = y
    ...
    >>> minimum
    6

Python offre une syntaxe abrégée (inspirée du C) pour faire ceci::

    >>> minimum = x if x < y else y
    >>> minimum
    6

