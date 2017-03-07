Exercise 5.6
============

Let :math:`f, g` be linear mappings. We consider the function :math:`f \circ
g`, defined as

.. math::
  f \circ g = \boldsymbol{x} \mapsto f(g(\boldsymbol{x}).

Firstly, we know that

.. math::
  f(g(\boldsymbol{x} + \boldsymbol{y})) = f(g(\boldsymbol{x}) + g(\boldsymbol{y}))
  
since :math:`g` is a linear mapping by assumption. Now we use the fact that
:math:`f` is a linear mapping to conclude that

.. math::
  f(g(\boldsymbol{x}) + g(\boldsymbol{y})) = f(g(\boldsymbol{x})) + f(g(\boldsymbol{y})).
  
We have therefore shown that :math:`(f \circ g)(\boldsymbol{x} +
\boldsymbol{y}) = (f \circ g)(\boldsymbol{x}) + (f \circ g)(\boldsymbol{y})`
and so we have established the first linear mapping law.

The second part of the proof is very similar: we show that :math:`f \circ g` is
compatible with scalar multiplication by first using the fact that :math:`g` is
compatible with scalar multiplication and then by using the fact that :math:`f`
is.
