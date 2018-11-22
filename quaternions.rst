Quaternions
===========

It is time to introduce you to the example I mentioned earlier of a division
ring which is not a field. This division ring is called the *quaternions*,
and it has important applications in 3D graphics and orbital mechanics of
satellites, due to its ability to represent orientations and rotations of
objects in three dimensions in a simple and efficient way.

The quaternions can be seen as an extension of the complex numbers in a similar
sense that the complex numbers can be seen as an extension of the real numbers.
Where complex numbers can be written :math:`a + bi`, where :math:`a` and
:math:`b` are real numbers, and :math:`i` is the 'imaginary unit' satisfying
:math:`i^2 = -1`, quaternions can be written :math:`a + bi + cj + dk`, where
:math:`a, b, c,` and :math:`d` are real numbers, and :math:`i, j,` and
:math:`k` are each different imaginary units. Addition is simple enough; as
with complex numbers, we add component-wise:

.. math::
  (a + bi + cj + dk) + (e + fi + gj + hk)

  = (a+e) + (b+f)i + (c+g)j + (d+h)k

Multiplication is a little more complex, but it follows from the fact that the
imaginary units :math:`i, j` and :math:`k` satisfy the following equation:

.. math::
  i^2 = j^2 = k^2 = ijk = -1

The first thing to note is that the multiplicative inverses of :math:`i, j,`
and :math:`k` are :math:`-i, -j,` and :math:`-k` respectively.

The above equation does in fact allow us to work out the product of any two
quaternions. For instance, we can work out what the product :math:`ij` is by
starting with the equation :math:`ijk = -1` and multiplying both sides by
:math:`-k` on the right:

.. math::
  ijk(-k) = -1(-k)

  ij(-k^2) = k

and then using the fact that :math:`-k^2 = 1`, we obtain :math:`ij = k`.

You may be wondering why I specified that we were multiplying by :math:`-k` 'on
the right'. For the more common number systems such as the real or complex
numbers, we don't need to specify, because multiplying on the left is the same
as multiplying on the right, due to both of these number systems being
commutative rings. Because quaternions are not commutative, it *does* matter in
this case, so we need to specify.

For example, if we now want to work out the product :math:`ji`, we can use the
fact that :math:`(ji)^{-1} = i^{-1} j^{-1}`. (Look back at Exercise 3.3 if this
is unclear.) Then, we have :math:`(ji)^{-1} = i^{-1} j^{-1} = (-i)(-j) = ij =
k`. Therefore, :math:`ji = k^{-1} = -k`. In particular, :math:`ij \neq ji`.

We can derive a complete rule for multiplying quaternions by making use of the
distributive property:

.. math::
  &(a + bi + cj + dk) * (e + fi + gj + hk)

  =\; &ae + afi + agj + ahk

   &+ bei + bf(i^2) + bg(ij) + bh(ik)

   &+ cej + cf(ji) + cg(j^2) + ch(jk)

   &+ dek + df(ki) + dg(kj) + dh(k^2)

  =\; &ae - bf - cg - dh

   &+ (af + be + ch - dg) i

   &+ (ag - bh + ce + df) j

   &+ (ah + bg - cf + de) k

The non-commutativity of the quaternions make them a little strange to work
with. However, there are subsets of the quaternions which are easier to deal
with.  You all may be relieved to learn that the quaternions for which
:math:`c` and :math:`d` are both zero behave identically to the complex
numbers, for instance.

Multiplicative inverses
^^^^^^^^^^^^^^^^^^^^^^^

Recall that a division ring is a ring in which all non-zero elements have
multiplicative inverses. We have already seen that the multiplicative inverses
of :math:`i, j,` and :math:`k` are :math:`-i, -j,` and :math:`-k` respectively,
but what about all the other quaternions?

We can provide a rule for finding the multiplicative inverse of a quaternion
without too much difficulty, although we will first need a couple of
operations.

Firstly, the *norm* of a quaternion :math:`q = a + bi + cj + dk` is defined as

.. math::
  \lVert q \rVert = \sqrt{a^2 + b^2 + c^2 + d^2}

(notice that the norm is always a nonnegative real number). Secondly, the
*conjugate* :math:`\bar q` of a quaternion :math:`q = a + bi + cj + dk` is
defined as :math:`\bar q = a - bi - cj - dk`; we simply negate :math:`b, c,`
and :math:`d`.

Then, the multiplicative inverse of a quaternion :math:`q` is given by

.. math::
  q^{-1} = \frac{\bar q}{\lVert q \rVert^2}

You can check this if you really want, but I haven't set it as an exercise
because it's a bit tedious. The important thing to remember is that for any
quaternion :math:`q`, we have that :math:`qq^{-1} = q^{-1}q = 1`.

Dividing quaternions
^^^^^^^^^^^^^^^^^^^^

The non-commutativity of quaternion multiplication makes defining a division
operation for quaternions a little thorny. With fields, we can define division
as follows:

.. math::
  a / b = ab^{-1}

But with quaternions, we have two options for the operation of dividing
:math:`a` by :math:`b`: either :math:`ab^{-1}` or :math:`b^{-1}a`; these two
choices will give us different results for most choices of :math:`a` and
:math:`b`.

My understanding is that there is no strong reason to prefer one over the
other, so instead we have to come up with a name for each of them so that
people know which one we are talking about; these names are 'right division'
and 'left division' respectively. (I can never remember which one is
which.)

Both of these operations are defined in the ``Data.DivisionRing`` module, which
is part of the Prelude.

Using quaternions for rotations
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

I won't go into this in too much detail here, but it turns out that a rotation
of :math:`\theta` radians about the axis :math:`(x, y, z)` in 3D space can be
represented by the quaternion

.. math::
  q = \cos \frac{\theta}{2} + \sin \frac{\theta}{2} \big[ xi + yj + zk \big]

Now, if we have a point :math:`(a, b, c)` in 3D space, we can consider it as a
quaternion :math:`p` by setting :math:`p = 0 + ai + bj + ck`.

If we now want to calculate where the point :math:`p` ends up after being
rotated about the origin by the rotation represented by :math:`q`, we
calculate:

.. math::
  qpq^{-1}

The resulting quaternion will have a zero real part, like :math:`p`, and we can
read off the :math:`i, j,` and :math:`k` coefficients to obtain the point in 3D
space where we end up.

We can also compose rotations easily; if we have two rotations represented by
quaternions :math:`q_1, q_2`, then the rotation given by first performing
:math:`q_1` and then performing :math:`q_2` is simply :math:`q_2 q_1`.

Further references
^^^^^^^^^^^^^^^^^^

If you want to learn more about quaternions and rotations, the Wikipedia
article `Quaternions and spatial rotation <https://en.wikipedia.org/wiki/Quaternions_and_spatial_rotation>`_
might be a good place to start.

I also highly recommend the YouTube video `What are quaternions, and how do you visualize them? A story of four dimensions <https://www.youtube.com/watch?v=d4EgbgTm0Bg>`_
by `3Blue1Brown <https://youtube.com/3Blue1Brown>`_.

There is also a PureScript library `purescript-quaternions <https://pursuit.purescript.org/packages/purescript-quaternions>`_,
which provides a Quaternion type, instances, and various operations, as well as
utilities for using quaternions to represent 3D rotations.
