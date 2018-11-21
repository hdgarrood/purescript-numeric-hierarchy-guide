Logic
=====

We will start with a short discussion of logic, in particular we will briefly
cover some notation and a few proof techniques. We will need these later on to
be able to make sense of statements concerning things like rings and fields,
and also to prove or disprove these statements.

You will probably be happy with the idea that statements such as "the sky is
blue" and "pigs can fly" can have truth-values (i.e. "true" or "false"). There
are also ways of combining statements to make new statements, which again you
are most likely familiar with already:

* If you have two statements :math:`P` and :math:`Q`, you can make a new
  statement ":math:`P \text{ and } Q`", which is true if both :math:`P` and
  :math:`Q` are true. This is often written as :math:`P \land Q`.
* Similarly, you can also make a new statement ":math:`P \text{ or } Q`", which
  is true if at least one of :math:`P` and :math:`Q` are true. This is often
  written as :math:`P \lor Q`.

So for example, if we let the symbol :math:`P` represent the statement "the sky
is blue", and let the symbol :math:`Q` represent the statement "pigs can fly",
the statement :math:`P \lor Q` is true, because at least one of them, in this
case :math:`P`, is true.

**Exercise 1.1.** Using the same assignment of the symbols :math:`P` and
:math:`Q`, what is the truth-value of the statement :math:`P \land Q`?

Truth tables
------------

We can describe the behaviour of logical operators like :math:`\land` and
:math:`\lor` using things called *truth tables*. For example, here is the truth
table for logical and (:math:`\land`):

========= ========= =================
:math:`P` :math:`Q` :math:`P \land Q`
========= ========= =================
T         T         T
T         F         F
F         T         F
F         F         F
========= ========= =================

The table lists the four possible combinations of truth-values of :math:`P` and
:math:`Q`, as well as the truth-value of :math:`P \land Q` in each case. If
this isn't clear, it might help to compare it to an implementation of
:math:`\land` in PureScript::

   logicalAnd :: Boolean -> Boolean -> Boolean
   logicalAnd true true = true
   logicalAnd true false = false
   logicalAnd false true = false
   logicalAnd false false = false

**Exercise 1.2.** Write out the truth table for logical or, :math:`\lor`.

Logical equivalence
-------------------

We say that two statements are *logically equivalent* if they always have the
same truth value as each other, that is, if they are always either both true or
both false. Here is a truth table for logical equivalence with some entries
missing:

========= ========= ===========================
:math:`P` :math:`Q` :math:`P \Leftrightarrow Q`
========= ========= ===========================
T         T         T
T         F         F
F         T         ?
F         F         ?
========= ========= ===========================

**Exercise 1.3.** Complete the missing entries of this truth table.

So for example, :math:`P \land P` is always logically equivalent to :math:`P`,
regardless of the truth-value of :math:`P`. We can express this in symbols by
using a double-ended arrow like this: :math:`P \land P \Leftrightarrow P`.

Logical negation
----------------

Another thing we can do with statements is *negate* them: make a new statement
which is true if the original statement is false, and false if the original
statement is true. If :math:`P` is a statement, then the logical negation of
:math:`P` is written as :math:`\neg P`.

The following two equivalences hold regardless of the truth-values of :math:`P`
and :math:`Q`:

.. math::

  \neg (P \land Q) \; \Leftrightarrow \; \neg P \lor \neg Q

  \neg (P \lor Q) \; \Leftrightarrow \; \neg P \land \neg Q

These two equivalences are called *De Morgan's laws.*

**Exercise 1.4.** Persuade yourself that De Morgan's laws hold. One way to do
this is to write out a truth table.

Logical implication
-------------------

We now consider statements of the form "if :math:`P`, then :math:`Q`", for
example:

* if it is raining, then we will get wet,
* if :math:`x` is even, then it can be divided by :math:`2` exactly,
* if :math:`y` is even and :math:`z` is even, then :math:`y + z` is even.

We represent this kind of statement by defining a new logical operator called
*logical implication*, which we write as a rightwards-pointing arrow:
:math:`\text{it is raining} \Rightarrow \text{we will get wet}`.

The logical implication operator is defined as follows:

========= ========= =======================
:math:`P` :math:`Q` :math:`P \Rightarrow Q`
========= ========= =======================
T         T         T
T         F         F
F         T         T
F         F         T
========= ========= =======================

That is, :math:`P \Rightarrow Q` is a logical statement just like all of the
others we have seen, and it has a truth-value which depends on the truth-values
of :math:`P` and :math:`Q`.

**Exercise 1.5.** Persuade yourself, by using a truth table (or any other
method that works for you), that :math:`P \Rightarrow Q` is always logically
equivalent to :math:`\neg P \lor Q` regardless of the truth-values of :math:`P`
and :math:`Q`.

The standard way of proving a statement of the form :math:`P \Rightarrow Q` is
to first assume that :math:`P` is true, and then show that :math:`Q` follows,
i.e. show that :math:`Q` must also be true.

For example, suppose we wanted to prove the statement

.. math::

  x \text{ is even} \Rightarrow x^2 \text{ is even}.

We would start by letting :math:`x` be some arbitrary integer and assuming that
it is even. Since :math:`x` is even, we can write :math:`x = 2m` for some
integer :math:`m`. Then, :math:`x^2 = 4m^2` and therefore we have shown
:math:`x^2` has :math:`4` as a factor, so it must also have :math:`2` as a
factor, which means it must be even.

Converses
---------

If we have a statement which is a logical implication, for example :math:`x
\text{ is even} \Rightarrow x \text{ can be divided by 2 exactly}`, there is
another closely related statement called its *converse*. To find the converse
of an implication statement, we simply swap the two operands. For example, the
converse of the statement

.. math::
  x \text{ is even} \Rightarrow x \text{ can be divided by 2 exactly}

is this:

.. math::
  x \text{ can be divided by 2 exactly} \Rightarrow x \text{ is even}

Notice that both of the above statements are true. However, this is often not
the case! If a statement is true, it is not safe to assume that its converse is
also true. For example, consider the statement

.. math::
  y \text{ is even and } z \text{ is even} \Rightarrow y + z \text{ is even}

The converse of this statement is

.. math::
  y + z \text{ is even} \Rightarrow y \text{ is even and } z \text{ is even}

Notice that, while the first is true, the second is not. For instance, if
we take :math:`y = z = 1`, then :math:`y + z` is even, but neither :math:`y`
nor :math:`z` is.

Contrapositives
---------------

If we have a statement which is a logical implication, for example
:math:`\text{my pet is a cat} \Rightarrow \text{my pet is a mammal}`, there is
another closely related statement called its *contrapositive*. To find the
contrapositive of a logical implication statement, we swap the operands and
negate them both. So, for example, the contrapositive of the statement
:math:`\text{my pet is a cat} \Rightarrow \text{my pet is a mammal}` is the
statement :math:`\text{my pet is not a mammal} \Rightarrow \text{my pet is not
a cat}`.

The first thing to notice is that any implication statement is always logically
equivalent to its contrapositive.

**Exercise 1.6.** Check this! Persuade yourself that :math:`P \Rightarrow Q` is
always logically equivalent to :math:`\neg Q \Rightarrow \neg P`, perhaps with
a truth table.

This exercise suggests another way of proving statements of the form :math:`P
\Rightarrow Q`, which is to instead assume that :math:`\neg Q` is true, and
show that :math:`\neg P` follows. This technique is called *contraposition;*
the new statement is called the *contrapositive* of the original one.

**Exercise 1.7.** Use contraposition to prove the statement

.. math::

  x^2 \text{ is odd} \Rightarrow x \text{ is odd}.

Another way of thinking of logical equivalence is in terms of logical
implication. Specifically, an alternative way of defining
:math:`\Leftrightarrow` is by saying that :math:`P \Leftrightarrow Q` is the
same as this bad boy:

.. math::

   (P \Rightarrow Q) \land (Q \Rightarrow P)

In fact, the standard way of proving a statement of the form :math:`P
\Leftrightarrow Q` is to first prove :math:`P \Rightarrow Q` and then to prove
:math:`Q \Rightarrow P`.

Sets
----

For our purposes, it will be sufficient to say a set is a collection of any
kind of mathematical object: sets may contain numbers, functions, sets of
numbers, and so on.

We can write a set by listing the elements in between curly braces, like this:

.. math::

  \{1, 2, 3\}

Note that sets have no concept of ordering, so the set :math:`\{1, 3, 2\}` is
the same as the set :math:`\{1, 2, 3\}`.

The only thing we can really do with a set is to ask whether it contains some
particular thing. The notation for the statement ":math:`a` exists within the
set :math:`A`" looks like this:

.. math::
  a \in A.

We also have a notation for the negation of this statement, i.e. ":math:`a`
does not exist within the set :math:`A`":

.. math::
  a \notin A.

Often (but not always), uppercase letters denote sets, and lowercase letters
denote elements of sets.

Here are a few sets you may have come across already:

* The set of *natural numbers,* :math:`\{0, 1, 2, 3, 4, ...\}`. That is, the
  set of all the integers which are not negative. This set comes up fairly
  often so we have a special notation for it: :math:`\mathbb{N}`. (Note:
  depending on context, :math:`0` is sometimes not considered to be an element
  of :math:`\mathbb{N}`; in this guide we will say that it is.)

* The set of *integers,* :math:`\{0, 1, -1, 2, -2, 3, -3, ...\}`. Like
  :math:`\mathbb{N}` but it also includes negative numbers. We have a special
  notation for this set too: :math:`\mathbb{Z}`, from the German *Zahlen,*
  which just means "numbers".

* The set of *real numbers,* which is the kind of number you're probably most
  used to. :math:`0, 1, 37, \frac{1}{2}`, and :math:`\pi` are all examples of
  real numbers. This set also has a special notation: :math:`\mathbb{R}`.

So for example, the following are all true:

.. math::

  6 \in \mathbb{N}

  \frac{2}{3} \in \mathbb{R}


  \frac{2}{3} \notin \mathbb{N}.

Quantifiers
-----------

Up to now, the symbols :math:`P` and :math:`Q` have always represented
statements. However we can also use symbols to represent *predicates*, which
are like functions which return statements. For example, we might have a
predicate ":math:`x` is even", ":math:`x` is divisible by 6", or ":math:`x` is
prime".

If we let :math:`P(x)` represent the predicate ":math:`x` is even", then we can
write the statement "2 is even" as :math:`P(2)`. Similarly we can
write the statement "3 is even" as :math:`P(3)`. In each case we get a
statement whose truth-value can depend on the specific value of :math:`x` which
was chosen — in this case, :math:`P(2)` would be true, and :math:`P(3)` would
be false.

If we have a predicate, we can make statements about the truth-values of a
predicate over all the possible values it can take as arguments by using things
called *quantifiers*.

The first quantifier we will introduce is called "for all", written as an
upside-down capital letter A like this: :math:`\forall`. Here is how we write the
statement "the square of any real number is greater than or equal to 0" using
the :math:`\forall` quantifier:

.. math::

  \forall x \in \mathbb{R}.\; x^2 \geq 0

This can be read as: "For all :math:`x` in :math:`\mathbb{R}`, :math:`x`
squared is greater than or equal to :math:`0`."

The standard way of proving a statement like this is more or less what you
might expect: we have to show that every element of the set satisfies the
predicate. If the set is finite, we can do this by checking each element
individually. However, individual checking quickly gets very tedious for even
fairly small sets. Additionally, we often deal with infinite sets, where
exhaustively checking each element individually is not possible. Therefore, we
will usually prove statements of this kind by constructing an argument which
deals with every single element of the set *at the same time.* In fact, we have
already seen an example of such a proof: the proof that :math:`x` being even
implies that :math:`x^2` is also even, from a moment ago.

The other quantifier we will use is written as a back-to-front capital letter
E, like this: :math:`\exists`, and can be read as "there exists". Here is how
we would write the statement "there exists a real number whose square is 4" in
mathematical notation:

.. math::

  \exists x \in \mathbb{R}.\; x^2 = 4

There are two possible values of :math:`x` which you can use as examples to
show that this statement is true: :math:`2` and :math:`-2`. In fact, the
standard way of proving a statement of the form :math:`\exists x. P(x)` is to
pick a specific value of :math:`x` and demonstrate that :math:`P(x)` is true
for that :math:`x` (again, as you might expect).

**Exercise 1.8.** Prove the statement :math:`\exists x \in \mathbb{R}.\; 3x + 4
= 13` by finding a suitable value for :math:`x`.

The last thing we need to know in this section is how to negate statements that
contain quantifiers. Here goes:

* The negation of the statement :math:`\forall x. P(x)` is :math:`\exists x.
  \neg P(x)`.
* The negation of the statement :math:`\exists x. P(x)` is :math:`\forall x.
  \neg P(x)`.

This is all rather pleasingly symmetric, isn't it? Try to make sense of these
two rules if you can; they will be useful later. Hopefully if you think about
them for a bit you'll be able to persuade yourself intuitively why they are
true.

**Exercise 1.9.** Show that the statement :math:`\forall x \in \mathbb{R}.\;
x < x^2` is false by finding a *counterexample* — that is, a value of
:math:`x` such that :math:`x < x^2` does not hold. Do you see how we are using
the first of the above two rules for negating statements with quantifiers here?
