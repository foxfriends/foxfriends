# Function Piping

__Piping__ is similar to @[function composition][] in that the output of one function
is *piped* directly into the next as an input. The difference is that, while function
composition is a way of constructing a function without any reference to a particular
value, function piping is more immediate: it starts with a value, which is piped
through functions, to produce another value.

Piping is often used in @[shell][] scripting, to connect different programs together.
Piping is also often used in @[stream][] processing, to transform the values of the
stream before they are output elsewhere.

Some @[functional][functional-programming] @[programming languages][programming-language],
such as @[F#][f-sharp] and @[Elm][]. An example of a (hypothetical) hello world program
using such an operator is seen here

```
print ("World" |> prepend "Hello ")
```
