# Lists

There are many different ways of storing *ordered* lists of data in a program, each with their own
tradeoffs in terms of performance and usability. Many @[programming languages][programming-language]
come with at least some of the following @[data structures][] built in to solve the problem
of storing lists:
*   @[Arrays][]
*   @[Vectors][]
*   @[Double-ended vectors][]
*   @[Linked lists][]
*   @[Doubly linked lists][]

Some common operations that are taken on lists are insertion, deletion, and indexed-access, each
of which can be done at the front, at the back, or at an arbitrary index in the list, often with
different performance characteristics which may influence your choice of list implementation for
a particular usage. Other common tasks include @[sorting][], @[searching][], or @[iterating][iterator]
the list.

Similar to lists in that they can store multiple points of data are @[sets][] and @[dictionaries][],
but they are not lists as they do not support the same operations.
