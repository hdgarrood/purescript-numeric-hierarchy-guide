PureScript implementations of objects discussed in this guide
=============================================================

If you're finding yourself wanting to use some of the mathematical objects
discussed in this guide, look no further. Many of these objects are implemented
in the core libraries, but for some of them, you'll have to look a little
further afield.

The information here is correct as of Nov 2018, but could easily change; new
libraries could pop up and replace older ones as the best choice in certain
contexts, libraries could become unmaintained, and so on.

**The integers,** :math:`\mathbb{Z}`. There are a few options for this:

1. The ``Int`` type built in to the language. This is not a completely
   faithful representation of :math:`\mathbb{Z}`, because it's a 32-bit integer
   type, which means that it cannot represent integers outside the range
   :math:`[-2^{31}, 2^{31}-1]`. In fact, since overflow is handled by wrapping
   around, this type is actually equivalent to the integers modulo
   :math:`2^{32}`. While not suitable for representing integers outside this
   range, this type has the advantage that interop is the easiest, and also it
   will have the best performance.
2. A wrapper around a JavaScript bigint library, such as `purescript-bigints`_.
3. A native implementation of arbitrarily-sized integers: this has the
   advantage of being able to work even if you're not compiling to JS. See e.g.
   `purescript-precise`_.

There is also work on adding arbitrarily-sized integers to JavaScript: there is
a `Stage 3 TC39 proposal <https://tc39.github.io/proposal-bigint/>`_, and they
`have already landed in (at least) Chrome <https://developers.google.com/web/updates/2018/05/bigint>`_.

**The real numbers,** :math:`\mathbb{R}`. These are notoriously difficult to
represent in the finite world of computers, since :math:`\mathbb{R}` is such a
monstrously large set that you can't even pair its elements up with the
elements of :math:`\mathbb{N}`. You'll essentially be forced to compromise and
to work with a simpler set...

**The rationals,** :math:`\mathbb{Q}`. The rationals are of course infinite,
but unlike the reals, they *can* in fact be paired up with the natural numbers,
which means you can faithfully represent them on a computer (as long as you
don't run out of memory). However, it may be prohibitively expensive in time or
memory or both to do this.

1. The ``Number`` type built in to the language, which is a double-precision
   IEEE 754 floating point number. This type does of course have a number of
   drawbacks, including having counterexamples to pretty much any law or
   property which you might expect them to have (e.g. ``0.1 + 0.2`` does not
   quite equal ``0.3``), and being inhabited by values like ``NaN`` and
   ``Infinity`` which can have surprising behaviour.

   However, they also have a number of important advantages. They are
   the default option for almost any work requiring an approximation of
   :math:`\mathbb{R}`; their operations are implemented in hardware basically
   everywhere, making them significantly faster than any other option; they
   have predictable performance and memory usage, which is very unlikely to be
   true for any other option; and there is already a significant amount of
   literature about how to write algorithms in such a way as to avoid their
   pitfalls, as well as freely available implementations of these algorithms
   (e.g. on the ``Math`` object in JS).

2. The ``Ratio`` type from `purescript-rationals`_. When combined with a
   big-integer implementation (see above), it gives you a completely faithful
   representation of :math:`\mathbb{Q}`.

3. The ``HugeNum`` type from `purescript-precise`_. This will be useful in some
   of the same contexts as ``Ratio``, although it is implemented in a slightly
   different way. Division does not yet appear to be implemented in this
   library, however.

**The natural numbers,** :math:`\mathbb{N}`. The library `purescript-naturals`_ 
provides a type backed by ``Int``, which means that it's perfect provided that
you don't need to go above :math:`2^{31}-1`.

**The complex numbers,** :math:`\mathbb{C}`. Since this set is essentially
:math:`\mathbb{R}^2`, we encounter many of the same issues that we would when
trying to represent :math:`\mathbb{R}`. As far as I'm aware, there's only one
option for these in PureScript: the `purescript-complex`_ library (although it
doesn't appear to be compatible with the latest versions of the core libraries
right now).

**Matrices.** There are number of JS libraries you can wrap for this, such as
`glMatrix`_, or `MathBox`_. MathBox in particular has PureScript bindings
already via `purescript-mathbox`_.

**The quaternions,** :math:`\mathbb{H}`. I made a library for these! It's
`purescript-quaternions`_.

**Modular arithmetic,** :math:`\mathbb{Z}_m` for some integer :math:`m`. 
I made a library for these too: `purescript-modular-arithmetic`_.

**Polynomials,** :math:`R[x]` for some ring :math:`R`. We're getting a bit more
exotic now. I would love to hear from you if you have a use case for this
library: `purescript-polynomials`_.

**The symmetric group,** :math:`S_n`. This is also one of mine:
`purescript-symmetric-groups`_.

.. _purescript-precise: https://pursuit.purescript.org/packages/purescript-precise
.. _purescript-bigints: https://pursuit.purescript.org/packages/purescript-bigints
.. _purescript-rationals: https://pursuit.purescript.org/packages/purescript-rationals
.. _purescript-complex: https://pursuit.purescript.org/packages/purescript-complex
.. _purescript-quaternions: https://pursuit.purescript.org/packages/purescript-quaternions
.. _purescript-polynomials: https://pursuit.purescript.org/packages/purescript-polynomials
.. _purescript-modular-arithmetic: https://pursuit.purescript.org/packages/purescript-modular-arithmetic
.. _purescript-symmetric-groups: https://pursuit.purescript.org/packages/purescript-symmetric-groups
.. _purescript-mathbox: https://pursuit.purescript.org/packages/purescript-mathbox
.. _purescript-naturals: https://pursuit.purescript.org/packages/purescript-naturals
.. _glMatrix: http://glmatrix.net
.. _MathBox: https://gitgud.io/unconed/mathbox
