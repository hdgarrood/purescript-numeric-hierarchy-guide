Matrices
========

Matrices are a source of many important examples of the algebraic structures we
are interested in, so we're going to get a bit more concrete in this chapter
and talk about matrices for a bit. You may already be aware that matrices have
many applications in computing; two examples that spring to my mind are 3D
graphics and machine learning.

Vectors
-------

We begin by talking about *vectors* in :math:`\mathbb{R}^n`; if you haven't
seen this before, an element of :math:`\mathbb{R}^n` is a collection of
:math:`n` elements of :math:`\mathbb{R}`. We usually write vectors in a column,
and it's also conventional to use bold symbols for vectors (to help distinguish
them from *scalars*, which are elements of :math:`\mathbb{R}`). For example:

.. math::
  \boldsymbol{x} = \begin{pmatrix}1\\0\\2\end{pmatrix}

  \boldsymbol{y} = \begin{pmatrix}4\\-2\\5\end{pmatrix}

  \boldsymbol{x}, \boldsymbol{y} \in \mathbb{R}^3

We define addition for :math:`\mathbb{R}^n` by adding corresponding components:

.. math::
  \boldsymbol{x} + \boldsymbol{y}
    &= \begin{pmatrix}1\\0\\2\end{pmatrix} + \begin{pmatrix}4\\-2\\5\end{pmatrix} \\
    &= \begin{pmatrix}1+4\\0+(-2)\\2+5\end{pmatrix} \\
    &= \begin{pmatrix}5\\-2\\7\end{pmatrix}

We can also multiply every component of a vector by some fixed number; this
operation is called *scalar multiplication:*

.. math::
  3\boldsymbol{x} &= \begin{pmatrix}3 \times 1\\3 \times 0\\3 \times 2\end{pmatrix} \\
                  &= \begin{pmatrix}3\\0\\6\end{pmatrix}

**Exercise 4.1.** Show that :math:`(\mathbb{R}^3, +)` is a group: first check
the three monoid laws, and then check the additional group law. Hint: we already
know that :math:`\mathbb{R}` forms a group under normal addition. How do you
find the inverse of a vector in :math:`(\mathbb{R}^3, +)`?

A note on the previous exercise: :math:`(\mathbb{R}^n, +)` is actually a group
for any :math:`n`, not just :math:`n = 3`. We will spend the majority of this
chapter working with :math:`\mathbb{R}^3`, but everything we're doing
generalises very naturally to different choices of :math:`n`.

**Exercise 4.2.** Show that scalar multiplication distributes over vector
addition in :math:`\mathbb{R}^3`; that is, :math:`\forall \boldsymbol{x},
\boldsymbol{y} \in \mathbb{R}^3, k \in \mathbb{R}.\; k(\boldsymbol{x} +
\boldsymbol{y}) = k\boldsymbol{x} + k\boldsymbol{y}`.

There is one more vector operation we need, called the *dot product*. It
takes two vectors in :math:`\mathbb{R}^n` and produces as a result a single
element of :math:`\mathbb{R}`, by multiplying corresponding components together
and then adding all of the results:

.. math::
  \boldsymbol{x} \cdot \boldsymbol{y}
    &= \begin{pmatrix}1\\0\\2\end{pmatrix} \cdot \begin{pmatrix}4\\-2\\5\end{pmatrix} \\
    &= (1 \times 4) + (0 \times -2) + (2 \times 5) \\
    &= 4 + 0 + 10 \\
    &= 14

The dot product is sometimes also called the *scalar product* because the
result is a scalar.

The dot product interacts nicely with the other two vector operations; the
following are true for any vectors :math:`\boldsymbol{x}, \boldsymbol{y},
\boldsymbol{z} \in \mathbb{R}^3` and scalars :math:`k_1, k_2 \in \mathbb{R}`:

.. math::
  \boldsymbol{x} \cdot (\boldsymbol{y} + \boldsymbol{z}) =
    \boldsymbol{x} \cdot \boldsymbol{y} + \boldsymbol{x} \cdot \boldsymbol{z}

  (k_1 \boldsymbol{x}) \cdot (k_2 \boldsymbol{y}) =
    k_1 k_2 (\boldsymbol{x} \cdot \boldsymbol{y})

We sometimes need to be a bit careful about keeping track of which operations
are which; in particular, note that in the first equation, we have *vector*
addition on the left hand side, but *scalar* addition on the right.

**Exercise 4.3.** Prove these two identities. Hint: we already know that
multiplication distributes over addition in :math:`\mathbb{R}`; that is,
:math:`\forall x, y, z \in \mathbb{R}.\; x(y + z) = xy + xz`.

Linear mappings
---------------

Now, suppose we have 3 vectors :math:`\boldsymbol{a_1}, \boldsymbol{a_2},
\boldsymbol{a_3} \in \mathbb{R}^3`. We can use these to define a function which
maps vectors in :math:`\mathbb{R}^3` to vectors in :math:`\mathbb{R}^3` like
this:

.. math::
  \boldsymbol{x}
    \mapsto
    \begin{pmatrix}
      \boldsymbol{a_1} \cdot \boldsymbol{x} \\
      \boldsymbol{a_2} \cdot \boldsymbol{x} \\
      \boldsymbol{a_3} \cdot \boldsymbol{x}
    \end{pmatrix}

That is, we produce a new vector where the first component is the dot product
of :math:`\boldsymbol{a_1}` with the parameter :math:`\boldsymbol{x}`, the
second component is the dot product of :math:`\boldsymbol{a_2}` with
:math:`\boldsymbol{x}`, and so on.

On notation: the arrow (:math:`\mapsto`) can be read "maps to". The
mathematical notation :math:`x \mapsto x + 4` means essentially the same thing
as the PureScript code ``\x -> x + 4``, that is, it denotes a function.

Functions which can be defined in this way have some useful and interesting
properties. Let :math:`f` be a function from :math:`\mathbb{R}^3` to
:math:`\mathbb{R}^3` defined in this way; then the following are true for all
:math:`\boldsymbol{x}, \boldsymbol{y} \in \mathbb{R}^3, k \in \mathbb{R}`:

.. math::
  f(\boldsymbol{x} + \boldsymbol{y}) = f(\boldsymbol{x}) + f(\boldsymbol{y})

  f(k \boldsymbol{x}) = k f(\boldsymbol{x})

**Exercise 4.4.** Prove this, using previously given properties of the dot
product.

That is, if we have a pair of vectors and a function :math:`f` defined as
above, we can add the vectors together and then apply :math:`f`, or we can
apply :math:`f` to each of the vectors individually and then add the results
together, but in both cases we will always get the same result. Similarly if we
have a vector and a scalar, we can multiply the vector by the scalar and then
apply :math:`f`, or apply :math:`f` to the vector first and then do the scalar
multiplication on the result, but either way the we end up with the same vector.

Functions of this kind are important enough that we have a name for them:
*linear mappings*.


