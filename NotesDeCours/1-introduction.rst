Introduction
============

Ces notes de cours sont rédigés en fonction du nouveau cours de logiciels
mathématiques du programme de bachelier en sciences mathématiques de
l'Université de Liège. Selon la `page du département`__,

    *le nouveau cours de logiciels mathématiques a pour but de familiariser les
    étudiants à l'informatique, outil omniprésent en sciences, en entreprises
    ou encore pour l'enseignement.*

__ http://www.math.ulg.ac.be/programme.html

Donné en première année du bachelier et totalisant 10 heures d'enseignement
théorique et 20 heures de pratique, il s'agit avant tout de donner un aperçu
des possibilités offertes par les logiciels pour faire des mathématiques.

L'environnement de travail proposé pour le cours de *Logiciel mathématiques*
est l'environnement scientifique Python permettant d'atteindre les divers
objectifs du cours. En effet, le langage Python est un langage *utilisé dans
les entreprises* et sa connaissance est un atout pour les chercheurs d'emploi.
De plus, les librairies scientifiques de l'environnement Python sont des
logiciels libres permettant aux futurs enseignants d'utiliser ces outils *pour
l'enseignement dans les écoles secondaires* sans avoir à payer des licences
dispendieuses que les écoles n'ont pas les moyens de payer.

Nous utiliserons l'interface Jupyter__ développée par la communauté IPython__.
L'interface Jupyter supporte plus de 40 langages de programmation, incluant les
langages populaires en sciences comme Python, R, Julia et Scala. Notons qu'il
est possible de tester l'utilisation R ou Python à l'adresse try.jupyter.org__.
Nous nous concentrerons dans la première partie du cours sur la librairie de
calcul formel SymPy__. Tout ces outils font partie du logiciel de mathématiques
Sage__ et nous couvrirons l'équivalent des quatres premiers chapitres de
l'excellente référence libre en français *Calcul mathématique avec Sage*
[Sage]_.

__ http://jupyter.org/
__ http://ipython.org/
__ http://try.jupyter.org/
__ http://www.sympy.org/
__ http://www.sagemath.org

.. [Sage] Zimmermann, Paul, Laurent Fousse, François Maltey, Matthias
   Meulien, Marc Mezzarobba, Clément Pernet, Nicolas M. Thiéry, et al. Calcul
   mathématique avec Sage. S. l.: CreateSpace Independent Publishing Platform,
   2013. http://sagebook.gforge.inria.fr/

Jupyter et les outils que nous présenterons sont utilisés dans les grandes
compagnies (Google, Microsoft, IBM, Nasa) et universités (Berkeley,
Northwestern University, George Washington University). Elles sont aussi
utilisées par les nouveaux médias tels que BuzzFeed__ qui a publié le 18
janvier 2016 une `analyse de 26000 matchs`__ de tennis professionnels pour
identifier des joueurs soupçonnés de matchs truqués. Ou encore par des
chercheurs qui ont `étudié et modélisé le mouvement du pendule à 5 liens`__.

__ http://www.buzzfeed.com/
__ http://data.blog.lemonde.fr/2016/01/18/comment-buzzfeed-et-la-bbc-ont-analyse-26-000-matchs-de-tennis/
__ http://www.moorepants.info/blog/npendulum.html


Dans le cours, nous aborderons aussi d'autres logiciels de mathématiques
complémentaires tels que Mathematica__ et Geogebra__. Finalement, dans la
dernière partie, nous ferons une introduction à la programmation en Python.

__ https://www.wolfram.com/mathematica/
__ http://www.geogebra.org/

