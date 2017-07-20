Euclidean rings
===============

Over the previous two chapters, we covered the Euclidean Algorithm, which
allows you to compute the greatest common divisor of two integers. We also
encountered a new example of a ring, namely polynomials, and noticed that they
both support a very similar kind of division.

It is this resemblance which motivates the idea of the structure we will cover
in this chapter: **euclidean rings**.

Let :math:`R` be an integral domain. A **euclidean function** is a function
:math:`f : R \setminus \{ 0 \} \rightarrow \mathbb{N}` satisfying:

* For :math:`a` and :math:`b` in :math:`R`, with :math:`b \neq 0`, there exist
  :math:`q` and :math:`r` in :math:`R` such that :math:`a = bq + r` and either
  :math:`r = 0` or :math:`f(r) < f(b)`.
* For all nonzero :math:`a` and :math:`b` in :math:`R`, we have :math:`f(a)
  \leq f(ab)`.

On notation: if :math:`A` and :math:`B` are sets then their **difference** is
defined as

.. math::
  A \setminus B = \{\, x \in A \,|\, x \notin B \,\}

that is, the elements of :math:`A` which are not in :math:`B`. So if :math:`R`
is a ring, then the set :math:`R \setminus \{0\}` consists of all elements of
:math:`R` except :math:`0`. Essentially, what we are doing here is saying that
for a euclidean function :math:`f`, the result of applying :math:`f` to
:math:`0` need not be defined.

A **euclidean ring**, or **euclidean domain**, is then defined as an integral
domain which can be endowed with a euclidean function.

I hinted at two examples of euclidean rings in the previous chapter. One is
:math:`\mathbb{Z}`, and the other is the ring of polynomials with coefficients
in some field. But what are their respective euclidean functions? In the case
of the integers the euclidean function is the absolute value function, which
takes :math:`x` to :math:`\lvert x \rvert`. In the case of polynomials over a
field, the euclidean function is the degree function :math:`\deg`.
