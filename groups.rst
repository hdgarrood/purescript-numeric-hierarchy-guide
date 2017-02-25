Groups
======

Suppose we have some arbitrary monoid :math:`(M, *)`, and we are given two
elements :math:`a, b \in M`, and we want to solve an equation of the form:

.. math::
  a * x = b

That is, we want to find some :math:`x \in M` such that the equation is
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
would be fine: in this case, the answer would be :math:`-2`. But :math:`-2
\notin \mathbb{N}`.

**Exercise 3.1.** Can you think of another example of a monoid and an equation
involving that monoid which has no solutions? Hint: we discussed one possible
monoid in the previous chapter.

So it appears that there's some fundamental difference between
the monoids :math:`(\mathbb{Z}, +)` and :math:`(\mathbb{N}, +)`. This suggests
that there might be a way of categorising monoids, based on whether any
equation of this form can be solved. Our next task as mathematicians is to try
to make this a bit more precise!

We do this by defining a new algebraic structure called a *group*, which is a
monoid with one extra requirement. Suppose we have a monoid :math:`(G, *)`. We
say that :math:`(G, *)` is a group if and only if it satisfies this additional
law:

* *Inverses.* :math:`\forall g \in G.\; \exists h \in G.\; g * h = h * g = e`

That is, every element has an inverse, and combining an element with its
inverse gives you the identity.

If you're wondering why I'm using different letters now, it's nothing more than
a convention: people generally use :math:`G` to refer to some arbitrary group,
and to use lowercase letters starting from :math:`g` to refer to elements of a
group.

:math:`(\mathbb{Z}, +)` is the first example of a group we will consider. In
this group, the inverse of :math:`1` is :math:`-1`, the inverse of :math:`-5`
is :math:`5`, and in general the inverse of :math:`x` is :math:`-x`.

:math:`(\mathbb{N}, +)` is not a group, because no positive elements have
inverses.

Uniqueness of inverses
----------------------

It turns out that in any group, every element has *exactly one* inverse. We can
prove this:

Let :math:`(G, *)` be a group, and let :math:`g \in G`. Suppose we have two
additional elements, :math:`h_1, h_2 \in G`, such that :math:`h_1` and
:math:`h_2` are both inverses of :math:`g`.

Then:

1. :math:`h_1` is equal to :math:`h_1 * e`, since :math:`e` is the identity
   element.
2. :math:`h_1 * e` is in turn equal to :math:`h_1 * (g * h_2)`: since :math:`g`
   and :math:`h_2` are inverses, we can replace :math:`e` with :math:`g * h_2`.
3. :math:`h_1 * (g * h_2)` is equal to :math:`(h_1 * g) * h_2` by the
   associativity law.
4. :math:`(h_1 * g) * h_2` is equal to :math:`e * h_2` since :math:`g` and
   :math:`h_1` are inverses.
5. :math:`e * h_2` is just :math:`h_2`.

So :math:`h_1 = h_2`, and therefore we have shown that any element has exactly
one inverse.

Because elements always have exactly one inverse, we can talk about *the*
inverse of an element, as opposed to just *an* inverse of an element. Also,
we can define a notation for the inverse of an element: if :math:`g` is some
element of a group, then we often write the inverse of :math:`g` as
:math:`g^{-1}`. Be a little bit careful here: this isn't always the same as the
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

And we have solved for :math:`x`. So, if we are dealing with a group, then an
equation of the form :math:`a * x = b` always has exactly one solution.
*Cancellation* — the ability to move elements to the other side of equations
like this — is arguably a defining property of groups.

Groups might seem like a simple concept but they give rise to an astonishing
amount of rather lovely mathematics. I don't want to dwell on them too much
here, because we want to get on to rings and fields and things, but I recommend
studying them in more depth if you get the chance.

In my experience, it's fairly uncommon to want a Group type class in PureScript
code, but if you do ever happen to want one, it's in the `purescript-group
library <https://pursuit.purescript.org/packages/purescript-group>`_.
