
Boucle ``for``
==============

Les exercices ci-bas sont tirés du livre de Gérard Swinnen 
Gérard Swinnen, `Apprendre à programmer avec Python 3`__, 2012.
que vous êtes invités à consulter pour en apprendre d'avantage.

__ http://inforef.be/swi/download/apprendre_python3_5.pdf

Exercice 1
----------

Soient les listes suivantes::

    sage: t1 = [31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31]
    sage: t2 = ['Janvier', 'Février', 'Mars', 'Avril', 'Mai', 'Juin',
    ....: 'Juillet', 'Août', 'Septembre', 'Octobre', 'Novembre', 'Décembre']

En utilisant ``t1`` et ``t2`` 
créer une nouvelle liste ``t3`` qui contient
tous les éléments des deux listes en les alternant, de telle manière
que chaque nom de mois soit suivi du nombre de jours correspondant :
``['Janvier',31,'Février',28,'Mars',31, etc...]``::

    sage:

Exercice 2
----------

Dans un conte américain, huit petits canetons s’appellent respectivement :
Jack, Kack, Lack, Mack, Nack, Oack, Pack et Qack. Écrivez un petit script qui
génère tous ces noms à partir des deux chaînes suivantes::

    sage: prefixes = 'JKLMNOP'
    sage: suffixe = 'ack'

Si vous utilisez une instruction ``for ... in ...``, votre script ne devrait
comporter que deux lignes::

    sage:

Exercice 3
----------

Écrire une boucle qui affiche ceci:

.. raw::

    +++++
    ++++++++
    +++++++++++
    ++++++++++++++
    +++++++++++++++++
    ++++++++++++++++++++
    +++++++++++++++++++++++

::

    sage:


Exercice 4
----------

Une intégrale peut se calculer comme la limite d'une somme de Riemann:

.. MATH::

    \int_0^1 x^2\,dx =
    \lim_{n\to\infty}\frac{1}{n}\sum_{i=0}^n{\left(\frac{i}{n}\right)^2}

Écrire une boucle qui calcule la somme de Riemann ci-dessus pour les
valeurs de `n=10, 100, 1000, 10000`::

    sage:

Combien de chiffres après la virgule sont corrects? ::

    sage:

Comment ce nombre de chiffres évolue lorsque `n` est multiplié par 10?::

    sage:

Pour les prochains exercices, vous pouvez utiliser SymPy.

Exercice 5
----------

Écrire une boucle qui affiche la factorisation de tous les entiers de 1 à
100::

    sage:

Exercice 6
----------

Écrire une boucle qui affiche la dérivée des fonctions `f_n(x)=x^n` pour
toutes les valeurs de `n` de 1 à 20::

    sage:

Exercice 7
----------

Écrire une boucle qui affiche la primitive des fonctions `\sin(x)`,
`\cos(x)`, `\tan(x)`, `\log(x)`, `\exp(x)`, `\sinh(x)` et `\cosh(x)`::

    sage:

Exercice 8
----------

Définir une matrice carrée `A` de votre choix. Écrire une boucle qui
affiche les 10 premières puissances de la matrice `A`. Comment se
comportent les coefficients?::

    sage:


