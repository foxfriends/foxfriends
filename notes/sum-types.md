# Sum Types

__Sum types__ are a types which may take one of many forms, typically expressed
as different constructors for that type. Sum types work well with @[pattern matching][]
to write code that branches based on a fixed number of different options.
Types such as the @[option type][] and @[result type][] are examples of sum types.

@[Statically typed][static-typing] @[functional][functional-programming] languages
such as @[Haskell][] often make great use of sum types for most branching operations.

In @[languages][programming-language] such as @[Rust][] or @[Swift][] they are created
using the `enum` keyword, as they have some similarity to the @[enumerations][] found
in languages such as @[C][]. Note that an enumeration is not the same as a sum type,
despite this reuse of name---the sum type *could* be considered a generalization of
enumerations.

More classically @[imperative][] languages, such as the previously mentioned C,
@[C++][cplusplus], or @[Java][], tend not to have sum types, and instead have only the
less easy-to-use @[union types][].
