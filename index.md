## Contents

1. Introduction (you are here!)
2. [Logic](./logic/)
3. [Groups](./groups/)

## Introduction

This is the first in what I hope will eventually be a series of posts giving an
introduction to the mathematics behind the numeric hierarchy of type classes in
PureScript's Prelude, aimed at people who haven't studied mathematics beyond
a high-school level.

Normally, algebraic structures like rings or fields are only introduced to
students at undergraduate level. One unfortunate side-effect of this is that
lots of the material currently available on the web which describes these
concepts isn't very accessible to people who haven't studied mathematics past a
high-school level. My aim with these posts is to help people develop intuition
for what these structures are and how they can be used so that that knowledge
can be applied in PureScript code. I also hope that I can help persuade you of
the beauty of mathematics and convince you that it is worth studying in its own
right.

I want to stress that it is *not* necessary to read and understand all of this
in order to be able to use the PureScript type classes like `Ring` or `Field`,
and to be able to write functions which work for any type which has a `Ring` or
`Field` instance. However, I do hope that it will help you answer questions
such as:

* "I want to write a function which works for many different numeric
  types, but should I give it a `Semiring` constraint, or a `Ring` constraint,
  or something else entirely?
* "I have written a function with a `Field` constraint, and I want to find an
  appropriate concrete type which is a `Field` to test it with. How do I do
  that?"

I will provide exercises throughout. Whenever you encounter an exercise, I
strongly recommend you attempt it before reading on! I speak from experience as
a maths student: in my personal experience, it's simply not possible to reach
the same level of understanding without having worked through problems myself.

I should note that I often find it extremely tempting to skip to the solution,
read through it, and tell myself "yes, I could have done that." Be careful of
this! It's very easy for me to persuade myself that I could have solved a
problem when in fact I probably wouldn't have been able to. But also it's okay
to look at the solution if you're really stuck; *attempting* the problem first
is the most important thing.

If you get stuck on an exercise for more than, say, 10 minutes, it's okay to
skip it (although if you find yourself needing to skip lots of exercises,
perhaps consider going back and rereading some earlier bits). Another good idea
if you get stuck is to do something else and come back to the problem the
following day &mdash; of course, if you're a programmer, you might already know
this.

One more thing I will say is that you shouldn't expect to be able to read this
sort of material anywhere nearly as quickly as you might read most other types
of non-fiction prose. Mathematical writing is usually extremely dense &mdash;
I don't mean this as a criticism of the writing style of mathematicians, but
rather to help avoid unrealistic expectations. In fact I think this density is
a mostly unavoidable consequence of the nature of mathematics. Don't be put off
if it takes you a long time to get through this!
