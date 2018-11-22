Exercise 3.5
============

Let :math:`X = \{ 1, 2, ... , n \}`, and let :math:`f : X \to X` be bijective.
We wish to determine how many possibilities there are for :math:`f`. To
determine a particular choice of :math:`f`, we need to say what it does to each
element of :math:`X`:

.. math::
  f(1) = \, ???

  f(2) = \, ???

  ...

  f(n) = \, ???

We have :math:`n` choices to make: on the right-hand side of each of the above
:math:`n` equations, we need to choose an element of :math:`X`. However,
remember that the function we end up with needs to be *bijective*. That means
that each element of :math:`X` needs to appear on the right-hand side of
exactly one of these equations.

Suppose we decide to make a choice for :math:`f(1)` first. We may choose any
element of :math:`X`, so we have :math:`n` options.

Now, we decide to make a choice for :math:`f(2)`. We may choose any element of
:math:`X` other than the element we chose for :math:`f(1)`, which means we have
:math:`n-1` choices.

For :math:`f(3)`, we may choose any element of :math:`X` other than the
elements we chose for :math:`f(1)` and :math:`f(2)`, which means we have
:math:`n-3` choices.

We continue this process until we reach the end of our list of equations, at
:math:`f(n)`. At this point there will only be one element of :math:`X`
remaining which we haven't yet picked, so we have no freedom at all here: we
have to choose that element for :math:`f(n)`.

In a process which involves making a sequence of choices, the total number of
end possibilities is equal to the product of the number of possibilities for
each choice. Therefore, the number of possibilities for an arbitrary
permutation :math:`f` of :math:`X` is

.. math::
  n \times (n-1) \times (n-2) \; \times \; ... \; \times \; 2 \times 1 = n!
