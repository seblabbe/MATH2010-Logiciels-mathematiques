MISC
====

https://docs.python.org/2/library/random.html

https://github.com/sympy/sympy/wiki/Pretty-Printing


TODO: Récupérer des exemples ici:
https://github.com/sympy/sympy/wiki/External-SymPy-Media%2C-Tutorials%2C-and-Presentations

https://www.nostarch.com/doingmathwithpython

http://byumcl.bitbucket.org/bootcamp2013/labs/sympy.html

https://github.com/sympy/sympy/wiki/Quick-examples (done)

from https://github.com/sympy/sympy/wiki/SymPy-vs.-Sage

Scipy : optimisation::

    >>> from scipy.optimize import fsolve
    >>> def opt_func(x):
    ...:    return x**3 + 2*x**2 + 8
    ...:
    >>> fsolve(opt_func, -2., full_output=1)

http://docs.sympy.org/latest/modules/geometry/index.html#an-in-depth-example-pappus-hexagon-theorem
An in-depth example: Pappus’ Hexagon Theorem

From Wikipedia ([WikiPappus]):

    Given one set of collinear points AA, BB, CC, and another set of collinear
    points aa, bb, cc, then the intersection points XX, YY, ZZ of line pairs
    AbAb and aBaB, AcAc and aCaC, BcBc and bCbC are collinear.

Widgets
-------

Animation série de Taylor de sinus

Introduction à la programmation
===============================

11 Types de données de Python
12 Listes
13 Boucle for
14 Autres structures de données (n-uplets, dictionaires, ensembles)

15 Conditions
16 fonctions

itérations
Variables
affectation
expressions

Programmation
-------------

Exercice: Créer une table de multiplication (idea from Doing math with Python book)

Exercie: Calculer les racines d'un polynôme de degré 2.

Données
-------

http://walstat.iweps.be/fichiers/donnees/200600.xls

::

    In [22]: pd.read_csv('200600.csv',header=10).head()
    Out[22]: 
       Code INS     Entités administratives e0 (ans) e60 (ans) e0 hommes (ans)  \
    0      1000                    Belgique     81,2      24,4            78,2   
    1      2000                     Flandre     81,1      24,4            78,0   
    2      3000                    Wallonie     79,8      23,6            76,4   
    3      4000          Bruxelles capitale     82,0      24,9            79,2   
    4     20002  Province du Brabant Wallon     81,8      24,7            78,8   

      e60 hommes (ans) e0 femmes (ans) e60 femmes (ans)  
    0             22,1            84,1             26,5  
    1             21,8            83,8             26,4  
    2             21,1            83,1             25,8  
    3             22,6            84,6             26,9  
    4             22,4            84,6             26,7  
Arbres remarquables Namur
http://data.gov.be/en/node/9979
http://opendata.digitalwallonia.be/dataset/ac46c2c9-b595-424c-8833-302b4a423fa2/resource/1289cb04-0189-495e-b10a-4d5cff907655/download/arbresremarquables.xls

Parking accessibles
http://data.gov.be/en/node/10025
http://opendata.digitalwallonia.be/dataset/af63c9c3-7d62-4ee7-bdf5-1f95072139b6/resource/a0c036a6-1cc9-4168-aa67-9fd30dcf4bf5/download/parkingshorsvoirieaccessiblesatous2013.xlsx



