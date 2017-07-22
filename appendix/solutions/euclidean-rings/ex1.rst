Exercise 11.1
=============

Let :math:`a, b \in \mathbb{Z}`, with both nonzero. We want to show that
:math:`\lvert a \rvert \leq \lvert ab \rvert`.

There are a few ways to do this. For the way I'm going to use here, our first
step is to show that :math:`\lvert ab \rvert = \lvert a \rvert \lvert b
\rvert` for any integers :math:`a, b.` In fact, this always holds, even if
:math:`a` or :math:`b` is zero. This can be proved by cases. We'll consider
four cases:

* :math:`a \geq 0, \; b \geq 0`
* :math:`a \geq 0, \; b < 0`
* :math:`a < 0,    \; b \geq 0`
* :math:`a < 0,    \; b < 0`

In the first case, since both :math:`a` and :math:`b` are nonnegative, we have
that :math:`\lvert a \rvert = a` and :math:`\lvert b \rvert = b`, so it follows
that :math:`\lvert a \rvert \lvert b \rvert` is equal to :math:`ab`.  Also,
since :math:`a` and :math:`b` are both nonnegative, their product :math:`ab` is
also nonnegative, so :math:`\lvert ab \rvert = ab` and we are done.

In the second case, we have that :math:`\lvert a \rvert = a` as before, but
:math:`\lvert b \rvert = -b`, since :math:`b` is negative, and so the right
hand side is equal to :math:`-ab`. Also, in this case, the product :math:`ab
\leq 0`, so on the left hand side, we have :math:`\lvert ab \rvert = -ab`. So
both sides are equal to :math:`-ab` and we are done.

The remaining two cases play out similarly, so I won't bother to write them
out.

Now we know that :math:`\lvert ab \rvert = \lvert a \rvert \lvert b \rvert`, we
can return to our original question. Using our new knowledge, we can rewrite
the statement we are trying to prove as :math:`\lvert a \rvert \leq \lvert a
\rvert \lvert b \rvert`. One thing we can do with inequalities is divide both
sides by a positive number. Since we have by assumption that :math:`a` is
nonzero, it follows that :math:`\lvert a \rvert > 0` and so we can divide both
sides by :math:`\lvert a \rvert`, leaving us with :math:`1 \leq \lvert b
\rvert`. And since :math:`b` is a nonzero integer, :math:`\lvert b \rvert` must
be a positive integer, so :math:`1 \leq \lvert b \rvert` is necessarily true,
and we are done.
