# Static typing

__Static typing__ is a kind of @[type system][] where the types are determined and
checked *statically* (i.e., before running the code, or at @[compile][compiler] time).
Languages with static types typically require some functions or variables to be declared
with type annotations specifying the type of variable, or use @[type inference][] to
determine the types of @[variables][] based on context.

Static typing forces the developer to think about the types of values on which a function
operates up front, and encode that into the program. Though this does require some effort,
in the long run I find that it tends to make programming easier, as the type checking
prevents simple bugs, such as calling functions with invalid values, and lead to
@[self-documentating code][].

Some examples of @[languages][programming-language] with static types include:
*   @[Rust][]
*   @[C++][]
*   @[Go][]

In languages which use static typing, there is often some way by which to switch to
@[dynamic types][dynamic-typing] for particular pieces of code, usually by using
some form of `Any` type with @[reflection][reflective-programming] capabilities.
