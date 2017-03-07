Exercise 5.5
============

Let :math:`\boldsymbol{a}_1, \boldsymbol{a}_2 \in \mathbb{R}^2`, and define

.. math::
  f = \boldsymbol{x} \mapsto
      \begin{bmatrix}\boldsymbol{a_1} \cdot \boldsymbol{x} \\
                     \boldsymbol{a_2} \cdot \boldsymbol{x} \end{bmatrix}

Then,

.. math::
  f(\boldsymbol{x} + \boldsymbol{y})
    &= \begin{bmatrix}
         \boldsymbol{a_1} \cdot (\boldsymbol{x} + \boldsymbol{y}) \\
         \boldsymbol{a_2} \cdot (\boldsymbol{x} + \boldsymbol{y})
       \end{bmatrix} \\
    &= \begin{bmatrix}
         \boldsymbol{a_1} \cdot \boldsymbol{x} + \boldsymbol{a_1} \cdot \boldsymbol{y} \\
         \boldsymbol{a_2} \cdot \boldsymbol{x} + \boldsymbol{a_2} \cdot \boldsymbol{y} \\
       \end{bmatrix} \\
    &= \begin{bmatrix}
         \boldsymbol{a_1} \cdot \boldsymbol{x} \\
         \boldsymbol{a_2} \cdot \boldsymbol{x}
       \end{bmatrix} +
       \begin{bmatrix}
         \boldsymbol{a_1} \cdot \boldsymbol{y} \\
         \boldsymbol{a_2} \cdot \boldsymbol{y}
       \end{bmatrix} \\
    &= f(\boldsymbol{x}) + f(\boldsymbol{y})

The important thing to note about this proof is that we are using the property
which we previously proved about the dot product, that :math:`\boldsymbol{x}
\cdot (\boldsymbol{y} + \boldsymbol{z}) = \boldsymbol{x} \cdot \boldsymbol{y} +
\boldsymbol{x} \cdot \boldsymbol{z}`.

Similarly,

.. math::

  f(k \boldsymbol{x})
    &= \begin{bmatrix}
         \boldsymbol{a_1} \cdot (k\boldsymbol{x}) \\
         \boldsymbol{a_2} \cdot (k\boldsymbol{x})
       \end{bmatrix} \\
    &= \begin{bmatrix}
         k (\boldsymbol{a_1} \cdot \boldsymbol{x}) \\
         k (\boldsymbol{a_2} \cdot \boldsymbol{x})
       \end{bmatrix} \\
    &= k \begin{bmatrix}
         \boldsymbol{a_1} \cdot \boldsymbol{x} \\
         \boldsymbol{a_2} \cdot \boldsymbol{x}
       \end{bmatrix} \\
    &= k f(\boldsymbol{x})

This argument similarly uses the other property of the dot product which we
proved a moment ago, namely that :math:`(k_1 \boldsymbol{x}) \cdot (k_2
\boldsymbol{y}) = k_1 k_2 (\boldsymbol{x} \cdot \boldsymbol{y})`.

We have proved that the two linear mapping laws hold for any such function
:math:`f`, and therefore we are done: any function defined in terms of dot
products like this is a linear mapping.
