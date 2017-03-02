Exercise 4.2
============

We need to come up with a recipe for finding the inverse of a vector in
:math:`(\mathbb{R}^2, +)`: that is, given a vector, find another vector such that
the sum of these two vectors is the the zero vector.

Suppose we have an :math:`\boldsymbol{x} \in \mathbb{R}^2`, so
:math:`\boldsymbol{x} = (x_1, x_2)`. If we add it to some other vector
:math:`\boldsymbol{y} = (y_1, y_2)`, we get :math:`(x_1 + y_1, x_2 + y_2)`.
For this sum to be equal to the zero vector we have to choose :math:`y_1, y_2`
so that the following two equations are satisfied:

.. math::
  x_1 + y_1 = 0

  x_2 + y_2 = 0

The solution is therefore

.. math::
  y_1 = -x_1

  y_2 = -x_2

or simply :math:`\boldsymbol{y} = -\boldsymbol{x}`. That is, you can invert a
vector in :math:`(\mathbb{R}^2, +)` by performing a scalar multiplication by
:math:`-1`.
