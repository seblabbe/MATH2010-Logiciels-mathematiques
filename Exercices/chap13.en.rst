
Loop ``for``
============

Exercise 1
----------

In an american novel, eigth small ducks are respectively called:
Jack, Kack, Lack, Mack, Nack, Oack, Pack et Qack. 
Write a small script that generates all these names from the two following strings::

    sage: prefixes = 'JKLMNOP'
    sage: suffix = 'ack'

If you use instruction ``for ... in ...``, the code should contain only two lines::

    sage: # edit here

Exercise 2
----------

Write a for loop that shows this::

    sage: # something
    +++++
    ++++++++
    +++++++++++
    ++++++++++++++
    +++++++++++++++++
    ++++++++++++++++++++
    +++++++++++++++++++++++

::

    sage: # edit here

Exercise 3
----------

Let the following lists::

    sage: t1 = [31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31]
    sage: t2 = ['January', 'February', 'March', 'April', 'May', 'June',
    ....: 'July', 'August', 'September', 'October', 'November', 'December']

Using ``t1`` and ``t2`` create a new list ``t3`` containing all elements of the
two lists alternating them in such a way that each Month is followed by the
corresponding number of days, that is, ``['Janvier',31,'Février',28,'Mars',31,
etc...]``::

    sage: # edit here

Exercise 4
----------

An integral can be computed as a limit of a Riemann sum:

.. MATH::

    \int_0^1 x^2\,dx =
    \lim_{n\to\infty}\frac{1}{n}\sum_{i=0}^n{\left(\frac{i}{n}\right)^2}

Write a for loop which computes the above Riemann sum for values of `n=10, 100,
1000, 10000`::

    sage: # edit here

How many digits after the decimal are correct?::

    sage: # edit here

How is this number of digits evolves when `n` is multiplied by 10?::

    sage: # edit here

Exercise 5
----------

Write a for loop which prints the factorization for each integer from 1 to 100::

    sage: # edit here

Exercise 6
----------

Write a for loop which prints the derivates of the functions `f_n(x)=x^n` for
all values of `n` from 1 to 20::

    sage: # edit here

Exercise 7
----------

Write a for loop which prints the primitive of the functions `\sin(x)`,
`\cos(x)`, `\tan(x)`, `\log(x)`, `\exp(x)`, `\sinh(x)` and `\cosh(x)`::

    sage: # edit here

Exercise 8
----------

Define a square matrix `A` of your choice. Write a for loop which prints the
first 10 powers of the matrix `A`. How are the coefficients behaving?::

    sage: # edit here

Reference
---------

Some of the exercises here are from the book of (Gérard Swinnen, `Apprendre à
programmer avec Python 3`__, 2012) that you are invited to consult to learn
more.

__ http://inforef.be/swi/download/apprendre_python3_5.pdf

