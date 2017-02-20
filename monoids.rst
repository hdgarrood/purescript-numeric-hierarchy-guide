Monoids
=======

You are probably already aware of *monoids* (via the ``Monoid`` type class),
since they come up quite often in programming. We'll just quickly remind
ourselves about what makes something a monoid and cover a few examples, but in
a slightly more mathematically-oriented way. The main aim of this section is to
make you a bit more comfortable about mathematical ideas and notations by using
them to describe an idea which you are hopefully already familiar with. Another
purpose of this section is to prepare you for the next section, in which we
will talk about a specific kind of monoid which turns out to be rather
important.

Here are a few rules about how adding integers together works:

* If we add together two integers, we always get another integer.
* It doesn't matter what order we bracket up additions, we always get the same
  answer. That is, :math:`(x + y) + z` is always the same as :math:`x + (y +
  z)` for any integers :math:`x, y, z`.
* Adding :math:`0` to any integer yields the same integer.

Here are a few more rules about how multiplying integers works:

* If we multiply two integers, we always get another integer.
* It doesn't matter what order we bracket up multiplications, we always get the
  same answer. That is, :math:`(xy)z` is always the same as :math:`x(yz)` for
  any integers :math:`x, y, z`.
* Multiplying any integer by :math:`1` yields the same integer.

Now, instead of integers, we will consider a different set: the set of
truth-values :math:`\{T, F\}`. This set corresponds to the ``Boolean`` type in
PureScript. Here are some rules for how the logical and :math:`\land` operation
works on truth-values:

* If we apply the :math:`\land` operation to two truth-values, we always get
  another truth-value.
* It doesn't matter what order we bracket up :math:`\land`, we always get the
  same answer. That is, :math:`(x \land y) \land z` is the same as :math:`x
  \land (y \land z)` for all :math:`x, y, z`.
* :math:`P \land T` is always the same as :math:`P`, for any truth-value
  :math:`P`. If it's not obvious what I mean by :math:`P \land T`, it means the
  same thing as the PureScript code ``p && true``.

Hopefully you can see the pattern by now. The general definition of a monoid is
as follows:

A monoid is a set :math:`X`, together with an operation :math:`*`, such that
the following laws hold:

1. *Closure.* :math:`\forall x, y \in X.\; x * y \in X`.
2. *Associativity.* :math:`\forall x, y, z \in X.\; (x * y) * z = x * (y * z)`.
3. *Identity.* :math:`\exists e \in X.\; \forall x \in X.\; e * x = x * e = x`.

Hopefully you can see that the operation :math:`*` corresponds to ``append`` in
PureScript, and that the identity element (conventionally written :math:`e`)
corresponds to ``mempty`` in PureScript.

A brief interlude on mathematical notation: if we want to refer to a specific
monoid, we write it as a pair where the first element is the set and the second
is the operation. For example, the monoid of integers under addition is written
as :math:`(\mathbb{Z}, +)`. The set of integers is written :math:`\mathbb{Z}` —
this comes from the German *Zahlen,* meaning "numbers".

**Exercise 2.1.** The set of all the non-negative integers is called the set of
*natural numbers*, and is written :math:`\mathbb{N}`. Consider this set
together with the operation of subtraction: :math:`(\mathbb{N}, -)`. This is
*not* a monoid. Can you say which of the three laws fail to hold (it might be
more than one) and why?

**Exercise 2.2.** The set of *rational numbers* is the set of numbers which can
be written as the ratio of two integers :math:`\frac{a}{b}`. There is a
short-hand notation for this set too: :math:`\mathbb{Q}` (for "quotient").
Persuade yourself that :math:`(\mathbb{Q}, +)` is a monoid by checking each of
the three laws. What is the identity element?

**Exercise 2.3.** (Harder) Prove that a monoid can only have one identity
element. Hint: imagine a monoid which has two distinct identity elements, and
consider what happens if you combine them with the monoid operation.

One more slightly strange example: Consider a set :math:`X`, which contains
precisely one element, :math:`x`. We can define an operation :math:`*` on this
set as follows:

.. math::

  x * x = x

That's all we need to do to define :math:`*`, because there are no other
possible values to consider. Then, :math:`(X, *)` is a monoid. It's not very
interesting which is why it gets called the *trivial monoid*. This corresponds
exactly to the ``Unit`` type in PureScript; the ``Unit`` type has precisely
this ``Monoid`` instance too.
