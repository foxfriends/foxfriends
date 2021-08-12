# Opaque Data

As opposed to @[transparent][transparent-data], an __opaque data__ value is one
for which the internal representation is not known to the holder of that data.
Typically this is done to better encapsulate data that should not be relied on,
to reduce @[coupling][].

When opaque data is encountered, typically it is expected only to be passed back
to wherever it came from, unchanged and uninterpreted. External code should never
attempt to determine meaning from opaque data.

Opaque data often comes in the form of a @[string][] for which the format specification
is not disclosed. In @[statically typed][static-typing] @[languages][programming-language],
@[structures][data-structure] made up of @[private fields][visibility] are a form of
opaque data.
