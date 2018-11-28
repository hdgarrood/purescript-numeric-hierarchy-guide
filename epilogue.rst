Epilogue
========

If you've read the entire thing and understood at least some of it, well done!
This text is essentially a whirlwind tour through some of the best bits of an
undergraduate maths degree, so going through it in a self-directed manner is
no mean feat.

We've now seen all of the type classes included in the PureScript numeric
hierarchy together with motivating examples of each. One of my goals in writing
this guide has been to persuade you that it does make sense to define the
numeric hierarchy as we have in PureScript, since it allows much better code
generality and reuse potential when compared to alternative approaches, such as
putting ``.add(other)`` methods on various classes without any type system
support to help us know which properties will be satisfied by objects of a
given class, or worse, reserving the built-in arithmetical operators for
built-in types.

Another benefit of the type class hierarchy approach is that by being based on
mathematical structures which are already very well studied, there is plenty of
information available on them via the web (provided that you have the
background to understand it). This means that it should be easier for us to
determine what the appropriate set of constraints should be for a particular
function.

To give an example, suppose we want to implement the `field of fractions`_ of
an arbitrary integral domain. The maths tells us that we do in fact need an
integral domain for this to work, so we know that we need to include this as a
constraint somehow. We don't actually have an integral domain type class in the
PureScript hierarchy, but the closest thing we have which is at least as strong
is ``EuclideanRing``, so we'll have to use a ``EuclideanRing a`` constraint in
our ``CommutativeRing (Fraction a)`` and ``DivisionRing (Fraction a)``
instances.

This is just my viewpoint, though. Are you convinced? Have I changed your
mind? Let me know. :)

.. _field of fractions: https://en.wikipedia.org/wiki/Field_of_fractions
