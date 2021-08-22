# Arrays

Arrays, available in pretty much every @[programming language][], are generally the most
primitive way of storing a @[list][lists] of data.

In high-level languages (such as @[Javascript][]), what is referred to as an "array" is often
more of a @[vector][vectors] than what I would considered to be an array by the definition below.
What I do consider to be an array is what might be referred to as an array in a lower-level
language such as @[C][] or @[Rust][], or even mid-level languages like @[Java][] or @[Haskell][].

In particular, arrays tend to be implemented such that in the actual @[memory][computer-memory]
layout of the data each entry of the array is stored directly following the previous entry.
This makes arrays very efficient for indexed access, as the memory address of any item can be
found immediately given the equation $\text{Address} = \text{Base} + \text{Size} \times \text{Index}$,
where $\text{Base}$ is the address of the first item in the array, $\text{Size}$ is the size of
each entry, and $\text{Index}$ is the index of the item in question (starting from 0).
It is due to this relation that, in most languages, the items in the array are 0-indexed, such
that what you might naturally call the "first" element of the array is actually the "zeroeth".

Additionally arrays are typically implemented in a way that they are fixed-length and not
resizeable. This is due to the high cost of reallocating and moving the data stored in an
array. Since the array is often the most primitive form of list, when such features are
required it is best to just use a higher-level @[abstraction][] anyway.

Due to the fixed-lengthedness of arrays, some of the usual list operations, namely insertion
and deletion, do not really exist as they might on other types of lists. Since no entry of an
array may ever be empty, and an array cannot be resized, items cannot be deleted or inserted,
only replaced.
