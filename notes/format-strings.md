# Format Strings

A format string is a @[string][strings] that is describes a format into which other
values will be inserted, allowing for a more natural syntax by which strings can
be composed than a bunch of concatenations. This is often implemented as a @[function][]
that takes as parameters the format string and the values to insert into that format.

Some examples from different @[languages][programming-language] to create the string
"Hello World" when the value of "World" is stored in a @[variable][variables] `name`:
*   @[Rust][]: `format!("Hello {}", name)`
*   @[C][]: `sprintf("Hello %s", name)` (**print** **f**ormatted to **s**tring)
*   @[Bash][]: `printf 'Hello %s' $name`

Related is @[string interpolation][], which solves the same problem in a different way.
