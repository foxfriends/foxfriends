# Function Composition

__Function composition__ describes attaching two @[functions][] together to produce a
new function such that the result of calling the first is immediately passed to the
second, and the result of that is the final result of this new function.

Function composition is written using the `∘` symbol, and is formally defined as:  

$$
(f \circ g) (x) \equiv g(f(x))
$$

Fairly common in mathematics, function composition is also frequently used in
@[functional programming][].
