# String Escaping

__Escaping__ is a technique used to encode arbitrary text unambiguously into a @[string][strings]
following certain restrictions. This is often performed by defining a character to use
as the *escape character* (commonly `\`) which, when encountered in the string, indiciates
that the following character should be interpreted specially.

For example, in order to encode a line break into a string literal in a @[language][programming-language] that
does not support multi-line string literals, we commonly use the escape sequence `\n`
to represent the newline (e.g. `hello\nworld"`. Now, in order to literally include the
backslash followed by an `n` in a string, it becomes necessary to instead escape the
escape character, becoming `\\n`. Similarly, to include a literal quotation mark
(`"`) in a string that is to be enclosed by such quotation marks, `\"` can be used
(e.g. `"\""`).
