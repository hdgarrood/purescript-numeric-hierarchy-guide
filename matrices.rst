Matrices
========

Matrices are a source of many important examples of rings and fields, so we're
going to get a bit more concrete in this chapter and talk about matrices for a
bit. You may already be aware that matrices have many applications in
computing; two examples that spring to my mind are 3D graphics and machine
learning.

Vectors
-------

We begin by talking about *vectors* in :math:`\mathbb{R}^n`; if you haven't
seen this before, an element of :math:`\mathbb{R}^n` is an ordered collection
of :math:`n` elements of :math:`\mathbb{R}`. We usually write vectors in a
column, and it's also conventional to use bold symbols for vectors (to help
distinguish them from *scalars*, which are elements of :math:`\mathbb{R}`). For
example:

.. math::
  \boldsymbol{x} = \begin{bmatrix}1\\0\end{bmatrix}

  \boldsymbol{y} = \begin{bmatrix}4\\-2\end{bmatrix}

  \boldsymbol{x}, \boldsymbol{y} \in \mathbb{R}^2

Sometimes it's helpful to be able to write vectors on one line, and we do so by
listing the components in parentheses, separated by commas. For example,
:math:`\boldsymbol{x} = (1, 0)`.

We define addition for :math:`\mathbb{R}^n` by adding corresponding components:

.. math::
  \boldsymbol{x} + \boldsymbol{y}
    &= \begin{bmatrix}1\\0\end{bmatrix} + \begin{bmatrix}4\\-2\end{bmatrix} \\
    &= \begin{bmatrix}1+4\\0+(-2)\end{bmatrix} \\
    &= \begin{bmatrix}5\\-2\end{bmatrix}

The identity element of vector addition is the *zero vector;* the vector which
has a zero for every component. This is quite an important vector so we have a
short-hand notation for it, which is a bold zero:

.. math::
  \boldsymbol{0} = \begin{bmatrix}0\\0\end{bmatrix}

We can also multiply every component of a vector by some fixed number. This
operation is called *scalar multiplication:*

.. math::
  3\boldsymbol{x} &= \begin{bmatrix}3 \times 1\\3 \times 0\end{bmatrix} \\
                  &= \begin{bmatrix}3\\0\end{bmatrix}

**Exercise 5.1.** We have seen that :math:`\mathbb{R}^2` is closed under vector
addition (that is, adding two vectors always gives you another vector), and
also that there is an identity element for vector addition in
:math:`\mathbb{R}^2`. Now, show that :math:`(\mathbb{R}^2, +)` is a monoid
by checking the remaining monoid law (associativity).

**Exercise 5.2.** Show that :math:`(\mathbb{R}^2, +)` is a group by explaining
how to find the inverse of an element.

A note on the previous exercise: :math:`(\mathbb{R}^n, +)` is actually a group
for any :math:`n`, not just :math:`n = 2`. We will spend the majority of this
chapter working with :math:`\mathbb{R}^2`, but everything we're doing
generalises very naturally to different choices of :math:`n`.

**Exercise 5.3.** Show that scalar multiplication distributes over vector
addition in :math:`\mathbb{R}^2`; that is, :math:`\forall \boldsymbol{x},
\boldsymbol{y} \in \mathbb{R}^2, k \in \mathbb{R}.\; k(\boldsymbol{x} +
\boldsymbol{y}) = k\boldsymbol{x} + k\boldsymbol{y}`.

There is one more vector operation we need, called the *dot product*. It
takes two vectors in :math:`\mathbb{R}^n` and produces as a result a single
element of :math:`\mathbb{R}`, by multiplying corresponding components together
and then adding all of the results:

.. math::
  \boldsymbol{x} \cdot \boldsymbol{y}
    &= \begin{bmatrix}1\\0\end{bmatrix} \cdot \begin{bmatrix}4\\-2\end{bmatrix} \\
    &= (1 \times 4) + (0 \times -2) \\
    &= 4 + 0 \\
    &= 4

The dot product is sometimes also called the *scalar product* because the
result is a scalar.

The dot product interacts nicely with the other two vector operations; the
following are true for any vectors :math:`\boldsymbol{x}, \boldsymbol{y},
\boldsymbol{z} \in \mathbb{R}^2` and scalars :math:`k_1, k_2 \in \mathbb{R}`:

.. math::
  \boldsymbol{x} \cdot (\boldsymbol{y} + \boldsymbol{z}) =
    \boldsymbol{x} \cdot \boldsymbol{y} + \boldsymbol{x} \cdot \boldsymbol{z}

  (k_1 \boldsymbol{x}) \cdot (k_2 \boldsymbol{y}) =
    k_1 k_2 (\boldsymbol{x} \cdot \boldsymbol{y})

We sometimes need to be a bit careful about keeping track of which operations
are which; in particular, note that in the first equation, we have *vector*
addition on the left hand side, but *scalar* addition on the right.

**Exercise 5.4.** Prove these two identities regarding dot products. Hint: we
already know that multiplication distributes over addition in
:math:`\mathbb{R}`; that is, :math:`\forall x, y, z \in \mathbb{R}.\; x(y + z)
= xy + xz`.

Linear mappings
---------------

Let :math:`f` be a function from :math:`\mathbb{R}^2` to :math:`\mathbb{R}^2`,
such that the following two laws are satisfied for all :math:`\boldsymbol{x},
\boldsymbol{y} \in \mathbb{R}^2, k \in \mathbb{R}`:

.. math::
  f(\boldsymbol{x} + \boldsymbol{y}) = f(\boldsymbol{x}) + f(\boldsymbol{y})

  f(k \boldsymbol{x}) = k f(\boldsymbol{x})

That is, if we have a pair of vectors and a function :math:`f` defined as
above, we can add the vectors together and then apply :math:`f`, or we can
apply :math:`f` to each of the vectors individually and then add the results
together, but in both cases we will always get the same result. Similarly if we
have a vector and a scalar, we can multiply the vector by the scalar and then
apply :math:`f`, or apply :math:`f` to the vector first and then do the scalar
multiplication on the result, but either way the we end up with the same vector.

Functions of this kind are important enough that we have a name for them:
*linear mappings*.

Here is one example of a linear mapping:

.. math::
  f(\begin{bmatrix}x_1\\x_2\end{bmatrix}) =
    \begin{bmatrix} 2x_1 + 3x_2 \\ x_1 - 2x_2 \end{bmatrix}

Try choosing a couple of vectors in :math:`\mathbb{R}^2` and checking that the
linear mapping laws are satisfied with those vectors.

Here is an example of a function which fails to be a linear mapping:

.. math::
  f(\begin{bmatrix}x_1\\x_2\end{bmatrix}) =
    \begin{bmatrix} x_1^2 \\ x_2 \end{bmatrix}

For example, if we take :math:`\boldsymbol{x} = (2, 0)` and :math:`k = 3`, then

.. math::
  f(k \boldsymbol{x}) =
    f(3 \begin{bmatrix}2\\0\end{bmatrix}) =
    f(\begin{bmatrix}6\\0\end{bmatrix}) =
    \begin{bmatrix}36\\0\end{bmatrix}

However, if we apply the function first and then do the scalar multiplication,
we get a different result:

.. math::
  k f(\boldsymbol{x}) =
    3 f(\begin{bmatrix}2\\0\end{bmatrix}) =
    3 \begin{bmatrix}4\\0\end{bmatrix} =
    \begin{bmatrix}12\\0\end{bmatrix}

Describing linear mappings with dot products
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Now, suppose we have 2 vectors :math:`\boldsymbol{a_1}, \boldsymbol{a_2}, \in
\mathbb{R}^2`. We can use these to define a function which maps vectors in
:math:`\mathbb{R}^2` to vectors in :math:`\mathbb{R}^2` like this:

.. math::
  \boldsymbol{x}
    \mapsto
    \begin{bmatrix}
      \boldsymbol{a_1} \cdot \boldsymbol{x} \\
      \boldsymbol{a_2} \cdot \boldsymbol{x} \\
    \end{bmatrix}

That is, we produce a new vector where the first component is the dot product
of :math:`\boldsymbol{a_1}` with the parameter :math:`\boldsymbol{x}`, and the
second component is the dot product of :math:`\boldsymbol{a_2}` with
:math:`\boldsymbol{x}`.

For example, let us take the following vectors for :math:`\boldsymbol{a_1}` and
:math:`\boldsymbol{a_2}`:

.. math::
  \boldsymbol{a_1} = \begin{bmatrix}1\\0\end{bmatrix}

  \boldsymbol{a_2} = \begin{bmatrix}4\\-2\end{bmatrix}

We can now define a function using them:

.. math::
  \begin{bmatrix}x_1\\x_2\end{bmatrix} \mapsto
    \begin{bmatrix}
      1x_1 + 0x_2 \\
      4x_1 - 2x_2 \\
    \end{bmatrix} =
    \begin{bmatrix}
      x_1 \\
      4x_1 - 2x_2
    \end{bmatrix}

This particular function takes :math:`(1,1)` to :math:`(1,2)`, and it takes
:math:`(2,0)` to :math:`(2, 8)` — check this!

It turns out that functions which can be defined in terms of dot products like
this are precisely linear mappings — that is, if you define a function in terms
of dot products in this way, it will always be a linear mapping, and
conversely, any linear mapping can be described in terms of dot products like
we have just done here.

**Exercise 5.5.** Show that any function defined in terms of dot products will
be a linear mapping, using previously given properties of the dot product.

**Exercise 5.6.** Show that the composition of two linear mappings is itself
a linear mapping. That is, if :math:`f` and :math:`g` are linear mappings, then
the function :math:`f \circ g`, which is defined as :math:`\boldsymbol{x}
\mapsto f(g(\boldsymbol{x}))`, is itself a linear mapping.

Representation of linear mappings as matrices
---------------------------------------------

An :math:`m \times n` matrix (read: ":math:`m` by :math:`n`") is a rectangular
array of things — usually numbers, but not always — with :math:`m` rows and
:math:`n` columns. Here is a :math:`2 \times 2` matrix:

.. math::
  \begin{bmatrix}
    1 & 2 \\
    3 & 4 \\
  \end{bmatrix}

We define matrix addition in more or less the same way as vector addition, i.e.
adding corresponding components:

.. math::
  \begin{bmatrix}
    1 & 2 \\
    3 & 4
  \end{bmatrix} +
  \begin{bmatrix}
    5 & 6 \\
    7 & 8
  \end{bmatrix} &=
  \begin{bmatrix}
    1+5 & 2+6 \\
    3+7 & 4+8
  \end{bmatrix} \\ &=
  \begin{bmatrix}
    6 & 8 \\
    10 & 12
  \end{bmatrix}

Again, there is a zero matrix which is the identity for matrix addition, and it
is also written :math:`\boldsymbol{0}`. This overloaded notation doesn't turn
out to be too much of a problem in practice, as it's usually clear from context
which is meant.

As you might expect, for any pair of natural numbers :math:`m, n
\in \mathbb{N}`, the set of :math:`m \times n` matrices forms an Abelian group
under addition. Note that matrices must have the same dimensions if you want to
be able to add them together.

We represent a linear mapping from :math:`\mathbb{R}^2` to :math:`\mathbb{R}^2`
as a matrix by taking the vectors :math:`\boldsymbol{a_1}` and
:math:`\boldsymbol{a_2}` which we used to define the linear mapping and putting
each of them in the corresponding row of the matrix. So components of
:math:`\boldsymbol{a_1}` become the first row and components of
:math:`\boldsymbol{a_2}` become the second row. Here is the matrix
representation of the example linear mapping which we saw just a moment ago:

.. math::
  \begin{bmatrix}
      1 & 0 \\
      4 & -2
  \end{bmatrix}

We can multiply a matrix by a vector by writing them next to each other; this
operation corresponds to *application* of the linear mapping to the vector:

.. math::
  \begin{bmatrix}
      1 & 0 \\
      4 & -2
  \end{bmatrix}
  \begin{bmatrix} 1 \\ 1 \end{bmatrix} =
  \begin{bmatrix} (1 \times 1) + (0 \times 1) \\ (4 \times 1) + (-2 \times 1) \end{bmatrix} =
  \begin{bmatrix} 1 \\ 2 \end{bmatrix}

We learned a moment ago that linear mappings can always be defined in terms of
dot products, and also that functions defined in terms of dot products are
linear mappings. Since a matrix is just another way of writing the vectors
:math:`\boldsymbol{a_1}` and :math:`\boldsymbol{a_2}`, matrices and linear
mappings are in one-to-one correspondence. This is very useful: if we are asked
a question about linear mappings which is difficult to answer, we can translate
it into an equivalent question about matrices (and vice versa) because of this
correspondence.  Sometimes, simply by translating a question about linear
mappings to one about matrices, we can make the answer immediately obvious,
even for questions which originally seemed very difficult.

We can generalise the operation of multiplying a matrix by a vector to allow us
to multiply matrices by other matrices. We do this by splitting the matrix on
the right hand side into columns, multiplying the matrix on the left by each of
these columns individually, and then joining up the resulting vectors so that
they form the columns of a new matrix.

For example, suppose we want to multiply these matrices:

.. math::
  A = \begin{bmatrix}
      1 & 0 \\
      4 & -2
  \end{bmatrix}

  B = \begin{bmatrix}
      1 & 5 \\
      1 & 3
  \end{bmatrix}

  AB = \;?

We start by splitting the right-hand matrix, :math:`B`, into columns:

.. math::
  \begin{bmatrix}1\\1\end{bmatrix} \;
  \begin{bmatrix}5\\3\end{bmatrix} \;

Then we multiply each of these by the left-hand matrix :math:`A`. We already
know that the result of multiplying :math:`A` by :math:`(1,1)` is
:math:`(1,2)`. The result of multiplying :math:`A` by the other column,
:math:`(5,3)`, is :math:`(5,6)` — again, I recommend checking this.  Finally we
put these columns back together:

.. math::
  AB = \begin{bmatrix}
    1 & 5 \\
    2 & 6
  \end{bmatrix}

In general, then, a product of :math:`2 \times 2` matrices looks like this:

.. math::
  \begin{bmatrix}
    a_1 & b_1 \\
    c_1 & d_1
  \end{bmatrix}
  \begin{bmatrix}
    a_2 & b_2 \\
    c_2 & d_2
  \end{bmatrix} =
  \begin{bmatrix}
    a_1 a_2 + b_1 c_2 & a_1 b_2 + b_1 d_2 \\
    c_1 a_2 + d_1 c_2 & c_1 b_2 + d_1 d_2
  \end{bmatrix}

The website http://matrixmultiplication.xyz is an interactive matrix
multiplication calculator, which you might like to play around with a bit to
get more of a feel for what is going on. I should also add that there are lots
of different ways of thinking about matrix multiplication. If what I've
described makes no sense to you, you might be able to find an alternative way
of thinking about it that works better for you with a little googling.

Matrix multiplication turns out to correspond to *composition* of linear
mappings. That is, if the matrix :math:`A` represents the linear mapping
:math:`f`, and the matrix :math:`B` represents the linear mapping :math:`g`,
then the matrix product :math:`AB` represents the linear mapping :math:`f \circ
g`.

Properties of matrix operations
-------------------------------

The set of :math:`n \times n` matrices under matrix multiplication turns out to
be a monoid:

* The result of multiplying two :math:`n \times n` matrices is always a
  :math:`n \times n` matrix.
* Matrix multiplication is associative; that is, if we have three :math:`n
  \times n` matrices :math:`A, B, C`, then :math:`(AB)C = A(BC)`.
* Matrix multiplication has an identity, called the *identity matrix*. There
  is an :math:`n \times n` identity matrix for every :math:`n \in \mathbb{N}`;
  multiplying any matrix by it gives you back the same matrix.

The question of how to prove that matrix multiplication is associative is a
very good example of one of those questions it is easy to see the answer to by
translating the question into a different one. Although possible, it is
extremely tedious to show that matrix multiplication is associative directly. A
better approach is to simply say that since matrix multiplication corresponds
to composition of linear mappings, and since function composition is
associative, matrix multiplication must be associative too.

The :math:`2 \times 2` identity matrix looks like this:

.. math::
  \begin{bmatrix}
      1 & 0 \\
      0 & 1
  \end{bmatrix}

You might like to try multiplying it with some other matrices to check that it
is indeed the identity for multiplication.

Matrix multiplication also distributes over matrix addition. That is, for
:math:`n \times n` matrices :math:`A, B, C,` we have that

.. math::
  A(B+C) = AB + AC

  (A+B)C = AC + BC

just like with real numbers. Therefore, we have seen that the three ring laws
for the set of :math:`n \times n` matrices under matrix addition and matrix
multiplication hold, and therefore this set is a ring. We denote the ring of
:math:`n \times n` matrices with entries in :math:`\mathbb{R}` by
:math:`\mathrm{Mat}(n; \mathbb{R})`.

However, unlike real numbers, matrix multiplication is not commutative. In fact
I promised to show you a non-commutative ring in the previous chapter; here it
is! With matrices, :math:`AB` does not always equal :math:`BA`. For example, if
we have

.. math::
  A = \begin{bmatrix}
      1 & 1 \\
      0 & 1
  \end{bmatrix}

  B = \begin{bmatrix}
      0 & 1 \\
      0 & 1
  \end{bmatrix},

then multiplying one way gives us

.. math::
  AB = \begin{bmatrix}
      0 & 2 \\
      0 & 1
  \end{bmatrix}

but the other way gives us

.. math::
  BA = \begin{bmatrix}
    0 & 1 \\
    0 & 1
  \end{bmatrix}.

Since matrices correspond to linear mappings, we can also conclude that linear
mappings form a noncommutative ring where the multiplication operation is
function composition. What will the addition operation be? (Hint: it's the
linear mapping analogue of matrix addition.)
