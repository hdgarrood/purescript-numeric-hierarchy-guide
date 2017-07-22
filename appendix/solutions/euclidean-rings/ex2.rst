Exercise 11.2
=============

Let :math:`F` be a field and let :math:`a, b \in F[x]`, with both nonzero. We
want to show that :math:`\deg(a) \leq \deg(ab)`.

Consider two nonzero polynomials :math:`a, b` and think about their product
:math:`ab`.  We already know that the leading term of :math:`ab` comes from the
product of the leading terms of :math:`a` and :math:`b`, whose powers of
:math:`x` will be :math:`\deg(a)` and :math:`\deg(b)` respectively. So the
power of :math:`x` in the leading term of :math:`ab` is :math:`\deg(a) +
\deg(b)`, i.e.  :math:`\deg(ab) = \deg(a) + \deg(b)`.

So our original inequality is equivalent to :math:`\deg(a) \leq \deg(a) +
\deg(b)` or equivalently, :math:`0 \leq \deg(b)`. But we know this to be true
already: the degree of a nonzero polynomial is always nonnegative! So we are
done.
