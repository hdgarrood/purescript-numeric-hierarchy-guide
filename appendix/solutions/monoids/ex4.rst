Exercise 2.4
============

We check each monoid law in turn:

*Closure.* If we have two functions :math:`f, g \in \mathrm{Maps}(X, M)`, then
their star product is itself a function from :math:`X` to :math:`M`, i.e.
:math:`f \star g \in \mathrm{Maps}(X, M)`. So closure is satisfied.

*Associativity.* Let :math:`f, g, h \in \mathrm{Maps}(X, M)`. Then:

.. math::
  (f \star g) \star h
    &= (x \mapsto f(x) * g(x)) \star h \\
    &= x \mapsto (f(x) * g(x)) * h(x) \\
    &= x \mapsto f(x) * (g(x) * h(x)) \\
    &= f \star (x \mapsto g(x) * h(x)) \\
    &= f \star (g \star h)

This gets a little bit messy, but the key observation is that associativity
of the star product follows from associativity of the underlying monoid
:math:`(M, *)`. So associativity is satisfied.

*Identity.* Let :math:`\iota : X \rightarrow M` be defined by :math:`\iota(x) =
e_M`, where :math:`e_M` denotes the identity element in :math:`M`. Then, for
any :math:`f \in \mathrm{Maps}(X, M)`, we have that:

.. math::
  f \star \iota = x \mapsto f(x) * e_M = x \mapsto f(x) = f

  \iota \star f = x \mapsto e_M * f(x) = x \mapsto f(x) = f

That is, :math:`\iota` is the identity element of :math:`(\mathrm{Maps}(X, M),
\star)`. So identity is satisifed, and this completes the proof.
