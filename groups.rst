Groups
======

Suppose we have some arbitrary monoid :math:`(X, *)`, and we are given two
elements :math:`a, b \in X`, and we want to solve an equation of the form:

.. math::
  a * x = b

That is, we want to find some :math:`x \in X` such that the equation is
satisfied. Can we always do this?

We will start by looking at some examples. First consider :math:`(\mathbb{Z},
+)`. In this case, one example of such an equation might be this:

.. math::
  4 + x = 7

You can probably see how to solve this already: simply subtract 4 from both
sides, and you're left with this:

.. math::
  x = 7 - 4 = 3

Easy. In fact, with this monoid, we can always solve this kind of equation,
regardless of which values of :math:`a` and :math:`b` we are given: in general,
the solution is :math:`x = b - a`.

Now we consider a different monoid: :math:`(\mathbb{N}, +)`. Can we solve the
following equation with this monoid?

.. math::
  4 + x = 2

We can't! If we were working with a set which contains negative numbers, we
would be fine: in this case, the answer would be :math:`-2`. But :math:`-2` is
not an element of :math:`\mathbb{N}` (the way we write this in
mathematical notation is :math:`-2 \notin \mathbb{N}`).

**Exercise 3.1.** Can you think of another example of a monoid and an equation
involving that monoid which has no solutions? Hint: we discussed one possible
monoid in the previous chapter.

So it appears that there's some fundamental difference between
the monoids :math:`(\mathbb{Z}, +)` and :math:`(\mathbb{N}, +)`. This suggests
that there might be a way of categorising monoids, based on whether any
equation of this form can be solved. Our next task as mathematicians is to try
to make this a bit more precise!

We do this by defining a new algebraic structure called a *group*, which is a
monoid with one extra requirement. Suppose we have a monoid :math:`(X, *)`. We
say that :math:`(X, *)` is a group if and only if it satisfies this additional
law:

* *Inverses.* :math:`\forall x \in X.\; \exists y \in X.\; x * y = y * x = e`

That is, every element has an inverse, and combining an element with its
inverse gives you the identity.

:math:`(\mathbb{Z}, +)` is the first example of a group we will consider. In
this group, the inverse of :math:`1` is :math:`-1`, the inverse of :math:`-5`
is :math:`5`, and in general the inverse of :math:`x` is :math:`-x`.

:math:`(\mathbb{N}, +)` is not a group, because no positive elements have
inverses.

Uniqueness of inverses
----------------------

It turns out that in any group, every element has *exactly one* inverse. We can
prove this:

Let :math:`(X, *)` be a group, and let :math:`x \in X`. Suppose we have two
additional elements, :math:`y, z \in X`, such that :math:`y` and :math:`z` are
both inverses of :math:`x`.

Then:

1. :math:`y` is equal to :math:`y * e`, since :math:`e` is the identity
   element.
2. :math:`y * e` is in turn equal to :math:`y * (x * z)`: since :math:`x` and
   :math:`z` are inverses, we can replace :math:`e` with :math:`x * z`.
3. :math:`y * (x * z)` is equal to :math:`(y * x) * z` by the associativity
   law.
4. :math:`(y * x) * z` is equal to :math:`e * z` since :math:`x` and :math:`y`
   are inverses.
5. :math:`e * z` is just :math:`z`.

So :math:`y = z`, and therefore we have shown that any element has exactly one
inverse.

Because elements always have exactly one inverse, we can talk about *the*
inverse of an element, as opposed to just *an* inverse of an element. Also,
we can define a notation for the inverse of an element: If :math:`x \in X` and
:math:`(X, *)` is a group, then we often write the inverse of :math:`x` as
:math:`x^{-1}`. Be a little bit careful here: this isn't always the same as the
exponentiation you might have seen before. It depends on the group we're
talking about. For example, we saw that in :math:`(\mathbb{Z}, +)`,
we find the inverse of an element by multiplying it by :math:`-1`.

**Exercise 3.2.** In an arbitrary group, what is the inverse of the identity element?

Cancellation
------------

Now we go back to our original problem, except this time, we assume that
we have a group, not just a monoid. Because it's an equation, we can do the
same thing to both sides, so we will combine both sides with :math:`a^{-1}` on
the left, like this:

.. math::
  a^{-1} * a * x = a^{-1} * b

We can now cancel:

.. math::
  x = a^{-1} * b

And we have solved for :math:`x`. So, if :math:`X` is a group, then an equation
of the form :math:`a * x = b` always has exactly one solution. *Cancellation* —
the ability to move elements to the other side of equations like this — is
arguably a defining property of groups.

Groups might seem like a very simple concept but they give rise to an
astonishing amount of rather lovely mathematics. I don't want to dwell on them
too much here, because we want to get on to rings and fields and things, but
I recommend studying them in more depth if you get the chance.

In my experience, it's fairly uncommon to want a Group type class in PureScript
code, but if you do ever happen to want one, it's in the `purescript-group
library <https://pursuit.purescript.org/packages/purescript-group>`_.
