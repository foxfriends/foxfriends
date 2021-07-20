# Pure Functions

A __pure function__ is a @[function][] which performs no side effects, and whose
return value is determined entirely based on its input parameters and nothing else.

In general (and in @[functional programming][] especially), we prefer to write pure
functions whenever possible, as they are easier to reason about, understand and
maintain, while also lending themselves better to @[optimization][].
