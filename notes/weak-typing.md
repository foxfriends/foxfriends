# Weak typing

A __weakly typed__ @[programming language][] is one where satisfying te @[type system][] is
more as a suggestion than as a requirement. When the type system does not provide a proper way
to express something, there are ways that it can be put aside and the values acted on directly.
Often, in those cases, more important than the logical "type" that the value has is the way
that value is represented.

Notably weakly typed is @[C][] (and, by extension, @[C++][cplusplus] also). By passing through
`void*`, values in C can be changed at any time. Other low-level languages, such as (unsafe)
@[Rust][] also provide means by which to reinterpret types (e.g. `std::mem::transmute`), but
with more safeguards in place. @[TypeScript][]'s type system could also be considered weak,
as the `any` type can allow the developer to change any type to any other, but the @[runtime][]
of the language (the @[Javascript][] runtime) is @[dynamically typed][dynamic-typing] but not
weakly typed.
