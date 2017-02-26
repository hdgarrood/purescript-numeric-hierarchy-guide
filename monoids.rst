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

A monoid is a set :math:`M`, together with an operation :math:`*`, such that
the following laws hold:

1. *Closure.* :math:`\forall x, y \in M.\; x * y \in M`.
2. *Associativity.* :math:`\forall x, y, z \in M.\; (x * y) * z = x * (y * z)`.
3. *Identity.* :math:`\exists e \in M.\; \forall x \in M.\; e * x = x * e = x`.

Hopefully you can see that the operation :math:`*` corresponds to ``append`` in
PureScript, and that the identity element (conventionally written :math:`e`)
corresponds to ``mempty`` in PureScript.

So far, we have seen three examples of monoids: integers under addition and
multiplication, and truth values under :math:`\land`.

We will now look at a few non-examples of monoids and talk about why they fail
to be monoids.

First, if we take the set of natural numbers which are less than 4, that is
:math:`\{0, 1, 2, 3\}`, and take addition as the operation, this fails to be a
monoid because it does not satisfy closure. To show this we need to find a pair
of elements such that their sum is not in the set. One such choice is :math:`3
+ 1`, which of course equals :math:`4`, which is not in the set. We say that a
set is *closed under* an operation if performing that operation on two elements
of the set always produces another element of the set; this is where the name
"closure" comes from.

An example of something failing to be a monoid because the operation is not
associative could be the set of floating point number values under addition.
For example, try ``(0.1 + 0.2) + 0.3`` in a console, and compare the result to
``0.1 + (0.2 + 0.3)``.

An example of something failing to be a monoid because of a lack of an
identity element could be the set of even numbers under multiplication. The
first two laws are satisfied, but since 1 is not an even number, we don't have
an identity element.

A brief interlude on notation: if we want to refer to a specific monoid, we
write it as a pair where the first element is the set and the second is the
operation. For example, the monoid of integers under addition is written as
:math:`(\mathbb{Z}, +)`.

**Exercise 2.1.** Consider the set of natural numbers together with the
operation of subtraction: :math:`(\mathbb{N}, -)`. This is *not* a monoid. Can
you say which of the three laws fail to hold (it might be more than one) and
why?

**Exercise 2.2.** The set of *rational numbers* is the set of numbers which can
be written as the ratio of two integers :math:`\frac{a}{b}`. There is a
short-hand notation for this set too: :math:`\mathbb{Q}` (for "quotient").
Show that :math:`(\mathbb{Q}, +)` is a monoid by checking each of the three
laws. What is the identity element?

**Exercise 2.3.** (Harder) Prove that a monoid can only have one identity
element. To do this, first suppose that you have two elements of some monoid;
call them, say, :math:`e` and :math:`e'`, and then show that if they are both
identity elements then they must be equal to each other. Be careful here: it's
not enough to take one specific example of a monoid and show that it only has
one identity element. You have to construct an argument which will work for
*any* monoid, which means you aren't allowed to assume anything beyond what is
in the definition of a monoid.

A quick note on the previous exercise: in general, if we want to prove that
there is a unique element of some set which has some particular property, we do
this by taking two arbitrary elements of the set, assuming that they both have
this property, and then showing that they must be equal.

Since monoids have a unique identity element, we can talk about *the* identity
element of a monoid, rather than just *an* identity element.

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
