
Fonctions ``def``
=================

Une fonction rassemble un ensemble d'instructions qui permettent d'atteindre un
certain objectif commun. Les fonctions permettent de séparer un programme en
morceaux qui correspondent à la façon dont on pense à la résolution d'un
problème.

La syntaxe pour la définition d'une fonction est::

    def FONCTION( PARAMETRES ):
        INSTRUCTIONS

La ligne d'en-tête commence avec ``def`` et se termine par un deux-points.  Le
choix du nom de la fonction suit exactement les mêmes règles que pour le choix
du nom d'une variable. Un bloc constitué d'une ou plusieurs instructions
Python, chacune indentée du même nombre d'espace (la convention est d'utiliser
4 espaces) par rapport à la ligne d'en-tête. Nous avons déjà vu la boucle
``for`` qui suit ce modèle.

Le nom de la fonction est suivi par certains paramètres entre parenthèses. La
liste des paramètres peut être vide, ou il peut contenir un certain nombre de
paramètres séparés les uns des autres par des virgules. Dans les deux cas, les
parenthèses sont nécessaires. Les paramètres spécifient les informations, le
cas échéant, que nous devons fournir pour pouvoir utiliser la nouvelle
fonction.

La ou les valeurs de retour d'une fonction sont retournées avec la commande
``return``. Par exemple, la fonction qui retourne la somme de deux valeurs
s'écrit::

    def somme(a, b):
        return a + b
    
    >>> somme(4,7)
    11

La fonction qui calcule le volume d'un parallépipède rectangle s'écrit::

    >>> def volume(largeur, hauteur, profondeur):
    ...     return largeur * hauteur * profondeur
    ...
    >>> v = volume(2,3,4)
    >>> v
    24

On peut rassemble le code sur la température de l'eau que l'on a écrit plus au
sein d'une fonction ``etat_de_leau`` qui dépend du paramètre ``temperature``::

    def etat_de_leau(temperature):
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

Cette fonction permet de tester le code sur la température de l'eau plus
facilement::

    >>> etat_de_leau(23)
    L'eau est liquide
    >>> etat_de_leau(-23)
    L'eau est solide
    >>> etat_de_leau(0)
    L'eau est en transition de phase solide-liquide
    >>> etat_de_leau(0.1)
    L'eau est liquide
    >>> etat_de_leau(102)
    L'eau est un gaz

