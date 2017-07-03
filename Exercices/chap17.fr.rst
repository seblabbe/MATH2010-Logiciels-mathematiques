Programmation avec ``def`` + ``while`` + ``for`` + ``if``
=========================================================

Exercice 1
----------

Deux nombres premiers `p` et `q` avec `p<q` sont jumeaux si `q-p=2`. Trouver
tous les nombres premiers jumeaux inférieurs à 10000::

    sage:

Exercice 2
----------

Le nombre 6 est un nombre *parfait*, car il est égal à la somme de ses
diviseurs propres: `6=1+2+3`. Écrire une fonction ``est_parfait(n)`` qui
retourne vrai ou faux selon que le nombre ``n`` est parfait::

    sage:

Trouver les quatre nombres parfaits inférieurs à 10000::

    sage:

Trouver tous les nombres parfaits inférieurs à 1000000::

    sage:

Exercice 3: Problème de Collatz
-------------------------------

Étudier les itérations successives de la fonction `f : \N \rightarrow \N` définie par
`f(n) = 3n+1` si `n` est impair
et `f(n) = n/2` sinon::

    sage:

Jusqu'à quel nombre `n` pouvez-vous vérifier que les itérations successives
sur un entier `n` atteignent le nombre 1?::

    sage:

Exercice 4: Série harmonique
----------------------------

La quantité `1 + \frac{1}{2} + \frac{1}{3} + \frac{1}{4} + \cdots`
est-elle bornée ?::

    sage:

Même question pour `1 + \frac{1}{2^2} + \frac{1}{3^2} + \frac{1}{4^2} +
\cdots`::

    sage:

Exercice 5: `\sqrt{2}` est irrationnel
--------------------------------------

Dire que `\sqrt{2}` est irrationnel signifie qu'il n'existe aucun nombre
rationnel `\frac{a}{b}` tel que `\frac{a}{b} = \sqrt{2}`.  Autrement dit, cela
signifie il n'existe pas d'entiers strictement positifs `a` et `b` tels que
`a^2 = 2b^2`.  Vérifier cette affirmation expérimentalement::

    sage:

Exercice 6
----------

Existe-t-il deux nombres entiers positifs `x` et `y` tels que `x^2 - 61y^2 = 1` ?::

    sage:

.. 1766319049,22615398

Exercice 7
----------

Combien y a-t-il de chaînes de caractères de longueur `n`,
qui ne contiennent que les lettres ``a`` et ``b``
mais qui ne contiennent pas « ``aa`` » ?
Calculer au moins jusqu'à `n = 10`::

    sage:

Reconnaissez-vous la suite qui apparaît ?::

    sage:

Exercice 8
----------

Trouver un nombre `n` tel que `2013 \times n` ne s'écrit qu'avec des « `1` »::

    sage:

Exercice 9: Conjecture de Goldbach
----------------------------------

Écrire une fonction ``est_premier(n)`` qui renvoie ``True`` si `n` est premier
et ``False`` sinon::

    sage:

Vérifier expérimentalement l'assertion suivante : « Pour tout nombre entier pair `n \geq 4`,
il existe deux nombres premier `p \geq 2` et `q \geq 2` tels que `n = p + q`. »::

    sage:

Jusqu'à quelle valeur de `n` arrivez-vous vérifier la conjecture ?::

    sage:

Exercice 10
-----------

On pose un grain de blé sur la première case d'un échiquier (`64` cases), puis
deux sur la deuxième case, quatre sur la troisième case et `2^n` sur la `n`
ième case jusqu'à `64`. En supposant qu'un grain de riz pèse `4` grammes, quel
est la masse totale (en tonnes) du riz sur l'échiquier?  (Note: la production
mondiale de riz par an est de `738` millions de tonnes par an (2012).)::

    sage:

Exercice 11
-----------

Le nombre `2520` est le plus petit nombre divisible par `1, 2, 3, \ldots, 10`.
Quel est le plus petit nombre divisible par `1, 2, 3, \ldots, 20`?::

    sage:

Exercice 12
-----------

La somme des chiffres de `2^{15} = 32768` est égale à `3 + 2 + 7 + 6 + 8 = 26`.
Quelle est la somme des chiffres de `2^{1000}` ?::

    sage:

Exercice 13
-----------

Résoudre les premiers problèmes de https://projecteuler.net/archives::

    sage:

