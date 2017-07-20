Polynomials
===========

It is time to meet yet another example of a ring.

A **polynomial** is a finite collection of **terms**, all added together, where
each term is formed of a product of two things: the **coefficient**, and the
**variable**, usually :math:`x`, raised to a non-negative integer power.  For
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

The **degree** of a polynomial is the highest power of :math:`x` appearing. So
for example, the degree of :math:`5x^2 + 2x + 4` is :math:`2`, and the degree
of :math:`x^3 + 1` is :math:`3`. Notationally, we write :math:`\deg(p)` for the
degree of a polynomial :math:`p`, so e.g. :math:`\deg(5x^2 + 2x + 4) = 2`.

The coefficient of the term with the highest power is also important and
therefore has a special name: it is called the **leading coefficient**. For
example, the leading coefficient of the polynomial :math:`5x^2 + 2x + 4` is
:math:`5`. A **monic** polynomial is a polynomial whose leading coefficient is
:math:`1`.

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
:math:`1_R` respectively. Notice that if :math:`R` is a commutative ring, then
so is :math:`R[x]`; this follows from how multiplication is defined in
:math:`R[x]`.

Here are some polynomials in the ring :math:`\mathbb{Z}_3[x]`:

.. math::
  &\overline{2} \\
  &x^3 + \overline{2} \\
  &\overline{2}x^2 + x + \overline{1}

Note that we usually don't bother writing down the coefficient if it is the
multiplicative identity; the second example there could also have been written
:math:`\overline{1}x^3 + \overline{2}`.

We have already seen that :math:`R` being a commutative ring implies that
:math:`R[x]` is a commutative ring. Another similar result is that if :math:`R`
has no zero-divisors then neither does :math:`R[x]`. To see this, first notice
that if :math:`p, q \in R[x],` with :math:`p \neq 0, q \neq 0,` the leading
coefficient of :math:`pq` is equal to the product of the leading coefficients
of :math:`p` and :math:`q`. If a polynomial is nonzero then its leading
coefficient is necessarily also nonzero, so it follows that the leading
coefficients of :math:`p` and :math:`q` are both nonzero, and therefore the
leading coefficient of :math:`pq` is also nonzero (here we are using the fact
that :math:`R` has no zero-divisors). So :math:`pq` is nonzero, and we are
done.

We can neatly wrap all of this up by simply saying that if :math:`R` is an
integral domain then so is :math:`R[x]`.

Polynomial division
-------------------

Consider the ring of polynomials with coefficients in some integral domain
:math:`R`. Let :math:`p, q \in R[x]`, with :math:`q \neq 0`, and :math:`q`
monic. Then, there exists :math:`a, b \in R[x]` such that :math:`p = aq + b`,
and either :math:`\deg(b) < \deg(q)`, or :math:`b = 0`.

Depending on your philosophy and outlook, it might or might not be a problem
that the following proof of this result is non-constructive, i.e. it proves
that :math:`a` and :math:`b` exist, but it doesn't give you an algorithm for
finding them. It's also a little trickier than many of the proofs we've seen so
far, so don't worry if you can't quite get your head around it straight away.
We won't go on to do anything that requires understanding this proof; we really
just want to make sure we're aware of the result.

Anyway, to prove this result, we start by choosing a polynomial :math:`a` which
ensures that the degree of :math:`p - aq` is as small as possible. Note that it
is always possible to find such a polynomial :math:`a`, because the degree is a
nonnegative integer, and any set of nonnegative integers is guaranteed to have
a smallest element.

Let :math:`r = \deg(p - aq)`, and let `c` be the leading coefficient of
:math:`p - aq`. So the leading term of :math:`p - aq` is :math:`cx^r`. Also,
let :math:`d = \deg(q)`.

Now, suppose that :math:`r \geq d`, and consider the polynomial :math:`p - (a +
cx^{r-d})q = p - aq - (cx^{r-d})q`. Since the leading term of :math:`q` is
:math:`x^d` (by assumption), the leading term of :math:`(cx^{r-d})q` is
:math:`cx^r`. Therefore, when we subtract :math:`(cx^{r-d})q` from :math:`p -
aq`, the :math:`x^r` terms cancel and the polynomial we are left with has
degree no higher than :math:`r-1`. This is a contradiction: we chose :math:`a`
to minimise the degree of :math:`p - aq`, but here we have another polynomial
:math:`a + cx^{r-d}`, for which :math:`p - (a + cx^{r-d})q` gives us a smaller
degree still.

Because we have reached a contradiction, we can deduce that :math:`r < d`, i.e.
:math:`\deg(p - aq) < \deg(q)`. Therefore, we can define :math:`b = p - aq`,
and we are done: :math:`p = aq + b` by construction, and also either :math:`b =
0` or :math:`\deg(b) < \deg(q)`.

If we want to allow division by any nonzero polynomial, not just monic
polynomials, we need to impose one additional requirement: that :math:`R` is a
field. In this case we can divide coefficients exactly, so if we want to divide
a polynomial :math:`p` by another polynomial :math:`q`, we can multiply
:math:`q` by the multiplicative inverse of its leading coefficient to make it
monic.

.. note::
  For example, in :math:`\mathbb{R}[x]`, we can multiply the polynomial
  :math:`2x + 1` by :math:`\frac{1}{2}` to give :math:`x + \frac{1}{2}`, which
  is monic. Note that we could do this if we were working in
  :math:`\mathbb{Z}[x]`.

Let :math:`c` be the leading coefficient of :math:`q`, so that :math:`c^{-1}q`
is monic. Now we can use the previous result to divide :math:`p` by
:math:`c^{-1}q`, which tells us that there are :math:`a` and :math:`b` such
that :math:`p = c^{-1}aq + b`, with either :math:`\deg(b) < \deg(q)` or
:math:`b = 0`. With a small shift in perspective we can now say that we have
divided :math:`p` by :math:`q`, by considering the quotient to be
:math:`c^{-1}a`.

The important thing to notice is that this theorem bears a strong resemblance
to the theorem regarding integer division which we saw in the previous chapter.
So now we might ask: is there a generalisation which can unify these two
concepts? The answer is of course yes: it's called a **euclidean ring**.
