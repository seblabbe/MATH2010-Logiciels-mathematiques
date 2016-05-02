Tableau de données
==================

Les données massives jouent et continueront de jouer un rôle important dans la
société du 21e siècle. Dans ce chapitre, nous ferons une introduction à une
librairie de l'environnement Python qui permet de représenter et analyser des
données. Cette librairie s'appelle pandas__, contraction des termes anglais
"panel" et "data". La librairie pandas joue le même rôle qu'un tableur comme
Microsoft Excel ou LibreOffice calc.

.. image:: images/pandas_logo.png
   :target: http://pandas.pydata.org/
   :width: 12cm

__ http://pandas.pydata.org/

Les principales structures de données de pandas sont les ``Series`` (pour
stocker des données selon une dimension) et les ``DataFrame`` (pour stocker des
données selon 2 dimensions - lignes et colonnes). On peut aussi représenter des
données selon trois dimensions ou plus avec ``Panel`` et ``Panel4D``.

Dans ce chapitre nous décrivons les tableaux de données à une et deux
dimensions. Nous verrons comment faire des calculs statistiques et des créer
des graphiques sur celles-ci. Nous verrons commencer importer et exporter des
données. Finalement, nous ferons un exemple basé sur le site de données de la
Belgique: http://data.gov.be/. On trouvera plus d'informations dans la
`documentation en ligne`__ de pandas.

__ http://pandas.pydata.org/pandas-docs/stable/

Tableau unidimensionnel de données
----------------------------------

En utilisant sympy, construisons les listes des nombres premiers inférieurs à
50::

    >>> from sympy import isprime
    >>> L = [i for i in range(50) if isprime(i)]
    >>> L
    [2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47]

La librairie pandas permet de représenter les tableaux unidimensionnels de
données appelés *séries*. Faisons un premier exemple. La liste Python de
nombres premiers ci-haut peut être transformée en une série de pandas en
faisant comme suit::

    >>> from pandas import Series
    >>> s = Series(L)
    >>> s
    0      2
    1      3
    2      5
    3      7
    4     11
    5     13
    6     17
    7     19
    8     23
    9     29
    10    31
    11    37
    12    41
    13    43
    14    47
    dtype: int64

Par défaut, les indices sont les nombres de ``0`` à ``n-1`` où ``n`` est la
taille de la liste. On peut accéder aux éléments de la série de la même façon
qu'on le fait pour les éléments d'une liste::

    >>> s[0]
    2
    >>> s[7]
    19

Afficher quelques statistiques
------------------------------

L'intérêt des séries de pandas par rapport aux listes Python de base est qu'un
grand nombres de fonctions utiles sont disponibles sur les séries de pandas et
qui retournent souvent d'autres séries. Par exemple, on peut obtenir une
brève description statistique des éléments d'une série avec la méthode
``describe()``::

    >>> s.describe()
    count    15.000000
    mean     21.866667
    std      15.338405
    min       2.000000
    25%       9.000000
    50%      19.000000
    75%      34.000000
    max      47.000000
    dtype: float64

On peut obtenir la séries des sommes cumulées des nombres premiers avec la
méthode ``cumsum()``::

    >>> s.cumsum()
    0       2
    1       5
    2      10
    3      17
    4      28
    5      41
    6      58
    7      77
    8     100
    9     129
    10    160
    11    197
    12    238
    13    281
    14    328
    dtype: int64

Il suffit de faire ``s.TOUCHE_TABULATION`` pour voir les nombreuses
possibilités offertes par pandas. On y reviendra.

Concaténation de deux séries
----------------------------

Avec pandas, il est possible de construire un tableau comportant plus d'une
colonne. Par exemple, les nombres premiers dans la première colonne et la somme
cumulée dans la deuxième. Une première façon est avec la fonction ``concat``
qui concatène deux séries::

    >>> from pandas import concat
    >>> concat([s, s.cumsum()])
    0       2
    1       3
    2       5
    3       7
    4      11
    5      13
    6      17
    7      19
    8      23
    9      29
    10     31
    11     37
    12     41
    13     43
    14     47
    0       2
    1       5
    2      10
    3      17
    4      28
    5      41
    6      58
    7      77
    8     100
    9     129
    10    160
    11    197
    12    238
    13    281
    14    328
    dtype: int64

La concaténation a été faite une en-dessous de l'autre. Ce n'est pas exactement
ce qu'on voulait. Pour spécifier que la concaténation doit être faite en
colonnes, il faut spécifier dans quelle direction (axe) ou veut concaténer les
données. On donne alors une valeur ``1`` à l'argument ``axis`` plutôt que ``0``
(la valeur par défaut) pour obtenir ce que l'on veut::

    >>> concat([s, s.cumsum()], axis=1)
         0    1
    0    2    2
    1    3    5
    2    5   10
    3    7   17
    4   11   28
    5   13   41
    6   17   58
    7   19   77
    8   23  100
    9   29  129
    10  31  160
    11  37  197
    12  41  238
    13  43  281
    14  47  328

Pour donner des titres plus parlant aux colonnes, il s'agit de spécifier une
liste de titres via l'argument ``keys``::

    >>> keys = ['Nombres premiers', 'Somme cumulée']
    >>> df = concat([s, s.cumsum()], axis=1, keys=keys)
    >>> df
        Nombres premiers  Somme cumulée
    0                  2              2
    1                  3              5
    2                  5             10
    3                  7             17
    4                 11             28
    5                 13             41
    6                 17             58
    7                 19             77
    8                 23            100
    9                 29            129
    10                31            160
    11                37            197
    12                41            238
    13                43            281
    14                47            328

Le type du tableau ci-haut est ``DataFrame`` pour tableau de données::

    sage: type(df)
    <class 'pandas.core.frame.DataFrame'>

Tableau 2-dimensionnel de données
---------------------------------

Une autre façon de créer ce tableau est en utilisant la fonction ``DataFrame``
directement::

    >>> from pandas import DataFrame

D'abord, on calcule en Python la liste des sommes cumulées::

    >>> L
    [2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47]
    >>> L_cumsum = [sum(L[:i]) for i in range(1,len(L)+1)]
    >>> L_cumsum
    [2, 5, 10, 17, 28, 41, 58, 77, 100, 129, 160, 197, 238, 281, 328]

On crée un objet de type...::
    
    >>> DataFrame({'une':L, 'deux':L_cumsum})
        deux  une
    0      2    2
    1      5    3
    2     10    5
    3     17    7
    4     28   11
    5     41   13
    6     58   17
    7     77   19
    8    100   23
    9    129   29
    10   160   31
    11   197   37
    12   238   41
    13   281   43
    14   328   47

::

    >>> DataFrame({'une':L, 'deux':L_cumsum},columns=['une','deux'])
        une  deux
    0     2     2
    1     3     5
    2     5    10
    3     7    17
    4    11    28
    5    13    41
    6    17    58
    7    19    77
    8    23   100
    9    29   129
    10   31   160
    11   37   197
    12   41   238
    13   43   281
    14   47   328

Pour faire des tableaux de données en dimensions supérieures::

    >>> from pandas import Panel,Panel4D

Afficher les premières/dernières lignes
---------------------------------------

...

Filtrer les données
-------------------

Dessiner les données
--------------------

Exporter des données
--------------------

...

Importer des données
--------------------

Exemple basé sur data.gov.be
----------------------------

Créer des 

Espérance de vie à la naissance (e0)
http://data.gov.be/en/node/15786
http://walstat.iweps.be/fichiers/donnees/200600.xls

Arbres remarquables Namur
http://data.gov.be/en/node/9979
http://opendata.digitalwallonia.be/dataset/ac46c2c9-b595-424c-8833-302b4a423fa2/resource/1289cb04-0189-495e-b10a-4d5cff907655/download/arbresremarquables.xls

Parking accessibles
http://data.gov.be/en/node/10025
http://opendata.digitalwallonia.be/dataset/af63c9c3-7d62-4ee7-bdf5-1f95072139b6/resource/a0c036a6-1cc9-4168-aa67-9fd30dcf4bf5/download/parkingshorsvoirieaccessiblesatous2013.xlsx

::

    In [1]: import pandas as pd
    In [2]: pd.read_excel('arbresremarquables.xls').head()

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

::

    In [3]: pd.read_excel('parkingshorsvoirieaccessiblesatous2013.xlsx')
    Out[3]: 
                          Nom  Nombre de places                 Adresse
    0      Parkings couverts                NaN                     NaN
    1  Parking Hôtel de Ville             350.0  rue des Dames Blanches
    2         Parking Léopold             500.0          square Léopold
    3       Parking du Centre             160.0              rue de Fer
    4           Parking Gifar             500.0      rue des Echasseurs
    5         Parking Beffroi             252.0           place d'Armes
    6                  P+R :                NaN                     NaN
    7          P+R St-Nicolas             276.0          av. Albert Ier
    8          P+R Namur Expo             475.0    av. Sergent Vrithoff


