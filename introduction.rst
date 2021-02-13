Introduction
============

Welcome! This guide aims to give you an introduction to the mathematics behind
the numeric hierarchy of type classes in PureScript's Prelude, and it's aimed
at people who haven't (necessarily) studied mathematics beyond a high-school
level.

Why?
----

Normally, algebraic structures like rings or fields are only introduced to
students at undergraduate level. One unfortunate side-effect of this is that
lots of the material currently available on the web which describes these
concepts is sometimes a little inaccessible for people who haven't studied
mathematics past a high-school level. My aim with this guide is to help people
develop intuition for what these structures are and how they can be used, so
that that knowledge can be applied in PureScript code. I also hope that I can
help you see a glimpse of the beauty of mathematics and convince you that it is
worth studying in its own right.

I want to stress that it is *not* necessary to read and understand all of this
in order to be able to use the PureScript type classes like ``Ring`` or
``Field``, and to be able to write functions which work for any type which has
a ``Ring`` or ``Field`` instance. However, I do hope that it will help you
answer questions such as:

* "I want to write a function which works for many different numeric
  types, but should I give it a ``Semiring`` constraint, or a ``Ring``
  constraint, or something else entirely?"
* "I have written a function with a ``Field`` constraint, and I want to find an
  appropriate concrete type which is a ``Field`` to test it with. How do I do
  that?"
* "What's the point in all of this maths mumbo-jumbo anyway — what's wrong with
  plain old Haskell-style ``Num``?"

Prerequisites
-------------

I will try to assume as little knowledge of mathematics as I can. If I
accidentally assume knowledge of something which makes you unable to understand
a part of this guide, please let me know by `opening an issue on
GitHub <https://github.com/hdgarrood/purescript-numeric-hierarchy-guide>`_ or
emailing me at harry@garrood.me.

Although this guide is primarily aimed at PureScript users, I will only
reference PureScript infrequently for the purpose of illustrating examples.
This guide is really about mathematics, not PureScript.

Therefore, as far as is reasonably possible, I am also interested in making
this guide accessible to programmers using other languages or libraries which
make use of these same abstractions (rings, fields, etc). If you fit into this
category, and you are unable to follow something I've written because it
requires more than a very basic level of PureScript knowledge, please feel free
to file an issue.

How to read this guide
----------------------

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
skip it or simply look at the solution (although if you find yourself needing
to skip lots of exercises, perhaps consider going back and rereading some
earlier bits). Another good idea if you get stuck is to do something else and
come back to the problem the following day — of course, if you're a programmer,
you might already know this.

One more thing I will say is that you shouldn't expect to be able to read this
sort of material anywhere nearly as quickly as you might read most other types
of non-fiction prose. Mathematical writing is usually extremely dense — I don't
mean this as a criticism of the writing style of mathematicians, but rather to
help avoid unrealistic expectations. In fact I think this density is a mostly
unavoidable consequence of the nature of mathematics. Don't be put off if it
takes you a long time to get through this!

License
-------

.. image:: https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png
   :target: https://creativecommons.org/licenses/by-nc-sa/4.0/

This work is licensed under a `Creative Commons
Attribution-NonCommercial-ShareAlike 4.0 International License
<https://creativecommons.org/licenses/by-nc-sa/4.0/>`_.

This means you are free to copy and redistribute it as well as make changes,
but you must give credit, link to the license, and indicate if changes were
made. The license also forbids commercial use.

Note that the work is not necessarily exclusively licensed under CC BY-NC-SA
4.0. In particular, if you're worried about whether your use of it counts as a
commercial use please contact me and we'll probably be able to sort something
out.
