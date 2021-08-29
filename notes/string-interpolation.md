# String Interpolation

String interpolation is a feature of some @[programming languages][programming-language]
that makes it easy to compose @[strings][] out of other values using a more 
fluent looking syntax than a bunch of concatenations.

Often this is by using a special sequence of characters within a string quoted a certain
way.

Some examples, to create the string "Hello World", where the text "World" is stored in a
@[variable][variables] `name`:
*   @[Javascript][]: `` `Hello ${name}` ``
*   @[Ruby][]: `"Hello #{name}"`
*   @[Swift][]: `"Hello \(name)"`

Related are @[format strings][], which solve the same problem in a different way.
