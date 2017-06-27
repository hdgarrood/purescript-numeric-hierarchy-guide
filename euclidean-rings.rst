Euclidean rings
===============

The reason I introduced polynomials in the previous chapter is that they are a
motivating example of a structure called a **euclidean ring**, or sometimes
**euclidean domain**. In this chapter we will cover this structure in a
slightly more abstract setting.

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
is a ring, then the set :math:`R \setminus \{0\}` is the set of nonzero
elements of :math:`R`. Essentially, what we are doing here is saying that
for a euclidean function :math:`f`, the result of applying :math:`f` to
:math:`0` need not be defined.
