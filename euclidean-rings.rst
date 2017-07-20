Euclidean rings
===============

Over the previous two chapters, we covered the Euclidean Algorithm, which
allows you to compute the greatest common divisor of two integers. We also
encountered a new example of a ring, namely polynomials, and noticed that they
both support a very similar kind of division.

In this chapter we will see how to generalise the Euclidean Algorithm and
discuss the resulting structure, which is called a **euclidean ring**.

Divisors, again
---------------

Instead of working in :math:`\mathbb{Z}` we will now work in an arbitrary
integral domain :math:`R`. The first thing we will want to do is generalise our
definition of "divisor"; fortunately this is easy:

Let :math:`a, b \in R`. We say that :math:`a` divides :math:`b` if there exists
some :math:`q \in R` such that :math:`aq = b`.

In fact it's the exact same definition except that we just replace
:math:`\mathbb{Z}` with :math:`R`. The definition of "common divisors" also
immediately generalises with no extra effort required. However, it's less
obvious how to define a *greatest* common divisor, since we might not have a
good way of ordering elements of an arbitrary integral domain. We address this
as follows:

Let :math:`a, b, d \in R` and suppose :math:`d \mid a` and also :math:`d \mid
b`, that is, :math:`d` is a common divisor of :math:`a` and :math:`b`. We say
that :math:`d` is a **greatest common divisor** of :math:`a` and :math:`b` if
for any other common divisor :math:`d'` of :math:`a` and :math:`b`, we have
that :math:`d' \mid d`.

Note that we have started saying "*a* greatest common divisor" rather than
"*the* greatest common divisor"; this is because greatest common divisors are
no longer guaranteed to be unique. For example, in the previous chapter we saw
that a greatest common divisor of :math:`462` and :math:`1071` was :math:`21`.
In this setting we would also consider :math:`-21` to be a greatest common
divisor of these two numbers.

I wouldn't blame you if, at this point, you said this was a nonsense
definition, because it's not clear that "greatest" really means anything at
this point. Don't worry — we will clear this all up shortly.

Generalising the Euclidean Algorithm
------------------------------------

In the last chapter we saw two key ideas which the Euclidean Algorithm relies
on to work:

1. For :math:`a, b, d \in \mathbb{Z}`, if :math:`d \mid a` and :math:`d \mid b`,
   then :math:`d \mid ma + nb` for any :math:`m, n \in \mathbb{Z}`.
2. Remainders keep getting smaller, and are guaranteed to eventually reach
   :math:`0`.

It's very pleasing to see that the first of these immediately generalises from
:math:`\mathbb{Z}` to an arbitrary integral domain. We can even use the exact
same proof as we did in the case of :math:`\mathbb{Z}`!

However, we can't generalise the second idea if all we have is an integral
domain — we need something a little stronger.

Let :math:`R` be an integral domain. A **euclidean function** is a function
:math:`f : R \setminus \{ 0 \} \rightarrow \mathbb{N}` satisfying:

* For :math:`a` and :math:`b` in :math:`R`, with :math:`b \neq 0`, there exist
  :math:`q` and :math:`r` in :math:`R` such that :math:`a = bq + r` and either
  :math:`r = 0` or :math:`f(r) < f(b)`.
* For all nonzero :math:`a` and :math:`b` in :math:`R`, we have :math:`f(a)
  \leq f(ab)`.

.. note::
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

How does this help us? Well, we now know that "remainders keep getting
smaller". That is, if we perform the Euclidean Algorithm on a pair of elements
:math:`a, b` from an arbitrary euclidean ring, then the first remainder
:math:`r_1` will be smaller than :math:`b` in the sense that :math:`f(r_1) <
f(b)`, and the second remainder :math:`r_2` will be smaller than :math:`r_1` in
the sense that :math:`f(r_2) < f(r_1)`, and so on until we reach :math:`0`.

So now we're done — we can use what is essentially the same argument as in the
case of integers to show that our GCD algorithm actually works with any
euclidean ring!

We still need to verify that integers and polynomials do actually form
euclidean rings, though, and to do this we need to find euclidean functions for
each of them.

Cast your mind back one more time to the theorem about integer division:

.. note::
  If we have two integers :math:`a, b`, with :math:`b > 0`, then there always
  exists a pair of integers :math:`q` and :math:`r` such that :math:`a = qb +
  r`, and :math:`0 \leq r < b`.

This is almost in the right form for us to show that :math:`\mathbb{Z}` is a
euclidean ring, but not quite. In particular we need to be able to deal any
nonzero :math:`b`, not just positive :math:`b`.

We can address this with the **absolute value function**. For any :math:`x \in
\mathbb{R}`, the absolute value of :math:`x` is defined as:

.. math::
  \lvert x \rvert = \begin{cases}
                      x  & \mathrm{if} \; x \geq 0 \\
                      -x & \mathrm{if} \; x < 0
                    \end{cases}

Note that for any real number :math:`x`, the absolute value of :math:`x` is
always nonnegative. Also, again for any real number :math:`x`, note that
:math:`\lvert x \rvert = \lvert -x \rvert` (check this if you need to).

We can prove that the absolute value function is a euclidean function on
:math:`\mathbb{Z}` by cases. First, we will cover the case where :math:`b > 0`,
and then we will cover the case where :math:`b < 0`.

In the case where :math:`b > 0,` we already know that we can find an
appropriate :math:`r` with :math:`0 \leq r < b;` since :math:`r` and :math:`b`
are both nonnegative, we must have :math:`r = \lvert r \rvert` and :math:`b =
\lvert b \rvert,` so :math:`\lvert r \rvert < \lvert b \rvert` as required. In
the case where :math:`b < 0,` we know that :math:`-b` is positive, so we can
divide :math:`a` by :math:`-b` and get a :math:`q` and :math:`r` satisfying
:math:`a = q(-b) + r` and :math:`0 \leq r < -b`.  Rearranging a little, we can
write :math:`a = (-q)b + r,` showing that our quotient is :math:`-q` and our
remainder :math:`r`. We also have that :math:`r < -b,` so :math:`\lvert r
\rvert < \lvert -b \rvert,` and of course :math:`\lvert -b \rvert = \lvert b
\rvert,` so again :math:`\lvert r \rvert < \lvert b \rvert` as required.

**Exercise ??** Complete the proof that the absolute value function is a
euclidean function on :math:`\mathbb{Z}` by showing that :math:`\lvert a \rvert
\leq \lvert ab \rvert` for all nonzero :math:`a, b \in \mathbb{Z}`.

Polynomials are a bit easier, since our polynomial division theorem is already
in the correct form; looking back at the theorem from the previous chapter:

.. note::
  Let :math:`F` be a field, and let :math:`a, b \in F[x]`, with :math:`b \neq
  0`. Then, there exists :math:`q, r \in F[x]` such that :math:`a = qb + r`,
  and either :math:`\deg(r) < \deg(b)`, or :math:`r = 0`.

So the degree function satisfies the first condition for being a euclidean
function.

**Exercise ??** Complete the proof that the degree function is a euclidean
function on :math:`F[x]` by showing that :math:`\deg(a) \leq \deg(ab)` for all
nonzero :math:`a, b \in F[x]`. Hint: can you find an expression for
:math:`\deg(ab)` in terms of :math:`\deg(a)` and :math:`\deg(b)`?

So the degree function is a euclidean function on polynomials, and therefore
polynomials are indeed euclidean rings.

There's one more example of a euclidean ring which we should mention, and that
is any field. Of course, in a field, you can always divide exactly, so this
isn't the most interesting example of a euclidean ring — but it's good to be
aware of nonetheless.

Let :math:`F` be a field, and suppose :math:`f : F \setminus \{ 0 \}
\rightarrow \mathbb{N}` is a euclidean function. Recall the second condition
for being a euclidean function, which is that for all nonzero :math:`a, b \in
F`, we have that :math:`f(a) \leq f(ab)`. Let :math:`x` be any element of
:math:`F`. If we set :math:`a = 1` and :math:`b = x` then we see that
:math:`f(1) \leq f(x)`.  Also, since :math:`F` is a field, :math:`x` must have
a multiplicative inverse, :math:`x^{-1}`. So if we set :math:`a = x` and
:math:`b = x^{-1}` we see that :math:`f(x) \leq f(1)`. The only way that both
of these things can be true is if :math:`f(x) = f(1)`, that is, :math:`f` is
constant: it always gives us back the same thing, no matter what we put in.

Now, we look back to the first condition, which says that for all nonzero
:math:`a, b \in F`, there exist :math:`q, r \in F` such that :math:`a = qb + r`
and either :math:`r = 0` or :math:`f(r) < f(b)`. However, since :math:`f` is
constant, there is no pair of elements :math:`r, b \in F` such that :math:`f(r)
< f(b)`. What this means is that whenever we divide two elements, we must
always hit the :math:`r = 0` case, i.e. we must always have :math:`q = ab^{-1}`
and :math:`r = 0`.

Therefore, whenever we try to run our GCD algorithm, it always terminates
immediately. In fact every single element of a field (apart from :math:`0`) is
a "greatest common divisor" of any pair of elements (I put "greatest common
divisor" in quotes here, because in this context it breaks down, and doesn't
really mean anything any more). But we have shown something interesting: for
any field, the *only option* for a euclidean function is a constant function,
which means that no field can have any euclidean ring structure other than this
rather uninteresting one.

Summary
-------

The answer to the question "what is a euclidean ring" of course is the
definition; there's no substitute for it, that is what a euclidean ring is.
However it's often useful to have an intuitive understanding to go along with
actual definition of what something is; allowing you to develop this intuition
has been the aim of these last three chapters. My intuitive understanding of a
euclidean ring is a ring which behaves "a bit like the integers", in the sense
that

* elements can be divided to give a quotient and a remainder,
* any pair of elements has at least one greatest common divisor, in the sense
  that any other common divisor divides a GCD,
* it has a euclidean function which tells you the "size" of an element (and
  this sense of "size" is exactly same as the sense of "greatest" in "greatest
  common divisor")
* the Euclidean Algorithm can be used to find a GCD of any two elements of the
  ring.
