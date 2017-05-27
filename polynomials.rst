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
denote the set of polynomials of coefficients in some ring :math:`R` by
:math:`R[x]`.

So, if we let :math:`R` be any ring, then :math:`R[x]` is a ring too; the
additive and multiplicative identities in :math:`R[x]` are :math:`0_R` and
:math:`1_R` respectively.
