Exercise 4.1
============

We need to prove the associativity law for :math:`(\mathbb{R}^2, +)`; that is,
we need to show that :math:`\forall \boldsymbol{x}, \boldsymbol{y},
\boldsymbol{z} \in \mathbb{R}^2.\; (\boldsymbol{x} + \boldsymbol{y}) +
\boldsymbol{z} = \boldsymbol{x} + (\boldsymbol{y} + \boldsymbol{z})`.

This result follows naturally from associativity of addition in
:math:`\mathbb{R}`:

.. math::
  (
    \begin{bmatrix}x_1\\x_2\end{bmatrix} +
    \begin{bmatrix}y_1\\y_2\end{bmatrix}
  ) +
  \begin{bmatrix}z_1\\z_2\end{bmatrix}
  &=
  \begin{bmatrix}x_1 + y_1\\x_1 + y_2\end{bmatrix} +
  \begin{bmatrix}z_1\\z_2\end{bmatrix}
  \\ &=
  \begin{bmatrix}x_1 + y_1 + z_1\\x_1 + y_2 + z_2\end{bmatrix}
  \\ &=
  \begin{bmatrix}x_1\\x_2\end{bmatrix} +
  \begin{bmatrix}y_1 + z_1\\y_1 + z_2\end{bmatrix}
  \\ &=
  \begin{bmatrix}x_1\\x_2\end{bmatrix} +
  (
    \begin{bmatrix}y_1\\y_2\end{bmatrix} +
    \begin{bmatrix}z_1\\z_2\end{bmatrix}
  )
