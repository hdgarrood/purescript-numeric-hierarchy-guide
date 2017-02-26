Exercise 3.1
============

If we take the monoid of the set of truth-values :math:`\{T, F\}` together with
:math:`\land`, we can write

.. math::
  F \land x = T

which is unsatisfiable; the equation does not hold for either of the two
possible values of :math:`x \in \{T, F\}`.

Another example is the monoid of strings, i.e. the ``Monoid String`` instance
in PureScript. The following equation is unsatisfiable, for any possible ``x ::
String`` value::

  "abc" <> x = "def"

One final example is the monoid :math:`(\mathbb{N}, \max)`, where
:math:`\max(x, y)` is defined to be the larger of :math:`x` and :math:`y`. Then
this equation is unsatisfiable:

.. math::
  \max(5, x) = 4

If :math:`x \leq 5`, then :math:`\max(5, x) = 5`. If :math:`x > 5`, then
:math:`\max(5, x) = x`. Either way, the result can never be :math:`4`.
