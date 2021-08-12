# Cursor (Pagination)

A __cursor__ for @[pagination][] is an @[opaque value][opaque-data] (typically a
@[string][]) which is included in the pagination response, and is expected to be
included in the next pagination request, allowing the server to pick up where it
left off and return the next page to the user.

Sometimes the cursor is as simple as the number of items already loaded, while
other times the cursor may be some ordered identifier of the data (such as a
date) or even a more complex string that stores some data from which the server
can reconstruct a larger amount of state.
