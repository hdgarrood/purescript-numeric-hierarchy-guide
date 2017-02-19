## 1: Logic

We will start with a quick discussion of logic. We will need this later on
because we will want to prove statements concerning things like rings and
fields.

You will probably be happy with the idea that statements such as "the sky is
blue" and "pigs can fly" can be assigned truth-values (i.e. "true" or "false").
There are also ways of combining statements to make new statements, which again
you are most likely familiar with already:

* If you have two statements $P$ and $Q$, you can make a new statement $P
  \text{ and } Q$, which is true if both $P$ and $Q$ are true. This is often
  written as $P \land Q$.
* Similarly, you can also make a new statement $P \text{ or } Q$, which is true
  if at least one of $P$ and $Q$ are true. This is often written as $P \lor Q$.

So for example, if we let the symbol $P$ represent the statement "the sky is
blue", and let the symbol $Q$ represent the statement "pigs can fly", the
statement $P \lor Q$ is true, because $P$ is true.

**Exercise 1.1.** Using the same assignment of the symbols $P$ and $Q$, what is
the truth-value of the statement $P \land Q$?

### Truth tables

We can describe the behaviour of logical operators like $\land$ and $\lor$
using things called *truth tables*. For example, here is the truth table for
logical and ($\land$):

| $P$ | $Q$ | $P \land Q$ |
| --- | --- | ----------- |
| T | T | T |
| T | F | F |
| F | T | F |
| F | F | F |

The table lists the four possible combinations of truth-values of $P$ and $Q$,
as well as the truth-value of $P \land Q$ in each case. If this isn't clear, it
might help to compare it to an implementation of $\land$ in PureScript:

    logicalAnd :: Boolean -> Boolean -> Boolean
    logicalAnd true true = true
    logicalAnd true false = false
    logicalAnd false true = false
    logicalAnd false false = false

**Exercise 1.2.** Write out the truth table for logical or, $\lor$.

### Logical equivalence

We say that two statements are *logically equivalent* if they are either both
true or both false. Here is a truth table for logical equivalence with some
entries missing:

| $P$ | $Q$ | $P \Leftrightarrow Q$ |
| --- | --- | --------------------- |
| T | T | T |
| T | F | F |
| F | T | ? |
| F | F | ? |

**Exercise 1.3.** Complete the missing entries of this truth table.

So for example, $P \land P$ is always logically equivalent to $P$, regardless
of the truth-value of $P$. We can express this in symbols by using a
double-ended arrow like this: $P \land P \Leftrightarrow P$.

### Logical negation

Another thing we can do with statements is *negate* them: make a new statement
which is true if the original statement is false, and false if the original
statement is true. If $P$ is a statement, then the logical negation of $P$ is
written as $\neg P$.

**Exercise 1.4.** Persuade yourself that $\neg (P \lor Q)$ is always logically
equivalent to $\neg P \land \neg Q$, regardless of the truth-values of $P$ and
$Q$. One way to do this is to write out a truth table.

Similarly, $\neg (P \land Q)$ is always logically equivalent to $\neg P \lor
\neg Q$. These two equivalences are called *De Morgan's laws*.

### Logical implication

We now consider statements of the form "if $P$, then $Q$". This way of
connecting logical statements is called *logical implication.* Another way of
saying the same thing is "$P$ *implies* $Q$". The symbol for logical
implication is an arrow: we can write the above statement as "$P \Rightarrow
Q$".

$P \Rightarrow Q$ is a logical statement just like all of the others we have
seen, and therefore it has a truth-value which depends on the truth-values of
$P$ and $Q$. Here is the truth table for logical implication:

| $P$ | $Q$ | $P \Rightarrow Q$ |
| --- | --- | ----------------- |
| T | T | T |
| T | F | F |
| F | T | T |
| F | F | T |

This might not match up exactly with your intuition: specifically, you might
expect $P \Rightarrow Q$ to be false if $P$ is false. If this bothers you, try
not to worry about it too much. We will later see that this it is convenient to
define logical implication in this way.

**Exercise 1.5.** Persuade yourself, by using a truth table (or any other
method that works for you), that $P \Rightarrow Q$ is always logically
equivalent to $\neg P \lor Q$ regardless of the truth-values of $P$ and $Q$.

Another way of thinking of logical equivalence is in terms of logical
implication. Specifically, an alternative way of defining $\Leftrightarrow$ is
by saying that $P \Leftrightarrow Q$ is the same as this bad boy:

$$(P \Rightarrow Q) \land (Q \Rightarrow P)$$

In fact, the standard way of proving a statement of the form $P \Leftrightarrow
Q$ is to first prove $P \Rightarrow Q$ and then to prove $Q \Rightarrow P$.

### Quantifiers

Up to now, the symbols $P$ and $Q$ have always represented statements. However
we can also use symbols to represent *predicates*, which are like functions
which return statements. For example, we might have a predicate "$x$ is even",
"$x$ is divisible by 6", or "$x$ is prime".

If we let $P(x)$ represent the predicate "$x$ is even", then we can
write the statement "2 is even" as $P(2)$. Similarly we can
write the statement "3 is even" as $P(3)$. In each case we get a statement
whose truth-value can depend on the specific value of $x$ which was chosen
&mdash; in this case, the first statement is true but the second is false.

If we have a predicate, we can make statements about the truth-values of a
predicate over all the possible values it can take as arguments by using things
called *quantifiers*.

The first quantifier we will introduce is called "for all", written as an
upside-down capital letter A like this: $\forall$. Here is how we write the
statement "for all $x$, the square of $x$ is greater than or equal to 0" using
the $\forall$ quantifier:

$$\forall x. x^2 \geq 0$$

There are lots of various things that can be squared, so in this case it's
preferable to be a bit more explicit about what values $x$ can take. In this
case we want $x$ to be a *real number,* which is the kind of number you're
probably most used to. $0, 1, 37, \frac{1}{2}$, and $\pi$ are all examples of
real numbers. The way we write "$x$ is a real number" in mathematical notation
is "$x \in \mathbb{R}$". The symbol $\in$ can be read "is an element of". A
better way of writing the above is therefore:

$$\forall x \in \mathbb{R}. x^2 \geq 0$$

The other quantifier we will use is written as a back-to-front capital letter
E, like this: $\exists$, and can be read as "there exists". Here is how we
would write the statement "there exists a real number whose square is 4" in mathematical notation:

$$\exists x \in \mathbb{R}. x^2 = 4$$

There are two possible values of $x$ which you can use as examples to show that
this statement is true: $2$ and $-2$. In fact, the standard way of proving
a statement of the form $\exists x. P(x)$ is to pick a specific value of $x$
and demonstrate that $P(x)$ is true for that $x$.

**Exercise 1.6.** Prove the statement $\exists x \in \mathbb{R}. 3x + 4 = 13$
by finding a suitable value for $x$.

The last thing we need to know in this section is how to negate statements that
contain quantifiers. Here goes:

* The negation of the statement $\forall x. P(x)$ is $\exists x. \neg P(x)$.
* The negation of the statement $\exists x. P(x)$ is $\forall x. \neg P(x)$.

This is all rather pleasingly symmetric, isn't it? Try to make sense of these
two rules if you can; they will be useful later. Hopefully if you think about
them for a bit you'll be able to persuade yourself intuitively why they are
true.

**Exercise 1.7.** Show that the statement $\forall x \in \mathbb{R}.
x < x^2$ is false by finding a *counterexample* &mdash; that is, a value of $x$
such that $x < x^2$ does not hold. Do you see how we are using the first of the
above two rules for negating statements with quantifiers here?
