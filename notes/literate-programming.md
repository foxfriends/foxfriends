# Literate Programming

__Literate programming__ is a @[programming paradigm][] for writing source code and
@[documentation][code-documentation] intertwined while *prioritizing the documentation*.
In particular, literate programming tools often make it possible to write the code
out of order so that it more closely follows the human thought process than the
execution order.

Literate programming was created by @[Donald Knuth][]. He calls the conversion of a literate
program to source code "tangling", while compiling that literate program to a readable document
is "weaving".

@[Haskell][]'s GHC compiler provides literate programming support built in, but literate
programming can be used with any @[programming language][] by using a preprocessor.

I built my own literate programming preprocessor [Outline][], which I think works ok
and was eventually forked and expanded into [Yarner][].

[Outline]: https://github.com/foxfriends/outline
[Yarner]: https://github.com/mlange-42/yarner
