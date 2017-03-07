Exercise 5.4
============

As in exercise 5.3, we will write the :math:`i`-th component of a vector
:math:`\boldsymbol{x}` as :math:`x_i`.

For the first identity:

.. math::
  \boldsymbol{x} \cdot (\boldsymbol{y} + \boldsymbol{z})
    &= \begin{bmatrix}x_1\\x_2\end{bmatrix} \cdot (\begin{bmatrix}y_1\\y_2\end{bmatrix} + \begin{bmatrix}z_1\\z_2\end{bmatrix}) \\
    &= \begin{bmatrix}x_1\\x_2\end{bmatrix} \cdot \begin{bmatrix}y_1+z_1\\y_2+z_2\end{bmatrix} \\
    &= x_1(y_1 + z_1) + x_2(y_2 + z_2) \\
    &= x_1y_1 + x_1z_1 + x_2y_2 + x_2z_2 \\
    &= (x_1y_1 + x_2y_2) + (x_1z_1 + x_2z_2) \\
    &= (\begin{bmatrix}x_1\\x_2\end{bmatrix} \cdot \begin{bmatrix}y_1\\y_2\end{bmatrix}) +
       (\begin{bmatrix}x_1\\x_2\end{bmatrix} \cdot \begin{bmatrix}z_1\\z_2\end{bmatrix}) \\
    &= \boldsymbol{x} \cdot \boldsymbol{y} + \boldsymbol{x} \cdot \boldsymbol{z}

For the second:

.. math::
  (k_1 \boldsymbol{x}) \cdot (k_2 \boldsymbol{y})
    &= \begin{bmatrix}k_1x_1\\k_1x_2\end{bmatrix} \cdot \begin{bmatrix}k_2y_1\\k_2y_2\end{bmatrix} \\
    &= (k_1x_1)(k_2y_1) + (k_1x_2)(k_2y_2) \\
    &= k_1 k_2 (x_1y_1 + x_2y_2) \\
    &= k_1 k_2 (\boldsymbol{x} \cdot \boldsymbol{y})
