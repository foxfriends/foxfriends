# Pagination

When designing web @[APIs][application-programming-interface], __pagination__ refers to
returning lists of data in chunks or "pages", rather than always returning the full list
of all data. Often, if loaded all at once, there may be thousands or millions of items
in the list which are just not feasible to send over the Internet all at once.

Depending on the type of API being created (@[REST][representational-state-transfer]
or @[GraphQL][] or whatever), there are different strategies for this, but in general
they all include:
*   A way of specifying how large the pages should be (`limit`)
*   A way of specifying which page to load (`offset`, `page`, or @[`cursor`][pagination-cursor])
*   A way of determining how many total items (or total pages) there are
*   A way of determining if there is a next/previous page.
