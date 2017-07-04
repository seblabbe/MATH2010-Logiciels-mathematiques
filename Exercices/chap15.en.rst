Functions ``def``
=================

Exercise 1
----------

Write a function computing the area of a triangle from the length of the three
sides::

    sage: # edit here

Exercise 2
----------

The duration of sunshine `D(\beta, d)` on a given place on Earth is given by
the formula

.. MATH::

    D(\beta,d) = 24 - \frac{24}{\pi}\arccos\left( \tan \beta \cdot
    \tan\left(\arcsin\left(\sin(\kappa)\cdot \sin\left(\frac{2\pi}{365}d
    \right)\right)\right)\right)

where `\kappa=\frac{23.44}{180}\pi` is the inclination of the eart in radian,
`d\in[0,365]` is the number of days after the spring equinox and
`\beta\in[-\pi/2,\pi/2]` is the latitude of the place in question.
Write the function ``D(beta, d)``::

    sage: # edit here

Construct the list of duration of sunshine in Marseille for the 31 days of the
month of July 2017::

    sage: # edit here

.. http://maths-au-quotidien.fr/lycee/duree.pdf
.. >>> D = 24 - S(24)/pi*acos(tan(beta)*tan(asin(sin(kappa)*sin(pi*S(2)/365*d))))
.. >>> DD = 24 - S(24)/pi*acos(tan(beta)*tan(alpha))

Exercise 3
----------

Let the sequence `u_{n+1}= \frac{1}{1+u_n^2}` with `u_0=0`.  Write a function
``U(n)`` which returns the value of `u_n`. Compute `u_{20}`::

    sage: # edit here

Exercise 4
----------

Write a function ``product_of_digits(n)`` which returns the product of the
digits of `n` written in base `10`::

    sage: # edit here

