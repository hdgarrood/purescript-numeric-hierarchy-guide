Complex numbers
===============

We encountered the set :math:`\mathbb{R}^2` in the :doc:`matrices` chapter, and
defined an addition operation which made :math:`(\mathbb{R}^2, +)` an abelian
group. In this section we will come across a multiplication operation on
:math:`\mathbb{R}^2` and we will see that with these two operations,
:math:`\mathbb{R}^2` can be made into a field, which is called the field of
*complex numbers*. When we are making use of the field structure we will
usually write this field as :math:`\mathbb{C}` rather than
:math:`\mathbb{R}^2`.

Complex numbers have a variety of applications, including in geometry, for e.g.
representing figures in two dimensions, for modelling behaviour of electrical
signals, and for analysing the behaviour of systems which can be modelled using
differential equations, such as how populations of different species in a food
web change over time, how heat flows through an object, or how mechanical
systems like suspension in a car will behave. They also function as useful
tools in many other areas of mathematics. For instance, they play a major role
in the proof that quintic equations — that is, equations of the form
:math:`ax^5 + bx^4 + cx^3 + dx^2 + ex + f = 0` — cannot be solved in general,
as well as offering some nifty tricks to perform otherwise difficult
integrations of real-valued functions.

First, instead of writing elements of :math:`\mathbb{R}^2` in the usual way,
i.e. :math:`(a, b)`, we will write them as :math:`a + bi`, where :math:`a` and
:math:`b` are real numbers. For example, we write :math:`(1,2)` as :math:`1 +
2i`, we write :math:`(1,0)` as just :math:`1`, and we write :math:`(0,1)` as
just :math:`i`. For a complex number :math:`a + bi`, we call :math:`a` the
"real part", and :math:`b` the "imaginary part".

Therefore, to add two complex numbers together, we simply add the real and
imaginary parts. That is, :math:`(a + bi) + (c + di) = (a+c) + (b+d)i`.

For the multiplication operation, if we remember that :math:`i^2 = -1`, the
rest sort of falls out. That is, to multiply two complex numbers together,
we can write :math:`(a + bi)(c + di) = ac + adi + bci + bdi^2`, making use of
distributivity, and then using distributivity again (but in the reverse
direction) and replacing :math:`i^2` with :math:`-1`, we can write this as
:math:`(ac - bd) + (ad + bc)i`.

.. note::

  This approach is a bit sloppy because we are assuming that
  :math:`\mathbb{C}` is a field before even defining its multiplication
  operation. I hope you can forgive me for this.

Notice that the subset of :math:`\mathbb{C}` given by the complex numbers which
have an imaginary part of :math:`0` behaves in exactly the same way as
:math:`\mathbb{R}`; because of this, we can consider :math:`\mathbb{R}` as a
subset of :math:`\mathbb{C}`. In the same vein we will describe elements of
:math:`\mathbb{C}` which have an imaginary part of :math:`0` as "real".

Another useful thing to notice is that to multiply a real number by a complex
number, you simply multiply the real and imaginary parts by that number. That
is, for :math:`a \in R`,

.. math::
  (a+0i)(c+di) = (ac + 0d) + (ad + 0c)i = (ac) + (ad)i

Establishing that :math:`\mathbb{C}` is a ring (in fact, a commutative ring)
with respect to these addition and multiplication operations is a little
tedious, so I won't set it as an 'official' exercise, but you may find it worth
doing anyway.

However, establishing that :math:`\mathbb{C}` is a field — in particular,
showing that all nonzero elements have multiplicative inverses — is more
interesting.

To find the multiplicative inverse of an arbitrary complex number, we use an
operation called *conjugation*. The *conjugate* of a complex number is obtained
by negating the imaginary part, i.e. the conjugate of :math:`a + bi` is
:math:`a - bi`. The first thing to notice is that multiplying a complex number
by its conjugate always yields a real number:

.. math::
  (a + bi)(a - bi)
  &= a^2 + abi - abi - b^2i^2 \\
  &= a^2 + b^2

Now, if we write the multiplicative inverse of :math:`a + bi` as a fraction
:math:`\frac{1}{a+bi}`, the answer becomes a little clearer. Just as with real
numbers, we can multiply top and bottom by the same quantity:

.. math::
  \frac{1}{a+bi}
  &= \frac{a-bi}{(a+bi)(a-bi)} \\
  &= \frac{a-bi}{a^2+b^2}

Now we have the product of a complex number with a real number, i.e. we have
:math:`a - bi` multiplied by :math:`\frac{1}{a^2 + b^2}`. As we showed before
we can simply multiply the real and imaginary parts by this real number,
which gives us the inverse of :math:`a + bi` as:

.. math::
  \frac{a-bi}{a^2+b^2} = \frac{a}{a^2+b^2} - \frac{b}{a^2+b^2}i

Let's check that this really is the multiplicative inverse of :math:`a + bi`,
just to be safe:

.. math::
  (a+bi) \left( \frac{a}{a^2+b^2} - \frac{b}{a^2+b^2}i \right)
  &= \frac{a^2}{a^2+b^2} - \frac{ab}{a^2+b^2}i + \frac{ab}{a^2+b^2}i - \frac{b^2}{a^2+b^2}i^2 \\
  &= \frac{a^2 + b^2}{a^2 + b^2} \\
  &= 1

So there you have it — we can indeed make :math:`\mathbb{R}^2` into a field!

There is so, so much more I could say about complex numbers, but I think I will
leave it here for now.
