Rings
=====

Congratulations on getting this far — we are finally ready to introduce rings!

I will begin by reminding you of some properties that the real numbers have.

Firstly, :math:`(\mathbb{R}, +)` is an Abelian group, where the identity
element is :math:`0`.

Secondly, :math:`(\mathbb{R}, \times)` — that is, the set :math:`\mathbb{R}`
together with multiplication — is a monoid, where the identity element is
:math:`1`.

Thirdly, multiplication *distributes over* addition. What this means is that
for all :math:`x, y, z \in \mathbb{R},`

.. math::
  x(y + z) = xy + xz

  (x + y)z = xz + yz.

Now we will consider a different set: the set of truth-values :math:`\{T, F\}`,
which from now on I will call :math:`\mathrm{Bool}`. I will first introduce a
new operation on :math:`\mathrm{Bool}` called *exclusive-or* or *XOR* for
short, written :math:`\oplus`:

========= ========= =================
:math:`P` :math:`Q` :math:`P \oplus Q`
========= ========= =================
T         T         F
T         F         T
F         T         T
F         F         F
========= ========= =================

An easy way to remember this is that :math:`P \oplus Q` is true if and only if
:math:`P` is different from :math:`Q`.

Firstly, :math:`(\mathrm{Bool}, \oplus)` is an Abelian group, with identity
:math:`F` (check this yourself if you want to).

Secondly, :math:`(\mathrm{Bool}, \land)` is a monoid, with identity :math:`T`
(we saw this monoid earlier on, in the monoids chapter).

Thirdly, :math:`\land` distributes over :math:`\oplus`; that is, for all
:math:`P, Q, R \in \mathrm{Bool},`

.. math::
  P \land (Q \oplus R) = (P \land Q) \oplus (P \land R)

  (P \oplus Q) \land R = (P \land R) \oplus (Q \land R)

I also encourage you to check this for yourself. Note that there are eight
possibilities to consider, since we need to check that this works for any
choice of :math:`P, Q,` and :math:`R`.

The last set I will talk about before giving you the definition of a ring is
:math:`\mathbb{Z}_3`, the set of integers modulo :math:`3`, which we saw in the
previous chapter. Recall that :math:`\mathbb{Z}_3` has three elements:

.. math::
  \mathbb{Z}_3 = \{\overline{0}, \overline{1}, \overline{2}\}

We saw in the previous chapter how to define an addition operation on
:math:`\mathbb{Z}_3` so that :math:`(\mathbb{Z}_3, +)` is an Abelian group,
with identity :math:`\overline{0}`.

I will now reveal that we can define a multiplication operation in
:math:`\mathbb{Z}_3`, which I will write as :math:`\cdot`, like this:

.. math::
  \overline{x} \cdot \overline{y} = \overline{xy}

For example, :math:`\overline{1} \cdot \overline{2} = \overline{1 \times 2} =
\overline{2}`, and :math:`\overline{2} \cdot \overline{2} = \overline{2 \times
2} = \overline{4} = \overline{1}`.

This makes :math:`(\mathbb{Z}_3, \cdot)` into a monoid, with identity
:math:`\overline{1}`.

Finally, multiplication distributes over addition in :math:`\mathbb{Z}_3` too;
we sort of get this "for free" since we have defined multiplication and
addition in terms of normal multiplication and addition in :math:`\mathbb{Z}`.

More generally, :math:`\mathbb{Z}_m` is a ring for any positive integer
:math:`m`, with multiplication defined in exactly the same way. So for example,
in :math:`\mathbb{Z}_{12}`, we have :math:`\overline{5} \cdot \overline{6}
= \overline{30} = \overline{6}`.

The definition
--------------

Now that you have seen some examples, I will give you the definition of a ring.
A *ring* is a set :math:`R` equipped with two binary operations :math:`+` and
:math:`\cdot`, called "addition" and "multiplication" respectively, such that
the three following laws hold:

1. :math:`(R, +)` is an Abelian group.
2. :math:`(R, \cdot)` is a monoid.
3. Multiplication distributes over addition. That is, for all :math:`x, y, z
   \in R,`

.. math::
  x \cdot (y + z) = x \cdot y + x \cdot z

  (x + y) \cdot z = x \cdot z + y \cdot z.

From now on I will generally omit the :math:`\cdot` symbol and represent
multiplication by writing two symbols next to each other; that is, I will write
:math:`xy` to mean :math:`x \cdot y`.

We call the the identity element of the group :math:`(R, +)` the *additive
identity* of the ring :math:`R`. The additive identity is written as
:math:`0_R` or just :math:`0` when it's clear from context which ring :math:`R`
we are talking about. Similarly, we call the identity element of the monoid
:math:`(R, \cdot)` the *multiplicative identity* of the ring :math:`R`. The
multiplicative identity is written as :math:`1_R` or simply :math:`1` when it's
clear which ring we are using.

Since :math:`R` forms a group under addition, every element :math:`x \in R` has
an additive inverse, which we will write :math:`-x`. We also write :math:`x -
y` as a shorthand for :math:`x + (-y)`.

An important thing to note is that in a ring, multiplication need not be
commutative! A ring in which the multiplication operation is commutative is
called a *commutative ring.* So far, all the rings we have seen have
commutative, but we will soon see some examples of non-commutative rings.

One last thing that I should mention quickly: just as there is a trivial monoid
and a trivial group, there is a trivial ring with just one element, usually
written :math:`\{0\}`. This ring is called the **zero ring**. It is not very
interesting so we often rule it out by saying we a dealing with a "non-zero
ring"; this phrase is nothing more than a shorthand for "any ring but the zero
ring".

Properties of rings
-------------------

So I have just shown you three examples of rings: :math:`\mathbb{R}`,
:math:`\mathrm{Bool}`, and :math:`\mathbb{Z}_m`. I will introduce a few more
exotic examples of rings in subsequent chapters, but for now, we will establish
a few properties which all rings have.

The first property is that :math:`\forall x \in R.\; 0x = 0`. That is,
multiplying anything by :math:`0` yields :math:`0`. We will prove this using
just the ring laws, so that we know it is true for any ring.

Let :math:`R` be a ring, and let :math:`x \in R`. Then:

1. We know that :math:`0x = (0 + 0)x`, since :math:`0` is the additive
   identity, and so anything is equal to itself plus :math:`0`.
2. By the distributive law, :math:`(0 + 0)x = 0x + 0x`.
3. We now have that :math:`0x = 0x + 0x`. Because we know that :math:`R` is a
   group under addition, we can subtract :math:`0x` from both sides, yielding
   :math:`0 = 0x`, as required.

Another property which holds for all rings :math:`R` is that :math:`\forall x,
y \in R.\; (-x)y = -(xy)`. We can prove this too:

1. By distributivity, we know that :math:`xy + (-x)y = (x + (-x))y.`
2. Since :math:`-x` is the additive inverse of :math:`x`, we know that
   :math:`(x + (-x))y = 0y.`
3. We proved a moment ago that :math:`\, 0y = 0.`
4. So :math:`\, xy + (-x)y = 0; \,` subtracting :math:`xy` from both sides yields
   :math:`(-x)y = -(xy)`, as required.

**Exercise 4.1.** Let :math:`R` be a ring. Prove that :math:`(-x)(-y) = xy` for
all :math:`x, y \in R`. Maybe you will find this a satisfying explanation of
why "a minus times a minus is a plus"!

Semirings
---------

We might want to come up with a slightly weaker structure than a ring, in which
we only require that :math:`(R, +)` is a commutative monoid rather than a
group. Unfortunately, though, if we do this, our proof that anything times
:math:`0` is :math:`0` will no longer work, because in the proof we used the
fact that any ring forms a group under its addition operation.

Having multiplication by :math:`0` always produce :math:`0` is a useful
property, though, so to make sure it still holds, we add it as an extra law. We
then obtain the following:

A *semiring* is a set :math:`R` equipped with two binary operations :math:`+`
and :math:`\cdot`, called "addition" and "multiplication" respectively, such
that the three following laws hold:

1. :math:`(R, +)` is a commutative monoid.
2. :math:`(R, \cdot)` is a monoid.
3. Multiplication distributes over addition. That is, for all :math:`x, y, z
   \in R,`

.. math::
  x \cdot (y + z) = x \cdot y + x \cdot z

  (x + y) \cdot z = x \cdot z + y \cdot z.

4. Anything multiplied by :math:`0` is :math:`0`.

I won't spend much time talking about semirings in this guide. One useful fact
about semirings is that the natural numbers do form a semiring, although they
do not form a ring; recall that :math:`(\mathbb{N}, +)` is a commutative monoid
but not a group.
