Integral domains
================

Now that you have seen a few examples of rings, we will talk about a
particular kind of ring called an *integral domain*.

There is a fact about :math:`\mathbb{R}` which you might know already, called
the **cancellation law**, which says that for any :math:`a, b, c \in
\mathbb{R}`, such that :math:`a \neq 0` and :math:`ab = ac`, it must be the
case that :math:`b = c`. We can establish this without too much effort: since
:math:`a` is nonzero, we can divide both sides of the equation :math:`ab = ac`
by :math:`a`, and this yields the desired result.

Now :math:`\mathbb{R}` is a ring, so we might now wonder if a version of the
above statement is true for all rings. In fact it is not, and at this point I
can show you two counterexamples!

First recall the ring :math:`\mathbb{Z}_{12}`. In this ring, if we let :math:`a
= \overline{6}, b = \overline{5},` and :math:`c = \overline{1}`, then :math:`a
\neq \overline{0}` and :math:`ab = ac`, but :math:`b \neq c` (check this!).

Now, consider the ring :math:`\mathrm{Mat}(2;\mathbb{R})`. In this ring, we
have

.. math::
  \begin{bmatrix} 1 & 1 \\ 1 & 1 \end{bmatrix}
  \begin{bmatrix} 0 & 0 \\ 0 & 0 \end{bmatrix}
  =
  \begin{bmatrix} 0 & 0 \\ 0 & 0 \end{bmatrix}

but also

.. math::
  \begin{bmatrix} 1 & 1 \\ 1 & 1 \end{bmatrix}
  \begin{bmatrix} -1 & -1 \\ 1 & 1 \end{bmatrix}
  =
  \begin{bmatrix} 0 & 0 \\ 0 & 0 \end{bmatrix}

so if we define

.. math::
  A = \begin{bmatrix} 1 & 1 \\ 1 & 1 \end{bmatrix}

  B = \begin{bmatrix} 0 & 0 \\ 0 & 0 \end{bmatrix}

  C = \begin{bmatrix} -1 & -1 \\ 1 & 1 \end{bmatrix}

then we have :math:`AB = AC` and :math:`A \neq 0`, but :math:`B \neq C`.

So what do we do now? Clearly the cancellation law holds for some rings, but
not all of them. Whenever we come across a new ring, or if we are just working
with some abstract ring and we don't know which specific ring it is, we would
like to be able to say whether the cancellation law holds in it.

To do this we need a new definition. Let :math:`R` be any ring, and let
:math:`a \in R` with :math:`a` nonzero. We say that :math:`a` is a
**zero-divisor** if there exists a nonzero :math:`b \in R` such that either
:math:`ab = 0` or :math:`ba = 0`.

.. note::
 In a commutative ring :math:`ab` is always equal to :math:`ba`, so it is
 redundant to say "either :math:`ab = 0` or :math:`ba = 0`"; we might as well
 just say ":math:`ab = 0`". However, we want our theory to work with
 noncommutative rings too, which is why we specify that either :math:`ab = 0`
 or :math:`ba = 0`.

**Exercise 6.1.** Show that :math:`a = \overline{3}` is a zero-divisor in
:math:`\mathbb{Z}_{12}` by finding a value :math:`b` such that :math:`ab =
\overline{0}`.

**Exercise 6.2.** Let :math:`R` be any ring. Show that the multiplicative
identity in :math:`R` cannot be a zero-divisor.

Now we can introduce integral domains; an **integral domain** is a non-zero
commutative ring which has no zero-divisors. We can equivalently define an
integral domain as a non-zero commutative ring :math:`R` in which for all
:math:`a, b \in R`, if both :math:`a \neq 0` and :math:`b \neq 0` then their
product :math:`ab \neq 0` (why?).

The natural first example of an integral domain is :math:`\mathbb{Z}`, and this
is probably where the name "integral domain" comes from.

Another example of an integral domain :math:`\mathbb{Z}_2`. Why is this an
integral domain? Well, it only has two elements: :math:`\overline{0}` and
:math:`\overline{1}`. We can immediately rule out :math:`\overline{0}`, because
that is part of the definition of a zero-divisor. We also saw in exercise 6.2
that :math:`\overline{1}` cannot be a zero-divisor of :math:`\mathbb{Z}_2`
because it is the multiplicative identity. Therefore :math:`\mathbb{Z}_2` has
no zero-divisors. It is also a commutative ring, as we saw in a previous
chapter.  Therefore :math:`\mathbb{Z}_2` is an integral domain.

One non-example which we have seen is :math:`\mathrm{Mat}(2;\mathbb{R})`. This
is not an integral domain because the matrix :math:`A` from earlier in this
chapter is a zero-divisor.

**Exercise 6.3.** Show that :math:`\mathbb{Z}_{12}` is not an integral domain
by finding a zero-divisor.

An interesting consequence of exercise 6.3 is that whether or not
:math:`\mathbb{Z}_m` is an integral domain depends on the choice of :math:`m`;
we now know that :math:`\mathbb{Z}_2` is an integral domain, but
:math:`\mathbb{Z}_12` is not.

**Exercise 6.4. (hard)** Try to establish whether :math:`\mathbb{Z}_m` is an
integral domain for a few more choices of :math:`m`. Can you think of a rule
for determining whether :math:`\mathbb{Z}_m` is an integral domain for any
given :math:`m`?

The cancellation law for integral domains
-----------------------------------------

The subheading of this paragraph probably gives the game away a bit. Well
anyway, I can reveal to you that the cancellation law holds for any integral
domain! We just need to state and prove this now.

Let :math:`R` be any integral domain. The cancellation law says that for any
:math:`a, b, c \in R`, such that :math:`a \neq 0` and :math:`ab = ac`, then
:math:`b = c`.

To prove this, suppose we have :math:`a, b, c \in R` with :math:`a \neq 0` and
:math:`ab = ac`. Then we can subtract :math:`ac` from both sides to get
:math:`ab - ac = 0`, and factor out :math:`a` on the left hand side to get
:math:`a(b - c) = 0`. Now since :math:`R` is an integral domain, and since
:math:`a \neq 0`, it must be the case that :math:`b - c = 0`, that is, :math:`b
= c`.

.. note::
  You might be wondering why this proof is different to the earlier proof I
  gave for why the cancellation law holds in :math:`\mathbb{R}`. The reason for
  this is that in :math:`\mathbb{R}`, every nonzero number has a multiplicative
  inverse, but this is not always true in an integral domain. For example,
  :math:`2` has no multiplicative inverse in :math:`\mathbb{Z}`.

