Matrices
========

Matrices are a source of many important examples of the algebraic structures we
are interested in, so we're going to get a bit more concrete in this chapter
and talk about matrices for a bit. You may already be aware that matrices have
many applications in computing; two examples that spring to my mind are 3D
graphics and machine learning.

We begin by talking about *vectors* in :math:`\mathbb{R}^n`; if you haven't
seen this before, an element of :math:`\mathbb{R}^n` is a collection of
:math:`n` elements of :math:`\mathbb{R}`. We usually write vectors in a column,
and it's also conventional to use bold symbols for vectors (to help distinguish
them from *scalars*, which are elements of :math:`\mathbb{R}`). For example:

.. math::
  \boldsymbol{x} = \begin{pmatrix}1\\0\\2\end{pmatrix}

  \boldsymbol{y} = \begin{pmatrix}4\\-2\\4\end{pmatrix}
  
  \boldsymbol{x}, \boldsymbol{y} \in \mathbb{R}^3

We define addition for :math:`\mathbb{R}^n` by adding corresponding components:

.. math::
  \boldsymbol{x} + \boldsymbol{y} &= \begin{pmatrix}1\\0\\2\end{pmatrix} + \begin{pmatrix}4\\-2\\4\end{pmatrix} \\
                                  &= \begin{pmatrix}1+4\\0+(-2)\\2+4\end{pmatrix} \\
                                  &= \begin{pmatrix}5\\-2\\6\end{pmatrix}

We can also multiply every component of a vector by some fixed number; this
operation is called *scalar multiplication:*

.. math::
  3\boldsymbol{x} &= \begin{pmatrix}3 \times 1\\3 \times 0\\3 \times 2\end{pmatrix} \\
                  &= \begin{pmatrix}3\\0\\6\end{pmatrix}

**Exercise 4.1** Show that :math:`(\mathbb{R}^3, +)` is a group: first check
the three monoid laws, and then check the additional group law. Hint: we already
know that :math:`\mathbb{R}` forms a group under normal addition. How do you
find the inverse of a vector in :math:`(\mathbb{R}^3, +)`?

There is one more vector operation we need, called the *dot product*. It
takes two vectors in :math:`\mathbb{R}^n` and produces as a result a single
element of :math:`\mathbb{R}`, by multiplying corresponding components together
and then adding all of the results:

.. math::
  \boldsymbol{x} \cdot \boldsymbol{y} &= (1 \times 4) + (0 \times -2) + (2 \times 4) \\
                                      &= 4 + 0 + 8 \\
                                      &= 12

The dot product is sometimes also called the *scalar product* because the
result is a scalar.
