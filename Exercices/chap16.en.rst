``while`` loop
==============

Exercise 1
----------

Write a ``while`` loop which print numbers from 0 to 20 in increasing order
without using the instruction ``if``::

    sage:

Same question but in decreasing order::

    sage:

Exercise 2
----------

What is the below program doing?

.. raw::

    a, b, c = 1, 1, 1
    while c < 11 :
        print(c, ": ", b)
        a, b, c = b, a+b, c+1

::

    sage:

Exercise 3
----------

Using a ``while`` loop, write a function ``orbit_product_of_digits(n)``
which returns the list of successive iterations of the function which returns
the product of digits, that is:

.. raw::

    [n, produit_des_chiffres(n), produit_des_chiffres(produit_des_chiffres(n)), ..., z]

until a computed number ``z<10`` is reached that can be written with only one digit::

    sage:

Can you find a number `n` such that the length of the orbit is larger than 5?::

    sage:

... larger than 10?::

    sage:

..  Conjecture: `f^k(n)` atteint un nombre < 10 en moins de k=11 iterations

Exercise 4
----------

The Taylor series of `\sin(x)` is

.. MATH::

    \sin x= \lim_{n\to\infty}\sum^{n}_{k=0} \frac{(-1)^k}{(2k+1)!} x^{2k+1} = x -
    \frac{x^3}{3!} + \frac{x^5}{5!} - \cdots

Write a function ``taylor_sin(x)`` which evaluates the Taylor series neglecting
the terms of the sums that are less than `10^{-5}` in absolute value::

    sage:
