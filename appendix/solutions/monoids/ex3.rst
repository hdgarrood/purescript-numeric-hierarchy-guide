Exercise 2.3
============

Let :math:`(M, *)` be a monoid, and let :math:`e, e' \in M`. Assume that
:math:`e` and :math:`e'` are both identity elements; that is,

.. math::
  \forall x \in M.\; e * x = x * e = x

  \forall x \in M.\; e' * x = x * e' = x.

Now what is the result of :math:`e * e'`? Since :math:`e` is an identity, we
must have that :math:`e * e' = e'`. Additionally, since :math:`e'` is an
identity, we must have that :math:`e * e' = e`. The only way that :math:`e *
e'` can be equal to both of these two things at once is if they are the same,
so we conclude that :math:`e = e'`, i.e. any monoid has exactly one identity
element.
