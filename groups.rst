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

**Exercise 3.1.** Can you think of another example of a monoid :math:`M` and
elements :math:`a, b \in M` so that the equation :math:`a*x = b` has no
solutions in :math:`M`? Hint: we discussed one possible monoid in the previous
chapter.

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
and lowercase letters starting from :math:`g` to refer to elements of a group.

We often omit the :math:`*` symbol; you might see people expressing the above
property as :math:`\forall g \in G.\; \exists h \in G.\; gh = hg = e`.

:math:`(\mathbb{Z}, +)` is the first example of a group we will consider. In
this group, the inverse of :math:`1` is :math:`-1`, the inverse of :math:`-5`
is :math:`5`, and in general the inverse of :math:`x` is :math:`-x`.

:math:`(\mathbb{N}, +)` is not a group, because no positive elements have
inverses.

:math:`(\mathbb{Q}, +)` and :math:`(\mathbb{R}, +)` are both groups, and these
groups both have the same rule for finding inverses as we saw with
:math:`(\mathbb{Z}, +)`. That is, we find the inverse of an element by
multiplying by :math:`-1`.

The trivial monoid is also a group, and unsurprisingly we call it the *trivial
group*. To show that the trivial monoid is a group, we need to find an inverse
for every element. Because the trivial monoid only has one element, there's
only one element which we need to find an inverse for: :math:`e`.  Similarly
there's only one candidate for that inverse: also :math:`e`. We already know
that :math:`e * e = e` so we are good; :math:`e^{-1} = e`, and :math:`\{e\}` is
a group.

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

Because elements of a group always have exactly one inverse, we can talk about
*the* inverse of an element, as opposed to just *an* inverse of an element
(just like with identity elements of monoids). Also, we can define a notation
for the inverse of an element: if :math:`g` is some element of a group, then we
often write the inverse of :math:`g` as :math:`g^{-1}`.

.. warning::
  This notation can be a little treacherous: it isn't always the same as
  exponentiation of numbers which you have probably seen before. It depends on
  the group we're talking about. For example, we saw that in
  :math:`(\mathbb{Z}, +)`, we find the inverse of an element by negating it.
  So in :math:`(\mathbb{Z}, +)`, we could write that :math:`4^{-1} = -4`.
  Normally, however, we would expect that :math:`4^{-1}` means the same thing
  as :math:`1/4`. This ambiguity can be a bit awkward, so it's best to avoid
  this notation for inverses in cases where it can be ambiguous.

**Exercise 3.2.** In an arbitrary group, what is the inverse of the identity
element?

**Exercise 3.3.** Let :math:`G` be a group, and let :math:`g, h \in G`. Show
that :math:`g^{-1} h^{-1} = (hg)^{-1}`.

Modular arithmetic
------------------

*Finite* groups — that is, groups with a finite number of elements — are often
a little easier to deal with, so we will now talk about an example of a finite
group. Modular arithmetic is a fairly widely known concept, but we will cover
it in a slightly more rigorous way than you may have seen before; the reason I
have done this is that it will help explain other concepts further along.

Let :math:`x, y, m \in \mathbb{Z},` with :math:`m > 0`. We say that :math:`x`
is *congruent to* :math:`y` modulo :math:`m` if and only if :math:`x - y` is a
multiple of :math:`m`. In mathematical notation:

.. math::
  x \equiv y \; (\mathrm{mod} \; m) \; \Leftrightarrow \; \exists a \in \mathbb{Z}.\; x - y = am

For example, we will take :math:`m = 12`. Then, :math:`15` is congruent to
:math:`3` modulo :math:`12`, because :math:`15 - 3 = 12`. Also, :math:`27` is
congruent to :math:`3` modulo :math:`12`, because :math:`27 - 3 = 24 = 2 \times
12`.

By contrast, :math:`2` is not congruent to :math:`1` modulo :math:`12`, because
:math:`2 - 1 = 1` and :math:`1` is not an integer multiple of :math:`12`.

Note that any integer is congruent to itself modulo :math:`12`, because we say
that :math:`0` counts as an integer multiple of :math:`12`; we can take
:math:`a = 0` in the definition above and we see that :math:`0 \times 12 = 0`.

Now, we ask: given some integer :math:`x \in \mathbb{Z}`, and a modulus
:math:`m \in \mathbb{Z}, m > 0`, can we find the entire set of integers which
are congruent to :math:`x` modulo :math:`m`? For example, can we find the
entire set of integers congruent to :math:`0` modulo :math:`12`?

Before we continue, we will introduce a new notation to describe sets like
this. It is called *set-builder notation,* and it looks like this:

.. math:: \{\, y \in \mathbb{Z} \,|\, x \equiv y \; (\mathrm{mod} \; m) \,\}

Read: "the set of :math:`y` in :math:`\mathbb{Z}` such that :math:`x` is
congruent to :math:`y` modulo :math:`m`".

We will define :math:`\overline{x}` to be this set; that is:

.. math:: \overline{x} = \{\, y \in \mathbb{Z} \,|\, x \equiv y \; (\mathrm{mod} \; m) \,\}

The set :math:`\overline{x}` is called the *congruence class* of :math:`x`.

In particular, when :math:`m = 12`, we have seen that :math:`15 \in
\overline{3}`, and :math:`27 \in \overline{3}`, but :math:`2 \notin
\overline{1}`. It turns out that in this case, :math:`\overline{15}` is
actually the exact same set as :math:`\overline{3}`, and again the exact same
set as :math:`\overline{27}`.

In fact, for any :math:`x \in \mathbb{Z}`, we have that :math:`\overline{x} =
\overline{x + m}`. To prove that two sets :math:`U` and :math:`V` are the same,
we first need to show that every element of :math:`U` is an element of
:math:`V`, and then we show that every element of :math:`V` is also an element
of :math:`U`.  It's not enough to just do one of these steps; we need to do
both, because :math:`U` might be a subset of :math:`V` or vice versa, and both
steps are required to rule this out.

Therefore, we first prove that every element of :math:`\overline{x}` is also an
element of :math:`\overline{x + m}`. Let :math:`x, y \in \mathbb{Z}`, with
:math:`y \in \overline{x}`. Then, there exists an :math:`a \in \mathbb{Z}` such
that :math:`x - y = am`. Then, adding :math:`m` to both sides, we have:

.. math:: x + m - y = am + m

  (x + m) - y = (a + 1)m

That is, :math:`x + m \equiv y \; (\mathrm{mod} \; m)` and :math:`y \in
\overline{x + m}`. So if :math:`y \in \overline{x}`, then we also have that
:math:`y \in \overline{x + m}`. The second part of the proof, that is, showing
that every element of :math:`\overline{x + m}` is also an element of
:math:`\overline{x}`, is very similar: the main difference is that we subtract
:math:`m` from both sides instead of adding.

The important thing to take from all this is that there are exactly :math:`m`
such congruence classes.  We will define a set :math:`\mathbb{Z}_m` containing
all of these, which we can write as :math:`\overline{0}` up to
:math:`\overline{m-1}`:

.. math:: \mathbb{Z}_{12} = \{ \overline{0}, \overline{1}, ... , \overline{10}, \overline{11} \}

Then, for each :math:`m \in \mathbb{Z}, m > 0`, every :math:`x \in \mathbb{Z}`
is contained in exactly one element of :math:`\mathbb{Z}_{m}`. I omit a proof
of this, but it follows as a consequence of congruence modulo :math:`m` being a
particular kind of relation called an *equivalence relation.* I might expand on
equivalence relations in a future version of this guide.

We can define an addition operation on this set, too:

.. math:: \overline{x} + \overline{y} = \overline{x + y}

For example, in :math:`\mathbb{Z}_{12}`, we have that :math:`\overline{8} +
\overline{9} = \overline{8 + 9} = \overline{17} = \overline{5}`.

It turns out that this addition operation satisfies all of the group axioms, so
we have a finite group. In particular, :math:`\overline{0}` is the identity
element. Again, I won't prove this right now for the sake of expediency,
although I might put a proof in an appendix later.

**Exercise 3.4.a.** Which element of :math:`\mathbb{Z}_{12}` solves the
equation :math:`\overline{3} + \overline{x} = \overline{2}`?

**Exercise 3.4.b.** What is the additive inverse of :math:`\overline{5}` in
:math:`\mathbb{Z}_{12}`? That is, which element of :math:`\mathbb{Z}_{12}`
solves the equation :math:`\overline{5} + \overline{x} = \overline{0}`?

.. _injectivity-and-surjectivity:

Permutations
------------

We now consider another example of a finite group which arises from the monoid
:math:`(\mathrm{Maps}(X, X), \circ)`, which we saw in the previous chapter.

Firstly, a very brief interlude on functions and terminology: a *function*
sends elements in one set to elements of some other set. If a function
:math:`f` sends elements of the set :math:`X` to elements of the set :math:`Y`,
we indicate this using mathematical notation by writing :math:`f : X
\rightarrow Y`, or equivalently, :math:`f \in \mathrm{Maps}(X, Y)`. We call the
set :math:`X`, from which :math:`f` takes its argument, the *domain;* we call
the set :math:`Y`, to which :math:`f` sends those elements, the *codomain*.

The first thing to notice is that not all elements of :math:`\mathrm{Maps}(X,
X)` are *invertible;* that is, given some :math:`f \in \mathrm{Maps}(X, X)`, we
can't always find a :math:`g \in \mathrm{Maps}(X, X)` such that :math:`f \circ
g = g \circ f = e`. For example, suppose that we take :math:`X = \{A, B\}` as
before. We defined a function :math:`f_A` in the previous chapter which sends
both :math:`A` and :math:`B` to :math:`A`. To invert :math:`f_A`, we need to
come up with a rule, so that if we are given any element :math:`y \in Y`, we
can find the unique element :math:`x \in X` satisfying :math:`f_A(x) = y`. That
is, given the result of applying :math:`f_A` to something, we have to be able
to find that thing.

But this is impossible! Suppose we are told that the result of applying
:math:`f_A` to something was :math:`A`. Well, :math:`f_A` always produces
:math:`A`, regardless of what you put in, so we can't know what the original
thing was; it could just as well have been :math:`A` or :math:`B` as far as we
know.

Alternatively, suppose we are told that the result of applying :math:`f_A` to
something was :math:`B`. But :math:`f_A` never produces :math:`B` as its
result, so we certainly can't find some other element :math:`x` such that
:math:`f_A(x) = B`.

So :math:`f_A` is not invertible, and similarly, neither is :math:`f_B` (recall
that :math:`f_B` was defined similarly to :math:`f_A`, except that the result
is always :math:`B` rather than :math:`A`).

However, :math:`f_{swap}` is invertible, and its inverse is :math:`f_{swap}`
(itself).

We have a few ways of classifying functions which we need to talk about briefly
before continuing. Specifically, we need to clarify what it means for a
function to be invertible.

Injectivity
^^^^^^^^^^^

Firstly, as we saw with :math:`f_A`, we can't invert a function if it sends two
different things to the same thing. Another example: the function :math:`f :
\mathbb{R} \rightarrow \mathbb{R}` given by :math:`f (x) = x^2` sends both of
:math:`2` and :math:`-2` to :math:`4`, so it is not invertible.

Functions which don't suffer from this problem are called *injective.* We say
that a function :math:`f : X \rightarrow Y` is *injective* if and only if

.. math::
  \forall x_1, x_2 \in X.\; x_1 \neq x_2 \Rightarrow f(x_1) \neq f(x_2)

The identity function :math:`f(x) = x` is injective, as is the function
:math:`f(x) = x^3`. For functions from :math:`\mathbb{R}` to
:math:`\mathbb{R}`, a good way of thinking about injectivity is that a function
:math:`f` is injective if and only if any horizontal line drawn on a graph will
only intersect with the curve :math:`y = f(x)` *at most once* — that is, either
exactly once or not at all.

Surjectivity
^^^^^^^^^^^^

Another problem that we saw with :math:`f_A` is that we can't invert a function
if there is some element in the codomain which isn't 'hit' by the function.
That is, if there's no element :math:`y` in the codomain such that :math:`f(x)
= y` for some :math:`x` in the domain, we can't invert it, because we don't
have anything to send :math:`y` to. The function :math:`f : \mathbb{R}
\rightarrow \mathbb{R}` defined by :math:`f(x) = x^2` also suffers from this
problem: there's no real number :math:`x` such that :math:`x^2 = -1`, for
example.

We call functions that don't suffer from this problem *surjective*. We say that
a function :math:`f : X \rightarrow Y` is *surjective* if and only if

.. math::
  \forall y \in Y.\; \exists x \in X.\; f(x) = y

The functions :math:`f(x) = x` and :math:`f(x) = x^3` are surjective in
addition to being injective. Using a similar idea to the one we had with
injectivity, a function :math:`f : \mathbb{R} \rightarrow \mathbb{R}` is
surjective if and only if any horizontal line drawn on a graph will intersect
with the curve :math:`y = f(x)` *at least once.*

Bijectivity
^^^^^^^^^^^

We are now ready to say what an invertible function is: a function is
invertible if it is both injective and surjective. Functions which are both
injective and surjective are also called *bijective*.

.. note::
  You might ask what the point is of having two words, *bijective* and
  *invertible*, which mean the same thing. It might just be a historical
  accident. There is a subtle difference between these words though: the word
  'invertible' is quite general, as it can refer to many different kinds of
  objects; by contrast, 'bijective' almost always refers to functions.

If a function :math:`f : X \rightarrow Y` is bijective, then it has an
*inverse,* which we usually write as :math:`f^{-1} : Y \rightarrow X`. For the
inverse of :math:`f`, we have that :math:`f^{-1}(f(x)) = x` for all :math:`x
\in X`, and additionally :math:`f(f^{-1}(y)) = y` for all :math:`y \in Y`. In
essence, :math:`f^{-1}` undoes the effect of :math:`f`, putting us back to
where we started.

Going back to the example from the last chapter, :math:`e` and :math:`f_{swap}`
are both injective and surjective and thus bijective, while :math:`f_A` and
:math:`f_B` fail to be either injective or surjective.

The symmetric group
^^^^^^^^^^^^^^^^^^^

If :math:`X` is some finite set, and we want to make a group out of
:math:`(\mathrm{Maps}(X, X), \circ)`, all we need to do is discard the elements
of :math:`\mathrm{Maps}(X, X)` which fail to be bijective.

Because the actual set :math:`X` we choose doesn't really matter in the context
of group theory, it is conventional to use integers from :math:`1` up to
:math:`n`; that is, we take :math:`X = \{ 1, 2, ... , n \}`. Clearly, then,
this set has :math:`n` elements.

The group of permutations on this set is very important, so it has a name: it
is called the *symmetric group of degree* :math:`n`. We denote this group by
:math:`S_n`.

.. note::
  Be careful not to confuse the set :math:`\{ 1, 2, ... , n\}` with the group
  of permutations on that set, :math:`S_n`. Remember that the elements of
  :math:`S_n` are *functions*, not numbers.

**Exercise 3.5.** If :math:`n` is a positive integer, the product of all
positive integers less than or equal to :math:`n` is called :math:`n`
factorial, written :math:`n!`. Show that :math:`S_n` has :math:`n!` elements.

As for checking the group laws for :math:`S_n`: we have already shown that
:math:`(\mathrm{Maps}(X, X), \circ)` is a monoid, which means that we
get associativity "for free", since we're using the same operation as before.
The identity function is bijective, which means we don't discard it and we can
use it for the identity element in our group, and so the identity law is
satisfied too. Also, we know that bijective functions have inverses, so the
inverses law is satisfied. The only thing left to check is closure; that is, we
need to check that the composite of two bijective functions is itself
bijective. This is true, although I will not prove it here. I encourage you to
look for a proof elsewhere on the web if you're itching to see one.

Cancellation
------------

Now that we have seen a few more examples of groups, we go back to our original
problem, except this time, we assume that we have a group, not just a monoid.
That is, we let :math:`(G, *)` be some group, and let :math:`a, b \in G`. We
want to know if there is a solution to the equation

.. math::
  a * x = b

Because it's an equation, we can do the same thing to both sides, so we will
combine both sides with :math:`a^{-1}` on the left, like this:

.. math::
  a^{-1} * a * x = a^{-1} * b

We can now cancel:

.. math::
  x = a^{-1} * b

And we have solved for :math:`x`. So, if we are dealing with a group, then an
equation of the form :math:`a * x = b` always has exactly one solution.
*Cancellation* — the ability to move elements to the other side of equations
like this — is arguably a defining property of groups.

Abelian groups
--------------

Before moving on we just need to talk about one more specific kind of group.

We say that a group is an *Abelian group,* or a *commutative group,* if it
satisfies the following additional law:

* *Commutativity.* :math:`\forall g, h \in G.\; g*h = h*g`.

Almost all of the groups we have seen so far have been Abelian; in particular,
you were probably already aware that :math:`x + y = y + x` for all :math:`x, y
\in \mathbb{R}`.

The only non-Abelian groups we have seen so far are the symmetric groups: the
symmetric group of degree :math:`n` is non-Abelian whenever :math:`n \geq 3`.

It is possible to prove, although we will not do so here, that any non-Abelian
group must have at least :math:`6` elements. In fact, the symmetric group of
degree :math:`3`, that is :math:`S_3`, is the smallest possible non-Abelian
group, with exactly :math:`6` elements.

A final note on groups
----------------------

Groups might seem like a simple concept but they give rise to an astonishing
amount of rather lovely mathematics. I don't want to dwell on them too much
here, because we want to get on to rings and fields and things, but I recommend
studying them in more depth if you get the chance.

In my experience, it's fairly uncommon to want a Group type class in PureScript
code, but if you do ever happen to want one, it's in the `purescript-group
library <https://pursuit.purescript.org/packages/purescript-group>`_.
