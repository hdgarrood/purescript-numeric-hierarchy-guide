The Euclidean Algorithm
=======================

We now return to the familiar world of the integers, where we will learn (or
perhaps remind ourselves) about what the **greatest common divisor** of two
integers is, and about an algorithm which allows us to compute them easily, and
why it works. This will form part of the motivation for the idea of a
**euclidean ring**, a structure which generalises the integers.

Integer division
----------------

Let :math:`a, b \in \mathbb{Z}`. We say that :math:`a` **divides** :math:`b` if
there exists some :math:`q \in \mathbb{Z}` such that :math:`aq = b`. Another
way of understanding this is that :math:`b` can be divided exactly by :math:`a`
to yield :math:`q`. Symbolically, we write :math:`a \mid b`.

For example, :math:`5 \mid 20`, and also :math:`4 \mid 20`.

Of course, we often have to deal with the less happy situation where integers
don't divide exactly into each other. All hope is not lost, though: if we have
two integers :math:`a, b`, with :math:`b > 0`, then there always exists a pair
of integers :math:`q` and :math:`r` such that :math:`a = qb + r`, and :math:`0
\leq r < b`. We usually call :math:`q` the **quotient** and we call :math:`r`
the **remainder**. You probably know already that a remainder of :math:`0`
indicates that the pair of integers we are dealing with do divide into each
other exactly.

Greatest common divisors
------------------------

If :math:`d` divides :math:`a`, and :math:`d` also divides :math:`b`, we say
that :math:`d` is a **common divisor** of :math:`a` and :math:`b`. If :math:`d`
is greater than any other common divisor of :math:`a` and :math:`b`, we say
that :math:`d` is the **greatest common divisor** of :math:`a` and :math:`b`.
This chapter is mostly concerned with finding the greatest common divisor of
any pair of integers; we can do this by using an algorithm called the Euclidean
Algorithm.

Before we go on to talk about the Euclidean Algorithm, though, we first need a
result concerning divisors. Here it comes:

Let :math:`a, b, d \in \mathbb{Z}`, and suppose that :math:`d \mid a` and that
:math:`d \mid b`.  Then, :math:`d \mid ma + nb` for any :math:`m, n \in
\mathbb{Z}`.

To prove this, we go back to the definition; we just need to find an integer
:math:`c` such that :math:`cd = ma + nb`. How might we go about that? Well we
already know that :math:`d \mid a`, so we know that there is an integer
:math:`c_1` such that :math:`c_1d = a`. We also know that :math:`d \mid b`, so
we know that there is another integer :math:`c_2` such that :math:`c_2d = b`.
It follows, then, that :math:`mc_1d = ma`, and that :math:`nc_2d = nb`. Add
these equations together and you get :math:`mc_1d + nc_2d = ma + nb`. The
distributive law allows us to rearrange the left hand side, yielding
:math:`(mc_1 + nc_2)d = ma + nb`, from which we can immediately deduce that
:math:`d \mid ma + nb`.

The Euclidean Algorithm
-----------------------

We will start by working through an example; suppose we want to find the
greatest common divisor of :math:`a = 1071` and :math:`b = 462`. Let's call
their greatest common divisor :math:`d`. So immediately we have that :math:`d
\mid 1071` and that :math:`d \mid 462`.

We start by dividing :math:`a` by :math:`b`:

.. math::
  1071 = 2 * 462 + 147

That is, we get a quotient of :math:`2` and a remainder of :math:`147`. How
does this help? Well, we now know that :math:`147 = 1071 - 2*462`. Using the
result from a moment ago, if we choose :math:`m = 1` and :math:`n = -2`, we
have that :math:`d \mid ma + nb`, that is, :math:`d \mid 147`.

We now divide :math:`462` by the remainder:

.. math::
  462 = 3 * 147 + 21

Using the same argument as before, we see that :math:`21 = 462 - 3*147` and
therefore :math:`d \mid 21`. We now divide our previous remainder by our new
remainder:

.. math::
  147 = 7 * 21

This time, it goes exactly. The significance of this is that we have found our
GCD: it is :math:`21`. Why? Well, starting from the final step and working
backwards, we now know that :math:`21 \mid 147`. Looking to the previous step,
since :math:`21 \mid 147` and :math:`21 \mid 21` (note that any integer divides
itself), we can deduce using that same result from a moment ago that :math:`21
\mid 3 * 147 + 21` i.e. :math:`21 \mid 462`. Now going back to the very first
step, we can use a similar argument to show that since :math:`21 \mid 462` and
:math:`21 \mid 147`, we have that :math:`21 \mid 1071`. So we have established
that :math:`21` is a common divisor of :math:`1071` and :math:`462`. It then
follows that :math:`d \geq 21`.

The only way that we can have :math:`d \geq 21` and :math:`d \mid 21`
simultaneously is if :math:`d = 21`, so we're done.

So the general form of the algorithm is that we keep dividing successive
remainders into each other until we find a pair that go exactly, and then the
last remainder is the greatest common divisor. In PureScript::

   gcd :: Int -> Int -> Int
   gcd a 0 = a
   gcd a b = gcd b (a `mod` b)

(note that ``a `mod` b`` computes the remainder when dividing ``a`` by ``b``.)

How do we know that the algorithm terminates, though? We refer to the theorem
from the beginning of the chapter:

.. note::
  If we have two integers :math:`a, b`, with :math:`b > 0`, then there always
  exists a pair of integers :math:`q` and :math:`r` such that :math:`a = qb + r`,
  and :math:`0 \leq r < b`.

In particular, :math:`r < b`. That is, the remainders *keep getting smaller*.
A sequence of nonnegative integers which keep getting smaller is guaranteed to
eventually reach :math:`0`, so we know that our algorithm will always terminate
and all is well.
