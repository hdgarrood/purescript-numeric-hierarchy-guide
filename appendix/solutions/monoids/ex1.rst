Exercise 2.1
============

The natural numbers together with subtraction :math:`(\mathbb{N}, -)` is not a
monoid; it fails to satisfy any of the three monoid laws!

It doesn't satisfy closure because if you subtract a larger number from a
smaller number, you get a negative number (recall that there are no negative
numbers in :math:`\mathbb{N}`).

It doesn't satisfy associativity. For example:

.. math::
  (3 - 0) - 2 &= 3 - 2 \\
              &= 1

But:

.. math::
  3 - (0 - 2) &= 3 - (-2) \\
              &= 5

It fails to satisfy identity as well. To see this, we will first note that
there is only one *right identity* in this set; that is, there is only one
:math:`e \in \mathbb{N}` which makes the following equation hold for all
:math:`x \in \mathbb{N}`:

.. math::
  x - e = x

It's not too difficult to see that this :math:`e` is :math:`0`. So :math:`0` is
the only possible candidate to be the identity element thus far. But remember
that we need it to work the other way around too: to be the identity element,
we need it to be a *left identity* too; that is, it needs to satisfy the
following for all :math:`x \in \mathbb{N}`:

.. math::
  e - x = x

But if we set :math:`e` to be :math:`0`, this won't work, so :math:`0` is not a
left identity. In fact no element of :math:`\mathbb{N}` is a left identity
under subtraction.
