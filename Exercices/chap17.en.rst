Programming with ``def`` + ``while`` + ``for`` + ``if``
=======================================================

Exercise 1
----------

Two prime numbers `p` and `q` with `p<q` are said *twin* if `q-p=2`. Find all
twin prime numbers below 10000::

    sage: # edit here

Exercise 2
----------

The number 6 is called a *perfect* number, because it is equal to the sum of
its proper divisors: `6=1+2+3`.  Write a function ``is_perfect(n)`` which
returns ``True`` or ``False`` whether the number ``n`` is perfect::

    sage: # edit here

Find all four perfect numbers below `10000`::

    sage: # edit here

Find all four perfect numbers below `10^6`::

    sage: # edit here

Exercise 3: Collatz Problem 
---------------------------

Study the successive iterations of the function `f : \mathbb N \rightarrow
\mathbb N` defined by `f(n) = 3n+1` if `n` is odd and `f(n) = n/2` otherwise::

    sage: # edit here

Up to which number `n` can you verify that the orbit `f^k(n)` for `k=0,1,2...`
reaches the number `1`::

    sage: # edit here

Exercise 4: harmonic series
---------------------------

Is the quantity `1 + \frac{1}{2} + \frac{1}{3} + \frac{1}{4} + \cdots`
bounded?::

    sage: # edit here

Same question for `1 + \frac{1}{2^2} + \frac{1}{3^2} + \frac{1}{4^2} +
\cdots`::

    sage: # edit here

Exercise 5: `\sqrt{2}` is irrational
------------------------------------

Saying that `\sqrt{2}` is irrational means that there is no integers `a` and
`b` such that `\frac{a}{b} = \sqrt{2}`. Equivalently, this means there is no
strictly positive integers `a` and `b` such that `a^2 = 2b^2`. Verify this
statement experimentally::

    sage: # edit here

Exercise 6
----------

Does there exist two positive integer numbers `x` and `y` such that `x^2 -
61y^2 = 1` ?::

    sage: # edit here

.. 1766319049,22615398

Exercise 7
----------

How many strings of length `n` containing only letters ``a`` and ``b`` but not
containing ``aa`` are there? Compute the value for each `n=1,2,...,10`::

    sage: # edit here

Do you know this sequence?::

    sage: # edit here

Exercise 8
----------

Find a number `n` such that `2013 \times n` can be written only with digits
`1`::

    sage: # edit here

Exercise 9: Conjecture de Goldbach
----------------------------------

Write a function ``is_prime(n)`` that returns ``True`` if `n` is prime
and ``False`` otherwise::

    sage: # edit here

Verify experimentally the following statement: « For each even integer `n \geq
4`, there exist two prime number `p \geq 2` and `q \geq 2` such that `n = p +
q` ». ::

    sage: # edit here

Up to which value of `n` are you able to verify this conjecture?::

    sage: # edit here

Exercise 10
-----------

A grain of rice is placed on the first square of a chessboard (containing `64`
boxes), then two on the second box, four on the third box and `2^n` on the
`n`-th box until `64`.  Assuming that a grain of rice weighs 4 grams, what is
the total mass (in tons) of rice on the board? 

Note: World production of rice per year is 738 million of tons (2012)::

    sage: # edit here

Exercise 11
-----------

The number `2520` is the smallest number divisible by `1, 2, 3, \ldots, 10`.
What is the smallest number divisible by `1, 2, 3, \ldots, 20`?::

    sage: # edit here

Exercise 12
-----------

The sum of the digits of `2^{15} = 32768` is equal to `3 + 2 + 7 + 6 + 8 = 26`.
What is the sum of the digits of `2^{1000}` ?::

    sage: # edit here

Exercise 13
-----------

Solve some more problems from https://projecteuler.net/archives::

    sage: # edit here

