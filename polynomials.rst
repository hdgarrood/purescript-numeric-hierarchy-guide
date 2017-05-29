Polynomials
===========

It is time to meet yet another example of a ring.

A *polynomial* is a finite collection of *terms*, all added together, where
each term is formed of a product of two things: the *coefficient*, and the
*variable*, usually :math:`x`, raised to a non-negative integer power.  For
example, the following are all polynomials:

.. math::
  &3 \\
  &x \\
  &3x + 2 \\
  &5x^2 + 2x + 4 \\
  &x^3 + 1

Looking again at the example :math:`5x^2 + 2x + 4,` we see that it has three
terms: namely, :math:`5x^2, 2x,` and :math:`4`. The coefficients of these terms
are :math:`5, 2,` and :math:`4` respectively.

The *degree* of a polynomial is the highest power of :math:`x` appearing. So
for example, the degree of :math:`5x^2 + 2x + 4` is :math:`2`, and the degree
of :math:`x^3 + 1` is :math:`3`.

Polynomial addition and multiplication both work how you would expect. To add
two polynomials together, we simply add together the coefficients of matching
pairs of terms. So for example, we add together the coefficients of :math:`x`
to obtain the coefficient of :math:`x` in the result, we add the coefficients
of :math:`x^2` to obtain the coefficient of :math:`x^2` in the
result, and so on.  For example:

.. math::
  (5x^2 + 2x + 4) + (3x + 2)
  &= (5+0)x^2 + (2+3)x + (4+2) \\
  &= 5x^2 + 5x + 6

To multiply polynomials of just one term, we multiply the coefficients and add
the powers. For example, :math:`(6x)(7x^2) = (6 \times 7)x^{1 + 2} = 42x^3`. To
multiply polynomials with more than one term, we make use of distributivity to
break them down into sums of products of single terms, and then combine them.
For example:

.. math::
  &(5x^2 + 2x + 4)(3x + 2) \\
  &= 5x^2(3x + 2) + 2x(3x + 2) + 4(3x + 2) \\
  &= (5x^2)(3x) + (5x^2)(2) + (2x)(3x) + (2x)(2) + 4(3x) + 4(2) \\
  &= 15x^3 + 10x^2 + 6x^2 + 4x + 12x + 8 \\
  &= 15x^3 + 16x^2 + 16x + 8

In the examples we have seen so far, the coefficients have come from
:math:`\mathbb{R}`. However, we can choose coefficients from any ring. We
denote the set of polynomials with coefficients in some ring :math:`R` by
:math:`R[x]`.

So, if we let :math:`R` be any ring, then :math:`R[x]` is a ring too; the
additive and multiplicative identities in :math:`R[x]` are :math:`0_R` and
:math:`1_R` respectively.

Here are some polynomials in the ring :math:`\mathbb{Z}_3[x]`:

.. math::
  &\overline{2} \\
  &x^3 + \overline{2} \\
  &\overline{2}x^2 + x + \overline{1}

Note that we usually don't bother writing down the coefficient if it is the
multiplicative identity; the second example there could also have been written
:math:`\overline{1}x^3 + \overline{2}`.

Polynomial division
-------------------

We have seen that we can define addition and multiplication operations on
polynomials

Integer division
----------------

You may already be aware that although integers can not always be divided
exactly, they can divided in a slightly looser sense. More formally, if we have
two integers :math:`a, b`, with :math:`b \neq 0`, then there exists a pair of
integers :math:`q` and :math:`r` such that :math:`a = qb + r`, and :math:`0
\leq r < \lvert q \rvert`. We usually call :math:`q` the *quotient* and we call
:math:`r` the *remainder*. In fact :math:`q` and :math:`r` are guaranteed to be
unique; there is always exactly one choice for them which satisfies both
of the conditions listed above.

.. note::
  If :math:`x` is an integer, :math:`\lvert x \rvert` is pronounced "the
  absolute value of x", and is defined as follows:

  .. math::
    \lvert x \rvert = \begin{cases}
                        x & \mathrm{if}\; x \geq 0 \\
                        -x & \mathrm{if}\; x < 0
                      \end{cases}

Why did I suddenly start talking about integer division in a chapter about
polynomials? Well, it turns out that polynomials can sometimes be divided in a
similar way.

Polynomial division
-------------------
