Fields
======

We are finally ready to talk about one of the most important types of rings,
namely **fields**. A field is a commutative ring for which all nonzero elements
have multiplicative inverses. That is, if :math:`F` is a field, and :math:`x
\in F`, then there exists an element :math:`y \in F` such that :math:`xy = 1`.
Equivalently, we can define a field as a commutative ring for which the nonzero
elements form a group under multiplication. We usually use the notation
:math:`x^{-1}` for the multiplicative inverse of :math:`x` in a field.

Here are some examples of fields which we have already seen:

* The real numbers, :math:`\mathbb{R}`
* The rational numbers, :math:`\mathbb{Q}`
* The integers modulo :math:`2`, :math:`\mathbb{Z}_2`. Note that the
  multiplicative inverse for :math:`1` in any ring necessarily exists (it is
  also :math:`1`), and this ring has no other nonzero elements to consider, so
  it must be a field.

Here are some non-examples:

* The ring of integers, :math:`\mathbb{Z}`. This fails to be a field because
  the only nonzero elements with multiplicative inverses are :math:`1` and
  :math:`-1`; there is no integer which can be multiplied by :math:`2` to yield
  :math:`1`, for example.
* The ring of integers modulo :math:`4`, :math:`\mathbb{Z}_4`. This fails to be
  a field because the element :math:`\overline{2}` does not have a
  multiplicative inverse. We can check this exhaustively:

  .. math::
    \overline{1} * \overline{2} = \overline{2} \\
    \overline{2} * \overline{2} = \overline{0} \\
    \overline{3} * \overline{2} = \overline{2}

  None of these are equal to :math:`\overline{1}`, so we can conclude that none
  of them is a multiplicative inverse of :math:`\overline{2}`.

* The ring of :math:`2 \times 2` matrices with entries in :math:`\mathbb{R}`.
  This fails to be a field because it is non-commutative, as we have seen, and
  also because there are nonzero elements which do not have multiplicative
  inverses.

A quick diversion into set theory
---------------------------------

There are a couple of important results concerning fields which we will soon
establish, but first we need another quick diversion into set theory. This
builds upon the :ref:`injectivity-and-surjectivity` section in the chapter on
groups, so if you need a refresher now might be a good time to revisit it.

Subsets
^^^^^^^

Let :math:`A` and :math:`B` be sets. We say that :math:`A` is a **subset** of
:math:`B` if :math:`x \in A \Rightarrow x \in B`, that is, every element of
:math:`A` is also an element of `B`. Symbolically, we write :math:`A \subseteq
B`.

One consequence of this definition is that every set is a subset of itself. If
we want to rule out this case, we would say that :math:`A` is a **proper
subset** of :math:`B`, and this is written :math:`A \subset B`.

Images of functions
^^^^^^^^^^^^^^^^^^^

We call the set of elements that can be produced as a result of applying
a function :math:`f` to an element of its domain the **image** of :math:`f`.
Note that this set is necessarily a subset of the codomain; in fact, another
way of defining a surjective function is one whose image is equal to its
codomain.

Notationally, the image of a function :math:`f : X \rightarrow Y` is written as
:math:`f(X)` — this is arguably a bit of an abuse of notation, as this looks
like we're applying a function to a set, which, if we're being pedantic,
doesn't make sense — but it is defined as follows:

.. math::
  f(X) = \{\, f(x) \,|\, x \in X \,\}

So we have that :math:`f(X) \subseteq Y` is true for any function :math:`f : X
\rightarrow Y`, and also that :math:`f(X) = Y` if and only if :math:`f` is
surjective.

Injectivity and surjectivity with finite sets
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Here is an important result which we will need shortly:

* Let :math:`X` be a set with finitely many elements, and let :math:`f : X
  \rightarrow X` be a function. Then :math:`f` is injective if and only if it
  is surjective.

In this proof we will use :math:`n` to refer to the size of the set :math:`X`,
i.e. :math:`X` has :math:`n` distinct elements.

First, suppose :math:`f` is injective. That is, if :math:`x \neq y`, then
:math:`f(x) \neq f(y)`. It follows that :math:`f(X)` has at least :math:`n`
elements, as each of the :math:`n` elements of :math:`X` which we can apply
:math:`f` to is mapped to a distinct element of the codomain of :math:`f`
(which, here, is also :math:`X`). Since :math:`X` is also the codomain of
:math:`f`, we have that :math:`f(X) \subseteq X`, and in particular,
:math:`f(X)` can have no more than :math:`n` elements (since :math:`X` only has
:math:`n` elements). So :math:`f(X)` has exactly :math:`n` elements, and since
each of them is an element of :math:`X` we can conclude that :math:`f(X) = X`,
i.e. :math:`f` is surjective.

Conversely, suppose that :math:`f` is surjective, i.e. each element of
:math:`X` can be obtained by applying :math:`f` to some (possibly different)
element of :math:`X`. In this case it must be injective; if it weren't, there
would be at least two elements of :math:`X` which were mapped to the same thing
by :math:`f`, and then of the remaining :math:`n - 2` elements of :math:`X`, we
have :math:`n - 1` elements of :math:`X` to reach, which is not possible.

Okay, that's everything. Back to fields!

Every field is an integral domain
---------------------------------

This is fairly straightforward to prove. Let :math:`F` be a field, and let
:math:`a, b \in F`, with :math:`a \neq 0`. Suppose :math:`ab = 0`. Since
:math:`F` is a field, :math:`a^{-1}` exists. Multiplying both sides by
:math:`a^{-1}` yields :math:`a^{-1}ab = a^{-1}0`, which simplifies to :math:`b
= 0`. That is, :math:`F` has no zero-divisors. We have by assumption that
:math:`F` is commutative (since this is one of the requirements for a field)
and therefore :math:`F` is an integral domain.

This gives us a useful trick for determining whether some ring is a field or
not: since all fields are integral domains, we can immediately deduce that a
ring cannot be a field if it fails to be an integral domain, e.g. if it has any
zero-divisors. Note that for two of the three non-examples of fields listed
earlier, namely :math:`\mathbb{Z}_4` and :math:`\mathrm{Mat}(2;\mathbb{R})`, it
can be shown that they are not fields in this way.

Let's do a quick recap on the hierarchy we have seen so far; we have:

* rings :math:`\supset` commutative rings :math:`\supset` integral domains
  :math:`\supset` fields.

That is, every commutative ring is a ring (but not every ring is
commutative), every integral domain is a commutative ring (but not every
commutative ring is an integral domain), and so on.

Every finite integral domain is a field
---------------------------------------

This is slightly more difficult to prove, so don't worry if the proof doesn't
make complete sense to you at first.

Let :math:`R` be a finite integral domain, and let :math:`a \in R` with
:math:`a \neq 0`. Now, define a function :math:`\lambda_a : R \rightarrow R` by
:math:`\lambda_a(x) = ax`, that is, the function :math:`\lambda_a` represents
multiplication by :math:`a`. Now let :math:`b, c \in R`, and notice that the
cancellation law for integral domains tells us that :math:`ab = ac` implies
:math:`b = c`. That is, if :math:`\lambda_a(b) = \lambda_a(c)`, then :math:`b =
c`. This is precisely what it means for the function :math:`\lambda_a` to be
injective.

Using our previously established result that an injective function on a finite
set must also be surjective, we can deduce that :math:`\lambda_a` is
surjective, and consequently also bijective. Therefore, it must have an inverse
function :math:`\lambda_a^{-1}`, and in particular if we let :math:`d =
\lambda_a^{-1}(1)`, then we have that :math:`ad = 1`, i.e. :math:`d` is a
multiplicative inverse for :math:`a`.

We have now found a multiplicative inverse for every nonzero element of
:math:`R`, and we have by assumption that :math:`R` is commutative, so it
follows that :math:`R` is a field.

Look back now to exercise 6.4 in the previous chapter, which asks you to
provide a rule for whether :math:`\mathbb{Z}_m` is an integral domain given any
:math:`m \geq 2`. This is quite a difficult exercise but the result is quite
useful, so I recommend that you look at the solution now if you weren't able to
solve it yourself.

Using our new result that every finite integral domain is a field, we can now
strengthen the result we found in exercise 6.4: since :math:`\mathbb{Z}_m` is
finite, if it is an integral domain, it must be a field. The field of integers
modulo :math:`m` for an appropriately chosen :math:`m` (I'm deliberately being
vague to avoid spoiling you for exercise 6.4 if you want to have another go at
it) is generally my go-to example of a field, as these fields tend to be the
simplest to deal with and can be faithfully represented on computers very
easily — unlike, say, :math:`\mathbb{R}`.
